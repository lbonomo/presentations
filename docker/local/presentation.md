---
marp: true
theme: default
paginate: true
# backgroundImage: url('https://marp.app/assets/hero-background.jpg')
# paginate: false
# footer: 
header: ![](./assets/images/docker.svg)![](./assets/images/humandecode.svg)
---
<style>   

	@font-face{
		font-family:"Gilroy W05 Bold";
		src:url("assets/fonts/Gilroy-W05-Bold.woff2") format("woff2"),url("assets/fonts/Gilroy-W05-Bold.woff") format("woff");
	}

    @font-face{
        font-family:"Gilroy W05 Light";
        src:url("assets/fonts/Gilroy-W05-Light.woff2") format("woff2"),url("assets/fonts/Gilroy-W05-Light.woff") format("woff");
    }	

	:root {
		--black: #3c3c3c;
		--white: #f4f4f4;
		--purple: #383182;
		--purple-light: #7b47f3;
		--coral: #f96e62;
	}
	
	div#p svg foreignObject section {
		font:32px/36px "Gilroy W05 Light";
	}

	body {
		font-family:"Gilroy W05 Light";
	}

	header  {
    	display: flex;
    	justify-content: space-between;
    	width: calc( 100% - 60px);
	}

	header img {
		display: block;
	}

	section {
		font: 32px/36px sans-serif;
		color: var(--black);
		font-weight: 150;
	}

	section h1,
	section h2,
	section h3,
	section h4,
	section h5 {
		font-family:"Gilroy W05 Bold";
		color: var(--black);
	}

	section.cover {
		background-color: var(--white);
		color: var(--black);
	}

	section.cover h1,
	section.cover h2
	{
		margin: 0 auto;
		padding: 0;
		font-weight: 300;
	}

	section.cover h1 {
		color: var(--purple);
		font: 172px/176px "Gilroy W05 Bold";
		font-size: 172px;
	}
	
	section.cover h2 {
		color: var(--coral);
		font: 64px/64px "Gilroy W05 Bold";
	}

	section.thanks h1 {
		font: 172px/176px "Gilroy W05 Bold";
		color: var(--coral);
		font-weight: 150;
		margin: 1rem auto;
	}

	section img {
		background-color: #fff0;
	}
</style>

<!-- _class: cover -->
# Docker
## para desarrolladores

---
## Alcances
Vamos a ver docker solo en local, como herramienta para desarrollar.
 - Es un proveedor de contenedores aislados.
 - 
## Limitaciones
 - Solo para plataformas de 64bit

---
# Que onda en MAC y Windows?
En Mac y Windows el soporte para instancias Linux no es nativo.
Docker Desktop agrega una capa de "virtualización"

## Que pasa con Docker Desktop? Tengo que pagar?
 - *Si* tu empresa tine más de 250 empleados.
 - *Si* tu empresa factura más de 10.000.000 anuales 🤑.

---
# Conceptos básicos
 - Contenedores OCI

---
# Contenedores
Mecanismo *ligero* de virtualización para la ejecución *aislada* de *procesos* dentro de un mismo host
 - ligero
 - aislado
   *cgroups* es una característica del kernel de Linux que nos permite limitar, medir y aislar el uso de recursos de un conjunto de procesos.
 - procesos

 `Docker > containerd > runC`

---
# Alternativas
 - Podman
   - pod
   - root
 - OpenVZ.
 - VirtualBox.
 - LXC (contenedores de Linux)
 - Registro de contenedores de Microsoft Azure.
 - Ranchero.
---
# Imágenes
 - Inmutable

## Docker Hub

### Alpine

### Traefik
https://doc.traefik.io/traefik/
https://hub.docker.com/_/traefik

`https://doc.traefik.io/traefik/`

---
# Dockerfile

`docker run -rm -it debian:latest bash`
 - rm: Eliminar cuando termina.
 - 

---


---
# .dockerignore
https://docs.docker.com/engine/reference/builder/

---
# Network

```bash
$ docker network create example01
```

 - `--network-alias`
---
# Ejemplos chulos

`docker run --rm --name db -e MYSQL_ALLOW_EMPTY_PASSWORD=yes -e MYSQL_DATABASE=app -d mariadb:latest`

---
# Docker Compose
---
# Preguntas?
<!-- _class: thanks -->
---
# Orquestadores
 - Docker Swarm ☠️
 - Docker Compose
 - Openshift
 - Kubernetes
---
# En la nube
 - AWS: ECS, EKS, Fargate
 - Google Cloud: GKE
 - Azure: AKS



# Alpine
 - `docker pull node:current-bullseye`
 - `docker pull node:current-alpine3.15`

```bash
$ docker image list node
REPOSITORY   TAG                  IMAGE ID       CREATED      SIZE
node         current-bullseye     0326e5cd53ea   2 days ago   991MB
node         current-alpine3.15   84c277656e40   2 days ago   168MB
$ docker run node:current-bullseye node --version
v17.7.1
$ docker run node:current-alpine3.15 node --version
v17.7.1
```

