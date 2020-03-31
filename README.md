Start Keycloak
/c/app/keycloak-9.0.2/bin/standalone.sh -Djboss.socket.binding.port-offset=100

Keycloak Setup
realm-id : spring-boot-keycloak-realm
client-id : spring-boot-keycloak-client
Access Type : confidential
Implicit Flow Enabled : ON
Service Accounts Enabled : ON

Access Token Endpoint
POST : http://localhost:8180/auth/realms/spring-boot-keycloak-realm/protocol/openid-connect/token
Content-Type : application/x-www-form-urlencoded
grant_type : client_credentials
client_id : spring-boot-keycloak-client
client_secret : 248ba185-7041-44e7-a6bc-6cd6091921ee

Refresh Token Endpoint
POST : http://localhost:8180/auth/realms/spring-boot-keycloak-realm/protocol/openid-connect/token
Content-Type : application/x-www-form-urlencoded
grant_type : refresh_token
client_id : spring-boot-keycloak-client
client_secret : 248ba185-7041-44e7-a6bc-6cd6091921ee
refresh_token : ${access_token}

Introspect Token
POST : http://localhost:8180/auth/realms/spring-boot-keycloak-realm/protocol/openid-connect/token/introspect
Content-Type : application/x-www-form-urlencoded
client_id : spring-boot-keycloak-client
client_secret : 248ba185-7041-44e7-a6bc-6cd6091921ee
token : ${access_token}

Using Authorization
GET : http://localhost:8080/ping
Authorization : Bearer ${access_token}
