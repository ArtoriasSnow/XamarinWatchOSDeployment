Necesitaremos un iPhone y un iWatch correctamente enlazados para poder desplegar en ellos nuestra app.

Antes de nada, hay que configurar los info.plist de los proyectos. 
A continuación se muestra un ejemplo de nombres: 


| Project  | Bundle Identifier |
| ------------- | ------------- |
| App.IOS  | com.Company.ExampleWatch |
| App.Watch  | com.Company.ExampleWatch.watchkit |
| App.WatchExtension | com.Company.ExampleWatchl.watchkit.watchkitextension |

	           
En el caso de los App.Watch y App.WatchExtension hay que añadir también el Watchkit Companion App Bundle Identifier 
(com.Company.ExampleWatch) y el WatchKit App Bundle Identifier (com.Company.ExampleWatch.watchkit), respectivamente.

No es necesario modificar el Entitlements.plist.

En los Project Options seleccionamos el Signing Identity y el Provisioning Profile (puede ser uno único para cada
proyecto, iOS-Watch-Watchextension, o incluso podemos usar un Wildcard). 
En la opción de Custom Entitlements no hay que añadir ningún fichero, a no ser que nuestra app los necesite.

A fecha de hoy no funciona desplegar directamente en el dispositivo desde Xamarin Studio 
así que hay que generar un fichero .IPA y realizar la instalación a través de Xcode.


1. Configurar nuestro proyecto en Debug | iPhone
2. Botón derecho sobre el proyecto iOS/Archive For Publishing
3. Una vez generado, seleccionar el fichero y pulsar en “Sign and distribute”
4. Pulsar sobre la opción Ad Hoc
5. Seleccionar el Provisioning Profile actual
6. Cuando finalice el proceso, abrir Xcode/Window/Devices
7. Seleccionar iPhone y añadir en la lista de programas instalados nuestro fichero IPA
8. Finalizada la instalación en iPhone se realizará automáticamente la instalación en el iWatch enlazado


Solución de problemas conocidos durante el proceso
--------------------------------------------------

*COULD NOT RESOLVE HOST IPs FOR WIFI DEBUGGER SETTINGS*
Hay que editar el fichero .csproj del proyecto en conflicto, editando el parámetro “DebugOverWifi” a false.


FAQ
-------------------------------------------------

"La app se instala en mi iPhone pero cuando está a punto de hacerlo en iWatch se cancela automáticamente y desaparece el icono"

Casi con total seguridad se trata de un problema de los Provisioning Profiles y/o Entitlements. Debemos asegurarnos de que están correctamente configurados en la web de apple.developer y añadidos en nuestro mac.
