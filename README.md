# preMercado SAP — Pre-Registration

This repository pre-registers the Statistical Analysis Plan (SAP) for the
preMercado growth engine, fixed before any campaign data was collected.

- engine-sap-preregistration-v0.8.md — the pre-registered analysis plan.
- engine-sap-preregistration-v0_8_md.tsr — an RFC-3161 trusted timestamp
  (FreeTSA) over that exact file, proving its content existed at the
  signed UTC time, independent of GitHub and of the author.

Registered: 28 May 2026. The authoritative time is inside the .tsr token.

## Verify (desktop, OpenSSL)
curl -o tsa.crt    https://freetsa.org/files/tsa.crt
curl -o cacert.pem https://freetsa.org/files/cacert.pem

openssl ts -verify -data engine-sap-preregistration-v0.8.md \
  -in engine-sap-preregistration-v0_8_md.tsr \
  -CAfile cacert.pem -untrusted tsa.crt
# -> Verification: OK

openssl ts -reply -in engine-sap-preregistration-v0_8_md.tsr -text | grep -i "Time stamp"
