FROM keycloak/keycloak:24.0.0 as builder

# Habilitar características específicas y base de datos
ENV KC_HEALTH_ENABLED=true
ENV KC_METRICS_ENABLED=true
ENV KC_DB=postgres

WORKDIR /opt/keycloak
# Aquí es donde se construye la imagen optimizada
RUN /opt/keycloak/bin/kc.sh build

FROM keycloak/keycloak:24.0.0
COPY --from=builder /opt/keycloak/ /opt/keycloak/

# Configurar variables de entorno para UTF-8
ENV LANG=C.UTF-8
ENV LC_ALL=C.UTF-8

ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]