# Keycloak SHA-1

A minimal fork of Keycloak BCrypt to support passwords hashed with SHA-1 (rather than BCrypt)

Add a password hash provider to handle SHA-1 passwords inside Keycloak.

## Build JAR

```bash
./gradlew assemble -Pdependency.keycloak.version=${KEYCLOAK_VERSION}
```

## Build Docker image

```bash
cp build/libs/keycloak-sha1-${KEYCLOAK_SHA1_VERSION}.jar docker
docker build \
    --build-arg keycloak_version=${KEYCLOAK_VERSION} \
    --build-arg keycloak_sha1_version=${KEYCLOAK_SHA1_VERSION} \
    -t jcschaff/keycloak-sha1 \
    docker
```

## Test with docker-compose

```bash
docker-compose up -d
```

## Install

### >= 17.0.0

```bash
curl -L https://github.com/jcschaff/keycloak-sha1/releases/download/${KEYCLOAK_SHA1_VERSION}/keycloak-sha1-${KEYCLOAK_SHA1_VERSION}.jar > ${KEYCLOAK_HOME}/providers/keycloak-sha1-${KEYCLOAK_SHA1_VERSION}.jar
```
You need to restart Keycloak.

### < 17.0.0

```bash
curl -L https://github.com/jcschaff/keycloak-sha1/releases/download/${KEYCLOAK_SHA1_VERSION}/keycloak-sha1-${KEYCLOAK_SHA1_VERSION}.jar > ${KEYCLOAK_HOME}/standalone/deployments/keycloak-sha1-${KEYCLOAK_SHA1
_VERSION}.jar
```
You need to restart Keycloak.

## Run with Docker

```bash
docker run \
    -e KEYCLOAK_ADMIN=${KEYCLOAK_ADMIN} \
    -e KEYCLOAK_ADMIN_PASSWORD=${KEYCLOAK_ADMIN_PASSWORD} \
    -e KC_HOSTNAME=${KC_HOSTNAME} \
    gleroy/keycloak-sha1 \
    start
```

The image is based on [Keycloak official](https://quay.io/repository/keycloak/keycloak) one.

## How to use
Go to `Authentication` / `Password policy` and add hashing algorithm policy with value `sha1`.

To test if installation works, create new user and set its credentials.
