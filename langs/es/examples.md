## Simples
> Esperar un dispositivo por `10` intentos, cargar archivos de instalación que están en la misma ruta del Config-Script (`HERE`) e iniciar el proceso de instalación.
```javascript
   Imprimir "-----------------------------"
   Imprimir " EJEMPLO DE INSTALACIÓN      "
   Imprimir "-----------------------------"

   Imprimir ">> Buscando dispositivos..."
   Esperar_dispositivo 10

   Imprimir ">> Cargando archivos..."
   Instalar "%HERE%\boot.img" en boot 
   Instalar "%HERE%\recovery.img" en recovery
   Instalar "%HERE%\system.img" en system
   Instalar "%HERE%\vendor.img" en vendor
   Instalar "%HERE%\magisk.zip" en "ZIP FILE"

   Imprimir ">> Iniciando instalación..."
   Presionar install
```


> Esperar un dispositivo por `10` intentos, cargar archivos de instalación PERO preguntarle al usuario si desea uno de ellos e iniciar el proceso de instalación.
```javascript
   Imprimir "-----------------------------"
   Imprimir " EJEMPLO DE INSTALACIÓN      "
   Imprimir "-----------------------------"

   Imprimir ">> Buscando dispositivos..."
   Esperar_dispositivo 10

   Imprimir ">> Cargando archivos..."
   Instalar "%HERE%\boot.img" en boot 
   Instalar "%HERE%\recovery.img" en recovery
   Instalar "%HERE%\system.img" en system
   Instalar "%HERE%\vendor.img" en vendor
   Si $(Pregunta "Magisk" Con "Desea instalar Magisk?")
      Instalar "%HERE%\magisk.zip" en "ZIP FILE"

   Imprimir ">> Iniciando instalación..."
   Presionar install
```


> Esperar un dispositivo idefinidamente (bucle), cargar archivos de instalación que están en la misma ruta del Config-Script (`HERE`) e iniciar el proceso de instalación.
```javascript
   Imprimir "-----------------------------"
   Imprimir " EJEMPLO DE INSTALACIÓN      "
   Imprimir "-----------------------------"

   Hasta $(Esperar_dispositivo 1)
        Imprimir "No se encuentra el dispositivo..."
   Imprimir ">> Dispositivo detectado!"

   Imprimir ">> Cargando archivos..."
   Instalar "%HERE%\boot.img" en boot 
   Instalar "%HERE%\recovery.img" en recovery
   Instalar "%HERE%\system.img" en system
   Instalar "%HERE%\vendor.img" en vendor
   Si $(Pregunta "Magisk" Con "Desea instalar Magisk?")
      Instalar "%HERE%\magisk.zip" en "ZIP FILE"
   
   Imprimir ">> Iniciando instalación..."
   Presionar install
```


> Antes de buscar un dispositivo, verificar si tal vez ya existe un dispositivo detectado por el usuario, cargar archivos de instalación que están en la misma ruta del Config-Script (`HERE`) e iniciar el proceso de instalación.
```javascript
   Imprimir "-----------------------------"
   Imprimir " EJEMPLO DE INSTALACIÓN      "
   Imprimir "-----------------------------"
   
   Si exist_device
        Imprimir ">> Ya existe un dispositivo!"
   SiNo
        Hasta $(Esperar_dispositivo 1)
                Imprimir "No se encuentra el dispositivo..."
        Imprimir ">> Dispositivo detectado!"

   Imprimir ">> Cargando archivos..."
   Instalar "%HERE%\boot.img" en boot 
   Instalar "%HERE%\recovery.img" en recovery
   Instalar "%HERE%\system.img" en system
   Instalar "%HERE%\vendor.img" en vendor
   Si $(Pregunta "Magisk" Con "Desea instalar Magisk?")
      Instalar "%HERE%\magisk.zip" en "ZIP FILE"
   
   Imprimir ">> Iniciando instalación..."
   Presionar install
```

## Avanzados

```javascript
   Imprimir "-----------------------------"
   Imprimir " EJEMPLO DE INSTALACIÓN      "
   Imprimir "-----------------------------"
   
   Desactivar reboot
   Activar format_data
   
   # Cambiar el modo por defecto a "fastbootD" (opción 2)
   Actualizar_key default_mode Con 2
   
   Si exist_device
        Imprimir ">> Ya existe un dispositivo!"
   SiNo
        Hasta $(Esperar_dispositivo 1)
                Imprimir "No se encuentra el dispositivo..."
        Imprimir ">> Dispositivo detectado!"

   Imprimir ">> Cargando archivos..."

   # boot_1.img / boot_2.img / boot_3.img
   Definir KERNEL con $(Opción "Kernels" "Escoja un kernel para su dispositivo:" Con "SkyFly" "ZanikDrugs" "I d k")
   Si KERNEL
      Instalar "%HERE%\kernels\boot_%KERNEL%.img" en boot
   SiNo
      Mensaje "ALERTA" con "No seleccionaste nada!"
      Abortar

   Para NOMBRE en "recovery" "vendor" "system"
       Instalar "%HERE%\%NOMBRE%.img" en "%NOMBRE%" 

   Para ZIP_NAME en "magisk" "safety_fix"
       Si $(Pregunta "%ZIP_NAME%" Con "Desea instalar %ZIP_NAME%?")
           Instalar "%HERE%\%ZIP_NAME%.zip" en "ZIP FILE"

   Si $(Pregunta "Setup" Con "Todo listo!`n`nDesea continuar?")
      Presionar install
      Mensaje "FINAL" con "Instalación satisfactoria!"
      Presionar only_reboot
   SiNo
      Abortar ">> Instalación cancelada"
   
```