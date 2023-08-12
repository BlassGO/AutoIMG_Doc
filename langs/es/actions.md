## Config Scripts
> Son archivos de texto con extensión `.config` que se interpretan gracias al pseudo-lenguaje [DinoCode](https://blassgo.github.io/DinoCode_Doc/ ':ignore').
>
> **->** La única diferencia respecto a los DinoScripts es que se utiliza ``` ` ``` para escapar carácteres especiales como saltos de línea ``` `n ```. Esto evita conflictos con rutas de archivos.
> 
> ```
> Mi_Script.config 
> ```

## Seguridad
> Por defecto, los `Config Scripts` trabajan bajo un modo restringido que impide acciones potencialmente peligrosas. Es posible solicitarle al usuario desactivar estas restricciones (así dependerá de la confianza del mismo hacia el desarrollador del Script).
> 
> ```javascript
> Desbloquear 
> ```

## Variables-Nativas

| **Variable**      | **DATO**                                                                                                                                                                                                                                                           | **EJEMPLO**                                      |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| CONFIG            | Ruta completa en donde está el Config Script.                                                                                                                                                                                                                      |                                                  |
| HERE              | Directorio en donde está el Config Script.                                                                                                                                                                                                                         |                                                  |
| TOOL              | Directorio en donde está el tool (AutoIMG).                                                                                                                                                                                                                        |                                                  |
| TMP               | Directorio temporal creado en el dispositivo Android (Requiere de la acción "asegurar_tmp").                                                                                                                                                                       |                                                  |
| PATH              | Cuando se ejecutan comandos Shell Script en el dispositivo Android los "comandos" en realidad son archivos (binarys) que se toman de distintos directorios. Aquí se pueden especificar directorios adicionales del dispositivo desde los cuales tomar más binarys. | Definir PATH con "/data/adb/magisk:/system/xbin" |
| serial            | Código serial del dispositivo Android (Requiere que exista un dispositivo detectado).                                                                                                                                                                              |                                                  |
| exist_device      | Es "verdadero" cuando se detectó un dispositivo previamente.                                                                                                                                                                                                       |                                                  |
| device_mode       | Corresponde al modo en el cuál se encuentra el dispositivo detectado (booted\fastboot\recovery\sideload).                                                                                                                                                          |                                                  |
| device_connection | Corresponde al tipo de conexión del dispositivo (USB\WIFI).                                                                                                                                                                                                        |                                                  |
| hidden_devices    | Cuando se define como "verdadero" habilita la búsqueda de dispositivos ocultos para Fastboot.                                                                                                                                                                      |                                                  |
| unlocked          | Es "verdadero" cuando el dispositivo tiene el bootloader desbloqueado (Requiere que el dispositivo haya sido detectado en modo fastboot).                                                                                                                          |                                                  |
| fastbootd         | Es "verdadero" cuando el dispositivo está usando FastbootD en lugar de Fastboot (Requiere que el dispositivo haya sido detectado en modo fastboot).                                                                                                                |                                                  |
| current_slot      | Corresponde al SLOT activo del dispositivo A\B (requiere que el dispositivo haya sido detectado en modo fastboot).                                                                                                                                                 |                                                  |
| current_anti      | Corresponde al número "ANTI ROLL BACK" de dispositivos Xiaomi (requiere que el dispositivo haya sido detectado en modo fastboot).                                                                                                                                  |                                                  |
| wireless_IP       | Permite definir un IP para la búsqueda de dispositivos.                                                                                                                                                                                                            |                                                  |
| wireless_PORT     | Permite definir un PORT para la búsqueda de dispositivos.                                                                                                                                                                                                          |                                                  |
| wireless_FORCE    | Cuando se define como "verdadero" establece que obligatoriamente se debe establecer una conexión inalámbrica (Por defecto, si se detecta un dispositivo USB se le da prioridad).                                                                                   |                                                  |
|                   |                                                                                                                                                                                                                                                                    |                                                  |
| exitcode          | Después de ejecutar algún comando en CMD de Windows, esto corresponde a su código de salida o error.                                                                                                                                                               |                                                  |
| general_log       | Ruta completa en donde está el registro de errores del tool (AutoIMG).                                                                                                                                                                                             |                                                  |
| formats           | Permite definir las extensiones de archivos soportadas por el selector de archivos del tool.                                                                                                                                                                       | Definir formats con "img" "bin" "mbn" "elf"      |
| version           | Versión del tool.                                                                                                                                                                                                                                                  |                                                  |
| build_date        | Fecha de compilación del tool.                                                                                                                                                                                                                                     |                                                  |
| winver            | Versión de Windows.                                                                                                                                                                                                                                                |                                                  |
|                   |                                                                                                                                                                                                                                                                    |                                                  |




## KEYs
> Las `KEY`s son identificadores que hacen referencia a algún componente visual de AutoIMG. Las KEY disponibles se muestran a continuación:
> 
> | **KEY**          | **Componente**                               |
> |------------------|----------------------------------------------|
> | header           | Texto "AutoIMG" en la cabecera               |
> | line             | Texto "------" en la cabecera                |
> | find_device      | Botón "Find My Devices"                      |
> | console          | El espacio en donde todo el texto se imprime |
> | reboot           | Interruptor "Reboot"                         |
> | format_data      | Interruptor "Format Data"                    |
> | disable_verify   | Interruptor "Disable Verify"                 |
> | install          | Botón INSTALL                                |
> |                  |                                              |
> | only_reboot      | Botón Reboot                                 |
> | reboot_fastboot  | Botón Fastboot                               |
> | reboot_recovery  | Botón Recovery                               |
> |                  |                                              |
> | default_mode     | fastboot (1) o fastbootd (2)                 |
> | preferences      | Interruptor "Save my preferences"            |
> | force_install    | Interruptor "Force the Installation"         |
> | ensure_recovery  | Interruptor "Prioritize Recovery"            |
> | ensure_shell     | Interruptor "Prioritize Shell"               |
> | all_formats      | Interruptor "Enable All file formats"        |
> | config_tracking  | Interruptor "Enable Config Tracking"         |
>

> Además de las KEYs generales, existen algunas "especiales" porque únicamente soportan acciones específicas. Las siguientes KEYs solo soportan la acción `Presionar`:
>
> | **KEY**         | **Componente**       |
> |-----------------|----------------------|
> | select          | Botón "Select File"  |
> | clean           | Limpieza de Config   |
> | install_manager | Installation Manager |

     
## Acciones con KEYs
> Estas acciones son específicas para KEYs.

> **Activar KEY**
> 
> Activa un interruptor (Encendido).
> 
> ```javascript
> Activar "disable_verify"
> ```

> **Desactivar KEY**
> 
> Desactiva un interruptor (Apagado).
> 
> ```javascript
> Desactivar "disable_verify"
> ```

> **Ocultar KEY**
>
> Oculta el componente (visualmente) al que hace referencia la KEY.
> ```javascript
> Ocultar "install"
> ```

> **Mostrar KEY**
>
> Muestra el componente (visualmente) al que hace referencia la KEY (después de que fue ocultado).
> ```javascript
> Mostrar "install"
> ```

> **Presionar KEY**
>
> Cuando el componente de la KEY es un botón, simula presionarlo.
> ```javascript
> Presionar "install"
> ```

> **Color "COLOR HEXADECIMAL" en KEY**
> 
> Cuando el componente de la KEY posee texto, permite cambiar su color (el color debe estar codificado en hexadecimal).
> ```javascript
> Color "02E27B" en "header"
> ```

> **Mover KEY hacia "NUEVA POSICIÓN / ALTURA / ANCHO"**
> 
> Permite cambiar la posición del componente de la KEY (siguiendo las coordenadas `x` `y`), su altura `h` o ancho `w`.
> ```javascript
> Mover "install" hacia "w200 h20 x20 y10"
> ```

> **Actualizar_key KEY con "NUEVO ESTADO"**
> 
> Cambia el estado de la KEY, el comportamiento varía según el tipo de componente al que hace referencia la KEY.
> ```javascript
> Actualizar_key "default_mode" Con 2       # Segunda opción fastbootD
> Actualizar_key "header" Con "H u h"       # Texto "AutoIMG" --> "H u h"
> ```


## Progreso
> Acciones para el control de la Barra de Progreso.

> **Activar_barra**
> 
> Activa la barra de progreso (oculta el botón "INSTALL" y en su lugar muestra la barra de progreso).
> 
> ```javascript
> Activar_barra
> ```

> **Añadir_progreso N**
> 
> Agrega un `N` porcentaje a la barra de progreso actualmente activa (`N` debe ser un número entero).
> ```javascript
> Añadir_progreso 30
> Dormir 2000          # 2 segundos
> Añadir_progreso 20
> Dormir 2000
> Añadir_progreso 50   # 100%
> ```

> **Desactivar_barra**
> 
> Restablece y deshabilita la barra de progreso (Y muestra nuevamente el botón "INSTALL").
> 
> ```javascript
> Desactivar_barra
> ```
     
     
## Dispositivos
> Acciones para la búsqueda de dispositivos.

> **Esperar_dispositivo N**
> 
> Busca un dispositivo por `N` intentos (`N` debe ser un número entero)
>
> **->** El dispositivo puede estar encendido, en modo Fastboot/Recovery/Sideload. Los modos más comunes están soportados.
> 
> ```javascript
> Esperar_dispositivo 10
> ```

> Para usar la búsqueda de dispositivos ocultos para `Fastboot`, se debe definir la Variable `hidden_devices`, de la siguiente manera:
> 
> ```javascript
> Definir hidden_devices Con VERDADERO   # Habilitar dispositivos ocultos
> Esperar_dispositivo 10
> Definir hidden_devices Con FALSO       # Deshabilitar dispositivos ocultos
> ```

> Para usar la búsqueda de dispositivos inalámbricos para `ADB`, se debe definir la Variable `wireless_IP` y `wireless_PORT`, de la siguiente manera:
> 
> ```javascript
> Definir wireless_IP Con "192.168.0.100"   # Definir IP del dispositivo
> Definir wireless_PORT Con "5555"          # Definir PORT del dispositivo
> 
> # Si se desea permitir únicamente la búsqueda inalámbrica
> # Definir wireless_FORCE Con TRUE
> Esperar_dispositivo 10
> 
> # Deshabilitar la búsqueda inalámbrica
> Definir wireless_IP Con
> Definir wireless_PORT Con
> ```

## Instalación
> Acciones para instalaciones convencionales.

> **Instalar "ARCHIVO" en "NOMBRE DE PARTICIÓN" con \<OPCIONES\>**
> 
> Esta acción es equivalente a seleccionar un archivo manualmente, es decir, el archivo solo se cargara (NO INSTALARA) para una instalación posterior.
> 
> ```javascript
> Instalar "carpeta\huh.img" en recovery
> ```
> Es posible definir opciones especiales para `fastboot.exe`
> ```javascript
> Instalar "carpeta\vbmeta.img" en vbmeta con "--disable-verity --disable-verification"
> ```
> Adicionalmente, existen nombres de partición especiales que indican que el archivo debe tener otro tipo de instalación.
> 
> | **NOMBRE DE PARTICIÓN** | **EXPLICACIÓN**                                                        |
> |-------------------------|------------------------------------------------------------------------|
> | UPDATE FILE             | El archivo será instalado como un ZIP de actualización por Fastboot.   |
> | ZIP FILE                | El archivo será instalado como un ZIP de flasheo (Recovery/Booted).    |
> | RAMDISK FILE            | El archivo será instalado como un parche de Ramdisk (Recovery/Booted). |


## Particiones (indirectas)
> Acciones para el manejo de particiones. Se consideran indirectas porque no trabajan en tiempo real, es decir, solo cargan una instrucción para cuando inicie el proceso convencional de instalación.

> **Eliminar "NOMBRE DE PARTICIÓN"**
> 
> Eliminar particiones desde FastbootD antes de la instalación (dispositivos compatibles). Esto solo carga la instrucción para cuando inicie el proceso de instalación.
> 
> ```javascript
> Eliminar product
> Eliminar odm
> ```

> **Crear "NOMBRE DE PARTICIÓN" con "TAMAÑO en KB/MB/GB/B"**
> 
> Crear particiones desde FastbootD antes de la instalación (dispositivos compatibles). Esto solo carga la instrucción para cuando inicie el proceso de instalación. Adicionalmente, el proceso de creación inicia siempre después de el de eliminación de particiones.
> 
> ```javascript
> Crear product con "200MB"
> ```

## Particiones (directas)
> Acciones para el manejo de particiones. Se consideran directas porque trabajan en tiempo real.

> **Actualizar "ARCHIVO DEL DISPOSITIVO" en "NOMBRE DE PARTICIÓN"**
> 
> Busca la partición e instala un archivo ya existente en el dispositivo en tiempo real (Solo modos compatibles como Custom Recovery).
> 
> ```javascript
> Actualizar "/sdcard/boot.img" en boot
> ```

> **Actualizar_enviar "ARCHIVO" en "NOMBRE DE PARTICIÓN"**
> 
> Busca la partición, envía un archivo existente en la computadora al dispositivo y lo instala en tiempo real (Solo modos compatibles como Custom Recovery).
> 
> ```javascript
> Actualizar_enviar "folder\boot.img" en boot
> ```

## Ramdisk\Kernel
> Acciones para el parcheo de Ramdisk y Kernel. Requieren de `magiskboot` en el dispositivo.
> ```javascript
> # Asegurar magiskboot
> Definir PATH con "/data/adb/magisk"
> ```

> **Actualizar_ramdisk "ARCHIVO DEL DISPOSITIVO" en "NOMBRE DE PARTICIÓN"**
> 
> Busca la partición y actualiza la ramdisk con un archivo ya existente en el dispositivo (Solo modos compatibles como Custom Recovery)
> 
> ```javascript
> Actualizar_ramdisk "/sdcard/ramdisk.cpio" en boot_a
> Actualizar_ramdisk "/sdcard/ramdisk.cpio" en boot_b
> ```

> **Actualizar_ramdisk_enviar "ARCHIVO" en "NOMBRE DE PARTICIÓN"**
> 
> Busca la partición, envía un archivo existente en la computadora al dispositivo y actualiza la ramdisk con él (Solo modos compatibles como Custom Recovery)
> 
> ```javascript
> Actualizar_ramdisk_enviar "folder\ramdisk.cpio" en boot_a
> Actualizar_ramdisk_enviar "folder\ramdisk.cpio" en boot_b
> ```

> **Actualizar_kernel "ARCHIVO DEL DISPOSITIVO" en "NOMBRE DE PARTICIÓN"**
> 
> Busca la partición y actualiza el kernel con un archivo ya existente en el dispositivo (Solo modos compatibles como Custom Recovery)
> 
> ```javascript
> Actualizar_kernel "/sdcard/kernel" en boot_a
> Actualizar_kernel "/sdcard/kernel" en boot_b
> ```

> **Actualizar_kernel_enviar "ARCHIVO" en "NOMBRE DE PARTICIÓN"**
> 
> Busca la partición, envía un archivo existente en la computadora al dispositivo y actualiza el kernel con él (Solo modos compatibles como Custom Recovery)
> 
> ```javascript
> Actualizar_kernel_enviar "folder\kernel" en boot_a
> Actualizar_kernel_enviar "folder\kernel" en boot_b
> ```

> **Instalar_ramdisk_recovery "NOMBRE DE PARTICIÓN"**
> 
> Busca la partición, genera una Ramdisk nueva a partir del Custom Recovery actual y la instala. Esto implica que esta acción solo es funcional cuando el dispositivo se encuentre en modo Recovery.
> 
> ```javascript
> Instalar_ramdisk_recovery boot_a
> Instalar_ramdisk_recovery boot_b
> ```

## ADB
> Acciones adicionales para `adb.exe`.

> **Adb "parámetros" \<Tiempo\>**
> 
> Ejecuta adb.exe con parámetros específicos. Si se especifica "Tiempo", la acción se detendrá a la fuerza si excede ese período.
> 
> ```javascript
> Imprimir $(adb "version")
> ```

> **Adb_serial "parámetros" \<serial\> \<Tiempo\>**
> 
> Versión extendida de la acción "adb" con soporte para SERIAL de un dispositivo.
> 
> ```javascript
> Imprimir $(adb_serial "shell echo huh" "E4X5A8M3P7L9E")
> ```

> **Enviar "ARCHIVO" hacia "RUTA DEL DISPOSITIVO"**
> 
> Enviar un archivo de la computadora al dispositivo.
> 
> ```javascript
> Enviar "carpeta\archivo.txt" hacia "/sdcard"
> ```

> **Esperar_shell**
> 
> Esperar a que ADB SHELL esté disponible.
> 
> ```javascript
> Esperar_shell
> ```

> **Shell "Comando"**
> 
> Ejecuta un comando Shell Script en el dispositivo.
> 
> ```javascript
> Imprimir $(Shell "echo Just test && ls /odm")
> ```


## Fastboot
> Acciones adicionales para `fastboot.exe`.

> **Fastboot "parámetros" \<Tiempo\>**
> 
> Ejecuta fastboot.exe con parámetros específicos. Si se especifica "Tiempo", la acción se detendrá a la fuerza si excede ese período.
> 
> ```javascript
> Imprimir $(fastboot "--version")
> ```

> **Fastboot_serial "parámetros" \<serial\> \<Tiempo\>**
> 
> Versión extendida de la acción "fastboot" con soporte para SERIAL de un dispositivo.
> 
> ```javascript
> Imprimir $(fastboot_serial "getvar all" "E4X5A8M3P7L9E")
> ```

> **Boot "ARCHIVO"**
> 
> Intenta bootear una IMG temporalmente desde Fastboot (dispositivos compatibles).
> 
> ```javascript
> Boot "carpeta\boot.img"
> ```


## URL
> Acciones para URLs.

> **Hacialink "URL"**
> 
> Abre una URL en el navegador por defecto.
> 
> ```javascript
> Hacialink "https://blassgo.github.io/DinoCode_Doc/"
> ```

> **Webconfig "URL"**
> 
> Permite leer y ejecutar un Config Script desde una URL RAW (Texto directo). El Script remoto se considerará una extensión del bloque actual, es decir, las Variables serán compartidas mutuamente.
> 
> ```javascript
> Definir REG con "Something"
> Webconfig "https://raw.githubusercontent.com/BlassGO/auto_img_request/main/support.config"
> 
> # El webconfig tiene la posibilidad de definir/modificar una Variable.
> Mensaje con REG
> ```

> **Read_xml "URL"**
> 
> Permite leer una URL RAW, retornando su contenido.
> 
> ```javascript
> Definir CONTENIDO con $(Read_xml "https://raw.githubusercontent.com/BlassGO/auto_img_request/main/support.config")
> ```

> **Descargar "URL" en "ARCHIVO" con \<OPCIONES\>**
> 
> Obtener un archivo desde un enlace de descarga directa (si el destino sale fuera de `HERE` o `TOOL`, necesitará la aprobación del usuario).
> 
> ```javascript
> Decargar "https://bitbucket.org/iBotPeaches/apktool/downloads/apktool_2.8.1.jar" en "folder\apktool.jar"
> ```
> | **Opción**                            | **Explicación**                                                                                                                                                 |
> |---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
> | MD2/MD4/MD5/SHA1/SHA256/SHA384/SHA512 | Define el tipo de HASH para la verificación del archivo. Requiere incluir el HASH (el orden no es relevante, puesto que según el tipo de HASH se buscará una cadena que corresponda).                                                                                                        |
> | force                                 | Por defecto, cuando el archivo ya existe y cumple con la verificación indicada NO se vuelve a descargar. Esta opción asegura siempre sobreescribir el archivo. |
>
> ```javascript
> Decargar "https://bitbucket.org/iBotPeaches/apktool/downloads/apktool_2.8.1.jar" en "folder\apktool.jar" con "SHA256 7b4a8e1703e228d206db29644b71141687d8a111b55b039b08b02dfa443ab0f9"
> Decargar "https://bitbucket.org/iBotPeaches/apktool/downloads/apktool_2.8.1.jar" en "folder\apktool.jar" con "force SHA256 7b4a8e1703e228d206db29644b71141687d8a111b55b039b08b02dfa443ab0f9"
> ```


## ZIPs
> Acciones para el manejo de ZIPs.

> **Unzip "ARCHIVO" "DESTINO" \<OPCIONES\>**
> 
>  Permite extraer archivos ZIPs de la computadora.
> 
> ```javascript
> Unzip "folder\custom.zip" "folder\extraido"
> ```
> | **Opción**  | **Explicación**                                                                                                                                                                        |
> |-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
> | inside-zip  | Establece que el ARCHIVO no debe tomarse como una ruta literal, sino como una referencia a una ruta que está dentro del propio ZIP (es necesario que el archivo tenga extensión .zip). |
> | regex:      | Establece que solo se deben extraer rutas del ZIP que coincidan con el patrón Regex. Esta opción siempre debe ir la final.                                                                                                   |
> | regex-name: | Establece que solo se deben extraer archivos/carpetas con un nombre que coincida con el Regex. No se puede combinar con "regex:" simultáneamente y siempre debe ir al final.                                      |
> | files       | Establece que solo se permite la extracción de archivos.                                                                                                                               |
> | folders     | Establece que solo se permite la extracción de carpetas.                                                                                                                               |
> | force       | Establece que siempre se deben sobreescribir archivos en el destino.                                                                                                                   |
> | mix-path    | Establece que se debe combinar la ruta de destino con cada ruta dentro del ZIP durante la extracción.                                                                                  |
> ```javascript
> Unzip "folder\custom.zip\folder_inside_zip" "folder\extraido" "inside-zip"
> # Dentro de patrones Regex se utiliza siempre "\" para escapar carácteres especiales.
> Unzip "folder\custom.zip" "folder\extraido" "regex: ^folder_inside_zip\\.*"
> Unzip "folder\custom.zip" "folder\extraido" "files regex-name: \.txt$"
> Unzip "folder\custom.zip" "folder\extraido" "force folders"
> Unzip "folder\custom.zip" "folder\extraido" "force files mix-path regex-name: \.txt$"
> ```



## Extra
> Acciones adicionales.

> **get_slot**
> 
>  Permite obtener la extensión del `SLOT` activo del dispositivo cuando está en modos diferentes a `Fastboot` (en los cuales no es posible usar la variable nativa `current_slot`). Si el dispositivo no es `A/B` no se retornará nada.
> 
> ```javascript
> Definir SLOT_ACTIVO con $(get_slot)
> Mensaje con SLOT_ACTIVO
> ```

> **get_cmdline "PROP a extraer"**
> 
>  Permite obtener valores de props especiales del dispositivo correspondientes a `/proc/cmdline` y `/proc/bootconfig` (Solo modos soportados como Booted/Recovery).
> 
> ```javascript
> Definir ESTADO con $(get_cmdline "androidboot.verifiedbootstate")
> Mensaje con ESTADO
> ```

> **Asegurar_tmp \<VERDADERO\>**
> 
>  Crea un directorio temporal en el dispositivo y se guarda en la variable `TMP`. Por defecto, el directorio temporal solo asegura un directorio válido para el envio de archivos desde la computadora, sin embargo, muchas veces los directorios válidos para el envio de archivos NO soportan la ejecución de binarys o shell scripts. Si se especifica `VERDADERO` se asegurará un directorio en donde sea posible ejecutar binarys o shell scripts PERO no necesariamente será válido para enviar archivos.
> 
> ```javascript
> Asegurar_tmp
> Mensaje con TMP
> ```

> **Setup_busybox "ENVIAR HACIA DIRECTORIO" \<CARGAR COMANDOS EN DIRECTORIO\>**
> 
>  Envia `busybox` de `bin\extras\` hacia la ruta especificaba (del dispositivo) y se asegura de que sea ejecutable. Si se especifica el segundo parámetro se cargaran todos los comandos de Busybox en ese directorio, simulando un directorio con múltiples binarys (combinándolo con la variable nativa `PATH` esto puede ser muy útil).
> 
> ```javascript
> Asegurar_tmp VERDADERO
> Setup_busybox TMP
> ```

> **Busybox "COMANDO"**
> 
>  Después de haber usado la acción `Setup_busybox` la ruta de Busybox dentro del dispositivo se mantiene en memoria, permitiendo el envío de comandos.
> 
> ```javascript
> Asegurar_tmp VERDADERO
> Setup_busybox TMP
> Busybox "echo Desde busybox"
> ```

> **Exist_file "ARCHIVO DEL DISPOSITIVO"**
> 
>  Permite comprobar la existencia de un archivo dentro del dispositivo (En reelidad, se soportan: archivos, carpetas, bloques...).
> 
> ```javascript
> Si $(exist_file "/sdcard/file.txt")
>    Imprimir "Existe!"
> ```

> **Exist_dir "DIRECTORIO DEL DISPOSITIVO"**
> 
>  Permite comprobar la existencia exclusiva de una carpeta dentro del dispositivo.
> 
> ```javascript
> Si $(exist_dir "/sdcard/folder")
>    Imprimir "Existe!"
> ```

> **Dormir N**
> 
>  Pausa por N milisegundos (3000 = 3 segundos).
> 
> ```javascript
> Dormir 3000
> ```

> **Imprimir "Texto" \<falso\>**
> 
>  Imprimir texto en la consola, "falso" evita hacer un salto de línea.
> 
> ```javascript
> Imprimir "Hola mundo!"
> Imprimir "Hola " falso
> Imprimir "mundo!"
> ```

> **Abortar "Texto" \<falso\>**
> 
>  Imprime texto en la consola, termina la ejecución y limpia cualquier instalación/configuración actual (Informado como error de Config). El parámetro "falso" evita hacer un salto de línea.
> 
> ```javascript
> Abortar "Hubo un error!"
> ```

> **Salir**
> 
>  Termina la ejecución pero mantiene las configuraciones precargadas (no se informa como error de Config).
> 
> ```javascript
> Salir
> ```

> **Mensaje \<Titulo\> con "Texto"**
> 
>  Muestra un mensaje.
> 
> ```javascript
> Mensaje con "Hola mundo!"
> Mensaje "Prueba" con "Hola mundo!"
> ```

> **Timed_msg "Texto" Tiempo \<verdadero\>**
> 
>  Muestra un mensaje durante N milisegundos, si se especifica "verdadero", el mensaje se colocará en la parte superior de la ventana del tool y lo seguirá.
> 
> ```javascript
> Timed_msg "Hola mundo!" 4000             # 4 segundos
> Timed_msg "Hola mundo!" 4000 verdadero
> ```

> **Seccion TAG**
> 
>  Permite llamar una sección TAG.
> 
> ```javascript
> :hola
>    Mensaje "Prueba" con "Hola mundo!"
> :main
>    Seccion hola
> ```

> **Pregunta \<Titulo\> con "Texto"**
> 
>  Permite hacer preguntas de SÍ/NO. Retorna "verdadero" o "falso" respectivamente.
> 
> ```javascript
> Pregunta "Título" con "¿Desea continuar?"
> 
> Si $(Pregunta "Título" con "¿Desea continuar?")
>     Mensaje con "OKAY"
> SiNo
>     Mensaje con "NAO"
> ```

> **Opcion \<Titulo\> \<Mensaje\> con "Primera opcion" "Segunda opcion" "Tercera opcion" "..."**
> 
>  Permite solicitar una opción al usuario. Se puede especificar cualquier número de opciones.
> 
> ```javascript
> Definir RESULTADO con $(Opcion "Prueba" "Escoja una opción:" con "Primera opcion" "Segunda opcion" "Tercera opcion")
> 
> Si RESULTADO=1
>     Mensaje con "Primera opción"
> SiNo Si RESULTADO=2
>     Mensaje con "Segunda opción"
> SiNo Si RESULTADO=3
>     Mensaje con "Tercera opción"
> SiNo
>     Mensaje con "No se selecciono ninguna opción"
> ```

> **Guardar "NOMBRE" con "DATO" en "ARCHIVO"**
> 
>  Guarda un `DATO` (de una línea máximo) vinculado a un `NOMBRE` (Solo carácteres alfanuméricos y guiones bajos) en un archivo externo de la computadora.
> 
> ```javascript
> Guardar "VERSION" con "1.0.0" en "folder\mis_datos.txt"
> Guardar "PASS" con VERDADERO en "folder\mis_datos.txt"
> ```

> **Obtener_guardado "ARCHIVO"**
> 
>  Obtiene todos los `DATOS` de un registro creado con "Guardar", convirtiendo los `NOMBRES` en Variables Globales. 
> 
> ```javascript
> Obtener_guardado "folder\mis_datos.txt"
> Mensaje con VERSION
> ```
