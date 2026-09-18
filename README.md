# Docker Swarm and Python Microservices Deployment

[🇪🇸 Español](#-español) | [🇬🇧 English](#-english)

---

## 🇪🇸 Español

Este proyecto implementa una arquitectura basada en **Docker Swarm** compuesta por dos componentes: un **Frontend** y un **Backend**. 

* **Backend:** Expone una API REST que devuelve el tiempo transcurrido en segundos desde el 1 de enero de 1970 (marca de tiempo Unix).
* **Frontend:** Consume la información de la API y la renderiza a través de una interfaz web.

### ❗ Advertencia de Seguridad
> **Uso exclusivo para desarrollo/laboratorio.** Esta aplicación **no** debe desplegarse en entornos de producción. Se ejecuta utilizando el servidor de desarrollo de Flask en modo *debug* y los contenedores no cuentan con medidas de endurecimiento (*hardening*), ejecutándose como usuario `root` sobre imágenes base con una gran superficie de ataque.

### Componentes

#### 1. Frontend
* **Puerto:** Expone la interfaz web en el puerto interno `8080`. 
* **Despliegue:** En el fichero `docker-swarm.yml`, este puerto se mapea al puerto `80` (estándar web) para simplificar el acceso desde el navegador.
* **Comunicación:** Consume la API del backend utilizando el nombre del servicio de Docker Swarm como resolución de host, aprovechando el balanceo de carga nativo de la plataforma.

#### 2. Backend
* **Puerto:** Publica la API en el puerto `5000` bajo el endpoint `/api`.
* **Comunicación:** Diseñado para recibir las peticiones del frontend a través de la URL configurada por parámetros de inicialización.

---

## 🇬🇧 English

This project implements a **Docker Swarm**-based architecture consisting of two components: a **Frontend** and a **Backend**.

* **Backend:** Exposes a REST API that returns the elapsed time in seconds since January 1, 1970 (Unix timestamp).
* **Frontend:** Consumes the API data and renders it through a web interface.

### ❗ Security Warning
> **For development/lab use only.** This application **must not** be deployed in production environments. It runs using Flask's development server in *debug* mode, and the containers lack security hardening (running as the `root` user on base images with a large attack surface).

### Components

#### 1. Frontend
* **Port:** Exposes the web interface on internal port `8080`.
* **Deployment:** In the `docker-swarm.yml` file, this port is mapped to port `80` (standard web port) to simplify browser access.
* **Communication:** Consumes the backend API using the Docker Swarm service name for host resolution, leveraging the platform's native load balancing.

#### 2. Backend
* **Port:** Exposes the API on port `5000` under the `/api` endpoint.
* **Communication:** Designed to receive requests from the frontend via the URL configured through initialization parameters.
