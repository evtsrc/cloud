# Práctica Cloud

## Índice
- [Práctica Cloud](#práctica-cloud)
  - [Índice](#índice)
  - [Prerequisitos](#prerequisitos)
    - [Linux (Ubuntu)](#linux-ubuntu)
      - [*Cliente de Azure*](#cliente-de-azure)
      - [*Cliente Terraform*](#cliente-terraform)
    - [Windows](#windows)
      - [*Cliente de Azure*](#cliente-de-azure-1)
      - [*Cliente Terraform*](#cliente-terraform-1)
  - [Práctica](#práctica)
  - [Configuración necesaria para comprobar la práctica](#configuración-necesaria-para-comprobar-la-práctica)
  - [Evualuación de la práctica](#evualuación-de-la-práctica)

## Prerequisitos

Esta práctica se puede realizar tanto sobre una máquina con Linux, como en una con Windows. Pero es preferible que utilicéis una máquina virtual con Ubuntu, ya que la necesitaréis para las prácticas de Dockers y Kubernetes. Los requisitos de instalación de esa máquina los tenéis explicados en el apartado de la práctica de [Kubernetes](https://github.com/evtsrc/kubernetes#práctica-kubernetes).

### Linux (Ubuntu)

Pasos para instalar el cliente de Azure y de Terraform en una máquina Ubuntu Linux.

#### *Cliente de Azure*

1. Es necesario tener los paquetes de curl y git instalados:

    ```
    sudo apt install curl git
    ```

2. Realizaremos la instalación del cliente de Azure, usando directamente el script que tienen preparado para Ubuntu, el cual añadirá el repositorio para poder hacer la instalación mediante el comando apt:

    ```
    curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
    ```

3. Podremos comprobar que se ha instalado correctamente de la siguiente manera:

    ```
    az --version
    ```

#### *Cliente Terraform*

1. Descargaremos el ejecutable para nuestra versión de SO [aquí](https://www.terraform.io/downloads.html). Lo siguiente sería con la que hay ahora mismo disponible para Linux 64 bits:

    ```
    wget https://releases.hashicorp.com/terraform/0.14.5/terraform_0.14.5_linux_amd64.zip
    ```
2. Descomprimimos el zip y llevamos el ejecutable a una ruta dentro de nuestro PATH:

    ```
    unzip terraform_0.14.5_linux_amd64.zip
    sudo mv terraform /usr/local/bin
    rm -f terraform_0.14.5_linux_amd64.zip
    ```
3. Y comprobamos que está todo correcto:

    ```
    terraform -version
    ```

### Windows

También se puede tener ambos clientes en entornos Windows, de la siguiente manera

#### *Cliente de Azure*

1. Descargaremos el instalador desde [aquí](https://aka.ms/installazurecliwindows)
   
2. Ejecutamos el fichero para instalarlo en nuestro equipo.
   
3. Podremos comprobar su instalación, desde una ventana de símbolo de sistema:
   
   ```
   az --version
   ```

#### *Cliente Terraform*

1. Descargaremos el paquete para nuestra versión de SO [aquí](https://www.terraform.io/downloads.html).
2. Dentro del fichero zip descargado, tenemos el ejecutable, lo descomprimimos en cualquier carpeta accesible a nuestro usuario y lo podemos ejecutar desde ahí.
3. Comprobamos que lo podemos ejecutar sin problemas:

    ```
    terraform -version
    ```

## Práctica

La práctica se describe en el [siguiente enlace](Práctica.md).

## Configuración necesaria para comprobar la práctica

Lo necesario para configurar nuestro servidor de frontend y los de backend está en el [siguiente enlace](Configuración.md).

## Evualuación de la práctica

Las pruebas y el método de evaluación, se describen en el [siguiente enlace](Evaluación.md)