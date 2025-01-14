
---
sidebar_position: 1
---
# Single Sign-On (SSO) Configuration

Stirling PDF allows login via Single Sign-On (SSO) using OAUTH2 OpenID Connect (OIDC)
These are
- ``oauth2.enabled`` Set this to 'true' to enable login (Note: ``enableLogin`` must also be 'true' for this to work)
- ``oauth2.issuer`` Set this to any provider that supports OpenID Connect Discovery ``/.well-known/openid-configuration`` end-point
- ``oauth2.clientId`` Client ID from your provider
- ``oauth2.clientSecret`` Client Secret from your provider
- ``oauth2.autoCreateUser`` Set this to 'true' to allow auto-creation of non-existing users

After the OAUTH2 login is enabled, a new button shows up on the login page as per the screenshot below:

![image](https://github.com/sahilph/Stirling-Tools.github.io/assets/812110/b0a84120-e8bb-4ea2-ac9e-4ec37520f7af)


## Settings file
```
security:
  enableLogin: true # set to 'true' to enable login
  ...
  ...
  oauth2:
    enabled: false # set to 'true' to enable SSO login (Note: enableLogin must also be 'true' for this to work)
    issuer: "" # set to any provider that supports OpenID Connect Discovery (/.well-known/openid-configuration) end-point
    clientId: "" # Client ID from your provider
    clientSecret: "" # Client Secret from your provider
    autoCreateUser: false # set to 'true' to allow auto-creation of non-existing users
```

## Local 
If running Java directly, you can set these via environment variables by running before starting the application
```
export DOCKER_ENABLE_SECURITY=true
export SECURITY_ENABLELOGIN=true
export SECURITY_OAUTH2_ENABLED=true
export SECURITY_OAUTH2_AUTOCREATEUSER=false
export SECURITY_OAUTH2_ISSUER="<issuer-url>"
export SECURITY_OAUTH2_CLIENTID="<client-id>"
export SECURITY_OAUTH2_CLIENTSECRET="<client-secret>"
```

## Docker

### Docker run
```
-e  DOCKER_ENABLE_SECURITY=true \
-e  SECURITY_ENABLELOGIN=true \
-e  SECURITY_OAUTH2_ENABLED=true \
-e  SECURITY_OAUTH2_AUTOCREATEUSER=false \
-e  SECURITY_OAUTH2_ISSUER="<issuer-url>" \
-e  SECURITY_OAUTH2_CLIENTID="<client-id>" \
-e  SECURITY_OAUTH2_CLIENTSECRET="<client-secret>" \
```

### Docker Compose
```
environment:
  DOCKER_ENABLE_SECURITY: true
  SECURITY_ENABLELOGIN: true
  SECURITY_OAUTH2_ENABLED: true
  SECURITY_OAUTH2_AUTOCREATEUSER: false
  SECURITY_OAUTH2_ISSUER: "<issuer-url>"
  SECURITY_OAUTH2_CLIENTID: "<client-id>"
  SECURITY_OAUTH2_CLIENTSECRET: "<client-secret>"
```
