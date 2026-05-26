# Portafolio de Sistemas Informáticos (FEEOE)
**Autor:** Ángel Puya Lucena  
**Curso:** 1º DAW | Año: 25/26  

---

## Índice
1. [Fase 1: Auditoría y Selección de Software](#fase-1-auditoría-y-selección-de-software)
2. [Fase 2: Entorno Colaborativo y Ofimática](#fase-2-entorno-colaborativo-y-ofimática)
3. [Fase 3: Comunicación y Transferencia](#fase-3-comunicación-y-transferencia)
4. [Fase 4: Documentación Técnica y Búsqueda](#fase-4-documentación-técnica-y-búsqueda)

---

## Fase 1: Auditoría y Selección de Software

A continuación se presenta la tabla de herramientas seleccionadas para el entorno productivo corporativo, detallando su propósito, licenciamiento y justificación técnica:

| Herramienta | Propósito | Tipo de Licencia | Justificación para el Entorno Productivo |
| :--- | :--- | :--- | :--- |
| **LibreOffice** | Suite ofimática (Documentos, hojas de cálculo) | GNU GPL v3 | Permite total independencia de proveedores de pago. Es ideal para reducir costes de licencias manteniendo compatibilidad total con formatos abiertos. |
| **Mozilla Firefox** | Navegador Web | MPL (Mozilla Public License) | Ofrece un equilibrio entre privacidad y rendimiento. Es altamente personalizable mediante políticas de grupo para entornos corporativos seguros. |
| **7-Zip** | Compresión y archivado de datos | GNU LGPL | Es la herramienta más eficiente para gestionar archivos pesados. Al ser de código abierto, garantiza que no haya "puertas traseras" ni costes por uso masivo. |
| **Bitwarden** | Gestión de contraseñas y seguridad | GPL / Propietaria | Crucial para la seguridad de la empresa. Permite compartir credenciales de forma cifrada entre empleados, evitando brechas de seguridad por contraseñas débiles. |
| **VLC Media Player** | Reproductor y convertidor multimedia | GNU GPL v2 | Elimina la necesidad de instalar paquetes de códecs externos que pueden ser inestables. Es una utilidad ligera y universal para cualquier departamento. |

---

## Fase 2: Entorno Colaborativo y Ofimática

### Manual de Bienvenida: EcoTech Solutions
> **¡Bienvenido al equipo de EcoTech!** > Estamos encantados de que te unas a nuestra misión de transformar la tecnología hacia un modelo sostenible y circular. Este documento te servirá de guía durante tus primeros días.

#### 1. Nuestra Misión y Visión
* **Misión:** Acelerar la transición a tecnologías verdes.
  * *Tecnología verde:* Uso de la ciencia y la innovación para crear productos, servicios y procesos que minimizan el impacto ambiental negativo.
* **Visión:** Ser el referente mundial en componentes biodegradables para 2030.

#### 2. Herramientas de Trabajo
Para garantizar la eficiencia, utilizamos un ecosistema en la nube:
* **Gestión Documental:** Google Drive / OneDrive (Edición en tiempo real).
* **Comunicación:** Slack o Microsoft Teams.
* **Gestión de Proyectos:** Trello o Asana.

#### 3. Normas del Espacio de Trabajo Colaborativo
1. **Nomenclatura:** Nombra tus archivos como `FECHA_NOMBRE_PROYECTO`.
2. **Comentarios:** Usa la función de mención (`@nombre`) para asignar tareas.
3. **Versiones:** No crees copias (ej. *"Manual_Final_V2"*). Usa el Historial de versiones integrado.

#### 4. Canales de Ayuda
* **Soporte TI:** `ticket-support@ecotech.com`
* **Recursos Humanos:** `hr@ecotech.com`

---

## Fase 3: Comunicación y Transferencia

### Tarea 1: Configuración de Cifrado Extremo a Extremo en Thunderbird (OpenPGP)

Para garantizar la privacidad y mitigar la exposición de mensajes frente a la vigilancia masiva o el propio proveedor de correo, se configura la tecnología OpenPGP:

1. **Acceso a la configuración:** Iniciamos Thunderbird y nos dirigimos a `Configuración` -> `Configuración de la cuenta`.
2. **Sección de Cifrado:** En el apartado de *Cifrado extremo a extremo*, seleccionamos la opción **Añadir clave...**
3. **Generación de la clave:** Creamos nuestra propia clave OpenPGP vinculada a la dirección de correo (`angel.puya.lucena.alu@iesfernandoaguilar.es`). 
4. **Expiración:** Configuramos la clave para que **no caduque** y utilizamos un algoritmo RSA de 3072 bits.
5. **Confirmación:** Una vez completado, el ID de la clave generada (ej. `0x086EDCF7E457BB19`) quedará correctamente asignado y activo.

### Tarea 2: Transferencia Segura de Logs con WeTransfer

Cuando necesitamos transferir archivos de registros pesados de forma rápida y sin pérdida de calidad (útil para material multimedia o logs extensos), se utiliza WeTransfer:

1. Accedemos a la página oficial de WeTransfer.
2. Pulsamos el botón **"Añadir archivos"** y seleccionamos el fichero `log.txt`.
3. Introducimos el correo electrónico del destinatario y nuestra dirección corporativa.
4. Hacemos clic en **"Transferir"**. El sistema generará de forma segura el enlace de descarga válido por el periodo establecido (ej. 3 días).

---

## Fase 4: Documentación Técnica y Búsqueda

### Resolución de Incidencias de Hardware

#### La Controladora RAID "quisquillosa"
El mensaje y la serie de pitidos o luces emitidos por la tarjeta corresponden a un mensaje **POST (Power-On Self-Test)**. Estos códigos de error específicos indican problemas de hardware detectables antes de iniciar el sistema operativo.
* **Solución:** Consultar los códigos de error detallados a partir de la **página 141** de la *HP ProLiant Servers Troubleshooting Guide*.

#### El Servidor que no acepta la RAM
En un servidor *Dell PowerEdge R720*, los fallos de reconocimiento de memoria suelen deberse a incompatibilidades de arquitectura o restricciones de posicionamiento físico:
* **Tipo de memoria:** El servidor puede requerir módulos **RDIMM** o **LRDIMM** en lugar de *ECC Unbuffered DDR3* estándar.
* **Restricción de Slots:** El R720 permite usar hasta 16 slots (8 por cada procesador), dictando la regla de arquitectura que **los slots 3 de cada canal deben permanecer vacíos** si no se cumple la configuración máxima admitida.
* **Referencia:** *Dell PowerEdge R720 Memory Upgrades*.

#### El SAI ruidoso
El ruido constante proviene de una alerta crítica del sistema: el SAI ha detectado que uno de sus **relés internos de seguridad** (encargado de prevenir el retorno de corriente o *backfeed*) se ha quedado soldado o está dañado. El equipo bloquea funciones para prevenir males mayores.
* **Procedimiento de reinicio / diagnóstico:**
  1. Apagar el SAI por completo.
  2. Desconectarlo de la toma de corriente eléctrica de la pared.
  3. Desconectar físicamente la batería interna del dispositivo.
  4. Mantener presionado el botón de encendido durante **10 segundos** para descargar los condensadores internos residuales.
