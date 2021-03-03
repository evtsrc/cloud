# Configuración de nuestra infraestructura

## Índice
- [Configuración de nuestra infraestructura](#configuración-de-nuestra-infraestructura)
  - [Índice](#índice)
    - [Servidor web nginx (**frontend**)](#servidor-web-nginx-frontend)
    - [Servidor de backend nuestra "app" (**backend**)](#servidor-de-backend-nuestra-app-backend)

Para poder evaluar nuestra instalación y mostrar que está funcionando, tendremos que hacer una serie de pasos para configurarla, muy similares a lo que se hizo en el ejercicio 1.

### Servidor web nginx (**frontend**)

En este caso, esto tendremos que hacerlo una única vez, ya que las instalación y modificaciones que realicemos perdurarán incluso después de apagar o reiniciar la máquina.

Instalaremos nginx como servidor web en la máquina frontend:

```
sudo apt install nginx
```

Al igual que en el ejercicio, añadimos lo siguiente en el fichero de configuración de nginx, para ser capaces de acceder a nuestra "app" desde internet, pasando a través del frontend. Para ello editaremos el mismo fichero de configuración:

```
sudo nano /etc/nginx/sites-available/default
```

Luego tendremos que añadir las siguientes líneas de configuración, justo después de donde está un apartado que empieza por Location /

```
        location /myapp {
                proxy_pass http://<ip_privada_backend>:8080/;
        }
```
---
**AVISO**: en el caso de que estemos con la parte tres y cuatro de la práctica, la IP privada de backend, debe ser la del balanceador y no la de ninguno de los servidores de backend.

---

Aquí podéis ver como quedaría el fichero de configuración, tras añadir estas tres líneas, con la IP del ejemplo anterior:

![Ejercicio 1 nginx configuración](./Ejercicio%201/images/Ejercicio1_nginx_proxy_pass.jpg "Ejercicio 1 nginx configuración")

Una vez hecha la configuración y guardados los cambios en el fichero (salid con Control-X y responder con Y para salir salvando los cambios), tendremos que reiniciar nginx para que los tenga en cuenta, con el siguiente comando:

```
sudo systemctl restart nginx
```

### Servidor de backend nuestra "app" (**backend**)

En este caso en concreto, este paso lo tendremos que repetir cada vez que nos salgamos de la conexión SSH o reiniciemos o paremos la máquina. Este comando lo tenemos que ejecutar y dejar funcionando, cada vez que queramos comprobar el funcionamiento o en la correción de la práctica.

Imitaremos una aplicación en nuestras máquinas de backend (en cada una de ellas si estamos en la parte 4 de la práctica), de forma parecida al ejercicio, salvo que en este caso lo que mostraremos en el fichero será el nombre del servidor. Lo haremos con los siguientes comandos, en cada uno de los servidores de backend:

```
echo `uname -n` > nombre.txt
python3 -m http.server 8080
```

Y como se indica al principio, este comando se quedará en funcionamiento siembre y cuando no lo interrumpamos (Control-C), cortemos la conexión SSH y/o apaguemos/reinicimos la máquina.