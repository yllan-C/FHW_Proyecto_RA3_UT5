# EJERCICIO 1. Identificación del equipo y del sistema


**Investiga para qué sirven las siguientes herramientas y comandos relacionados con la identificación del hardware y del sistema operativo:**
 **Para cada herramienta deberás indicar:**

* Qué información proporciona.
* Por qué puede ser útil para un técnico informático.
* Un ejemplo de comando que se podría ejecutar.
* Qué datos importantes habría que anotar en un informe técnico.




#### **1. inxi**

* **Qué hace:** Resumen completo del sistema (hardware y software).
* **Utilidad:** Vistazo rápido general para un diagnóstico inicial.
* **Ejemplo:** `inxi -F`
* **Para el informe:** CPU, gráfica, versión del Kernel y distribución.

#### **2. lshw**

* **Qué hace:** Lista detallada de todo el hardware.
* **Utilidad:** Ver capacidades máximas (ej. cuánta RAM admite) y modelos exactos.
* **Ejemplo:** `sudo lshw -short`
* **Para el informe:** Modelo de la placa base y RAM instalada.

#### **3. dmidecode**

* **Qué hace:** Muestra datos de fábrica de la placa base (DMI/SMBIOS).
* **Utilidad:** Obtener números de serie y versión de BIOS sin abrir el PC.
* **Ejemplo:** `sudo dmidecode -t bios`
* **Para el informe:** Número de serie del equipo y versión de la BIOS.

#### **4. lspci**

* **Qué hace:** Lista los componentes internos conectados por PCI (gráfica, red, sonido).
* **Utilidad:** Identificar el modelo exacto de una tarjeta para buscar sus drivers.
* **Ejemplo:** `lspci`
* **Para el informe:** Modelo exacto de la tarjeta gráfica y de red.

#### **5. lsusb**

* **Qué hace:** Lista los periféricos conectados por USB.
* **Utilidad:** Comprobar si el ordenador detecta físicamente un ratón, teclado, etc.
* **Ejemplo:** `lsusb`
* **Para el informe:** ID del fabricante y producto de los dispositivos.

#### **6. uname**

* **Qué hace:** Muestra información del núcleo (kernel) del sistema operativo.
* **Utilidad:** Saber si el sistema es de 32 o 64 bits y qué kernel usa.
* **Ejemplo:** `uname -a`
* **Para el informe:** Arquitectura del procesador y versión del Kernel.

#### **7. lsblk**

* **Qué hace:** Muestra los discos duros, pendrives y sus particiones.
* **Utilidad:** Ver cómo está dividido el disco y dónde está montado cada volumen.
* **Ejemplo:** `lsblk`
* **Para el informe:** Estructura de particiones y tamaños de disco.

#### **8. df**

* **Qué hace:** Muestra el espacio libre y usado en los discos.
* **Utilidad:** Vigilar si el equipo se está quedando sin almacenamiento.
* **Ejemplo:** `df -h`
* **Para el informe:** Capacidad total del disco y porcentaje de uso.

#### **9. free**

* **Qué hace:** Muestra el estado de la memoria RAM y Swap (intercambio).
* **Utilidad:** Detectar problemas de lentitud por falta de memoria RAM.
* **Ejemplo:** `free -h`
* **Para el informe:** RAM total instalada y tamaño de la partición Swap.

