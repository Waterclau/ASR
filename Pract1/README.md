# Parte 1
## Paso 1: Crear una instancia de máquina virtual (VM) para el salto
Tras iniciar sesion en google cloud, navegamos a la sección VM instances y creamos dos instancias para este apartado. 
![image](https://github.com/Waterclau/ASR/assets/91564866/ca012ff7-6dc9-48ba-a514-ac526a1b8259)
Como se puede ver en esta imagen , creamos una VM que utilizaremos como salto y otra llamada WEB que simulará la función del servidor web. 
En ambas máquinas ha sido necesario configurar la región, disco de arranque (con sistema Ubunto) y etiquetas que utilizaremos para asociar las reglas de firewall creadas a continuación.

## Paso 2 : editar las reglas de firewall
En este apartado creamos dos reglas, una para el servidor de salto y otra para el servidor de web.
![image](https://github.com/Waterclau/ASR/assets/91564866/b4a830f5-7b37-4e41-864e-931ba765523e)
En cada uno de los firewalls configuraremos las reglas para que se pueda acceder desde nuestra máquina y permita conexiones seguras con el servidor. 
![image](https://github.com/Waterclau/ASR/assets/91564866/7de02703-4165-498c-bb2c-0c682257e60a)

ssh-keygen -t rsa -b 2048 -f "ruta\hacia\la\clave\id_rsa"

![image](https://github.com/Waterclau/ASR/assets/91564866/d73ee061-fddb-431f-98a1-b08a9405e5a7)

![image](https://github.com/Waterclau/ASR/assets/91564866/c674a5fe-f05d-463d-9fbe-05eaabce6766)

