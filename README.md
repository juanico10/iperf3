# iperf3
Proyecto para crear un servidor iperf3 en Docker.
*iperf3* es la última versión del popular programa iperf para medir el ancho de banda entre dos o más equipos en red local o Internet.

<p align="center">
        <img src="https://github.com/JuanRodenas/iperf3/blob/main/iperf3.webp" alt="iperf3" width="800" height="400"/>
    </a>
    <br>
    <strong>iperf para medir el ancho de banda</strong>
</p>
<!-- markdownlint-enable MD033 -->

[![GitHub](https://img.shields.io/static/v1.svg?color=blue&labelColor=555555&logoColor=ffffff&style=for-the-badge&label=JuanRodenas&message=GitHub&logo=github)](https://github.com/JuanRodenas "view the source for all of our repositories.")
![Docker Pulls](https://img.shields.io/docker/pulls/juanico/iperf3?logo=docker&style=for-the-badge)
![Docker Image Version (latest by date)](https://img.shields.io/docker/v/juanico/iperf3?logo=docker&style=for-the-badge)

## Enlaces a desarrollador
| PROYECTO | LINK |
| :-- | :--: |
| Docker hub | [Link](https://hub.docker.com/r/juanico/iperf3/) |
| Web IPERF | [Link](https://iperf.fr/) |



## Archivos para la ejecución en docker
Descargar docker compose [docker-compose.yml](https://github.com/JuanRodenas/iperf3/blob/main/docker-compose.yml)

### Tag imagenes
The architectures supported by this image are:

| Architecture | Available | Tag |
| :----: | :----: | ---- |
| x86-64 | ✅ | :stable |
| arm | ✅ | :arm |

### Lanzar el contenedor
~~~
docker-compose up -d
~~~

### Ver el log para ver los test
~~~
docker-compose logs -f
~~~
Y empezaremos a ver las conexiones.

## Ejecución de cliente iperf3 en Windows, Linux y macOS con el archivo descargable:
Descargamos el achivo de la [web](https://iperf.fr/) y una vez descomprimido lo ejecutamos con:
* En windows:
~~~
iperf3.exe
~~~

* En linux:
~~~
iperf3
~~~
* También hay apps para móviles, en la web del desarrollador.

ejemplo de un comando:
`iperf3 -c IP -P 50 -f g -t 5`

## Argumentos
Los siguientes argumentos se pueden introducir después de la ejecución del propio programa, de la siguiente forma: «iperf3 -argumentos» y no importa el orden a la hora de introducir los argumentos.

### Opciones de configuración generales: para cliente y servidor
```
    -p puerto: podremos elegir el puerto a utilizar, ya sea TCP o UDP, este puerto debe ser exactamente tanto en el servidor como en todos los clientes.
    –cport puerto: esta opción nos permite especificar el puerto en el lado del cliente, solo para iperf 3.1 o superior.
    -f formato: podremos elegir la unidad de medición que nos aparecerá a la hora de ver la velocidad.
        k: Kbits
        K: Kbytes/s
        m: Mbits
        M: MBytes/s
        g: Gbps
        G: GBytes/s
    -i intervalo: intervalo de tiempo medido en segundos donde iperf3 nos mostrará toda la información de ancho de banda, jitter y pérdida de paquetes. Por defecto es 0.
    -F nombre_archivo: en el cliente es el archivo leído y escrito en la red local, en lugar de usar información aleatoria. En el servidor es lo leído desde la red y escrito a un archivo.
    -B host: permite realizar un binding a una tarjeta e red en concreto, ideal por si tenemos múltiples interfaces.
    -V: salida con todos los detalles (verbose)
    -J: salida en formato JSON
    –logfile archivo: envía la salida a un archivo de registro (solo en iperf 3.1)
    –d: debug
    -v: version del programa
    -h: lanza la ayuda del programa
```


### Opciones de configuración solo para el servidor
```
    -s: arranca iperf en modo servidor.
    -D: arranca el programa en segundo plano como demonio.
    -I: escribe un archivo con el ID del proceso, ideal para usarlo con -D (demonio).
```


### Opciones de configuración solo para el cliente
```
    -c direccion_IP: arranca iperf en modo cliente para conectarnos a un servidor, debemos definir la dirección IP justo después.
    –sctp: utiliza este protocolo SCTP en lugar de TCP (por defecto).
    -u: utiliza el protocolo UDP en lugar de TCP (por defecto).
    -b ancho_de_banda: permite definir un ancho de banda en N bits/sec, por defecto es 1MB/s en UDP e ilimitado en TCP. Si utilizamos el argumento -P para enviar múltiples flujos de datos, este ancho de banda se aplica a cada uno de ellos.
    -t tiempo: en segundos para transmitir información a la máxima velocidad. Por defecto son 10 segundos, pero podremos poner lo que queramos.
    -n número: número de datos a transmitir, en lugar de utilizar tiempo (-t) usamos datos.
    -k paquetes: número de paquetes a transmitir, en lugar de usar tiempo (-t) o datos (-n).
    -l (L minúscula): longitud del buffer leído o escrito.
    -P número: número de flujos de datos simultáneos, recomendable poner 5 o superior para exprimir la red al máximo.
    -R: el tráfico de iperf normalmente va desde el cliente hasta el servidor, si ponemos este argumento, el tráfico irá desde el servidor hasta el cliente.
    -w tamaño: permite especificar el tamaño de ventana de TCP
    -M mss: permite configurar el MSS de TCP
    -N: configura la opción no-delay de TCP.
    -4: utilizamos redes IPv4.
    -6: utilizamos redes IPv6.
    -S: tipo de servicio para los paquetes salientes.
    -L etiqueta: permite configurar la etiqueta de flujo para redes IPv6.
    -Z: utiliza el método zero-copy, reduce muchísimo el uso de CPU por parte del programa.
    -O segundos: omite los primeros X segundos del test, para evitar problemas con el TCP slowstart y que nos proporcione una medida sin la ráfaga del principio.
    -T título: permite poner un título delante de cada cadena
    -C algoritmo: permite configurar el algoritmo de congestión, solamente en Linux con iperf 3.0 y en FreeBSD con iperf 3.1
```

## Ejemplo de un cliente
A continuación, podéis ver un ejemplo, podemos ejecutar el cliente iperf3 con algunos argumentos muy interesantes:

`iperf3.exe -c 192.168.1.10 -P 50 -p 5000 -f g -t 5`
* Explicación de la línea:
~~~
-c 192.168.1.10: actúa en modo cliente con la IP definida.
-P 50: mandamos un total de 50 conexiones TCP
-p 5000: hacemos uso del puerto 5000, el por defecto es 5201
-f g: mostramos la velocidad en Gbps
-t 5: lanzamos el test durante 5 segundos.
~~~

## Conclusión
Con esta información puedes configurar un servidor iperf3, podemos usar programas como jperf o iperf3 para medir la velocidad entre dos ordenadores.

## Ready!
