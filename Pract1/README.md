# 1a Solución: creación de máquina de salto 
## Paso 1: Crear una instancia de máquina virtual (VM) para el salto
Tras iniciar sesion en google cloud, navegamos a la sección VM instances y creamos dos instancias para este apartado.

![image](https://github.com/Waterclau/ASR/assets/91564866/9ff77c1e-7caa-426e-9a92-57ef91115af5)

Como se puede ver en esta imagen , creamos una VM que utilizaremos como salto y otra llamada WEB que simulará la función del servidor web. 
En ambas máquinas ha sido necesario configurar la región, disco de arranque (con sistema Ubunto) y etiquetas que utilizaremos para asociar las reglas de firewall creadas a continuación.

##  Paso 2: Establecer las reglas de firewall
A continuación creamos dos reglas de firewall:

![image](https://github.com/Waterclau/ASR/assets/91564866/b4a830f5-7b37-4e41-864e-931ba765523e)

La primera se encarga de establecer una conexión segura entre nuestro pc y el servidor de salto.

![image](https://github.com/Waterclau/ASR/assets/91564866/7de02703-4165-498c-bb2c-0c682257e60a)

Mientras que la segunda se encarga de establecer una conexión segura entre el servidor de salto y el servidor web.
En cada una de estas reglas variamos las etiquetas y los rangos de ip necesarios para que se ajusten a las conexiones que queremos establecer en cada paso. 
En el de salto , es necesario añadir la ip de nuestro pc, mientras que en el del servidor web se debe añadir la ip interna del servidor de salto.

## Paso 3: Claves ssh

En este paso generaremos las claves SSH , las cuales son claves criptográficas compuestas por una clave privada y una clave pública, usadas para autentificar y cifrar la comunicación entre sistemas, mediante el siguiente comando: 

#### ssh-keygen -t rsa -b 2048 -f "ruta\hacia\la\clave\id_rsa"

Una vez hecho esto añadiremos la clave pública en google cloud.

![image](https://github.com/Waterclau/ASR/assets/91564866/4123d8da-a2c2-45f1-abd4-6df9fad99983)

Tras esto nos conectaremos a la máquina de salto desde la consola de nuestro pc mediante el siguiente comando: 
#### ssh "ip externa del servidor de salto" -i "ruta\hacia\la\clave\id_rsa" .
Si hemos configurado el firewall de manera correcta , deberíamos ver como ahora estamos dentro de nuestra máquina de salto: 

![image](https://github.com/Waterclau/ASR/assets/91564866/81cb7734-75fb-46c7-9146-6ef86a1ea739)

Dentro de la máquina de salto generaremos unas nuevas claves ssh y repetiremos los mismos pasos para conectarnos a la máquina del servidor web.

![image](https://github.com/Waterclau/ASR/assets/91564866/41eded52-8abe-43e1-9b96-867ce7ab0eb1)

Desde el servidor web instalaresmos ngx , para comprobar que nuestra configuración funciona de manera correcta, mediante los siguientes comandos:
#### sudo apt update
#### sudo apt install nginx

Si ahora accedemos a la ip de nuestro servidor web mediante google chrome veremos la siguiente ventana, siendo correcta nuestra configuración.

![image](https://github.com/Waterclau/ASR/assets/91564866/907750a3-c4ff-4fee-99be-1d2136d5089b)

# 2da mejora solución: introducción a los WAF - Web Application Firewall (firewall capa 7) 

## ¿Qué ventajas e inconvenientes tiene hacer HTTPS offloading en el balanceador?

### Ventajas

* Mejoras en rendimiento

Al permitir al balanceador hacere HTTPS offloading, este se encarga de las tareas de descarga de los cifrado y descrifado, quitando trabajo de los servidores, resultando en unos mejores tiempos de respuesta.

* Mayor seguridad

Se incrementan las medidas de seguridad al implementar WAF, que maneja el tráfico antes de su llegada a los servidores backend. 

### Inconvenientes 

* Mayor complegidad

La configuración de HTTPS offloading aumenta significativamente la complegidad de la configuración del cifrado del tráfico entre los servidores. 

### Pasos necesarios

Para esta parte crearemos una nueva VM , web2 , y utilizaremos la VM de salto del apartado anterior.

![image](https://github.com/Waterclau/ASR/assets/91564866/cb082db0-3370-48d0-99e2-f511bcbfe704)

Actualizaremos las reglas de firewall para que permita realizar el health check.

![image](https://github.com/Waterclau/ASR/assets/91564866/94db974e-44eb-432d-b156-3c7d9f3310f1)

Además crearemos una instacia de grupo para facilitar la gestión del WAF. Mediante este grupo podemos aplicar las regals de seguridad para todas las intancias que pertenezcan a este grupo. 

![image](https://github.com/Waterclau/ASR/assets/91564866/2c9134c0-a73b-4bc9-95a9-8fcf81b125b0)

load balancer

![image](https://github.com/Waterclau/ASR/assets/91564866/015e9b03-001d-49d6-8904-6be13a6326bc)

ngx




# 4ta mejora solución - 1 punto
Algunas de las mejoras que se podrían implantar podrían ser las siguientes: 

#### Configuración de VPN

Mediante la implementación de uan red privada virtual para acceder al servidor web se mejoraría la seguridad de nuestro sistema , a que añadiríamos un nuevo método de seguridad para que solo los usuarios con acceso puediesen conectarse a esa VPN. 

#### Protección de ataques de fuerta bruta 

Para ello se podría configurar el WAF para detectar este tipo de ataques de las siguientes maneras: 

Bloqueo de intentos fallidos : configurando un mecanisomo que limite el acceso despues de un nº de intentos

Uso de autenticación multifactor (MFA) : El MFA requiere que los usuarios proporcionen más de uan forma de autenticación antes del acceso, por lo que se aumenta la seguridad de nuestro sistema incrementanto las capas de seguridad. 

Reglas de bloqueo de IP: bloqueando asi las IP que intenten acceder sin éxito un determinado número de veces. 

#### Respaldo y restauración del WAF 

Configurar un plan de respaldo y restauración para el WAF y las reglas de configuración. Esto garantiza que, en caso de falla del WAF o de cambios no deseados en las reglas, puedas restaurar rápidamente la configuración correcta.
