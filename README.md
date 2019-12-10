# Estrategia de implementación módulo para angularjs core_module_angularjs

Con el fin de unificar las interfaces gráficas de angularjs, a su vez agrupar funcionalidades para mejorar el proceso de mantenimiento, se debe realizar la implementación del módulo core_module_angularjs en los diferentes aplicativos escritos en angularjs.
 
## Implementación módulo core_module_angularjs

Para la implementación del módulo en cualquier cliente angularjs se deben seguir los siguientes pasos:
1. Ubiquese en la raiz principal de su proyecto desde la terminal

2. Ejecute 

```
bash <(curl -Ls https://gist.githubusercontent.com/fabianLeon/25d3b4a068fab7bb6e69b0c14c56ac59/raw/a111fa4036640fce22fbd9b282bfd4a93188dabc/update.sh)

```
3. El paso anterior debió dejar el proyecto de la siguiente forma.

```
app
├── core
│   ├── core.module.js
│   ├── css // folder con css común
│   ├── fonts // folder con fuentes
│   ├── footer // componente footer
│   ├── header // componente header
│   ├── menu-aplicaciones // componente de menú de aplicaciones
│   ├── menu-lateral // componente de menú lateral
│   ├── notificaciones // componente de notificaciones
│   ├── scripts
│   └── services
│       ├── implicit_token.js
│       ├── notificacion.js
│       └── theme.js
├── favicon.ico
├── images
├── index.html
├── resolucion.json
├── robots.txt
├── scripts
│   ├── app.js
│   ├── controllers
│   ├── decorators
│   ├── directives
│   ├── environment
│   │   ├── environment.js
│   │   ├── environment_prod.js
│   │   └── environment_test.js
│   ├── models
│   └── services
├── styles
│   └── custom.css
└── views
```
