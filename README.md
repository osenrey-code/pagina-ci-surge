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
- `SURGE_DOMAIN`: dominio completo elegido para el sitio, por ejemplo
  `https://pagina-ci-usuario.surge.sh`.

Estos valores no se guardan en el código ni en el historial de Git.

## Prueba local

La página no requiere dependencias. Puede abrirse `index.html` directamente en
el navegador o servirse con cualquier servidor estático.

## Publicación manual opcional

Con Node.js y Surge instalados:

```bash
npm install --global surge
surge ./ https://pagina-ci-usuario.surge.sh
```

Después del primer despliegue, los siguientes se realizan automáticamente al
enviar cambios a `main`.
