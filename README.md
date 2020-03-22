Start Keycloak
/c/app/keycloak-9.0.0/bin/standalone.sh -Djboss.socket.binding.port-offset=100

Keycloak Setup
client-id : spring-boot-keycloak-client
Access Type : confidential
Service Accounts Enabled : ON

Access Token Endpoint
POST : http://localhost:8180/auth/realms/spring-boot-keycloak-realm/protocol/openid-connect/token
Content-Type : application/x-www-form-urlencoded
grant_type : client_credentials
client_id : spring-boot-keycloak-client
client_secret : e4d11ad9-a35d-44af-9274-3ff9f6f6e969

Refresh Token Endpoint
POST : http://localhost:8180/auth/realms/spring-boot-keycloak-realm/protocol/openid-connect/token
Content-Type : application/x-www-form-urlencoded
grant_type : refresh_token
client_id : spring-boot-keycloak-client
client_secret : e4d11ad9-a35d-44af-9274-3ff9f6f6e969
refresh_token : ${access_token}

Introspect Token
POST : http://localhost:8180/auth/realms/spring-boot-keycloak-realm/protocol/openid-connect/token/introspect
Content-Type : application/x-www-form-urlencoded
client_id : spring-boot-keycloak-client
client_secret : e4d11ad9-a35d-44af-9274-3ff9f6f6e969
token : ${access_token}

Using Authorization
GET : http://localhost:8080/ping
Authorization : Bearer ${access_token}
