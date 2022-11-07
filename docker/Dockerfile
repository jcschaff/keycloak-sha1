ARG keycloak_version=19.0.0

FROM quay.io/keycloak/keycloak:${keycloak_version}

ARG keycloak_sha1_version=0.9.0

EXPOSE 8080

COPY ./keycloak-sha1-${keycloak_sha1_version}.jar /opt/keycloak/providers/