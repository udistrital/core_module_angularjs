# Estrategia de implementación módulo para angularjs core_module_angularjs

Con el fin de unificar las interfaces gráficas de angularjs, a su vez agrupar funcionalidades para mejorar el proceso de mantenimiento, se debe realizar la implementación del módulo core_module_angularjs en los diferentes aplicativos escritos en angularjs.
 
## Implementación módulo core_module_angularjs

Para la implementación del módulo en cualquier cliente angularjs se deben seguir los siguientes pasos:
1. Ubiquese en la raiz principal de su proyecto desde la terminal y ejecute

```bash
bash <(curl -Ls https://gist.githubusercontent.com/fabianLeon/25d3b4a068fab7bb6e69b0c14c56ac59/raw/07f76b36c5a2c593651c93bf642eff76eb80e1db/update.sh)

```
  Lo anterior debió dejar una estructura de archivos como la siguiente

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

2. Ajuste el index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
	...
    <!-- Place favicon.ico and apple-touch-icon.png in the root directory -->
    <!-- build:css(.) styles/vendor.css -->
    <!-- bower:css -->
 	...
    <!-- endbower -->
    <!-- endbuild -->
 
 
    <!-- build:css(.tmp) styles/main.css -->
    <link rel="stylesheet" href="styles/custom.css">
    <!-- endbuild -->
    <link rel="stylesheet" href="styles/custom.css">
    <link rel="stylesheet" href="core/css/steeper.css">
    <link rel="stylesheet" href="core/css/core.css">
    <link rel="stylesheet" href="core/footer/footer.css">
    <link rel="stylesheet" href="core/header/header.css">
    <link rel="stylesheet" href="core/menu-lateral/menu-lateral.css">
    <link rel="stylesheet" href="core/menu-aplicaciones/menu-aplicaciones.css">
    <link rel="stylesheet" href="core/notificaciones/notificaciones.css">
    <link rel="stylesheet" href="core/css/ui-grid.css">
    <link rel="stylesheet" href="https://pruebasassets.portaloas.udistrital.edu.co/nix-style.css"> <!-- nix-style.css, gaia-style.css, athenea-style.css y urano-style.css -->
    <link rel="stylesheet" href="https://pruebasassets.portaloas.udistrital.edu.co/oas-style.css">
    <link rel="stylesheet" href="https://pruebasassets.portaloas.udistrital.edu.co/logo-stylus.css">
    <link rel="stylesheet" href="https://pruebasassets.portaloas.udistrital.edu.co/logo-info.css">
    <link rel="stylesheet" href="https://pruebasassets.portaloas.udistrital.edu.co/isotipo-header.css">
    <link rel="stylesheet" href="https://pruebasassets.portaloas.udistrital.edu.co/logo-header.css">
</head>

<body ng-app="contractualClienteApp">

    <div ng-controller="headerCtrl">
        <div ng-if="!isLogin" id="nb-global-spinner" class="spinner">
            <div class="blob blob-0"></div>
            <div class="blob blob-1"></div>
            <div class="blob blob-2"></div>
            <div class="blob blob-3"></div>
            <div class="blob blob-4"></div>
            <div class="blob blob-5"></div>
        </div>
        <div ng-if="isLogin" ng-include="'core/header/header.html'" ng-controller="headerCtrl">
        </div>
        <div ng-if="isLogin" class="body-container-menuaplicaciones"
            ng-include="'core/menu-aplicaciones/menu-aplicaciones.html'" ng-controller="menuaplicacionesCtrl">
        </div>
        <div ng-if="isLogin" class="body-container-notificaciones"
            ng-include="'core/notificaciones/notificaciones.html'" ng-controller="notificacionesCtrl">
        </div>
        <div ng-if="isLogin" class="container-app">
            <div id="menu-sidebar-container" ng-class="sidebarClases.sidebarContainerClase" ng-controller="headerCtrl">
                <div id="menu-sidebar" ng-include="'core/menu-lateral/menu-lateral.html'"
                    ng-controller="menuLateralCtrl" ng-class="sidebarClases.sidebarDivClase">
                </div>
            </div>
            <div ng-class="sidebarClases.containerBodyClase" ng-controller="headerCtrl">
                <div ng-view="" ng-class="sidebarClases.containerDivClase" ng-controller="headerCtrl">
                </div>
            </div>
        </div>
        <div ng-if="isLogin" class="container-footer" ng-include="'core/footer/footer.html'" ng-controller="footerCtrl">
        </div>
    </div>

    <!-- Google Analytics: change UA-XXXXX-X to be your site's ID -->
	...

    <!-- build:js(.) scripts/vendor.js -->
    <!-- bower:js -->
	...
    <!-- endbower -->
    <!-- endbuild -->


    <!-- build:js({.tmp,app}) scripts/scripts.js -->
    <script src="scripts/app.js"></script>
    <script src="scripts/controllers/main.js"></script>
    <script src="core/core.module.js"></script>
    <script src="core/header/header.js"></script>
    <script src="core/footer/footer.js"></script>
    <script src="core/menu-lateral/menu-lateral.js"></script>
    <script src="core/menu-lateral/opciones-component/opciones-directive.js"></script>
    <script src="core/menu-aplicaciones/menu-aplicaciones.js"></script>
    <script src="core/notificaciones/notificaciones.js"></script>
    <script src="core/services/notificacion.js"></script>
    <script src="core/services/theme.js"></script>
    <script src="core/services/implicit_token.js"></script>
    <!-- endbuild -->

</body>
<!-- build:js({.tmp,app}) scripts/extras.js -->
<script src="scripts/environment/environment.js"></script>
...

<!-- endbuild -->
<script src="https://ajax.googleapis.com/ajax/libs/angular_material/1.1.0/angular-material.min.js"></script>
<script src="bower_components/bootstrap-fileinput/js/locales/es.js"></script>

</html>

```
3. En app/scripts/app.js agregue el módulo core

```js
'use strict';

/**
 * @ngdoc overview
 * @name MODULE_APP
 * @description
 * # MODULE_APP
 *
 * Main module of the application.
 */
angular
    .module('MODULE_APP', [
        // Módulos de otras librerías
        ... ,
        'core'
    ])
```
4. Configure environment en app/scripts/environment de cada entorno, test, prod y environment.js para local
```js
'use strict';

// Reemplace MODULE_APP por el nombre del módulo de la aplicación principal

/**
 * @ngdoc service
 * @name MODULE_APP.config
 * @description
 * # config
 * Constant in the MODULE_APP.
 */


angular.module('MODULE_APP')
  .constant('CONF', {
    APP: "", // Nombre de la app, esto cargará el logo.
    APP_MENU: "", // Ingrese valor de la aplicación asociado al menú registrado en wso2
    GENERAL: {
      WSO2_SERVICE: "http://jbpm.udistritaloas.edu.co:8280/services",
      CONFIGURACION_SERVICE: "https://autenticacion.portaloas.udistrital.edu.co/api/configuracion_crud_api/v1/",
      NOTIFICACION_WS: "wss://pruebasapi.portaloas.udistrital.edu.co:8116/ws/join",
      TOKEN: {
        AUTORIZATION_URL: "https://autenticacion.portaloas.udistrital.edu.co/oauth2/authorize",
        URL_USER_INFO: "https://autenticacion.portaloas.udistrital.edu.co/oauth2/userinfo",
        CLIENTE_ID: "pszmROXqfec4pTShgF_fn2DAAX0a",
        REDIRECT_URL: "http://localhost:9000/",
        RESPONSE_TYPE: "id_token token",
        SCOPE: "openid email documento",
        BUTTON_CLASS: "btn btn-warning btn-sm",
        SIGN_OUT_URL: "https://autenticacion.portaloas.udistrital.edu.co/oidc/logout",
        SIGN_OUT_REDIRECT_URL: "http://localhost:9000/",
        SIGN_OUT_APPEND_TOKEN: "true",
      },
    },
  });

```

5. edite el .drone.yml para que funcione la configuración de environment
```yml
 - name: buildtest
    image: node:10.7.0
    commands:
     - npm install -g grunt-cli bower
     - npm install natives
     - npm install
     - bower install --allow-root
     - cp -f app/scripts/environments/environment_test.js app/scripts/environments/environment.js
     - grunt build
    when:
      branch: [test]
      event: [push, pull_request]

  - name: buildmaster
    image: node:10.7.0
    commands:
     - npm install -g grunt-cli bower
     - npm install natives
     - npm install
     - bower install --allow-root
     - cp -f app/scripts/environments/environment_prod.js app/scripts/environments/environment.js
     - grunt build
    when:
      branch: [master]
      event: [push, pull_request]
```

5. Elimine del index

```html
<!-- build:js({.tmp,app}) scripts/extras.js -->
 <script src="scripts/services/implicit_token.js"></script>
 <script src="scripts/services/notificacion.js"></script>
 <script src="scripts/controllers/menu.js"></script>
 <script src="scripts/controllers/footer.js"></script>
 <script src="scripts/directives/notificacion_list/notificacion_list.js"></script>
 <script src="scripts/services/config.js"></script>
<!-- endbuild -->
```

6. Ajuste de Gruntfile.js
Añanda en Gruntfile lo siguiente

```js
, {
          expand: true,
          cwd: '<%= yeoman.app %>/core',
          src: '**/*.*',
          dest: '<%= yeoman.dist %>/core'
        },
```
En el  task copy 
```js
    // Copies remaining files to places other tasks can use
    copy: {
      dist: {
        files: [{
          expand: true,
          dot: true,
          cwd: '<%= yeoman.app %>',
          dest: '<%= yeoman.dist %>',
          src: [
            '*.{ico,png,txt}',
            '*.html',
            'images/**/*.{webp}',
            'styles/fonts/**/*.*'
          ]
        }, {
          expand: true,
          cwd: '<%= yeoman.app %>/views',
          src: '**/*.html',
          dest: '<%= yeoman.dist %>/views'
        }, {
          expand: true,
          cwd: '<%= yeoman.app %>/core',
          src: '**/*.*',
          dest: '<%= yeoman.dist %>/core'
        },{
          expand: true,
          cwd: 'bower_components/angular-ui-grid/fonts',
          src: ['*.eot', '*.svg', '*.ttf', '*.woff'],
          dest: '<%= yeoman.dist %>/styles/fonts/'
        }, {
          expand: true,
          cwd: '<%= yeoman.app %>/scripts',
          src: '**/*.json',
          dest: '<%= yeoman.dist %>/scripts'
        }, {
          expand: true,
          cwd: '.tmp/images',
          dest: '<%= yeoman.dist %>/images',
          src: ['generated/*']
        }, {
          expand: true,
          cwd: 'bower_components/bootstrap/dist',
          src: 'fonts/*',
          dest: '<%= yeoman.dist %>'
        }]
      },
```

