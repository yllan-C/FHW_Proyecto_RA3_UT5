# EJERCICIO 4. Diseño de una plantilla de informe técnico.

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
