# Práctica 6

## 1. Creación del cluster

![image](https://github.com/Waterclau/ASR/assets/91564866/d6b107ec-0e68-434f-b0f5-fc82ad33abbb)


### 1.1. Despliegue de una imagen docker basada en php :

![image](https://github.com/Waterclau/ASR/assets/91564866/c5fc9ec0-7c8e-45cc-9068-24ca00b75fa2)

### 1.2. Inspección de los despliegues que se encuentran en funcionamiento en nuestro cluster:

![image](https://github.com/Waterclau/ASR/assets/91564866/30d92df1-4648-46d5-ad9d-f63ad294b790)

Podemos comprobar como todo funciona correctamente ya que nos muestra que tenemos un despliegue llamado php-apache y que hay 3/3 pods funcionando de manera correcta.

## 2. Aplicar el HPA

![image](https://github.com/Waterclau/ASR/assets/91564866/067952cf-6e52-428e-ba29-ecf88d3ad8c6)

Este comando configura un HPA que mantendrá gestionadas entre $min_replicas y max_replicas replicas de los pods controlados por el despliegue php_deployment, donde hay que tener en cuenta los siguientes argumentos: 
--cpu-percent: Umbral de uso de CPU para activar el escalado automático.
--min: Mínimo de réplicas que se mantendrán activas.
--max: Máximo de réplicas permitidas.
He remplazado $php_deployment con php-apache, $cpu_threshold con 50, $min_replicas con 2, y $max_replicas con 10. 

Una vez el HPA está configurado, podemos comprobar su estado mediante el siguiente comando: 

![image](https://github.com/Waterclau/ASR/assets/91564866/acd41651-c613-4e39-bb5a-382494f6a035)

## 3. Habilitar el autoescalado 

Habilitamos el autoescalado del clúster con un mínimo de 1 nodo y un máximo de 5 nodos:

![image](https://github.com/Waterclau/ASR/assets/91564866/62ac751e-534e-429b-9c48-9e57073a00ec)

De esta manera activamos la capacidad del clúster para ajustar automáticamente el número de nodos según la carga de trabajo.

También podemos cambiar el perfil de autoescalado. Esto significa que el clúster autoescalará de manera más agresiva, eliminando nodos más rápidamente si no son necesarios.

![image](https://github.com/Waterclau/ASR/assets/91564866/2f605fda-14e9-4990-8a34-cf20edee4fe0)

Por último, comprobamos la cantidad actual de nodos en el clúster para confirmar que el autoescalado está funcionando según lo esperado: 

![image](https://github.com/Waterclau/ASR/assets/91564866/b2907949-3ad0-4e00-82f0-58ca2e851797)










