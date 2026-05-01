#  Portada

- Alumno/a: _Yllán Cazorla Más_
- Puesto/Equipo asignado:1
- Fecha: _01/05/2026_
- Módulo: **Fundamentos de Hardware (1º ASIR)**
- Unidad: **UT5**
- Reto: **Reto 03 Preparacion tecnica —**

![alt text](../assets/portada/65328ddf-5c32-4b44-833d-6f6c06bcfdca.jpg)

## EJERCICIO 1. Identificación del equipo y del sistema


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


## EJERCICIO 2. Comprobación del estado del disco duro y de la memoria RAM.

**Investiga herramientas que permitan comprobar el estado físico y lógico del disco duro, así como el estado de la memoria RAM del equipo.**

**Debes investigar, al menos, las siguientes herramientas:**

**Para cada herramienta deberás explicar:**

* Qué comprueba exactamente.
* Si se utiliza desde entorno gráfico, desde terminal o desde el arranque del equipo.
* Qué tipo de errores puede detectar.
* Qué resultados indicarían que el equipo está en buen estado.
* Qué resultados indicarían que existe un problema.

Además, deberás explicar qué es la información **S.M.A.R.T.** de un disco duro y por qué es especialmente importante revisarla en ordenadores antiguos.

### **Información S.M.A.R.T.**

* **Qué es:** Tecnología de autodiagnóstico integrada en discos duros y SSDs que registra su salud y desgaste.
* **Importancia:** En ordenadores antiguos es vital revisarla para predecir un fallo del disco inminente y evitar la pérdida de datos antes de que ocurra.


### **1. smartmontools (`smartctl`)**

* **Comprueba:** Los registros internos de salud S.M.A.R.T. del disco.
* **Entorno:** Terminal.
* **Errores:** Sectores defectuosos o fallos mecánicos.
* **Buen estado:** Resultado general `PASSED` y cero sectores reasignados.
* **Problema:** Resultado `FAILED` o números altos en tasas de error.

### **2. GSmartControl**

* **Comprueba:** Es la versión visual (interfaz gráfica) de `smartctl`.
* **Entorno:** Entorno gráfico.
* **Errores:** Fallos de S.M.A.R.T. y sectores dañados.
* **Buen estado:** Salud marcada como `PASSED` en color verde.
* **Problema:** El disco o sus atributos aparecen resaltados en rojo o rosa.

### **3. memtest86+**

* **Comprueba:** La integridad física del 100% de la memoria RAM.
* **Entorno:** Arranque del equipo (desde un USB/CD, antes de cargar el sistema operativo).
* **Errores:** Módulos de RAM defectuosos o ranuras de la placa base dañadas.
* **Buen estado:** Columna de errores a `0` tras completar los ciclos de prueba.
* **Problema:** Aparición de líneas rojas con direcciones de memoria fallidas.

### **4. memtester**

* **Comprueba:** La estabilidad de la memoria RAM libre disponible.
* **Entorno:** Terminal (dentro del sistema operativo).
* **Errores:** Bits defectuosos o inestabilidad de la memoria bajo carga.
* **Buen estado:** Todas las pruebas devuelven el mensaje `ok`.
* **Problema:** Mensajes de `FAILURE` en alguna prueba.

### **5. badblocks**

* **Comprueba:** La superficie física del disco duro escaneando bloque por bloque.
* **Entorno:** Terminal.
* **Errores:** Daños físicos irrecuperables en los platos del disco duro o celdas del SSD.
* **Buen estado:** Finaliza indicando `0 bad blocks found`.
* **Problema:** Imprime una lista de números en pantalla (sectores muertos a los que no se puede acceder).

## EJERCICIO 3. Comprobación de rendimiento, temperaturas, red y estabilidad.

**Investiga herramientas que permitan comprobar si el equipo funciona de forma estable después de instalar Linux.**

Para cada herramienta deberás indicar:

* Cuál es su función principal.
* Qué información aporta al técnico.
* Un ejemplo básico de uso.
* Qué datos deberían incluirse en un informe final de comprobación.

También deberás proponer una pequeña batería de pruebas teóricas que realizarías en un ordenador antiguo para comprobar:

* Temperatura del procesador.
* Uso de memoria RAM.
* Estado de la red.
* Estado del disco.
* Estabilidad general del sistema.

**Debes investigar, al menos, las siguientes herramientas:**

### **1. lm-sensors (y el comando `sensors`)**

* **Función principal:** Detectar y leer los sensores de hardware de la placa base, procesador y tarjeta gráfica.
* **Información que aporta al técnico:** Muestra la temperatura en tiempo real, el voltaje de los componentes y la velocidad de rotación de los ventiladores (RPM). Es crucial para detectar sobrecalentamientos.
* **Ejemplo básico de uso:** `sensors` (Muestra las lecturas actuales de todos los sensores detectados).
* **Datos para el informe:** Temperatura del procesador en reposo (Idle) y bajo carga, y si los ventiladores giran a la velocidad adecuada.

### **2. htop**

* **Función principal:** Es un monitor del sistema interactivo (un administrador de tareas) para la terminal.
* **Información que aporta al técnico:** Permite ver en tiempo real el consumo de CPU por núcleo, el uso de memoria RAM, la memoria Swap y los procesos que están consumiendo más recursos.
* **Ejemplo básico de uso:** `htop`
* **Datos para el informe:** Consumo de memoria RAM con el sistema recién arrancado (sin aplicaciones abiertas) y porcentaje de uso del procesador en reposo.

### **3. stress-ng**

* **Función principal:** Herramienta para someter al sistema a pruebas de estrés (carga máxima de trabajo).
* **Información que aporta al técnico:** Sirve para forzar el hardware al 100% y comprobar si el sistema es estable o si se apaga/congela por problemas térmicos o de alimentación.
* **Ejemplo básico de uso:** `stress-ng --cpu 4 --timeout 60s` (Estresa 4 núcleos de la CPU durante 60 segundos).
* **Datos para el informe:** Confirmación de si el equipo superó la prueba de estrés sin reinicios inesperados ni bloqueos (Kernel Panic).

### **4. iperf3**

* **Función principal:** Medir el ancho de banda máximo real de una red IP.
* **Información que aporta al técnico:** Indica la velocidad real de transferencia entre dos equipos. Es ideal para descartar que una conexión lenta se deba a un cable de red en mal estado o a un puerto defectuoso.
* **Ejemplo básico de uso:** `iperf3 -c 192.168.1.100` (Se conecta a un equipo que actúa como servidor para medir la velocidad).
* **Datos para el informe:** Tasa de transferencia real obtenida en la red local (por ejemplo, 940 Mbits/sec) y pérdida de paquetes.

### **5. ethtool**

* **Función principal:** Consultar y controlar la configuración de los controladores y el hardware de las tarjetas de red por cable (Ethernet).
* **Información que aporta al técnico:** Muestra a qué velocidad ha negociado la tarjeta de red con el router/switch (10 Mbps, 100 Mbps o 1000 Mbps) y si el enlace físico está activo.
* **Ejemplo básico de uso:** `ethtool enp3s0` (Sustituyendo 'enp3s0' por el nombre de la interfaz de red).
* **Datos para el informe:** Velocidad negociada del puerto Ethernet y estado del enlace (Link detected: yes/no).

### **6. ping**

* **Función principal:** Comprobar la conectividad a nivel de red con otro equipo o servidor en Internet usando paquetes ICMP.
* **Información que aporta al técnico:** Confirma si el equipo tiene salida a Internet o acceso a la red local, y mide la latencia (retraso) de la conexión.
* **Ejemplo básico de uso:** `ping -c 4 8.8.8.8` (Envía 4 paquetes a los servidores DNS de Google).
* **Datos para el informe:** Porcentaje de paquetes perdidos (Packet loss) y latencia media en milisegundos (ms).

### **7. GParted**

* **Función principal:** Editor de particiones gráfico.
* **Información que aporta al técnico:** Permite visualizar de forma muy intuitiva la estructura del disco duro, el sistema de archivos de cada partición, el espacio ocupado/libre y realizar alineaciones o redimensiones de forma segura.
* **Ejemplo básico de uso:** Se ejecuta desde el menú de aplicaciones gráficas del sistema o mediante `sudo gparted` en terminal.
* **Datos para el informe:** Tabla de particiones utilizada (MBR o GPT) y sistemas de archivos detectados (ext4, btrfs, ntfs, etc.).

### **8. HardInfo (o HardInfo2)**

* **Función principal:** Generador de perfiles de sistema y herramienta de benchmarking (comparativa de rendimiento) en entorno gráfico.
* **Información que aporta al técnico:** Agrupa toda la información de hardware (similar a AIDA64 en Windows) y permite realizar pequeños test de rendimiento para comparar la CPU con otros modelos de referencia.
* **Ejemplo básico de uso:** Se ejecuta desde el entorno gráfico buscando "System Profiler and Benchmark" o en terminal con `hardinfo`.
* **Datos para el informe:** Resumen global del hardware instalado y puntuaciones obtenidas en los benchmarks de CPU (ej. CPU Blowfish, CPU Crypto).


### **Batería de Pruebas Teóricas para un Ordenador Antiguo**

Para asegurar que un ordenador antiguo recuperado con Linux es estable y apto para ser entregado a un usuario, realizaría la siguiente rutina:

1. **Estado del disco:**
   * Abriría la herramienta **Discos** (GNOME Disks) o usaría `smartctl` (del ejercicio anterior) para leer los datos S.M.A.R.T. y confirmar que no hay sectores defectuosos. Revisaría la estructura con **GParted** .
2. **Estado de la red:**
   * Usaría **ping** hacia el router para comprobar que no hay cortes en la red Wi-Fi y **ethtool** para confirmar que el puerto Ethernet negocia a la velocidad máxima que soporta la placa.
3. **Uso de memoria RAM:**
   * Abriría **htop** recién arrancado el equipo. En un ordenador antiguo con Linux (ej. XFCE o LXQt), el consumo en reposo no debería superar los 500-800 MB de RAM.
4. **Temperatura del procesador y Estabilidad general:**
   * Dejaría **htop** abierto en una ventana y lanzaría el comando `sensors` en otra para ver la temperatura inicial.
   * Ejecutaría **stress-ng** durante 10 o 15 minutos para poner la CPU al 100%.
   * Durante la prueba, vigilaría `sensors` periódicamente: si la temperatura sube de 85-90ºC o el equipo se apaga de golpe, indicaría que la pasta térmica está seca, el disipador está sucio o la fuente de alimentación falla. Si aguanta los 15 minutos sin problemas, el sistema es completamente estable.

## EJERCICIO 4. Diseño de una plantilla de informe técnico.

Diseña una plantilla de informe técnico que usarás en la segunda fase práctica. Esta plantilla deberá servir para comprobar si un ordenador está apto o no apto para su uso después de instalar Linux.

La plantilla deberá incluir, como mínimo, los siguientes apartados:

* Datos del alumno o alumna.
* Identificación del equipo.
* Características del hardware: CPU, RAM, disco, tarjeta gráfica y red.
* Versión de Linux instalada.
* Estado del disco duro.
* Estado de la memoria RAM.
* Comprobación de red.
* Comprobación de temperaturas y estabilidad.
* Incidencias detectadas.
* Conclusión final: apto, apto con observaciones o no apto.

La plantilla puede realizarse en forma de tabla y deberá estar preparada para ser utilizada posteriormente en un equipo real.

### 1. Datos Generales e Identificación


| **Campo**                        | **Detalle**                                                  |
| ---------------------------------- | -------------------------------------------------------------- |
| **Fecha de comprobación:**      | [DD/MM/AAAA]                                                 |
| **Alumno/a (Técnico):**         | [Nombre y Apellidos]                                         |
| **Identificación del Equipo:**  | [Marca, Modelo, Número de Serie o Etiqueta Interna]         |
| **Versión de Linux instalada:** | [Distribución, Entorno de Escritorio y Versión del Kernel] |


### 2. Características del Hardware


| **Componente**              | **Especificaciones detectadas**             | **Comando sugerido**    |
| ----------------------------- | --------------------------------------------- | ------------------------- |
| **Procesador (CPU):**       | [Modelo, Núcleos, Frecuencia base]         | `lshw` / `inxi -C`      |
| **Memoria RAM:**            | [Capacidad Total y tipo, ej. 8GB DDR3]      | `free -h` / `dmidecode` |
| **Almacenamiento (Disco):** | [Tipo (HDD/SSD), Capacidad Total, Marca]    | `lsblk` / `lshw`        |
| **Tarjeta Gráfica (GPU):** | [Marca, Modelo, Controlador en uso]         | `lspci` / `inxi -G`     |
| **Tarjeta de Red:**         | [Ethernet / Wi-Fi, Modelo, Velocidad máx.] | `lspci` / `ethtool`     |

### 3. Comprobación de Diagnóstico y Estabilidad


| **Prueba**                 | **Resultado / Valores Obtenidos**                    | **Estado (Apto/Fallo)** |
| ---------------------------- | ------------------------------------------------------ | ------------------------- |
| **Estado del Disco Duro:** | Sectores reasignados: [X] - Resultado SMART: [X]     | [ ]                     |
| **Estado de la RAM:**      | Ciclos pasados: [X] - Errores encontrados: [X]       | [ ]                     |
| **Comprobación de Red:**  | IP asignada: [Sí/No] - Ping: [X] ms - Vel: [X] Mbps | [ ]                     |
| **Temperaturas (Reposo):** | CPU: [X] °C - GPU: [X] °C                          | [ ]                     |
| **Temperaturas (Carga):**  | CPU máx: [X] °C (tras X minutos de estrés)        | [ ]                     |
| **Estabilidad General:**   | ¿Se apaga o congela bajo estrés? [Sí/No]          | [ ]                     |


### 4. Conclusión y Observaciones


| **Apartado**                | **Detalle**                                                                                                                                                      |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Incidencias detectadas:** | *[Describe aquí cualquier problema: ruidos raros del disco, puertos USB que no funcionan, teclas rotas, sobrecalentamiento, etc. Si no hay, indica "Ninguna".]* |
| **Medidas correctivas:**    | *[¿Qué has hecho para arreglarlo? Ej: Cambio de pasta térmica, limpieza de ventiladores, sustitución de módulo RAM.]*                                       |

**CONCLUSIÓN FINAL DEL EQUIPO:**
*(Marca con una X la opción correspondiente)*

* [ ] **APTO:** El equipo funciona perfectamente, es estable y el hardware está sano.
* [ ] **APTO CON OBSERVACIONES:** El equipo es funcional, pero tiene limitaciones o defectos menores (ej.  disco duro con desgaste pero usable).
* [ ] **NO APTO:** El equipo presenta fallos críticos de hardware (RAM defectuosa, disco a punto de fallar, sobrecalentamiento extremo que apaga el equipo).
