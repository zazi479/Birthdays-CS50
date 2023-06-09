# Birthdays-CS50

Detalles de la implementación
Completa la implementación de una aplicación web que permita a los usuarios almacenar y realizar un seguimiento de los cumpleaños.

- Cuando la ruta / es solicitada vía GET, tu aplicación web debe mostrar, en una tabla, todas las personas en tu base de datos junto con sus cumpleaños.
- Primero, en app.py, añade lógica en el manejo de tu petición GET para consultar la base de datos birthdays.db para todos los cumpleaños. Pasa todos esos datos a tu plantilla index.html.
- A continuación, en index.html, añade lógica para representar cada cumpleaños como una fila en la tabla. Cada fila debe tener dos columnas: una columna para el nombre de la persona y otra columna para el cumpleaños de la persona.
- Cuando la ruta / es solicitada vía POST, tu aplicación web debería añadir un nuevo cumpleaños a tu base de datos y luego volver a renderizar la página index.
- Primero, en index.html, añade un formulario HTML. El formulario debe permitir a los usuarios introducir un nombre, un mes y un día de cumpleaños. Asegúrate de que el formulario se envía a / (su "acción") con un método post.
- Luego, en app.py, añade lógica en el manejo de la petición POST para INSERTAR una nueva fila en la tabla de cumpleaños basándote en los datos proporcionados por el usuario.

 Abrimos el entorno virtual de Flask en python
 ![](https://github.com/zazi479/Birthdays-CS50/blob/3b448bd5ca0e7a1aeacc960a73a26124751559f0/flask/abrir%20el%20entorno%20flask.png)
 
 
Para realizar los puntos que nos solicitan debemos completar el código para poder crear una aplicación web Flask que permite agregar y mostrar cumpleaños.

La parte complicada es completar la funcion principal que en este caso es la funcion def Index:

![](https://github.com/zazi479/Birthdays-CS50/blob/3b448bd5ca0e7a1aeacc960a73a26124751559f0/flask/funcion%20flask.png)

Esta funcion tiene dos metodos(GET,POST), si la solicitud es POST (es decir, se envió un formulario), se realizará lo siguiente:
- Se obtienen los datos del formulario (nombre, mes y día del cumpleaños).
- Se verifica que los campos de nombre, mes y día no estén vacíos.
- Al insertar un registro de cumpleaños con alguno de los campos está vacío, se asigna un mensaje de error correspondiente.Por contra si  todos los campos están completos, se insertan los datos del cumpleaños en la base de datos utilizando la consulta INSERT INTO.
- Se recuperan todos los cumpleaños de la base de datos utilizando la consulta SELECT * FROM birthdays.
- Se renderiza la plantilla "index.html" pasando el mensaje de error (si hay alguno) y la lista de cumpleaños.

Si la solicitud es GET:
- Simplemente se recuperan todos los cumpleaños de la base de datos y se renderiza la plantilla "index.html" pasando la lista de cumpleaños.

La función index se ejecuta cuando se accede a la ruta principal ("/") de la aplicación.



# HTML

El body del HTML lo dividiremos en dos div, el primero llamado "jumbotron" y el segundo lo llamamos "section".

Empezamos por **la primera** parte del body:

![](https://github.com/zazi479/Birthdays-CS50/blob/247fda1caed4c391387351517aa0078516f6ff6c/flask/body%201.png)

En esta parte creamos en si el funcionamiento de la aplicación que permite a los usuarios agregar cumpleaños a una base de datos y verlos en una página web.

- Primero debemos configurarla aplicación Flask y establece opciones de configuración.
- Despues se conecta la aplicación a una base de datos SQLite llamada "birthdays.db".

Ahora desglosamos paso a paso el código:
- ```<div class="jumbotron">```: Esta es una clase de Bootstrap que se utiliza para mostrar un encabezado destacado en la parte superior de la página. En este caso, contiene el título "Birthdays".

- ```<div class="container">```: Esta es otra clase de Bootstrap que se utiliza para envolver el contenido principal de la página y proporcionar un margen y un espacio adecuados alrededor del contenido.

- ```<iv class="section>```: Este div se utiliza para agrupar elementos relacionados dentro del contenedor principal.

- ```<div class="error_message">```: Esta clase se utiliza para mostrar un mensaje de error si ocurre algún problema al agregar un cumpleaños. El contenido del mensaje se muestra utilizando una variable {{ message }}, que se espera que sea proporcionada por el código Python.

- ```<h2>Add a Birthday</h2>```: Este encabezado muestra el título del formulario para agregar un cumpleaños.

- ```<form action="/" method="POST">```: Este formulario se envía a la ruta principal ("/") de la aplicación Flask utilizando el método POST cuando se envía.

- ```<input name="name" type="text" placeholder="Name" autocomplete="off" autofocus>```: Este es un campo de entrada de texto donde se espera que el usuario ingrese el nombre del cumpleañero.

- ```<input name="month" type="number" placeholder="Month" max="12" min="1" autocomplete="off" autofocus>```: Este es un campo de entrada numérico donde se espera que el usuario ingrese el mes del cumpleaños. Se especifica un rango mínimo y máximo permitido (1 a 12).

- ```<input name="day" type="number" placeholder="Day" max="31" min="1" autocomplete="off" autofocus>```: Este es otro campo de entrada numérico donde se espera que el usuario ingrese el día del cumpleaños. Se especifica un rango mínimo y máximo permitido (1 a 31).

- ```<input type="submit" value="Add Birthday">```: Este es un botón de envío que se utiliza para enviar el formulario y agregar el cumpleaños a la base de datos.



**La segunda** parte del body es el div "section",que muestra todos los cumpleaños almacenados en la base de datos.

![](https://github.com/zazi479/Birthdays-CS50/blob/247fda1caed4c391387351517aa0078516f6ff6c/flask/body2.png)

- ```<div class="section">```: Este div se utiliza para agrupar elementos relacionados dentro del contenedor principal.

- ```<h2>All Birthdays</h2>```: Este encabezado muestra el título de la sección que muestra todos los cumpleaños.

- ```<table>```: Este elemento crea una tabla para mostrar los cumpleaños.

- ```<thead>```: Esta etiqueta define la sección de encabezado de la tabla.

- ```<tr>```: Esta etiqueta define una fila en la sección de encabezado de la tabla.

- ```<th>Name</th>```: Esta etiqueta define una celda de encabezado que muestra el texto "Name".

- ```<th>Birthday</th>```: Esta etiqueta define otra celda de encabezado que muestra el texto "Birthday".

- ```<tbody>```: Esta etiqueta define la sección de cuerpo de la tabla.

- ```{% for birthday in birthdays %}```: Esta es una construcción de plantilla de Flask que crea un bucle que itera sobre la lista de cumpleaños proporcionada (variable birthdays).

- ```<tr>```: Esta etiqueta define una fila en la sección de cuerpo de la tabla para cada cumpleaños.

- ```<td>{{ birthday.name }}</td>```: Esta etiqueta define una celda que muestra el nombre del cumpleañero obtenido de la variable birthday.

- ```<td>{{ birthday.month}}/{{ birthday.day }}</td>```: Esta etiqueta define otra celda que muestra la fecha del cumpleaños (mes y día) obtenida de la variable birthday.

- ```{% endfor %}```: Esta etiqueta finaliza el bucle for.

 En resumen, este parte del código HTML crea una sección en la página web que muestra una tabla con todos los cumpleaños almacenados en la base de datos. Cada fila de la tabla representa un cumpleaños y muestra el nombre y la fecha del cumpleaños.
 
 Para poder comprobar que nuestro código funciona debemos de ejecutar en el terminal 
 ``` Flask run ```  y hacer ctrl click en el link que nos proporciona.
 
 ![](https://github.com/zazi479/Birthdays-CS50/blob/fc2b3ed4d8a189ac5faeb5c25996ff7772bd86a3/flask/abrir%20la%20web.png)

Ahora mostramos el resultado de este codigo.

![](https://github.com/zazi479/Birthdays-CS50/blob/d8015078c4cb053e3304d01805263910ecf89e85/flask/flask%20foto%20final%20maximo%20cumple.png)

Como se puede ver en la imagen he podido añadir la fecha de mi propio cumpleaños.

Para resumir,con este código, puedes crear tu propia página web para administrar y ver cumpleaños. La página te permite agregar nuevos cumpleaños a una base de datos y luego ver la lista completa de cumpleaños almacenados. Es una forma divertida de mantener un registro de todos los cumpleaños importantes en tu vida.








