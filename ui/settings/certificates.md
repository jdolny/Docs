# Certificates

Certificates are used to generate and export the Toems CA and Intermediate certs. These certificates are used as part of the communication process b/w Toec and Toems to verify identities and encrypt data.

#### Actions
Action | Description
------|------------
Generate Certificates | Creates the needed certificates for Theopenem.  Organization Name must be filled out in Admin Settings->Server before certificates can be generated.


> [!CAUTION]
> After the certificates are generated they should not be changed if Toec has already been deployed.  Otherwise, all communication with the endpoints will break until Toec is reinstalled.