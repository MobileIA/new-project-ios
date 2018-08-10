# new-project-ios
Manuales y estandares para proyectos iOS

# Como crear un proyecto
1. Abrir XCode y realizar wizard para la creación de un proyecto.
2. Iniciar cocoaPods: pod init
3. Agregar librerias que se van a usar y ejecutar: pod install
```pod
pod 'MobileiaCore'
pod 'PureLayout'
```

# Crear controlador con MobileIA Core:
1. Crear archivo ViewController:
```swift
import UIKit
import MobileiaCore

class CameraController: MIAViewController<CameraView> {

}
```
2. Crear archivo de vista:
```swift
import UIKit
import MobileiaCore

class CameraView: MIAView {
    
    var cameraView : CameraView!;
    
    override func setupViews() {
        super.setupViews();
        
        cameraView = CameraView();
        self.addSubview(cameraView);
    }
    
    override func setupConstraints() {
        cameraView.autoPinEdgesToSuperviewEdges();
    }
}

```

# Iniciar ViewController sin usar Storyboard;
1. Abrir AppDelegate:
```swift
self.window = UIWindow(frame: UIScreen.main.bounds)
self.window?.backgroundColor = UIColor.white;
self.window?.rootViewController = SplashViewController.factoryController();
self.window?.makeKeyAndVisible()
```

# Crear archivo de Constante:
```swift
class Constant: NSObject {
    static let BASE_URL = "http://test.mobileia.com/api/";
    
    static let MOBILEIA_LAB_APP_ID = 11523;
    
    static let IS_TESTING = false;
}
```

# Integrar MobileIA Authentication
1. pod 'MobileiaAuthenticationCore'
2. En AppDelegate:
```swift
import MobileiaCore

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {

    var window: UIWindow?

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
        
        // Inicializar MobileIA
        Mobileia.getInstance().appId = Constant.MOBILEIA_LAB_APP_ID;
        
        // Override point for customization after application launch.
        return true
    }

```


# Incluir Firebase
1. pod 'Firebase/Core'
2. en AppDelegate:
```swift
import Firebase

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {

    var window: UIWindow?

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
        
        FirebaseApp.configure()
        
        // Override point for customization after application launch.
        return true
    }
```

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


# Librerias utiles
https://github.com/codestergit/SweetAlert-iOS