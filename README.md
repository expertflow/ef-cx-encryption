# EF-CX-Encryption

## Overview

This is a Spring Boot dependency that provides seamless integration with Spring Cloud Vault and MongoDB Interceptor for encrypting data at rest. Simply add this dependency to your Spring Boot application, and it will automatically configure everything without requiring additional setup.

## Features

- Seamless Vault Integration – Uses Spring Cloud Vault for communicating with Vault.

- MongoDB Interceptor – Automatically encrypts and decrypts fields in MongoDB.

- Zero Configuration – Just add the dependency, and it's ready to use.

- Plug & Play – No need to define beans manually.

## How to use
1. Import the library in the pom.xml of your application.
```
<dependency>
    <groupId>io.github.expertflow</groupId>
    <artifactId>ef-cx-encryption</artifactId>
    <version>1.0.2</version>
</dependency>
```
2. Add the following properties in the application.properties or application-prod.properties file.
```
# configure access to Vault
spring.cloud.vault.uri=${VAULT_URI}
spring.cloud.vault.authentication=approle
spring.cloud.vault.app-role.role-id=${VAULT_ROLE_ID}
spring.cloud.vault.app-role.secret-id=${VAULT_SECRET_ID}
spring.cloud.vault.ssl.trust-store=file:./vault_truststore.p12
spring.cloud.vault.ssl.trust-store-password=${TRUST_STORE_PASSWORD}
spring.cloud.vault.ssl.trust-store-type=pkcs12
spring.cloud.vault.ssl.key-store=file:./vault_keystore.p12
spring.cloud.vault.ssl.key-store-password=${KEY_STORE_PASSWORD}
spring.cloud.vault.ssl.key-store-type=pkcs12

# configure path to Vault transit secrets engine
transit.path=${VAULT_TRANSIT_PATH}
transit.key=${VAULT_TRANSIT_KEY}
transit.encryption-schema=${ENCRYPTION_SCHEMA_PATH}

# enable or disable encryption at rest
ef.enable-encryption=${ENABLE_ENCRYPTION}
```

## Requirements
- Java 17+
- Spring Boot 3.x
