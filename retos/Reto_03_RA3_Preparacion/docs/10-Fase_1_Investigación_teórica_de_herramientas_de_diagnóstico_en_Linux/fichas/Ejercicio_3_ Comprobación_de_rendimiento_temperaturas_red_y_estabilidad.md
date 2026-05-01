# EJERCICIO 3. Comprobación de rendimiento, temperaturas, red y estabilidad.

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
