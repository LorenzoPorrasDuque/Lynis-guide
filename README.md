# OPENVAS
Repositorio dedicado a una instalacion basica y uso adecuado de OPENVASS 
```mermaid
graph LR
A[User] -- WEB --> B((OPENVASS))
B --> D{Metasploitable: 2}

```
# Instalacion 
OpenVas ofrece multiples productos relacionados el escaneo de vulnerabilidades, pero en este caso solo suaremos la version free.

Esta misma puede ser descargada en el siguiente enlace https://www.greenbone.net/en/openvas-free/

Asi mismo en la pagina se puede encontrar el turorial de su instalacion

<img width="615" height="424" alt="image" src="https://github.com/user-attachments/assets/5b6f47cd-5832-4b28-af4a-3d605951ef18" />

Se accede al Wizard

<img width="619" height="409" alt="image" src="https://github.com/user-attachments/assets/9aad544d-97d5-40d6-b37c-af0e7de30eb3" />

Se crea el ussuario para la interfaz grafica y ya dependiendo de si se tiene o no una key de los otros productos se deja o se inserta esta misma key.

Ya finalmente de la instalacion podremos observarn la ip del dispositivo donde estara nuestra web interface

<img width="362" height="171" alt="image" src="https://github.com/user-attachments/assets/8f1c7cbd-d647-4700-a5ba-312082eee479" />

# Uso

Ya con la inferza instalada, iniciamos sesion con el usuario antes creado y tendremos la siguiente interfaz

<img width="2557" height="1007" alt="image" src="https://github.com/user-attachments/assets/48a2bfb4-36f7-4af7-8089-a4cf8eff991f" />

## Escaneo basico
Openvas nos da la capacidad de hacer escaneos a multiples ips o host individuales

Para ello iremos a la ventana de Configuration -> Targets, donde podremos anadir nuestros targets.

En este caso estamos usando la maquina de Metaesploitable2 que se puede encontrar en https://www.vulnhub.com/entry/metasploitable-2,29/

Una configuracion basica es la siguiente

<img width="1023" height="1190" alt="image" src="https://github.com/user-attachments/assets/081ec29e-3222-4920-b212-af1d1a667b46" />

Asi mismo hay configuraciones adicionales tales como

<img width="1026" height="624" alt="image" src="https://github.com/user-attachments/assets/06790eec-c749-4fe0-8ba6-dc7b18cbe0ae" />

Esto con el fin si somos administradores poder ir a mas profunidad, en este caso con el proposito de la herramienta, nos limitaremos a solo hacer analisis desde la ip objetivo.

# Resultados

# Metodologia 
