# Página web con integración continua

Proyecto académico de una página web estática publicada automáticamente en
Surge mediante GitHub Actions.

## Flujo de integración continua

Cada `push` a la rama `main` ejecuta el workflow
`.github/workflows/main.yaml`. El workflow instala la CLI de Surge y publica
el contenido del repositorio.

## Secretos requeridos en GitHub

En el repositorio, abrir **Settings > Secrets and variables > Actions** y crear:

- `SURGE_TOKEN`: token privado obtenido con `surge token`.

El token no se guarda en el código ni en el historial de Git. El dominio público
del proyecto es `pagina-ci-osenrey.surge.sh` y se conserva también en `CNAME`.

## Prueba local

La página no requiere dependencias. Puede abrirse `index.html` directamente en
el navegador o servirse con cualquier servidor estático.

## Publicación manual opcional

Con Node.js y Surge instalados:

```bash
npm install --global surge
surge ./ pagina-ci-osenrey.surge.sh
```

Después del primer despliegue, los siguientes se realizan automáticamente al
enviar cambios a `main`.
