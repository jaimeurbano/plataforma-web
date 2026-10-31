# Persistencia en Render con Neon

Para conservar cuentas e intentos después de reiniciar o volver a desplegar en Render:

1. En Neon, copia la cadena de conexión PostgreSQL del proyecto. No la publiques ni la agregues a Git.
2. En Render, abre el servicio web y ve a **Environment**.
3. Agrega `DATABASE_URL` y pega la cadena de conexión como valor.
4. Guarda los cambios y espera a que Render reinicie o despliegue el servicio.
5. En los logs de inicio, confirma que indique `Almacenamiento activo: PostgreSQL`.
6. Registra una cuenta de prueba y revisa que aparezca en la tabla `codequiz_users` de Neon. Los intentos se guardan en `codequiz_attempts`.

El servidor crea las tablas si no existen. Sin `DATABASE_URL`, usa los archivos de `.data` para desarrollo local. Los datos que solo existieran en archivos locales no se copian automáticamente a Neon; después del cambio, vuelve a registrar las cuentas que necesites.
