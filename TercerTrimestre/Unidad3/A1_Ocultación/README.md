
# Ocultación de la información

---

## 1. Encriptación

### 1.1. Encriptado simétrico

* Antes que nada, nos aseguramos tener instalado GPG

![GPG2 Instalado](./images/gpg2-instalado.png)

* Creamos un fichero de texto llamado `/home/jorge/mensaje1-jorge24.txt`.
  * Escribimos dentro nuestro nombre, fecha de hoy y el título de una película.

![Mensaje 1](./images/mensaje1.png)

* Tras esto, hacemos una encriptación simétrica con GPG.
* Enviamos el fichero encriptado al compañero para que lo desencripte.

![Desencriptación](./images/desencriptado.png)

### 1.2. Encriptado asimétrico

**Alumno1**

Genera un par de claves pública/privada.
  * `gpg --gen-key` para generar un par de claves pública/privada.
  * Consultar las claves públicas con alguno de los siguientes comandos `gpg --list-public-keys`, `gpg --list-keys` o `gpg -k`. La línea `pub 2048/IDNUMBER` muestra la información con el identificador de la clave pública.
  * `tree .gnupg`. Comprobaremos que se crea un directorio oculto, dentro del home de nuestro usuario con el nombre `.gnugp`. Ahí es donde se guarda la información de claves de GPG para nuestro usuario.

**Alumno2**

* Crea un fichero de texto `mensaje2-alumno24.txt`.
    * Escribir dentro el nombre del alumno, la fecha de hoy y una frase/mensaje.

![Mensaje 2](./images/mensaje2.png)

* Importa la clave pública del compañero.
    * `gpg --import nombre-alumno23.pub.gpg`

![Importar clave](./images/importada.png)

* Hace una encriptación asimétrica con GPG con la clave pública recibida.
    * `gpg --list-public-keys`, para ver las claves públicas que tenemos.
    * `gpg --encrypt --recipient PUBLIC_KEY_IDNUMBER mensaje2-nombre-alumnoXX.txt`
* Alumno2 envía el fichero a alumno1 para que lo desencripte.

**Alumno1**

* Alumno1 desencripta el fichero `gpg -d mensaje2-alumno23.txt.gpg`.

---

## 2. Firma

Hacemos lo siguiente:

* Creamos el documento `firma-nombre-alumnoXX.txt`.
    * Escribir dentro el nombre del alumno, la fecha de hoy y un grupo de música.
* Vamos a firmar digitalmente el documento en modo ASCII.
    * `gpg --clearsign firma-nombre-alumnoXX.txt`
* Consultar el fichero que se ha generado con la firma `firma-alumnoXX.txt.asc`
* Comprobar que la firma es correcta.
    * `gpg --verify firma-nombre-alumnoXX.txt.asc`

![Firma correcta](./images/firma-verificada.png)

* Modificamos el documento `firma-nombre-alumnoXX.txt.asc`.
* Comprobamos que ahora el fichero tiene la firma incorrecta.

![Firma incorrecta](./images/firma-incorrecta.png)

---

## 3. Esteganografía

> [De andar por casa (zip y cat)](http://www.linuxhispano.net/2014/07/03/ocultar-datos-en-imagenes-esteganografia-de-andar-por-casa/)

* Consultamos el enlace sobre estenografía de "Andar por casa (zip y cat)".
* Creamos un fichero de texto con un mensaje oculto (`secreto-nombre-alumnoXX.txt`).
    * Escribimos dentro el nombre del alumno, la fecha de hoy y un refrán o frase famosa.
* Creamos un fichero zip con el mensaje oculto.

![Zip secreto](./images/zip-secreto.png)

* Descargamos una `imagen1-nombre-alumnoXX.png` que nos guste.
* Incrustamos el fichero zip dentro de la `imagen1-nombre-alumnoXX.png`, obteniendo un fichero `imagen2-nombre-alumnoXX.png`.
* Pasamos el fichero `imagen2-nombre-alumnoXX.png` al compañero.
* Verificamos el formato de las imágenes, bien usando el comando `file` o capturando vista de la misma.

![Fichero incrustado](./images/cat-file.png)

* El compañero debe aplicar el proceso necesario para extraer el mensaje oculto dentro de la `imagen2-nombre-alumnoXX.png`.

![Extraer mensaje oculto](./images/unzip.png)

---

## 4. Partición encriptada

### 4.1. Teoría: contenedor encriptado

Es posible crear un fichero encriptado, que a su vez puede contener directorios y ficheros manteniendo los datos de forma confidencial. La ventaja de usar un contenedor encriptado sobre encriptar particiones es que se pueden añadir sin tener que reparticionar el disco. Se montan en un dispositivo Loop y se comportan como si fueran particiones normales.

### 4.2. Proceso: partición encriptada

Por seguridad, vamos a hacer una instantánea de la MV antes de empezar con este apartado.
* Crear directorio `/home/nombre-alumno/datos-cifradosXX.d`.
* Ir a `Yast -> Particionador`. Crear una partición encriptada.
* Montar partición encriptada en la carpeta anterior.
* Reiniciar la MV para que active los cambios que hemos realizado.
* Escribir el password del contenedor para poder activarlo.
* `df -hT | grep datos-cifradosXX.d`, comprobamos que hay un dispositivo montado.
* Poner archivos dentro del contenedor.
* Reiniciar la MV.
* Comprobar a acceder a los ficheros del contenedor cuando se pone la contraseña correcta y cuando no.

![Contraseña](./images/passphrase.png)
