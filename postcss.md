# ¿Front-end en una aplicación Rails?

Al usar Rails, cualquier desarrollador (full-stack) se habrá encontrado con algunos de los siguientes puntos:
- El problema de que **las vistas son poco amigables de programar**, Rails no provee de *live reloading* para ver los cambios al instante
- **Mucho javascript** en las vistas puede resultar **no muy atractivo** para un ruby developer
- **Bootstrap/Foundation** me gustan, son fáciles de usar, pero ponerme a modificarlos **nunca queda como quiero** ni se bien que es lo que está pasando por debajo

Con Postcss, cualquiera es capaz de crear su propio fronte-end framework a bajo costo de tiempo y esfuerzo. La variedad y gran practicidad de plugins que Postcss dispone, hacen de su uso una gran herramienta a la hora de programar interfaces de usuario.

# Postcss en Ruby on Rails

[Postcss](http://postcss.org) es una herramienta para transformar CSS con javascript. Postcss es modular, se pueden instalar [plugins]() según la coneveniencia del usuario.

Para correr Postcss haremos uso de [Gulp](http://gulpjs.com), un automatizador de tareas para javascript.

Ahora la cuestión sería cómo configurar todo esto en Rails, sabiendo que Rails también tiene su propio *asset pipeline*.

Dejaremos el *Rails asset pipeline* intacto para que cualquier gema que requiera usarlo pueda hacerlo sin problemas (por ejemplo: Rails admin/Active admin que usa y genera sus propias vistas); nuestro código CSS vivirá en otro lugar y será procesado por Postcss sin pasar por el *asset pipeline* de Rails.

## Pasos para configurar
_Aplicación de Rails ya creada_

- Ejecutar `npm init` y configurar el archivo **package.json**
- Instalar gulp localmente `npm install gulp`
- Agregar en el .gitignore la carpeta /node_modules
- Crear archivo **gulpfile.js** en directorio raíz
- En **config/application.rb** requerir los archivos:

            config.assets.paths << Rails.root.join("public", "assets", "stylesheets")
            config.assets.paths << Rails.root.join("public", "assets", "javascripts")
- En **app/assets/stylesheets/application.css** requerir el archivo de salida que está en public:
`*= require main`
- En **config/environments/development.rb** configurar (para aprovechar BroswerSync):

            config.assets.debug = true
            config.assets.digest = false
- En **package.json** agregar en *scripts* lo siguiente para limpiar y compilar:

            "postinstall": "gulp clean; gulp css;"
- Para usar un plugin de postcss primero se debe instalar usando `npm install --save-dev [nombre_plugin]`

## El archivo gulpfile.js

- Se deben requerir los siguiente módulos:

        var gulp = require('gulp')
        var postcss = require('gulp-postcss')
        var browserSync = require('browser-sync').create()
        var del = require('del');
        var rename = require('gulp-rename')
- Y adicionalmente las partes de postcss que se desean usar (ver http://postcss.parts):

        var rucksack = require('rucksack-css')
        var cssnext = require('postcss-cssnext')
        var cssnested = require('postcss-nested')
        var mixins = require('postcss-mixins')
        var lost = require('lost')
        var atImport = require('postcss-import')
        var csswring = require('csswring')
        var materialShadow = require('postcss-material-shadow-helper')
        var instagram = require('postcss-instagram')
        var coloralpha = require('postcss-color-alpha')
- Deberá tener las siguientes cuatro fuciones principales:

        gulp.task('clean', function () {
          del('./public/assets/stylesheets');
        });

        gulp.task('serve', function () {
          browserSync.init({
            proxy: 'localhost:3000',
            files: ['./app/views/**']
          })
        })

        gulp.task('css', function(){
          var processors = [
            atImport({
              path: ["./gulp/stylesheets"]
            }),
            cssnested,
            lost(),
            rucksack(),
            cssnext({ browsers: ['> 1%', 'last 3 versions', 'ie 8']}),
            materialShadow(),
            instagram()
            // csswring()
          ]
          return gulp.src('./gulp/stylesheets/main.css')
            .pipe(postcss(processors))
            .pipe(gulp.dest('./public/assets/stylesheets'))
            .pipe(rename({
                    suffix: '.self'
                }))
            .pipe(browserSync.stream() )
        })

        gulp.task('watch', function(){
          gulp.watch('./gulp/stylesheets/*.css', ['css'])
          gulp.watch('./app/views/**/*.html').on('change', function(){
             browserSync.reload()
           })
        })

        gulp.task('watch', function(){
          gulp.watch('./gulp/stylesheets/*.css', ['css'])
          gulp.watch('./app/views/**/*.html').on('change', function(){
             browserSync.reload()
           })
        })

        gulp.task('default', ['watch', 'serve'])


## Ejemplos
El siguiente [ejemplo](https://github.com/juanmanuelramallo/postcss-rails-laplatarb) fue desarrollado para una charla en laplata.rb. Ver el código fuente en CSS **/gulp/stylesheets/main.css** que tiene comentarios en cada línea que usa un plugin de Postcss.

En producción, se puede observar la página de un [estudio inmobiliario platense](cabralpropiedades.com.ar) que dispone toda la interfaz de usuario creada con Postcss (sin usar ningún framework de front-end como Bootstrap o Foundation), y que al mismo tiempo usa para la sección de administración el *Rails asset pipeline* sin crear conflictos entre ambos caminos que toman los archivos de estilos.

## Consideraciones

- Las carpetas del código fuente deberán estar en **/gulp/stylesheets** (crear la carpeta)
- El archivo principal del código CSS será: **/gulp/stylesheets/main.css**
- Todo lo procesado por Postcss irá directo a **/public/assets**
- Para correr el servidor local con live-reloading se debe primero poner a correr `rails server` y luego `gulp` en la terminal

Para profundizar un poco más en el manejo de assets usando Gulp (en Rails) observar el siguiente [proyecto en github](https://github.com/vigetlabs/gulp-rails-pipeline).
