# Optimización del Tiempo de Arranque de Docker

## Introducción

Este documento proporciona una guía paso a paso para optimizar el tiempo de arranque de Docker y mejorar el rendimiento del sistema.

## Pasos Realizados

### Limpieza de Recursos no Utilizados con Comandos de Docker

Docker proporciona comandos específicos para limpiar y eliminar recursos no utilizados. A continuación se detallan los comandos utilizados:

#### Eliminar contenedores inactivos:

```bash
docker container prune
```

Este comando elimina todos los contenedores detenidos. Asegúrate de que no necesitas ninguno de esos contenedores antes de ejecutarlo.
Eliminar imágenes no utilizadas:

```bash
docker image prune -a

Este comando elimina todas las imágenes que no están asociadas con un contenedor en ejecución ni con una imagen referenciada.
Eliminar volúmenes no utilizados:


```bash
docker volume prune
```

Esto elimina todos los volúmenes no utilizados.
Eliminar redes no utilizadas:


```bash
docker network prune
```

Este comando elimina todas las redes no utilizadas.
Eliminar imágenes específicas por nombre o etiqueta:


```bash
docker rmi nombre_de_la_imagen:etiqueta
```

Reemplaza nombre_de_la_imagen:etiqueta con el nombre y la etiqueta de la imagen que deseas eliminar.
Eliminar contenedores específicos por ID o nombre:

```bash
docker rm nombre_o_id_del_contenedor
```

Reemplaza nombre_o_id_del_contenedor con el ID o nombre del contenedor que deseas eliminar.
Eliminar todas las imágenes no utilizadas, contenedores, volúmenes y redes:

```bash
docker system prune -a
```

Este comando combina los comandos anteriores y elimina todas las imágenes no utilizadas, contenedores, volúmenes y redes.

Asegúrate de revisar qué se va a eliminar antes de confirmar la operación, ya que estos comandos eliminarán permanentemente los recursos.
Limpieza Adicional
Limpiar los registros de Docker:

Puedes intentar limpiar los registros de Docker para que se actualicen. Esto se hace eliminando el archivo de registro actual y permitiendo que Docker cree uno nuevo.

```bash
sudo rm /var/lib/docker/containers/*/*.log
sudo systemctl restart docker
```

Ten en cuenta que al hacer esto, se perderá el historial de registros de los contenedores. Sin embargo, esto puede ayudar a que las advertencias desaparezcan.

Eliminar archivos residuales manualmente:

Si las advertencias persisten, puedes intentar buscar y eliminar archivos residuales manualmente.

```bash
sudo find /var/lib/docker -name "*sha256*" -exec rm -rf {} \;
```

**¡Ten mucho cuidado con este comando! Eliminará archivos de la ubicación de Docker. Asegúrate de entender lo que estás haciendo y ten en cuenta los posibles riesgos.**

Limpiar Cachés con Herramientas Externas
BleachBit y Stacer:

Además de los comandos de Docker, se utilizaron herramientas externas como BleachBit y Stacer para limpiar cachés y mejorar el rendimiento del sistema.

    BleachBit: Herramienta de limpieza del sistema.

    Stacer: Administrador de sistemas para Ubuntu.

Aviso

Estos pasos deben realizarse con precaución, asegurándote de entender las consecuencias de las acciones ejecutadas. Siempre realiza copias de seguridad antes de realizar cambios significativos en el sistema.

¡Esperamos que estos pasos hayan mejorado el rendimiento de Docker en tu sistema
