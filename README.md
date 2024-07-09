

La mejor manera de disfrutar un libro tecnológico, como en este caso [Book: Kubernetes para profesionales: Desde cero al despliegue de aplicaciones seguras y resilientes](https://0xword.com/es/libros/213-kubernetes-para-profesionales-desde-cero-al-despliegue-de-aplicaciones-seguras-y-resilientes.html), es subrayarlo, tomar nota y parar para probar sus ejemplos en tu propia terminal. Por esa razón, en esta organización de Git, resumiremos todos sus capítulos con ejemplos y gráficos.

# Kubernetes I : Introducción
![Logo](https://res.cloudinary.com/dz3erohks/image/upload/v1720208192/k8s_yhbypb.png)

En este capítulo I será introductorio para entender que es Kubernetes, su arquitectura, sus componentes, los sabores de K8s y los clientes.

## Kubernetes (K8s)
Kubernetes es una plataforma creada por Google para poder orquestar los contenedores, es decir, facilitar el despliegue, escalado y sobre todo la gestión automática de dichos contenedores.


### Arquitectura:

K8s al igual que cualquier otro clúster, está formado por nodos (Control Plane) que controlan el clúster.

![](./assets/Screenshot%202024-07-05%20at%2021.39.23.png)

A continuación procedemos a explicar cada uno de los componentes que aparecen en la figura[x]

- Elementos del Control Plane: 
  `Control Plane` son los nodos que controlan el clúster, pueden estar alojados tanto en la misma máquina como separados por diferentes nodos.

    * `kube-apiserver`: Todas aquellas peticiones que realiza el usuario al usar el comando `kubectl`, una interfaz gráfica o de forma programada las recibe este componente, es decir, es una API REST que se encarga de atender a aquellos clientes que desean interactuar con nuestro clúster.  

    * `etcd`: Es una base de datos de tipo clave-valor de alta disponibilidad usada por `ube-apiserver` para presistir el estado del clúster.

    * `kube-scheduler`: Se encarga de decidir dónde se despliegan los Pods dentro del clúster.

    * `kube-controller-manager`: Se encarga de ejecutar los controladores.
      Los controladores son procesos que se ejecutan de forma continua (loop) escuchando eventos en el clúster.
      Existen controladores para cada cosa practicamente en K8s como de nodos, replicaSet, admisión...etc

    * cloud-controller-manager: Se encarga de ejecutar los controladores de la nube, que son procesos capaces de interactuar con la nube para crear recursos (AWS, Google o Azure).

- Nodos:
  * `Container engine`: Es el motor de contenedores que usa Kubernetes para gestionar los contenedores. Hasta la versión 1.24 Kubernetes usaba por defecto Docker, pero en la versiones posteriores, este ha sido remplazado por CRI-O.

   * `Kubelet`: Es el que se encarga de la ejecución de los contenedores en el Pod, es decir, cuando el `kube-scheduler` decide en qué nodo tiene que ejecutar el contenedor, `kubelet` en comunicación con `kube-apiserver` recibe la información, crea y ejecuta los contenedores definidos en dicho Pod.
    
  * `Kube-proxy`: Se encarga de controlar el tráfico de red interno del clúster. Cualquier tipo de comunicación de red (que no sea local) de un Pod, pasa por este componente, y se encarga de enrutar el tráfico a su destino.

### Sabores de Kubernetes:

Podemos crear un clúster de K8s desde cero, pero disponemos de otra opciones que hacen esta tarea más amena como:

  * `Minikube` : Minikube permite la creación de un clúster de kubernetes de forma local en macOs, Linux y Windows. Es una herramienta ideal para los desarrolladores y nuevo usuarios. Además soporta distintas arquitecturas como ARM e Intel.
  ### Nota : Requisitos Instalación
  - **Al menos 2 CPUs**.
  - **2GB** de memoria libre al menos.
  - **20GB de espacio** libre en disco.
  - Un **motor de contenedores** (Docker o Podman) o un gestor de máquinas virtuales/hipervisor.
  
  ```bash macOs
     brew install minikube
  ```
  ```bash 
     minikube start
  ```
  ```bash macOs
    Si usamos minikube con el driver de virtualbox o wmware no habrá problemas, **pero si usamos el drive de Docker o Podman**, el acceso a nodo del clúster podría variar con respecto al uso de máquinas virtyales por el tema de separación completa de recursos.
  ```


 ### Clientes:

  El cliente oficial en Kubernetes es `kubectl`. Es una herramienta de línea de comandos.
  También existe una interfaz web oficial que permite al usuario interactuar con clúster desde el navegador de forma visual.

  ```bash 
     minikube dashboard
  ```
## Authors

- [@Younes Kabiri Farah](https://github.com/younesKabiriFarah)


## Acknowledgements

 - [Kubernetes](https://kubernetes.io/docs/home/)
 - [Book: Kubernetes para profesionales: Desde cero al despliegue de aplicaciones seguras y resilientes](https://0xword.com/es/libros/213-kubernetes-para-profesionales-desde-cero-al-despliegue-de-aplicaciones-seguras-y-resilientes.html)


## Features

- Conceptos básicos
- Pods
- Exponiendo Pods
- Workloads
- Configuración de aplicaciones y secretos
- Selección de nodos
- Volúmenes Persistentes
- Autorización Basada en Roles
- Politicas de Red
- Contexto y Políticas de Seguridad

