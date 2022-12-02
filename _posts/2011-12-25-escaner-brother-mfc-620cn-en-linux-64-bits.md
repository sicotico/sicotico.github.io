---

title: "Escaner Brother MFC-620CN en Linux 64-bits"
date: "2011-12-25"
categories: 
  - "sin-categoria"
---

Hace tiempo hice un post parecido , rondaba el 2008 y aun no había entrado en el mundo de los 64bits muy a fondo. Utilizando ia32libs podía utilizar algunos drivers de 32.

Tiempo ha pasado y esto ha evolucionado , Ubuntu también y gracias a ello instalar esta impresora se convertía en un juego de niños. Tenemos los drivers empaquetados en el repositorio oficial. Sigue existiendo el centro de [documentación para Linux de Brother](https://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html "Brother Drivers for Linux distributions")

Ahora ha tocado actualizar esa información para la nueva Ubuntu 11.10 Oneric que por razones desconocidas para mí las librerías no se situaban en la carpeta correcta.

**NOTA:** Información interesante tener anotada respecto al hardware son su **Product\_ID** y **Vendor\_ID** , fácilmente obtenibles con `lsusb`

Las instrucciones de instalación y la descarga del paquete deb

[https://welcome.solutions.brother.com/bsc/public\_s/id/linux/en/instruction\_scn1a.html](https://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1a.html)

FAQ de Brother para el caso especial de 11.10

[https://welcome.solutions.brother.com/bsc/public\_s/id/linux/en/faq\_scn.html#f00101](https://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

Permisos a los usuarios para acceder al dispositivo

[https://welcome.solutions.brother.com/bsc/public\_s/id/linux/en/instruction\_scn1c.html#u9.10](https://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

_En el caso de tener algún problema para escanear , porque no sea detectado utilizar estos pasos_

Foro Alemán donde detalla más a fondo donde aplicar los permisos en udev

- Apliqué las variantes 40 y 55 que consisten en crear dos ficheros rules de udev
- Creé el fichero de configuración de sane para Brother , ya que no existía.Aquí es donde utilizaremos la información

**/etc/sane.d/brother.conf**

#Ubuntu Natty

# Brother USB
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
usb 04f9 **01e9**
