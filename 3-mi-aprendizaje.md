# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado al realizar la práctica también se debe documentar.

# Mi Aprendizaje
### Conceptos que aprendí:

* **Servicios y dependencias (`depends_on` y `condition: service_healthy`)**: Aprendí a configurar servicios dependientes, como WordPress que espera a que MySQL esté listo antes de iniciar. Esto evita errores de conexión durante el arranque de los contenedores.

* **Redes (`networks`)**: Configurar redes tipo `bridge` permite que los contenedores se comuniquen por nombre de servicio sin exponer puertos adicionales.

* **Volúmenes (`volumes`)**: Entendí la importancia de montar volúmenes locales para persistencia de datos.
    Esto asegura que los datos no se pierdan al eliminar los contenedores.

* **Healthcheck**: Configurar healthchecks con comandos como `mysqladmin ping` o `curl http://localhost` permite que Docker detecte si un servicio está realmente disponible antes de iniciar servicios.


### Problemas que resolví:

1. **Rutas largas y con espacios en Windows**:
   Inicialmente, los volúmenes locales no se montaban correctamente. La solución fue usar comillas y barras `/` en lugar de `\`, por ejemplo:

   ```yaml
   volumes:
     - "C:/Users/sebas/.../copia-contenedor-wordpress:/var/www/html"
   ```

2. **Inicio de WordPress antes que MySQL**:
   WordPress fallaba al conectarse a la base de datos. Lo resolví usando `depends_on` con `condition: service_healthy` y configurando un healthcheck en MySQL.
```
docker exec -it contenedor-wordpress bash
```
