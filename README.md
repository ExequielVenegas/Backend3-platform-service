# Platform Service

Reúne Config Server y Eureka en una sola aplicación Spring Boot.

| Parte | Uso |
|---|---|
| Config Server | Entrega propiedades centralizadas a Account y Web |
| Eureka | Registra instancias y permite que Web descubra Account |

Puerto interno 8761. No publicado a Windows. Pertenece a la red backend.
Auth arranca de forma independiente para evitar dependencias circulares.

## Configuración

Usa el perfil native y lee config-repo montado en /config como solo lectura.
Los archivos se versionan junto al proyecto; no hay un repositorio Git remoto
consultado automáticamente. No guardar secretos en esa carpeta.
CONFIG_REPO_LOCATION permite cambiar su ubicación.
Eureka no se registra a sí mismo ni busca otro servidor.

Las aplicaciones registradas deben aparecer UP. Web y Account confirman
config-server como origen en /actuator/info.