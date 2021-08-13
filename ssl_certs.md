### SSL Cert: certificate verifies identity and public key of a webserver, issued by a 3d party.
### CA: certificate authority

## 2 types of CAs:
1. root CAs
2. intermediate CAs
  
## rules:
  - if cert changes, must be revoked

## concepts:
  - certificate transparency: logs kept of what domains have been registered on certs 

## High-overview steps
1. client requests page through https ->  
2. server responds with public key + ssl cert -> client verifies if digital signature is valid -> 
3. client generates shared secret key (uses server's pubkey to encrypt it); server decrypts encrypted private key with its own private key

## random facts:
  - typically lasts for 3 years, depending on ca
  - group called CA Browser Forum: handles cert legal, admin, etc

## certificate chains:
  - end-user certificate: cert you get for hosting server with ssl
  - to be trusted, cert must be issued by CA included in the trust store of client 
    - client can check if cert of the issuing CA was issued by a CA included in trust store
    - ie. to see if MyCert is trusty, check if issuer's CertA was issued by TrustedCA, ad infinitum
      - in this case, MyCert is End User cert, CertA is intermediate CA's cert (issued by TrustedCA, who is Root CA)

## Problems:
1. Bygone SSL:
  - Multiple people can own certs for same domain - man in the middle potential
  - add Subject Alt Names to cert to have it cover multiple domains (not just subdomains)
  - eg. Per A has multiple domains: example.com + test.com
    - they have 1 cert to cover both
    - they release test.com - domain is available again (but is still added to cert)
    - Per B buys test.com, registers a new cert for it
    - Per A can have clients visit malicious site pretending to be test.com
