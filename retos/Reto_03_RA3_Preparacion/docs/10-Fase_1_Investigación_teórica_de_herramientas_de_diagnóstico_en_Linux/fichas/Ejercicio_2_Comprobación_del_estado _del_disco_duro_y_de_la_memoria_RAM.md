# EJERCICIO 2. Comprobación del estado del disco duro y de la memoria RAM.

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
