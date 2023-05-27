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

![](https://github.com/zazi479/Birthdays-CS50/blob/3b448bd5ca0e7a1aeacc960a73a26124751559f0/flask/funcion%20flask.png)7

Esta funcion tiene dos metodos(GET,POST), si la solicitud es POST (es decir, se envió un formulario), se realizará lo siguiente:
- Se obtienen los datos del formulario (nombre, mes y día del cumpleaños).
- Se verifica que los campos de nombre, mes y día no estén vacíos.
- Al insertar un registro de cumpleaños con alguno de los campos está vacío, se asigna un mensaje de error correspondiente.Por contra si  todos los campos están completos, se insertan los datos del cumpleaños en la base de datos utilizando la consulta INSERT INTO.
- Se recuperan todos los cumpleaños de la base de datos utilizando la consulta SELECT * FROM birthdays.
- Se renderiza la plantilla "index.html" pasando el mensaje de error (si hay alguno) y la lista de cumpleaños.

Si la solicitud es GET:
- Simplemente se recuperan todos los cumpleaños de la base de datos y se renderiza la plantilla "index.html" pasando la lista de cumpleaños.

La función index se ejecuta cuando se accede a la ruta principal ("/") de la aplicación.
