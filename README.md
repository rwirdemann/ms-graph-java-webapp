# Java Webapp zur Nutzung der Microsoft Graph-API  

## Microsoft Authentication Library for Java (MSAL4J)

Die Anwendung nutzt die Microsoft Authentication Library for Java

- Anfragen eines Id Token für den Benutzer-Login
- Anfragen eines Access Token zur Durchführung von API-Requests

## Setup
1. Anwendung unter [Azure portal](https://portal.azure.com) registrieren
1. Redirect URLs hinterlegen:
    - `https://localhost:8443/msal4jsample/secure/aad`.
    - `https://localhost:8443/msal4jsample/graph/me`
1. Client Secret anlegen
1. application.properties mit den Daten aus der registrierten App anpassen

```
# src/main/resources/application.properties
aad.clientId=<CLIENT_ID>
aad.authority=https://login.microsoftonline.com/<TENANT_ID>>/
aad.secretKey=<CLIENT_SECRET>
aad.redirectUriSignin=https://localhost:8443/msal4jsample/secure/aad
aad.redirectUriGraph=https://localhost:8443/msal4jsample/graph/me
aad.msGraphEndpointHost=https://graph.microsoft.com/
```

## HTTPs für localhost konfigurieren
```
Beispiel:  
keytool -genkeypair -alias testCert -keyalg RSA -storetype PKCS12 -keystore keystore.p12 -storepass password

# src/main/resources/application.properties
server.ssl.key-store-type=PKCS12
server.ssl.key-store=classpath:keystore.p12
server.ssl.key-store-password=password
server.ssl.key-alias=testCert
```

## Credits

Der Code dieser Anwendung basiert auf dem Repository [GitHub](https://github.com/Azure-Samples/ms-identity-java-webapp).

Weitere Information zu OAuth2 im Microsoft-Kontext findet ihr hier [Authentication Scenarios for Azure AD](http://go.microsoft.com/fwlink/?LinkId=394414).
