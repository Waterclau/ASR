## Paso 1: Crear un archivo YAML para el ConfigMap (configmap-asr.yaml):

![image](https://github.com/Waterclau/ASR/assets/91564866/4ea924c5-f27e-4267-a5b3-cfc12ca46d30)

Este archivo se encargará de almacenar nuestro escenario de pruebas de Artillery. 

## Paso 2: Crear el ConfigMap en Kubernetes:

![image](https://github.com/Waterclau/ASR/assets/91564866/8a742cab-4573-4870-b3b6-1e9f8c0c66cd)

En este paso se utiliza kubectl apply para crear el ConfigMap en el clúster.

## Paso 3: Crear un archivo YAML para el trabajo (job-artillery.yaml):

![image](https://github.com/Waterclau/ASR/assets/91564866/36c553b6-2223-454c-9a10-85a9b4a2e252)

Define la especificación del trabajo que ejecutará las pruebas de Artillery.El trabajo ejecuta pruebas de carga utilizando la herramienta Artillery y un escenario de pruebas almacenado en un ConfigMap. El contenedor en el pod no se reiniciará automáticamente en caso de fallo y se permiten hasta 4 reintentos en caso de error

## Paso 4: Crear el trabajo en Kubernetes:

![image](https://github.com/Waterclau/ASR/assets/91564866/7adae8c7-a408-469e-b905-8c3de30e987d)









