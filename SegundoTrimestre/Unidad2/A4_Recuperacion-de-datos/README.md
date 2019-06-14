
# Recuperación de datos

---

## 1. Preparar el disco roto

* Añadimos un segundo disco duro `(sdb)` a la MV OpenSUSE de 10MB con el nombre *roto*.

* Iniciamos la MV y usamos la herramienta `Particionador` de Yast, para crear una partición primaria que coja todo el segundo disco y le daremos formato `ext2`.

* Creamos el directorio `/mnt/disco_roto`.

* Consultamos el UID de nuestro usuario con `id jorge` (en mi caso).
* `mount /dev/sdb1 /mnt/disco_roto -o defaults,uid=UIDNUMBER`, monta la partición en la ruta especificada estableciendo los permisos adecuado para el usuario UID.

* Tras esto comprobamos que se ha hecho bien con:
  * `df -hT`
  * `mount | grep disco_roto`

* Copiamos/Descargamos en dicha partición `(sdb1)` 3 ficheros:
  * `FILE1`: Fichero PDF
  * `FILE2`: Imagen/foto
  * `FILE3`: Canción y/o vídeo
  * Comprobamos que están con `ls /mnt/disco_roto`
* Ahora borramos `FILE1`, `FILE2` y `FILE3` usando los comandos habituales de borrado. Si borramos por el entorno gráfico, además debemos vaciar la papelera.
* Feedback de comprobación `ls /mnt/disco_roto`

---

## 2. Clonación alfa



---

## 3. Recuperación

### 3.1. Herramientas de recuperación



### 3.2. Instalando PhotoRec



### 3.3. Recuperando con PhotoRec



---

## 4. Recuperar ficheros de texto plano



---

## 5. Borrado seguro

### 5.1. Herramientas de borrado seguro



### 5.2. Proceso de borrado seguro



---

## 6. Recuperar esquema de particionado
