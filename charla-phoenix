Charla Elixir Noviembre
===================

# Introducción

Hola a todos. Mi nombre es Nicanor Perera. Trabajo en Snappler. Hace varios años que trabajo como desarrollador Ruby on Rails, y hace algunos meses estoy haciendo experimentos con el lenguaje de programación Elixir y el framework web Phoenix.

Esta charla es acerca de mis experiencias y mi intención es darle una aproximación al lenguaje desde la perspectiva de un programador Rails.

# Programación funcional

Para hablar de Elixir y Phoenix, antes tengo que explicar brevemente qué es esto de la programación funcional.


# Sin efectos secundarios

En la programación funcional no existen los efectos secundarios. No hay variables globales. Los valores que retorna una función dependen únicamente de sus parámetros de entrada. A partir de los mismos parámetros, una función retorna siempre el mismo resultado.
 
Al eliminar los efectos secundarios se puede predecir el comportamiento de un programa mucho más fácilmente. Las funciones puras son muy fáciles de testear.


# Inmutabilidad

En programación funcional no existe el concepto de variable como existe en lenguajes imperativos. Cuando se pasa un dato a una función, esta no lo modifica sino que retorna un nuevo dato. Esto aplica también para estructuras de datos. Por ejemplo, agregar un dato a una lista en programación imperativa significa tomar un dato y mutar una lista. En cambio en programación funcional se toma un dato, una lista y se retorna una lista nueva.

Si las estructuras de datos son inmutables, entonces se eliminan los problemas de interacción entre hilos de ejecución por mutación de datos. Esto, sumado a la ausencia de efectos secundarios hace que la programación funcional sea muy buena para implementar programas concurrentes.


# Transformaciones sin estado de datos inmutables

La programación orientada a objetos es acerca de objetos que se envían mensajes. Estos objetos consisten en datos y comportamiento fuertemente acoplado. 

La programación funcional desacopla los datos del comportamiento (las funciones).

En programación orientada a objetos, suele ocurrir que existan algunos bugs que sólo ocurren cuando un objeto está en un estado en particular. Reproducir el problema puede ser complicado porque de entrada no se sabe cual es el estado (todo está oculto dentro de un objeto). Y una vez que se descifra puede ser difícil reproducirlo, porque quizás sólo ocurre luego de que lo activa una cadena particular de eventos.

En programación funcional se pasan los datos a través de un conjunto de funciones y los datos nunca mutan. La salida de una función es la entrada de la función siguiente. Cuando ocurre un error es más fácil descifrar qué pasa y dónde pasa. La mutación significa pérdida de información, y no hay mutación en programación funcional.

# Erlang y Concurrencia

Erlang es un lenguaje de programación concurrente y funcional. Corre sobre una máquina virtual llamada BEAM. Fue desarrollado por Ericsson y diseñado desde las bases para escribir aplicaciones **escalables**, **tolerantes a fallos**, **distribuídas**, **de tiempo real** y **de alta disponibilidad**. Absolutamente todo en el lenguaje, la máquina virtual y las librerías reflejan ese propósito, lo que hace que Erlang sea la mejor plataforma para desarrollar este tipo de software.

Como Erlang fue creado con la concurrencia en mente es naturalmente bueno para usar sistemas con múltiples núcleos.

La creación, gestión y comunicación de procesos es sencilla en Erlang, mientras que en muchos lenguajes, los hilos se consideran un apartado complicado y propenso a errores. En Erlang toda concurrencia es explícita.

En Erlang todo es un proceso. Los procesos de Erlang no son procesos de Sistema Operativo, sino que son procesos de la Máquina Virtual. Son muy livianos (300B). Tan livianos que una computadora relativamente buena puede tener millones de procesos corriendo concurrentemente.

La creación y destrucción de procesos es una operación liviana. Los procesos están isolados entre sí.  Los procesos no comparten recursos. Hacen lo que tienen que hacer o fallan.

La única manera en que pueden interactuar entre sí es a través del pasaje de mensajes. Los procesos tienen nombres únicos. Si conoces su nombre, entonces podés enviarles mensajes. Además, un proceso puede supervisar a otros procesos. Si un proceso falla, el proceso supervisor puede revivirlo en un estado seguro. 

En Erlang existe el concepto de HotSwapping: se puede actualizar código ejecutandose en producción sin tener que detener el programa en funcionamiento.

Estas características hacen que Erlang sea un sistema tolerante a fallos y que nunca detenga su ejecución.

# Jose Valim

José Valim, y es uno de los programadores detrás de Plataformatec. Es un conocido contribuidor en la comunidad Ruby on Rails.

En 2010, José Valim estaba trabajando en mejorar la velocidad de Rails en sistemas de múltiples núcleos, ya que las máquinas que usaba en producción cada vez venían con más núcleos.

Como cuenta él, toda la experiencia fue muy frustrante. Rails no proveía las herramientas apropiadas para resolver problemas de concurrencia. Ahí fue cuando José comenzó a mirar otras tecnologías y eventualmente se topó con la Máquina Virtual de Erlang.

José comenzó a usar Erlang más y más, y notó que extrañaba algunas construcciones que estaban presentes en otros lenguajes. Fue ahí que decidió crear Elixir, en un intento de traer novedosas herramientas por encima de la máquina virtual de Erlang.

# Elixir

Elixir es un lenguaje funcional y dinámico diseñado para construir aplicaciones mantenibles y escalables y es usado exitosamente en desarrollo web y en el dominio del software embebido.


# Tipos de datos

En elixir podemos encontrar tipos de datos como **enteros**, **flotantes**, **rangos**, **booleanos**, **binarios** (los strings se implementan como binarios codificados en UTF8), **átomos** (son constantes para los que su nombre es su propio valor. Son similares a los simbolos en Ruby).

Y también estructuras de datos como **tuplas** (Es una conjunto de elementos ordenados), **listas** y **mapas** (conjunto de claves-valor, similares a los hashes en Ruby).

Todas estas estructuras de datos son inmutables. Esto significa que si le agregan un elemento a una lista, o tupla, o eliminan un elemento de un mapa, no están en realidad modificando la estructura, sino que están retornando una estructura nueva.

En elixir no tenés que preocuparte de clonar o duplicar una estructura de datos porque otra función la pueda haber mutado de una forma que no te esperabas.

# Structs

Son una extensión construida sobre los mapas que proveen chequeos en tiempo de compilación y valores por defecto. Son lo más parecido a clases en Ruby en cuanto a su sintaxis, pero no dejan de ser una simple estructura de datos.

En elixir los datos son muy eficientes y baratos. Y las estructuras de datos también, ya que son valores agregados.

En OO, si tenemos dos strings iguales no son el mismo string. Cada uno tiene su propio *object_id*. En programación funcional no existe tal diferenciación. Los valores son **fáciles de fabricar**, **identificables**, **comparables**, **compartibles** y **se definen por sí mismos**.

Si tenemos dos listas, y ambas tienen los mismos números en el mismo orden, decimos que son **la misma lista**.

#Funciones anónimas

En Elixir las funciones son un ciudadano de primera clase, lo que significa que pueden ser pasadas como parámetro a otras funciones, de la misma forma en que pueden serlo un entero o un string.


# Elixir & Ruby

Elixir tiene muchas contrucciones parecidas a Ruby. Y tiene mucho sentido, porque José Valim se inspiró fuertemente en la sintaxis de Ruby para crear Elixir.

Si bien se ven similares en sintaxis, los enfoques para solucionar problemas en un lenguaje y otro son diferentes. De hecho, Elixir en ese sentido se parece mucho más a Erlang que a Ruby.

La instalación de Elixir es muy sencilla y está muy bien documentada. Se debe instalar primero Erlang, y luego Elixir. Si han podido instalar Ruby alguna vez, no van a tener ninguna dificultad en instalar Elixir.

#Consola interactiva

Al igual que Ruby, Elixir cuenta con una consola interactiva, llamada IEX (Interactive - Elixir). Una vez que instalaron Elixir, pueden acceder a la consola interactiva escribiendo *iex*.

#Match Operator

El símbolo **"="** es el operador de match y muchas veces su comportamiento es similar a la asignación en Ruby, pero en la práctica son muy diferentes:

Si la expresión de la izquierda no es igual en valor o en estructura, la operación retorna error.

En caso de que lo que haya a la izquierda sea una variable, entonces se le asigna el resultado de la derecha.

**2 = x** retorna error porque los lados no matchean: las variables son asignadas sólo cuando están en el lado izquierdo.

El operador Match no es sólo usado para valores simples: es muy útil para desestructurar tipos de datos más complejos. Por ejemplo podemos hacer pattern matching en tuplas.

    {a, b} = {:hello, “world”}

En este caso, se inicializan los identificadores **a** y **b** con el atomo **:hello** y el string **“world”**.

A esto se lo llama pattern matching. El patrón de la derecha encaja estructuralmente con el de la izquierda

El pattern matching va a fallar si ambos lados no pueden ser igualados estructuralmente. Por ejemplo si las tuplas tienen diferentes tamaños, o de un lado tengo una tupla y del otro una lista, entonces la operación Match va a fallar.

Más interesante, podemos hacer matching sobre valores específicos.

    {:ok, result} = {:ok, 42}

En este ejemplo el lado izquierdo sólo va a matchear con el lado derecho cuando lo que haya del lado derecho sea una tupla de dos elementos cuyo primer valor sea el atomo **:ok**.


Este potencial se puede aprovechar para tuplas, y también en listas, mapas y structs.

# Funciones

Ya vimos funciones anónimas así que ahora voy a hablarles de funciones nombradas. En elixir agrupamos las funciones en módulos. Los módulos se definen con la macro **“defmodule”** y las funciones con la macro **“def”**.

    defmodule Math do
      # Esto es un comentario
      def sum(a,b) do
        a + b
      end
        
    end
        
    Math.sum(1,2) #=> 3

Una funcion puede ser definida varias veces para distintos parametros de entrada. Elixir intentará usar cada clausula en orden hasta que la primera *matchée*. 

    defmodule Math do
      def zero?(0) do
        true
      end
      
      def zero?(x) when is_integer(x) do
        false
      end
    end

En el ejemplo, si se envìa como parámetro **0**, va a matchear con la primera deficinión y retornará **true**. 

Si le mando el valor **5**, va a intentar matchear con la primera definición pero no va a poder, porque **0** no matchea con **5**. Luego va a matchear con la segunda, lo que le asigna el valor **5** a la variable **x**. Y la función retorna **false**.


La macro **when** define una guarda, que me permite definir condiciónes extras. En este caso, el parámetro que se envía a la función tiene que ser obligatoriamente un número entero. Si mando algo que no sea un número, por ejemplo el string **“hola”**. Elixir va a lanzar un error que dirá algo similar a **“la función zero? no existe para “hola”**.

Esto facilita el debugging y hace que las funciones sean más seguras, al no estar definidas para valores no permitidos.

Las funciones pueden ser escritas con esta notación:

    defmodule Math do
      def zero?(0), do: true  
      def zero?(x) when is_integer(x), do: false
    end

Si quieren saber cual es la forma preferida, pueden leer las guías de estilos: https://github.com/christopheradams/elixir_style_guide

# Pipe operator

    expression |> function_call()

El Operador Pipe es muy similar a los pipes de Unix. Lo que hace es introducir la expresión que está a la izquierda como primer argumento de la función que se llama a la derecha.

A continuación se muestra una porción de código de un programa en *Ruby On Rails* que tenemos andando en producción.

class AvailabilityManager


      def call(query)
        adapted_query = Adapter.call(query)
        xml_query     = XMLBuilder.call(adapted_query)
        xml_response  = API.call(xml_query, :some_option)
        response      = Parser.call(xml_response)
    
    
        return response
      end
    
    
    end

Básicamente lo que hace el método **call** es consultar sobre la disponibilidad de hoteles a una API XML externa.

Funcionamiento: Llega una consulta en formato *JSON*. **Adapter** la modifica. Luego **Builder** recibe la entrada modificada y la traduce a formato *XML*. **API** recibe la consulta en *XML* y retorna una respuesta XML. **Parser** toma esa respuesta *XML*, la parsea y finalmente se retorna el resultado.

Si escribieramos este código en Elixir, lo más probable es que usemos el operador **pipe** y el código se vea más o menos así: 

    defmodule AvailabilityManager do
    
      def call(query) do
        query
        |> Adapter.call
        |> XMLBuilder.call
        |> API.call(:some_option)
        |> Parser.call
      end
    
    end

El propósito del operador **pipe**  es hacer énfasis en los datos siendo transformados por una serie de funciones.


# Macros

Elixir adopta la metaprogramación. De hecho la mayor parte de Elixir está escrita en Elixir mismo.
https://github.com/elixir-lang/elixir

La magia detrás de esto está en las macros.

Una macro es una instrucción que se expande automáticamente en un conjunto de instrucciones para ejecutar una tarea en particular durante la compilación. 

Gran parte de las funcionalidades en el núcleo de elixir están implementadas en macros.

*Nota: recomiendo mucho mirar el código de elixir para ver cómo está implementado.*


# Testing

Elixir viene equipado con un framework de Testing llamado **ExUnit**.

Podemos correr nuestros tests con el comando **mix test**.

    defmodule MyTest do
      use ExUnit.Case
    
      test “the truth” do
        assert 1 + 1 == 2
      end
    
    end

La linea **use Exunit.Case** importa las funciones y macros necesarias para correr tests. Es común que los programas en *Elixir* tengan por lo menos una línea más de código que los programas escritos en *Ruby*. Esto es porque en *Elixir* no existe la herencia, entonces para importar funciones o macros se usan ese tipo de construcciones.

    Finished in 0.03 seconds (0.02s on load, 0.01s on tests)
    1 tests, 0 failures

A simple vista pareciera que la función **assert** simplemente verifica que la expresión de la derecha sea verdadera. En realidad **assert** no es una función, sino que es una macro. Esta macro analiza el código. En este caso entiende que la expresión es una igualdad y provee un buen reporte siempre que haya un fallo.

    1) test the truth (ExampleTest)
         test/example_test.exs:5
         Assertion with == failed
         code: 1 + 1 == 3
         lhs:  2
         rhs:  3
         stacktrace:
           test/example_test.exs:6
    
    Finished in 0.03 seconds (0.02s on load, 0.01s on tests)
    1 tests, 1 failures


Si lo que comparamos son strings, el test hace un **diff** de los valores a la izquierda y a la derecha.

    assert “hola mundo lindo” == “hola bello mundo”

    1) test the truth (MundoTest)
         test/mundo_test.exs:5
         Assertion with == failed
         code: “hola mundo lindo” == “hola bello mundo”
         lhs:  “hola mundo lindo”
         rhs:  “hola bello mundo”
         stacktrace:
           test/mundo_test.exs:6
    
    Finished in 0.02 seconds
    1 tests, 1 failures


# Interoperabilidad con Erlang

Uno de los beneficios de construir sobre la máquina virtual de *Erlang* es la gran cantidad de librerías disponibles para nosotros. Elixir tiene interoperabilidad con Erlang. Esto significa que podemos usar librerías de Erlang en Elixir y viceversa.


# Aplicaciones

La mayoría de los paquetes de elixir son compartidos en forma de aplicación, y tienen una estructura de código similar. Esto es muy bueno porque cuando uno se familiariza con esta estructura es muy fácil encontrar dónde está definido lo que uno busca por ejemplo al analizar código de otras personas.

En *Elixir* y *Erlang*, una aplicación es un componente que implementa una funcionalidad específica y que puede ser iniciado y parado como una unidad, y además puede ser reutilizado por otros sistemas.

Una aplicación se crea con el comando mix **new nombre**.

    nombre
      ├── lib
      │   └── nuevo.ex
      ├── config
      ├── test
      └── mix.exs

Así como los archivos de *ruby* tienen la extensión **.rb**, los de *elixir* tienen la extensión **.ex**. Dentro de la carpeta **lib** es donde va a ir todo nuestro código.

También tenemos carpetas para correr tests y para archivos de configuración.

En el archivo **mix.exs** se define el nombre de la aplicación, la versión de la aplicación, la versión de Elixir, y las dependencias entre otras cosas.

# Mix

Mix es una herramienta que viene con *Elixir* y provee tareas para crear, compilar y testear tus aplicaciones, manejar sus dependencias y mucho más.

Es muy poderoso y muy rápido. Haciendo analogía con el mundo *Rails*, cumple las funciones de *Bundle* y de *Rake*.

Es muy extensible y es fácil crear tus propias tareas.


# Phoenix vs Rails

*Phoenix* es un framework web escrito en Elixir.

La mayor parte del equipo detrás de Phoenix viene de la comunidad Rails, por lo que es natural que hayan tomado algunas de las excelentes ideas que trae Rails. 

Ambos son frameworks MVC que se centran en la productividad. Proveen una estructura de directorio por defecto y generadores, ambos tienen un archivo de rutas, ambos usan bases de datos relacionales por defecto (sqlite3 en Rails y Postgresql en Phoenix). Ambos promueven mejores practicas de seguridad por defecto y vienen equipados con herramientas de testing.

Pero **Phoenix NO es Rails**. 

# Nueva aplicación

Si queremos usar el stack por defecto debemos instalar *postgresql*, *node.js* y *Phoenix*.

Para crear una aplicación *Phoenix* debemos escribir el comando **mix phoenix.new nombre_aplicacion**.

# Estructura de directorios

La estructura de directorios creada por Phoenix es similar a la siguiente:

    phoenix_application
      ├── lib
      │   ├── probando
      │   │   ├── endpoint.ex
      │   │   └── repo.ex
      │   └── probando.ex
      ├── config
      │   ├── config.ex
      │   ├── dev.ex
      │   ├── prod.ex
      │   └── test.ex
      ├── priv
      ├── test
      └── web
      │    ├── channels
      │    ├── controllers
      │    ├── models
      │    ├── static
      │    ├── views
      │    ├── templates
      │    ├── gettext.ex
      │    ├── router.ex
      │    └── web.ex
      └── mix.exs

Si miramos con detenimiento vamos a ver que tienen muchos puntos en común con la estructura de una aplicación Rails.

# Phoenix es Elixir

Es común que los programadores *ruby* digamos que somos **programadores Rails**. Esto no ocurre así con *Phoenix*.

Si miramos con detenimiento podemos observar que la aplicación tiene un archivo mix.exs, y las carpetas lib, config y test entre otras. Esto es porque **una aplicación Phoenix es una aplicación Elixir**.

Esto significa que hay una sóla manera de construir, correr, testear y desplegar tus aplicaciones: **la manera Elixir**.

Al ser una aplicación elixir, contás con herramientas de **supervisión**, **tolerancia a fallos** e **introspección** en tu sistema en ejecución. 

# Plug

*Plug* es una librería escrita en *Elixir* que proporciona una especificación para crear módulos acoplables entre aplicaciones web. Estos módulos se llaman plugs.

Para esto utiliza la estructura **Conn**.

    %Plug.Conn{}

Esta estructura tiene información de la petición y la respuesta HTTP. 

En *Rails*, *Rack* separa la petición de la respuesta. En *Phoenix* en cambio, manejamos el concepto de conexión. En cada paso del ciclo de vida de la conexión interactuamos con *Plug*. La conexión comienza partiendo de un módulo llamado *Endpoint*, pasa por las *rutas* y termina en los *controladores*, que se encargan de completar el ciclo.


# Endpoint

El ciclo de vida de petición y respuesta en Phoenix difiere mucho del enfoque que Rails toma con Rack. Como regla general, explicito es mejor que implicito. Phoenix favorece la explicitud en todo el recorrido de una petición.

Cuando generás una aplicación, podés ver todos los plugs por los que pasa la solicitud en el archivo endpoint.ex.

    defmodule MyApp.Endpoint do
      use Phoenix.Endpoint, otp_app: :my_app
    
    
      socket "/socket", MyApp.UserSocket
      plug Plug.Static, at: "/", only: ~w(css images js)
      plug Plug.RequestId
      plug Plug.Logger
      plug Plug.Parsers, parsers: [:urlencoded, :multipart, :json]
      plug Plug.MethodOverride
      plug Plug.Head
      plug Plug.Session, store: :cookie
      plug MyApp.Router
    end

Mientras que Rails segrega todo el middleware de Rack en una parte de la aplicación oculta a los ojos del programador, Phoenix hace todos los plugs explicitos. Tenes una mirada instantánea a simple vista de todo el ciclo de vida de la solicitud simplemente viendo los plugs en tu endpoint y tu router.

El plug **Static** sirve archivos estáticos. si no lo encuentra, pasa la conexión al siguiente plug. **RequestId** agrega el header *"x-request-id"* en caso de que no exista. Este header sirve para debugging. **Logger** guarda en los logs info de la petición. Algo como: `GET /index.html Sent 200 in 572ms`. **Parsers** toma el body de la solicitud y lo parsea en caso de que sea necesario para poder ser usado luego en los controladores. **MethodOverride** cambia el verbo post por el verbo definido en el parámetro *_method*, que puede ser *put*, *patch* o *delete*. **Head** convierte el verbo HTTP *HEAD* end un requerimiento *GET*. **Session** configura variables de sesión y almacenamiento de cookies.

Finalmente la conexión es pasada al **router**, que por sí mismo implementa también *Plug*.

# Router

Así es como se ve un archivo de rutas sencillo en Ruby on Rails, con acciones para el indice y la vista de articulos, y con root path manejado por ese controlador.

    Rails.application.routes.draw do
      resources :articles, only: [:show, :index]
      root to: "pages#index"
    end

El archivo de rutas de Phoenix es un poco más complejo.

    defmodule MyWeb.Router do
      use MyWeb.Web, :router
    
    
      pipeline :browser do
        plug :accepts, ["html"]
        plug :fetch_session
        plug :fetch_flash
        plug :protect_from_forgery
        plug :put_secure_browser_headers
      end
    
    
      pipeline :api do
        plug :accepts, ["json"]
      end
    
    
      scope "/", MyWeb do
        pipe_through :browser
        resources "/articles", ArticleController, only: [:index, :show]
        get "/", PageController, :index
      end
    end


Los **pipelines** son simplemente *plugs* apilados uno encima de otro con un orden y nombre específico. Por defecto, la ruta de phoenix tiene 2 pipelines. Browser y Api.


El pipeline :browser tiene 5 plugs: **:accepts** define los formatos que va a aceptar. **:fetch_session** y**:fetch_flash** nos permiten usar la información de sesión y mensajes flash respectivamente en los controladores. Usar 
**:protect_from_forgery** y **:put_secure_browser_headers** nos protege de ataques *CSRF*

Al igual que en el caso del endpoint, gracias a que definimos los plugs de forma explícita, podemos ver de un vistazo exactamente lo que está ocurriendo en nuestra aplicación.

Incluso podemos crear nuestros propios *plugs*.

Por ejemplo, si tuviéramos un *scope* para administradores, podríamos crear un *plug* de autentificación, que sólo permita pasar a un usuario que tenga rol administrador.

Según las guías de Phoenix: **Si nos preguntamos *“¿Puedo poner esta funcionalidad en un plug?"*, usualmente la respuesta es sí.**

Más info: http://www.phoenixframework.org/docs/understanding-plug


# Controladores

Los **controladores** de *Phoenix* actuan como módulos intermedios. Sus funciones, llamadas acciones, son invocadas desde un router en respuesta a una petición HTTP.

Las acciones toman los datos necesarios y realizan los pasos necesarios antes de invocar a la capa de vista y renderizar un template o retornar una respuesta JSON.

    defmodule MyWeb.ArticleController do
      use MyWeb.Web, :controller
      
      def show(conn, %{"id" => id}) do
        article = Repo.get!(MyWeb.Article, id)
        render(conn, "show.html", article: article)
      end
    end

Los controladores de Phoenix están construidos sobre el paquete **Plug** y ellos mismos son plugs.



Las acciones de Rails parecieran mucho más simples que las de phoenix:

    class ArticlesController < ApplicationController
      def show
        @article = Article.find(params[:id])
      end           
    end

Y esto es porque Phoenix favorece la forma explícita de escribir código.

No todos los programadores rails lo saben, pero la acción **show** de Rails llama implicitamente a **render “show.html”**. Además, todas las variables de instancia son copiadas de la instancia del controlador a la instancia de la vista, que es una capa de complejidad que pocos conocen cuando comienzan a programar en Ruby on Rails.

Además de eso, los programadores deben ser concientes de todo el estado implicito de la instancia, como el hash *params* o el *request object*, y cualquier variable de instancia creada en los filtros *before_actions*.

Convención sobre configuracion es algo bueno, pero hay un punto en el que el comportamiento implicito sacrifica la claridad. **Phoenix optimiza por claridad**.


**conn** es nuestra bolsa de datos y linea de comunicación con el servidor web. Como Phoenix favorece el código explícito, **conn** es pasado como parámetro a las acciones *Phoenix* y es enviado explicitamente como parámetro a la acción *render*. En Phoenix, las acciones de un controlador **son simplemente funciones**.


# Testing de controllers

La programación funcional y el contrato con *Plug* hace que sea muy sencillo testear los controladores de forma aislada. Simplemente es necesario pasar una conexión:

    test "sends 404 when article is not found" do
      conn = MyController.show(conn(), %{"id" => "not-found"})
      assert conn.status == 404
    end

Y suele ser trivial hacer tests de integración de tu endpoint entero. :

    test "shows articles" do
      conn = get conn(), "/articles/123"
      assert %{id: "123"} = json_response(conn, :ok)
    end

# Vistas

*Phoenix* separa templates de vistas. Las vistas de *phoenix* tienen dos trabajos: renderizar los templates y proveer funciones que puedan ser usadas por los mismos.

    defmodule MyWeb.ArticleView do
      use MyWeb.Web, :view
        
      def title do
        "Funcional |> Concurrente |> Divertido"
      end
    end

Si en *Rails* se han preguntado alguna vez dónde poner lógica de vistas, o si usar decorators o presenters, en *Phoenix* no tienen que preguntárselo más. La vista es el lugar indicado para ese tipo de lógica.

# Templates

Los templates son archivos a los que pasamos datos para formar respuestas HTTP completas. Para una aplicación web son documentos HTML, y para una API pueden ser respuestas JSON o XML.

**EEx** es el sistema de templates por defecto de *Phoenix* y es muy similar a *ERB* de *Ruby*. De hecho es parte de *elixir* mismo.

    <h2><%= @article.title %></h2>
    <p><%= @article.description %></p>
        
    <%= link “Editar”, to: article_path(@conn, :edit, @article) %>
    <%= link “Volver”, to: article_path(@conn, :index) %>

Los templates de Phoenix son precompilados, lo que los hace extremadamente rápidos.

De hecho cuando miramos la consola de una aplicación en ejecución, es común ver informes como estos:

    [info] GET /
    [info] Sent 200 in 396µs

La letra griega µ (Mu) significa microsegundo. O sea millonésimas de segundo. Es muy común que una vista *Phoenix* responda entre 2 y 3 ordenes de magnitud más rápido que una aplicación Rails.



# Ecto

**Ecto** es una librería escrita en Elixir. En *Phoenix*, cumple la función que cumple *ActiveRecord* en *Rails*.

Ecto tiene 4 componentes principales:

**Ecto.Repo** Un repositorio es un wrapper alrededor de una base de datos. A través del repositorio podemos crear, actualizar, eliminar y realizar consultas a la base de datos.

**Ecto.Schema**  Los esquemas son usados para mapear los datos de las filas de una tabla en estructuras de Elixir.

**Ecto.Changeset** Los conjuntos de cambios proveen formas de filtrar, comprobar y realizar validaciones en los datos.

**Ecto.Query** Las consultas son usadas para traer información de un repositorio. Los queries son seguros y evitan problemas como inyección SQL al mismo tiempo que son acoplables, permitiendo armar una consulta pieza por pieza.

Más info: https://hexdocs.pm/ecto/Ecto.html


# Migración

Cada migración es una nueva versión de una base de datos. En Rails cada vez que corrés una migración, esta actualiza un archivo llamado *schema*. Una migración rails se ve así: 

    class CreateArticles < ActiveRecord::Migration[5.0]
      def change
        create_table :articles do |t|
          t.string :name
          t.text :description        
          t.timestamps
        end
      end
    end

En Phoenix en cambio, el programador es el encargado de definir explícitamente cómo quiere mapear los datos de la base de datos a estructuras de Elixir. Las migraciones en Phoenix se definen de forma muy similar a las de Rails:

    defmodule MyWeb.Repo.Migrations.CreateArticle do
      use Ecto.Migration
    
      def change do
        create table(:articles) do
          add :title, :string
          add :description, :string
          timestamps
        end
      end
    end


# Modelos

Un modelo de *Phoenix* es simplemente un *struct* de *Elixir*. Estas estructuras no tienen estado y son super livianas. Son fáciles de comparar y compartir. El *schema* debe ser definido explicitamente.

    defmodule MyWeb.Article do
      use MyWeb.Web, :model
    
      schema "articles" do
        field :name, :string
        field :description, :string
        timestamps()
      end
    
      def changeset(struct, params \\ %{}) do
        struct
        |> cast(params, [:name, :description])
        |> validate_required([:name])
      end
    end

Cuando se traen objetos de la base de datos en *Rails*, la operación tiene que hacer trabajo extra al instanciar cada uno de los objetos.

Para validar los datos, hay que pasarlos a través de *changesets*. Es un poco más verboso que en *Rails*, pero es mucho más flexible. 


# Assets

Rails implementó una herramienta específica para manejar el *assets pipeline*. Pero Phoenix piensa que hay que usar **la herramienta indicada para el trabajo indicado**.

Para manejar assets estáticos, Phoenix usa por defecto usa un manejador de paquetes de Javascript muy fácil de configurar y usar llamado **brunch**. Cumple las mismas funciones que *Webpack*, *Grunt* o *Gulp*. Se puede cambiar por cualquiera de estos según las preferencias. 

Esto es muy poderoso, ya que las mejores herramientas de hoy en día para manejar assets funcionan en node.js.

En Phoenix pueden usar todos los paquetes javascripts que existen en el mercado de forma muy sencilla. Si te gusta JS6 tenés un paquete para usarlo (Babel viene por defecto en Phoenix). Si querés usar *SCSS*,  *LESS*,  *PostCSS*, *CoffeeScript*, simplemente tenés que agregar el paquete al archivo de configuración de brunch.


# Live Reload

Phoenix viene con **live-reload** para el desarrollo. Esto significa que tan pronto como modificás y guardás un archivo *.js* o *.css*, o el código de un template o una vista, este es automáticamente recargado en tu navegador (sin necesidad de actualizar la página).

Una vez que agregas esta funcionalidad a tu workflow de desarrollo, es difícil volver atrás.

# Canales

Phoenix fue construido desde el primer día para enfrentarse a los retos de la moderna, altamente conectada web en tiempo real. Los canales traen conecciones en tiempo real, agnósticas en cuanto al transporte a tu aplicación, lo que puede escalar en millones de clientes usando tu aplicación en un único servidor.

Es distinto a Rails en que históricamente, las funcionalidades de tiempo real no han tenido gran importancia.

La web está evolucionando para incluir dispositivos conectados como teléfonos, relojes, tostadoras inteligentes. Phoenix es un framework que está preparado para poder evolucionar con nuevos protocolos.

Rails entró hace poco en las funcionalidades de tiempo real con ActionCable. Phoenix tomó muchas de sus ideas de Rails, y hace no mucho Rails tomó esta idea de Phoenix.
ActionCable suele venir con muchas dependencias como Faye, Celluloid, EventMachine y Redis.

Como Phoenix corre sobre la máquina virtual de Erlang, Phoenix tiene todas estas funcionalidades en tiempo real de forma gratuita desde el comienzo.

# Comunidad

Algo que tienen en común Ruby y Elixir es que ambos tienen una comunidad increíble de programadores. La comunidad de Elixir es aún pequeña, pero está creciendo increíblemente cada día.


Es posible
Hay un mito de que la programación funcional es complicada. Y que hay que ser matemáticos, y que hay que entender cómo funcionan las monadas y los functors y hay que saber teoría de conjuntos y un montón de cosas más.

No se preocupen. No es necesario saber nada de eso para programar en Elixir. De hecho, si en algún momento aprendieron (y siguen aprendiendo) a programar en Ruby están totalmente capacitados para aprender a programar en Elixir.

Por supuesto que no va a ser fácil. Hay muchos conceptos nuevos que uno tiene que aprender. Todo cuesta al principio. En el camino van a tener muchas frustraciones, pero si se animan, a medida que vayan aprendiendo van a dejar todos los obstáculos detrás.


#Cierre

Hace casi 7 años que soy programador *Ruby on Rails*. Empecé trabajando en una empresa llamada [Xaver](http://www.xaver.com.ar/) y hace un poco más de 2 años trabajo en [Snappler](http://www.snappler.com/). La primera vez que use Ruby estaba increíblemente entusiasmado.

Me encantaba la facilidad con la que podía escribir código, la expresividad y la elegancia. Y no usar puntos y comas al final de cada línea.

En su momento había un artículo de cómo hacer un blog en 10 minutos usando *Ruby on Rails*. Unos minutos después tenía un blog funcionando. Un poco más de trabajo y había podido agregar estilos. Un poco más y la había logrado subir a *Heroku*.

De repente podía hacer cosas. Parece tonto pero en su momento era muy importante. Podía ser un programador extremadamente productivo por mi cuenta.

Hace tiempo que tenía muchas ganas de probar un lenguaje funcional y hace unos meses me topé con *Elixir* y *Phoenix*. Quedé maravillado con la facilidad de escribir código en *Elixir*, con todas las ventajas que ofrecía la programación funcional y con el poder de *Erlang*. Y de algún modo la historia se repitió. Encontré un artículo de cómo hacer un *chat room* en 10 minutos. A los pocos minutos tenía un *chat* completo funcionando en tiempo real.

Con Elixir y Phoenix volví a sentir el entusiasmo que había sentido 7 años atrás.

# Whatsapp

Recientemente *Facebook* compró *Whatsapp* por **19 mil millones de dolares**. Whatsapp corre sobre la máquina virtual de *Erlang*, y cada computadora en la que corre el servidor de *Whatsapp* puede manejar **2 millones de conexiones** al mismo tiempo.

Hoy en día *Whatsapp* tiene **900 millones de usuarios** y sólo **50 ingenieros**. Eso hace que **el ratio programador/cliente sea 1  por cada 18 millones**. Elixir y Phoenix tienen todo ese poder.

# Futuro 

La ley de Moore dejó de aplicar hace varios años. Para hacer computadoras más rápidas cada día las máquinas vienen con más y más procesadores. Elixir es capaz de aprovechar todo este potencial.

La web está evolucionando. La web moderna es **altamente conectada** y necesita sistemas en tiempo real. Requiere incluir dispositivos conectados como teléfonos, relojes y sistemas embebidos. Necesita sistemas de alta disponibilidad. Sistemas escalables, tolerantes a fallos y distribuidos.

*Phoenix* fue construido desde el primer día para enfrentarse a los retos de la web moderna y poder adaptarse a los nuevos desafíos que aparezcan. Las tecnologías avanzan muy rápidamente y en nuestro rubro es importante poder adaptarse a los nuevos requerimientos. Simplemente hay que vencer los miedos y animarnos. El futuro está al alcance de nuestras manos.

Así que les pregunto: ¿Se animan a enfrentar los desafíos que propone la nueva web?

Gracias
