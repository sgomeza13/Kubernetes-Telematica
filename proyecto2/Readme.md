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
# Kubernetes administrado en EKS (aws) o GKS (gcp)

## 1. breve descripción de la actividad
El objetivo de la actividad fue desplegar una aplicación monolítica como lo es WordPress de manera que se garantice la alta disponibilidad, el buen manejo de los recursos y el mejoramiento de la experiencia del usuario. Haciendo uso de los servicios administrados que nos brinda los proveedores de Cloud (en este caso GCP) para facilitar y tener garantía de todas las configuraciones de despliegue.

## Video
- https://drive.google.com/file/d/1EJMp9s5z5UwWRo1aAlNRT52FGKiKanZD/view?usp=sharing
  
## ¿Que se logró y que no se logró?:
- **Se logró**
  
 - Conexión NFS entre los nodos del cluster.
 - Creación y conexión a base de datos mediante servicio administrado.	
 -implementación de LoadBalancer para el despliegue de la aplicación a internet.

- **No se logró**:
 - Conexión de la base de datos dentro del cluster.

# 2. Descripción del ambiente de desarrollo y técnico: lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

## como se Configura  y ejecuta.

1. Crear el cluster de Kubernetes estándar (no autopilot).
2. Clonar el repositorio.
3. Crear un disco nuevo en el compute engine.
4. Modificar el archivo 001-nfs-server.yaml ,poniendole el pdname por el nombre del disco creado en el paso anterior.
   ![image](https://github.com/sgomeza13/Kubernetes-Telematica/assets/74980999/a90432c8-3115-4f62-9cb2-da89046f32e0)
5. Ejecutar el siguiente comando:
```
kubectl apply -f 001-nfs-server.yaml
```
6. Ejecutar el siguiente comando:
```
kubectl apply -f 002-nfs-server-service.yaml
```


## detalles del desarrollo.



# descripción y como se configura los parámetros del proyecto (ej: ip, puertos, conexión a bases de datos, variables de ambiente, parámetros, etc)
## IP o nombres de dominio en nube o en la máquina servidor.


## como se lanza el servidor.



## una mini guia de como un usuario utilizaría el software o la aplicación



