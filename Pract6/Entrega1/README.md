## Paso 1: Crear un archivo YAML para el ConfigMap (configmap-asr.yaml):

![image](https://github.com/Waterclau/ASR/assets/91564866/4ea924c5-f27e-4267-a5b3-cfc12ca46d30)

En este paso, se crea un archivo YAML llamado configmap-asr.yaml que define un ConfigMap en Kubernetes. El ConfigMap se utiliza para almacenar el escenario de pruebas de Artillery que será utilizado por el trabajo (job). El archivo contiene la configuración del ConfigMap, incluyendo el nombre del ConfigMap y el escenario de pruebas de Artillery que se almacena en él.

## Paso 2: Crear el ConfigMap en Kubernetes:

![image](https://github.com/Waterclau/ASR/assets/91564866/8a742cab-4573-4870-b3b6-1e9f8c0c66cd)

Después de crear el archivo YAML del ConfigMap, se utiliza el comando kubectl apply para crear el ConfigMap en el clúster de Kubernetes. El ConfigMap se crea con el nombre especificado en el archivo YAML y se carga con el escenario de pruebas de Artillery.

## Paso 3: Crear un archivo YAML para el trabajo (job-artillery.yaml):

![image](https://github.com/Waterclau/ASR/assets/91564866/36c553b6-2223-454c-9a10-85a9b4a2e252)

En este paso, se crea un archivo YAML llamado job-artillery.yaml que define un trabajo (job) en Kubernetes, donde se define la especificación del trabajo que ejecutará las pruebas de Artillery.El trabajo ejecuta pruebas de carga utilizando la herramienta Artillery y un escenario de pruebas almacenado en un ConfigMap. El contenedor en el pod no se reiniciará automáticamente en caso de fallo y se permiten hasta 4 reintentos en caso de error

## Paso 4: Crear el trabajo en Kubernetes:

![image](https://github.com/Waterclau/ASR/assets/91564866/7adae8c7-a408-469e-b905-8c3de30e987d)

Una vez que se ha definido el archivo YAML del trabajo, se utiliza el comando kubectl apply para crear el trabajo en el clúster de Kubernetes. El trabajo se ejecutará y utilizará el escenario de pruebas de Artillery del ConfigMap para realizar las pruebas.







