# new-project-ios
Manuales y estandares para proyectos iOS

# Como crear una libreria y subirla a CocoaPods
1. Abrir Xcode
2. File -> New -> Project -> Cocoa Touch Framework
3. Crear git
4. Commit de los cambios
5. Subir a github y crear release
6. Creamos archivo para Pods:
    pod spec create NombreProyecto
7. Editar archivo con los datos del proyecto
8. Ejecutar: pod lib lint
9. Crear cuenta: pod trunk register <Your Email> (Solo una vez)
10. Publicar Pod: pod trunk push TuProyecto.podspec