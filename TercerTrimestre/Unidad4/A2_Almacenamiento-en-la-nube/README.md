
# Almacenamiento en la nube

---

## 1. Nube ajena

Practicaremos el almacenamiento usando la nube de un proveedor externo.

Pasos a realizar:
* Elegir alguna de las siguientes herramientas:
  * `DropBox`
  * `Google Drive`
  * `OneDrive`
  * `Mega`

Yo voy a utilizar `Google Drive`

![](./images/.png)

* Realizar la instalación y configuración de la herramienta elegida sobre:
  * `Windows`
  * `GNU/Linux`
  * `Android`
* Mostraremos su uso mediante ejemplos.

A continuaciónles mostraré un vídeo de unos sencillos pasos de como subir y crear archivos facilmente en la nube.

![](./images/.png)

---

## 2. Nube propia con NextCloud Server en OpenSUSE Leap

Vamos a utilizar un servicio de almacenamiento libre, asi qque utilizaremos NextCloud, aunque tambien pueden utilizar ownCloud.

![](./images/.png)

### 2.1. Servidor Web Apache: Instalación y configuración

Comando | Explicación
------- | -----------
`zypper in apache2` | Instalar Apache2.
`systemctl start apache2` | Iniciar Apache2.
`systemctl enable apache2` | Inicio automático del servicio apache después de reiniciar.

![Instalar Apache2](./images/.png)

* Abrimos el acceso Web desde el cortafuegos
  * Vamos a `Yast` -> `Cortafuegos`
  * Añadir en `Servicios Autorizados` de la `Zona externa` a: `apache2`, `http`, `https`.

![](./images/.png)

### 2.2. PHP: Instalación y configuración

Comando | Explicación
------- | -----------
`zypper in php7 php7-mysql apache2-mod_php7` | Instalar PHP7.
`a2enmod php7` | Habilitar mod-php

![](./images/.png)

### 2.3. Database MariaDB

Instalación:

Comando | Explicación
------- | -----------
`zypper in mariadb mariadb-tools` | Instalar MariaDB.
`systemctl start mariadb` | Iniciar el servicio de MariaDB.
`systemctl enable apache2` | Inicio automático del servidor MariaDB en cada inicio.
`mysql_secure_installation` | Configurar el servicio MariaDB con seguridad mejorada.

![](./images/.png)

Configuración para NextCloud:

> Incluir exactamente las líneas de comandos posteriores, con el punto y coma en las que lo tengan.

1. `mysql -u root -p`

2. `create database nextcloud;` Crear la base de datos de NextCloud.

3. `create user nextclouduser@localhost identified by 'some-password-here';` Crear el nuevo usuario de NextCloud.

4. `grant all privileges on nextcloud.* to nextclouduser@localhost identified by 'some-password-here';`. Conceder los privilegios necesarios sobre el usuario de NextCloud.

> Sustituir 'some-password-here' por la contraseña deseada.

5. `exit;` Salir de la configuración de la base de datos.

### 2.4. NextCloud



![](./images/.png)

---

## 3. Comprobar vía web



![](./images/.png)

---

## 4. NextCloud Desktop Client



![](./images/.png)
