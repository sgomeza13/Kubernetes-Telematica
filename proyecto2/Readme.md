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
  
## ¿Que se logró y que no se logró?:
- **Se logró**
  
 - Conexión NFS entre los nodos del cluster.
 - Creación y conexión a base de datos mediante servicio administrado.	
 -implementación de LoadBalancer para el despliegue de la aplicación a internet.

- **No se logró**:
 - Conexión de la base de datos dentro del cluster.

# 2. Descripción del ambiente de desarrollo y técnico: lenguaje de programación, librerias, paquetes, etc, con sus numeros de versiones.

## como se Configura  y ejecuta.
### Creación Wordpress
1. Crear el cluster de Kubernetes estándar (no autopilot).
2. Clonar el repositorio.
3. Crear un disco nuevo en el compute engine. (el disco debe estar en la misma region del cluster)
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
7. Obtener la IP del nfs-server 
```
kubectl get services
```
(copiar el cluster IP del nfs-server)
8. Modificar el archivo: wordpress-pvc.yaml
![image](https://github.com/sgomeza13/Kubernetes-Telematica/assets/74980999/e315f4cd-0cf9-4bbc-908f-3606194fbb01)
(Cambiar la IP por la obtenida en el paso anterior)
9. Ejecutar el siguiente comando:
```
kubectl apply -f wordpress-pvc.yaml
```
10. Ejecutar el siguiente comando:
```
kubectl apply -f wordpress-deployment.yaml
```
11. Ejecutar el siguiente comando:
```
kubectl apply -f wordpress-service.yaml
```
### Creación Base de datos
1. Crear instancia de SQL
![image](https://github.com/sgomeza13/Kubernetes-Telematica/assets/74980999/1be3cc99-396f-4b63-87e4-63ace0268e62)
![image](https://github.com/sgomeza13/Kubernetes-Telematica/assets/74980999/49c7f7b6-c446-443d-ae38-babef7a12a98)
![image](https://github.com/sgomeza13/Kubernetes-Telematica/assets/74980999/44be514c-d2c1-46be-bb2b-6d3ed76a9e9d)
2. Agregar cuenta y crear base de datos
![image](https://github.com/sgomeza13/Kubernetes-Telematica/assets/74980999/ce96771c-95e7-4834-a081-e9555ff9310c)
3. Crear base de datos dentro de la instancia
![image](https://github.com/sgomeza13/Kubernetes-Telematica/assets/74980999/5c73d49a-70a0-41b9-a0fe-b0ef9dd1f3d7)
4. Activar alta disponibilidad
![image](https://github.com/sgomeza13/Kubernetes-Telematica/assets/74980999/5e0a0c0b-a8c6-483c-834a-321ebe80f2b8)
6. Ingresar valores de la base de datos en Wordpress
![image](https://github.com/sgomeza13/Kubernetes-Telematica/assets/74980999/5f0be649-066d-46bc-bd6b-99979cf00f0d)

Para mas detalles verl el video.
## Video
- https://drive.google.com/file/d/1EJMp9s5z5UwWRo1aAlNRT52FGKiKanZD/view?usp=sharing

## IP del servicio corriendo ACTUALMENTE
http://34.67.224.168/

## Comparación entre opcion 1 y opcion 2
La elección depende de sus necesidades específicas y prioridades por ejemplo:

1) crear el servicio de base de datos en HA dentro del clúster Kubernetes

Ventajas:
- Mayor control: Puede tener un control más directo sobre la configuración y el rendimiento de la base de datos al alojarla en el mismo clúster Kubernetes.
- Menor latencia: Al estar dentro del clúster, la latencia entre la aplicación y la base de datos suele ser menor.

Desventajas:
- Mayor complejidad: Configurar y administrar una base de datos en alta disponibilidad en Kubernetes es complejo y requiere más tiempo y experiencia.
- Responsabilidad adicional: el administrador se encarga de configurar y respaldar la base de datos, lo que implica trabajo adicional.

2) utilizar un servicio de base de datos administrado externo al clúster.

Ventajas:
- Facilidad de gestión: Los servicios de base de datos administrados se encargan de la mayoría de las tareas de administración, como copias de seguridad, escalabilidad y actualizaciones.
- Alta disponibilidad incorporada: Estos servicios ofrecen alta disponibilidad de forma nativa.
- Menos carga operativa: Al delegar la administración a un proveedor externo, su equipo puede centrarse en el desarrollo de la aplicación en lugar de la administración de la base de datos.

Desventajas:
- Costos adicionales: Los servicios administrados son mas costosos, y estos costos pueden aumentar a medida que crece su aplicación.

## Referencias
- Jayanandana, N. (2023, 2 agosto). NFS Persistent volumes with kubernetes on GKE — a case study. Medium. https://nilesh93.medium.com/nfs-persistent-volumes-with-kubernetes-a-case-study-ce1ed6e2c266
- storagefreak. (2020, 21 octubre). WordPress on kubernetes in Google Cloud for beginners [Vídeo]. YouTube. https://www.youtube.com/watch?v=xguheW_GEi4



