# Birthdays-CS50

Detalles de la implementación
Completa la implementación de una aplicación web que permita a los usuarios almacenar y realizar un seguimiento de los cumpleaños.

- Cuando la ruta / es solicitada vía GET, tu aplicación web debe mostrar, en una tabla, todas las personas en tu base de datos junto con sus cumpleaños.
- Primero, en app.py, añade lógica en el manejo de tu petición GET para consultar la base de datos birthdays.db para todos los cumpleaños. Pasa todos esos datos a tu plantilla index.html.
- A continuación, en index.html, añade lógica para representar cada cumpleaños como una fila en la tabla. Cada fila debe tener dos columnas: una columna para el nombre de la persona y otra columna para el cumpleaños de la persona.
- Cuando la ruta / es solicitada vía POST, tu aplicación web debería añadir un nuevo cumpleaños a tu base de datos y luego volver a renderizar la página index.
- Primero, en index.html, añade un formulario HTML. El formulario debe permitir a los usuarios introducir un nombre, un mes y un día de cumpleaños. Asegúrate de que el formulario se envía a / (su "acción") con un método post.
- Luego, en app.py, añade lógica en el manejo de la petición POST para INSERTAR una nueva fila en la tabla de cumpleaños basándote en los datos proporcionados por el usuario.

Para realizar los puntos que nos solicitan debemos ccompletar el código para poder crear una aplicación web Flask que permite agregar y mostrar cumpleaños.

La parte complicada es completar la funcion principal que en este caso es la funcion def Index:

