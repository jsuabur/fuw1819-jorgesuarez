
# iSCSI en Windows Server 2008

Vamos a montar un almacenamiento iSCSI con Windows Server 2012 (64 bits).

> *El siguiente texto está copiado de un enlace de internet*

```
Para los que no estén familiarizados con iSCSI,
digamos que es una manera de “encapsular” comandos SCSI en paquetes IP.
De esta manera podemos acceder a sistemas de almacenamiento externos
usando una red IP en lugar de los tradicionales buses SCSI
o los canales de fibra.
Es decir, una buena forma de montarnos una SAN.

La solución consta de al menos dos componentes.
Un iSCSI Initiator y un Target.
* El initiator es lo que utilizamos en el equipo que va a aceder a esos volumenes,
* El Target es lo que nos permitirá crear el sistema de almacenamiento compartido, y el que permitira el acceso a las LUNs que se hayan creado a cada cliente específico.

Generalmente esta tecnología está ya incluida en el propio hardware de los servidores y de los sistemas SAN, que ofrecen este tipo de conectividad a través de dispositivos multifunción.

Sin embargo esto no excluye que un iniciador software se pueda conectar a un Target hardware o viceversa.

El iSCSI initiator puede descargarse gratuitamente, para Windows XP y Windows server 2003. En Windows Vista y Windows Server 2008 viene ya incluido por defecto. Los iniciadores software son muy útiles en entornos virtualizados, ya que permiten a las máquinas virtuales el acceso a sistemas de tipo SAN mediante tarjetas de red, generalmente dedicadas en el host y en el guest.
```

---

## 1.

Necesitamos 2 MV's con Windows Server, en mi caso utilizaré `Windows Server 2008`.

<table text-align="center">
  <tr>
    <th>MV1</th>
    <th colspan="2">`Initiator`</th>
  </tr>
  <tr>
    <th>Interfaz de Red</th>
    <th>Red puente</th>
    <th>Red interna</th>
  </tr>
  <tr>
     <th>Nombre</th>
     <td>enp3s0</td>
     <td>san</td>
  </tr>
  <tr>
    <th>IP</th>
    <td>172.19.24.21</td>
    <td>192.168.24.22</td>
  </tr>
  <tr>
    <th>Gateway</th>
    <td>255.255.0.0</td>
    <td>NO</td>
  </tr>
</table>

![](./images/.png)

---

## 2.



![](./images/.png)

---

## 3.



![](./images/.png)

---

## 4.



![](./images/.png)

---

## 5.



![](./images/.png)
