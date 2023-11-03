# Práctica 6

## 1. Creación del cluster

![image](https://github.com/Waterclau/ASR/assets/91564866/d6b107ec-0e68-434f-b0f5-fc82ad33abbb)


## 2. Despliegue de una imagen docker basada en php :

![image](https://github.com/Waterclau/ASR/assets/91564866/c5fc9ec0-7c8e-45cc-9068-24ca00b75fa2)

## 3. Inspección de los despliegues que se encuentran en funcionamiento en nuestro cluster:

![image](https://github.com/Waterclau/ASR/assets/91564866/30d92df1-4648-46d5-ad9d-f63ad294b790)

Podemos comprobar como todo funciona correctamente ya que nos muestra que tenemos un despliegue llamado php-apache y que hay 3/3 pods funcionando de manera correcta.

## 4. Aplicar el HPA

![image](https://github.com/Waterclau/ASR/assets/91564866/067952cf-6e52-428e-ba29-ecf88d3ad8c6)

Este comando configura un HPA que mantendrá gestionadas entre $min_replicas y max_replicas replicas de los pods controlados por el despliegue php_deployment, donde hay que tener en cuenta los siguientes argumentos: 
--cpu-percent: Umbral de uso de CPU para activar el escalado automático.
--min: Mínimo de réplicas que se mantendrán activas.
--max: Máximo de réplicas permitidas.
He remplazado $php_deployment con php-apache, $cpu_threshold con 50, $min_replicas con 2, y $max_replicas con 10. 

Una vez el HPA está configurado, podemos comprobar su estado mediante el siguiente comando: 

![image](https://github.com/Waterclau/ASR/assets/91564866/acd41651-c613-4e39-bb5a-382494f6a035)





