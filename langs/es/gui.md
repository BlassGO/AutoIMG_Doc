<h2>GUI --> Guía de uso</h2>

>
> <p align="center"> <img src="https://raw.githubusercontent.com/BlassGO/AutoIMG_Doc/main/images/tool.png"></p>
> 
> **1.** Permite buscar dispositivos conectados. Si se hace una pulsación larga se hará una búsqueda de dispositivos ocultos para `Fastboot`.
> 
> **2.** Permite seleccionar archivos para la instalación (Uno por uno, el orden en el que son cargados también será el orden en el que serán instalados).
> 
> **3.** Permite especificar en qué partición del dispositivo se debe instalar el archivo seleccionado (Se puede editar antes de cargar un siguiente archivo).
> 
> **4.** Permite limpiar todas las configuraciones actuales, es decir, vaciar el listado de archivos seleccionados y restablecer todas las configuraciones a su punto inicial.
> 
> **5.** Inicia el proceso de instalación.
> 
> **6.** Indica que después de la instalación de archivos por Fastboot, se debe aprovechar para formatear el dispositivo.
> 
> **7.** Indica que cualquier archivo que tenga dirección a la partición `vbmeta*` debe ser instalado con los parámetros `--disable-verity --disable-verification`.
> 
> **8.** Indica que el dispositivo debe ser reiniciado cuando culmine todo el proceso de instalación.


>
> <p align="center"> <img src="https://raw.githubusercontent.com/BlassGO/AutoIMG_Doc/main/images/tool2.png"></p>
> 
> **1.** Permite hacer un reinicio normal.
> 
> **2.** Permite reiniciar en modo Fastboot (O FastbootD en función del modo por defecto).
> 
> **3.** Permite reiniciar en modo Recovery.


>
> <p align="center"> <img src="https://raw.githubusercontent.com/BlassGO/AutoIMG_Doc/main/images/tool3.png"></p>
> 
> **1.** Abre el gerente de instalación, que permite revisar y modificar la lista de archivos para la instalación.
> <p align="center"> <img src="https://raw.githubusercontent.com/BlassGO/AutoIMG_Doc/main/images/install_manager.png"></p>
> 
> **2.** Abre el gerente de dispositivos, que permite revisar y seleccionar un dispositivo para la instalación.
> <p align="center"> <img src="https://raw.githubusercontent.com/BlassGO/AutoIMG_Doc/main/images/device_manager.png"></p>
> 
> **3.** Permite seleccionar el modo por defecto en el que trabajará todo el Tool. Usar siempre `Fastboot` o `FastbootD`.
> 
> **4.** Permite definir un SLOT (`a`\\`b`) para las particiones de toda la instalación. Durante la instalación automaticamente se verifica si el nombre de la partición de destino de cada archivo cuenta con un SLOT definido en su nombre (`_a`\\`_b`) y si no se encuentra, se verifica si existe una partición con el nombre base y con la extensión del SLOT por defecto (system `_` SLOT), dirigiendo el archivo hacia la misma. El estado `auto` asegura siempre usar el SLOT activo del dispositivo.
> 
> **5.** Indica que se deben recordar las preferencias seleccionadas en cada apertura del Tool.
> 
> **6.** Por defecto, siempre se verifica si el tamaño del archivo de instalación no es superior al de la partición de destino del dispositivo, sin embargo, en dispositivos de particiones dinámicas el tamaño de las particiones pertenecientes a `SUPER` es relativo y puede expandirse durante la instalación. Activar la instalación forzada es útil para proceder con la instalación de todas formas.
>
> **7.** Indica que siempre se debe preferir el uso de `Recovery` para el flasheo de archivos `ZIP`. Recordando que el Tool también soporta el flasheo de estos archivos con el dispositivo encendido.
>
> **8.** Indica que siempre se debe preferir el uso de `ADB SHELL` para el reinicio del dispositivo. Esto aumenta la compatibilidad con el software del dispositivo.
> 
> **9.** Habilita todas las extensiones de archivos en el selector de archivos.
>
> **10.** Indica que se debe mostrar un seguimiendo paso a paso de cada línea de un `Config Script`. Esto es útil para ver su flujo.


>
> <p align="center"> <img src="https://raw.githubusercontent.com/BlassGO/AutoIMG_Doc/main/images/tool4.png"></p>
> 
> **1.** IP para la conexión inalámbrica.
> 
> **2.** PORT para la conexión inalámbrica.
> 
> **3.** Iniciar conexión inalámbrica.
>
> **4.** Desactivar conexión inalámbrica. Esto retorna a una búsqueda normal de dispositivos por USB.