## info de la materia: Tópicos especiales en Telemática st0263 
#
## Estudiante(s): 
- Simon Gomez Arango - sgomez13@eafit.edu.co
- Sara María Castrillón Ríos - smcastril1@eafit.edu.co
- Manuela Tolosa - mtolosag@eafit.edu.co
#
## Profesor: 
Edwin Nelson Montoya Múnera - emontoya@eafit.edu.co
#
# Kubernetes

## 1. breve descripción de la actividad
#Descripción:

El reto consiste en desplegar una aplicación de código abierto LAMP (Linux, Apache, MySQL, PHP), similar a WordPress, en un clúster de Kubernetes con alta disponibilidad. Este despliegue se realizará en Google Cloud Platform (GCP) utilizando MicroK8s en 6 máquinas virtuales(3 para base de datos  y las otras 3 para WordPress). La aplicación debe contar con balanceador de cargas y alta disponibilidad en todas las capas (aplicación, base de datos y almacenamiento). Se permite el escalado dinámico de nodos en el clúster de Kubernetes.

nos estamos basando en la siguiente arquitectura :
![image](https://github.com/sgomeza13/reto4_telematica/assets/74980999/567790a2-9db2-49e3-a0c6-84bd292923eb)

-Pacheco, J. (2019, mayo 1). Wordpress High Availability on kubernetes - Jose Pacheco. Medium. https://medium.com/@icheko/wordpress-high-availability-on-kubernetes-f6c0bcc2f28d

## ¿Que se logró y que no se logró?:
### A Nivel funcional:
- **Se logró**

- **No se logró**:

### A nivel no funcional:
- **Se logró**

- **No se logró**

## 2. información general de diseño de alto nivel, arquitectura, patrones, mejores prácticas utilizadas:

### Componentes:



# 3. Descripción del ambiente de desarrollo y técnico: lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

Lenguaje de programacion: 

Librerias :
## como se compila y ejecuta.


## detalles del desarrollo.


# descripción y como se configura los parámetros del proyecto (ej: ip, puertos, conexión a bases de datos, variables de ambiente, parámetros, etc)
## IP o nombres de dominio en nube o en la máquina servidor.


## como se como se instala y despliega.
-Lo primero que debes realizar es crear una máquina virtual, una vez creada le instalas Docker con los siguientes comandos:
``` 
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

-luego descargas la imagen de my-sql con el siguiente comando : ```docker pull mysql:5.7```

-A continuación creas un contenedor con : ```sudo docker run -d --name mysql-container -e MYSQL_ROOT_PASSWORD=password -e MYSQL_USER=user -e MYSQL_PASSWORD=password -e MYSQL_DATABASE=my-sql -p 3306:3306 mysql:5.7```

-Verificas que el contenedor se creo correctamente con  ```docker ps```

-Ahora desde el cliente que se quiere conectar a my-sql 
```
sudo apt update
sudo apt install mariadb-client
```

```mysql -u user -p -h 10.128.0.7 -P 3306```


## una mini guia de como un usuario utilizaría el software o la aplicación

## Fuentes:

-Pacheco, J. (2019, mayo 1). Wordpress High Availability on kubernetes - Jose Pacheco. Medium. https://medium.com/@icheko/wordpress-high-availability-on-kubernetes-f6c0bcc2f28d


-NetworkChuck [@NetworkChuck]. (2020, septiembre 8). you need to learn Kubernetes RIGHT NOW!! Youtube. https://www.youtube.com/watch?v=7bA0gTroJjw


-Run a Single-Instance Stateful Application. (s/f). Kubernetes. Recuperado el 25 de octubre de 2023, de https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/




