## Com crear un projecte de Flutter
Per a crear un projecte de flutter necessitem executar el següent quan premem `Ctrl+Shift+P` en Visual Studio Code:

<p align= "center">
   <img src="../README/Crear projecte Flutter en VSCode.png" alt="Pas 1: Creació del projecte de Flutter" width="600"/>
</p>
<p align="center"><em>Pas 1: Creació del projecte de Flutter</em></p>

```bash
# Crear nou projecte de flutter en VSCode
Flutter: New Project 
```
 

Quan premem la tecla *Enter* apareixerà el següent:
<p align= "center">
   <img src="../README/Creacio aplicació Flutter.png" alt="Pas 2: Creació de l'aplicació de Flutter" width="600"/>
</p>
<p align="center"><em>Pas 2: Creació de l'aplicació de Flutter</em></p>

Haureu de prémer la primera opció (Application) esta generara tota l'estructura de directoris perquè pugueu executar l'aplicació de flutter en qualsevol dispositiu.

Perquè genera les carpetes dels respectius sistemes operatius, ara hem d'assignar la carpeta a l'aplicació, en aquest cas la posaré dins de la carpeta *`Projecte_Falla`*:

<p align= "center">
   <img src="../README/Assignar carpeta per a l&apos;aplicació.png" alt="Pas 3: Assignació de la carpeta per a la aplicació de Flutter" width="600"/>
</p>
<p align="center"><em>Pas 3: Assignació de la carpeta per a la aplicació de Flutter</em></p>

I després poseu el nom que vulgueu, en el meu cas es dirà *prova*:

<p align= "center">
   <img src="../README/nom de l&apos;aplicació.png" alt="Pas 4: Nom de l'aplicació" width="600"/>
</p>
<p align="center"><em>Pas 4: Nom de l'aplicació</em></p>

Al posar-li el nom, premeu la tecla *Enter* i se us generara de forma aproximada el següent:
```bash
# Estructura de directoris 
prova/
├── .dart.tool/
├── .idea/
│   ├── libraries/
│   │   ├── Dart_SDK.xml
│   │   └── KotlinJavaRuntime.xml
│   ├── runConfigurations/
│   │   └── main_dart.xml
│   ├── modules.xml
│   ├── workspace.xml
├── android/
│   ├── buildOutputcleanup/
│   │   ├── buildOutputcleanup
│   │   ├── cache.prperties
│   │   └── outputFiles.bin
│   ├── kotlin/
│   │   ├── errors/
│   │   └── sessions/
│   ├── noVersion/
│   │   └── buildLogic.lock/
│   ├── noVersion/
│   │   └── vcs-1/
│   ├── gc.properties
│   ├── app/
│   │   ├── .cxx/     
│   │   ├── src/
│   │   │   ├── debug/ 
│   │   │   │   ├── AndroidManifest.xml
│   │   │   ├── main/
│   │   │   │   └── java/
│   │   │   │   │   └── io/
│   │   │   │   │       └── flutter/
│   │   │   │   │           └── GeneratedPluginRegistrant.java
│   │   │   │   ├── kotlin/
│   │   │   │   │   └── MainActivity.kt
│   │   │   │   ├── res/
│   │   │   │   │   ├── drawable/
│   │   │   │   │   │   ├── launch_background.xml
│   │   │   │   │   ├── drawable-v21/
│   │   │   │   │   │   ├── launch_background.xml
│   │   │   │   │   ├── mipmap-hdpi/
│   │   │   │   │   │   ├── ic_launcher.png
│   │   │   │   │   ├── mipmap-mdpi/
│   │   │   │   │   │   ├── ic_launcher.png
│   │   │   │   │   ├── mipmap-xhdpi/
│   │   │   │   │   │   ├── ic_launcher.png
│   │   │   │   │   ├── mipmap-xxhdpi/
│   │   │   │   │   │   ├── ic_launcher.png
│   │   │   │   │   ├── mipmap-xxxhdpi/
│   │   │   │   │   │   ├── ic_launcher.png
│   │   │   │   │   ├── values/
│   │   │   │   │   │   ├── style.xml
│   │   │   │   │   └── values-night/
│   │   │   │   │       └── style.xml
│   │   │   │   └── AndroidManifest.xml    
│   │   │   └── profile/         
│   │   └── build.gradle.kts
│   ├── gradle/
│   ├── .gitignore
│   ├── build.gradle.kts
│   ├── prova_android.iml
│   ├── gradle.properties
│   ├── gradlew
│   ├── gradlew.bat
│   ├── local.properties
│   ├── settings.gradle.kts
├── build/
│   ├──reports
│   │   └──problems
│   │       └── problems-report.html
├── ios/
│   ├── Flutter/
│   │   ├── .AppFrameworkinfo.plist 
│   │   ├── Debug.xconfig
│   │   ├── flutter_export_environment.sh 
│   │   ├── Generated.xcconfig
│   │   └── Release.xcconfig
│   ├── Runner/
│   │   ├── Assets.xcassets/ 
│   │   ├── Base.Iproj/
│   │   ├── AppDelegate.swift
│   │   ├── GeneratedPluginRegistrant.h
│   │   ├── GeneratedPluginRegistrant.m
│   │   ├── Info.plist
│   │   └── Runner-Bridging-Header.h
│   ├── Runner.xcodeproj/
│   │   ├── project.xcworkspace/
│   │   │   ├── xcshareddata/
│   │   │   │   ├── IDEWorkspaceChecks.plist
│   │   │   │   └── WorkspaceSettings.xcsettings    
│   │   │   └── contents.xcworkspacedata
│   │   ├── xcshareddata/
│   │   │   └── xcschemes/
│   │   │       └── Runner.xcscheme
│   │   └── project.pbxproj
│   ├── Runner.xcworkspace/
│   │   ├── xcshareddata/
│   │   │   ├── IDEWorkspaceChecks.plist
│   │   │   └── WorkspaceSettings.xcsettings    
│   │   └──contents.xcworkspacedata    
│   ├── RunnerTests/
│   │   └── RunnerTests.swift
│   ├── .gitignore
├── lib/
│   ├── main.dart
├── linux/
│   ├── flutter/
│   │   └── ephemeral/
│   │       └── .plugin_symlinks/
│   ├── runner/
│   │   ├── CMakeList.txt
│   │   ├── main.cc
│   │   ├── my_application.cc
│   │   └── my_application.h       
│   ├── .gitignore
│   ├── CMakeList.txt
├── macos/ 
│   ├── Flutter/
│   │   ├── ephemeral/
│   │   │   ├── flutter_export_environment.sh
│   │   │   └── Flutter-Generated.xcconfig
│   │   ├── Flutter-Debug.xcconfig/  
│   │   ├── Flutter-Release.xcconfig/
│   │   └── GeneratedPluginRegistrant.swift/       
│   ├── Runner/
│   │   ├── Assets.xcassets/
│   │   │   ├── AppIcon.appiconset
│   │   │   │   ├── app_icon_16.png
│   │   │   │   ├── app_icon_32.png
│   │   │   │   ├── app_icon_64.png
│   │   │   │   ├── app_icon_128.png
│   │   │   │   ├── app_icon_256.png
│   │   │   │   ├── app_icon_512.png
│   │   │   │   ├── app_icon_1024.png
│   │   │   │   └── Contents.json  
│   │   ├── Base.Iproj/
│   │   │   └── MainMenu.xib
│   │   ├── Configs/
│   │   │   ├── AppInfo.xcconfig
│   │   │   ├── Debug.xcconfig
│   │   │   ├── Release.xcconfig
│   │   │   └── Warnings.xcconfig
│   │   ├── AppDelegate.swift
│   │   ├── DebugProfile.entitlements
│   │   ├── Info.plist
│   │   ├── MainFlutterWindow.swift
│   │   └── Release.entitlements      
│   ├── Runner.xcodeproj/
│   │   ├── project.xcworkspace/
│   │   │   └── IDEWorkspaceChecks.plist
│   │   ├── xcshareddata/ 
│   │   │   └── Runner.xcscheme 
│   │   └── project.pbxproj   
│   ├── Runner.xcworkspace/
│   │   ├── xcshareddata/
│   │   │   └── IDEWorkspaceChecks.plist
│   │   └── contents.xcworkspacedata  
│   ├── RunnerTets/
│   │   └── RunnerTests.swift  
│   └── .gitignore   
├── web/    
│   ├── icons/
│   │   ├── Icon-192.png 
│   │   ├── Icon-512.png
│   │   ├── Icon-maskable-192.png  
│   │   └── Icon-maskable-512.png  
│   ├── favicon.png
│   ├── index.html
│   ├── manifest.json 
├── windows/
│   ├── flutter/
│   │   ├── ephemeral/
│   │   │   └── plugin_symlinks
│   │   ├── Flutter-Debug.xcconfig/  
│   │   ├── Flutter-Release.xcconfig/
│   │   └── GeneratedPluginRegistrant.swift/ 
│   ├── runner/
│   │   ├── resources/
│   │   │   └── app_icon.ico
│   │   ├── CMakeLists.txt  
│   │   ├── flutter_window.cpp
│   │   ├── flutter_window.h
│   │   ├── main.cpp
│   │   ├── resource.h
│   │   ├── runner.exe.manifest
│   │   ├── Runner.rc
│   │   ├── utils.cpp
│   │   ├── utils.h
│   │   ├── win32_window.cpp
│   │   └── win32_window.h   
│   ├── .gitignore
│   └── CMakeLists.txt
├── .flutter-plugins
├── .flutter-plugins-dependencies
├── .gitignore
├── .metadata
├── analysis_options.yaml
├── devtools_options.yaml
├── prova.iml
├── pubspec.yaml
└── README.md              
```

I se us obrira el main automàticament amb el següent contingut:

<p align= "center">
   <img src="../README/main de l&apos;aplicació.png" alt="Contingut del fitxer main.dart de l'aplicació" width="1000"/>
</p>
<p align="center"><em>Pas 5: Contingut del fitxer main.dart de l'aplicació</em></p>

Ara si voleu veure que és premeu **F5** o en el terminal escriviu:
```bash
#Executar aplicació flutter
flutter run
```
Tardarà una estona en executar, però no us preocupeu, que la primera vegada en Android ha d'instal·lar-se l'aplicació i afegir les dependències a l'aplicació, però quan acabe obrira automàticament l'aplicació.
Quan s'òbriga veureu el següent:

<p align= "center">
   <img src="../README/Pantalla demo inicial.jpg" alt="El primer que veus al executar l'aplicació" width="200"/>
</p>
<p align="center"><em>Pas 6: El primer que veus al executar l'aplicació</em></p>

Com veieu no és més que un simple comptador que al prémer al botó de *+* augmentara el valor per 1:

<p align= "center">
   <img src="../README/Pantalla demo al apretar el boto +.jpg" alt="El que veus al prémer el botó de '+'" width="200"/>
</p>
<p align="center"><em>El que veus al prémer el botó de '+'</em></p>

Amb això ja tens una aplicació Flutter bàsica en funcionament.