# Reconocimiento Facial
## Modelo solución:
El procedimiento comienza de la siguiente manera:
En capturandoRostros.py vamos a capturar las personas que deseamos reconocer. En entrenanamiento.py entrenamos el reconocedor de rostros con EigenFaces. Finalmente podremos probar el método en reconocimientoFacial.py

![modelo-solucion](https://user-images.githubusercontent.com/53346752/102184583-b2691f80-3e7d-11eb-93c2-987a5f25b36b.png)

## Haar Cascade:
OpenCV nos ofrece clasificadores pre entrenados no solo de rostros de personas (como el que usaremos en este post), sino de ojos, sonrisa, caras de gatitos, entre otros. Puedes encontrar estos archivos XML en la carpeta: opencv/data/haarcascades/, o puedes encontrarlos en el repositorio de OpenCV en github: https://github.com/opencv/opencv/tree/master/data/haarcascades.

### detectMultiScale
Para emplear la detección de rostros con haar cascade en OpenCV vamos a necesitar del módulo detectMultiScale que ayudará a detectar los objetos de acuerdo al clasificador que se utilice. Este nos permitirá obtener un rectángulo delimitador en donde se encuentre el objeto que se desea encontrar dentro de una imagen, para ello se deben especificar algunos argumentos que veremos a continuación (Puedes consultar otros que se pueden usar en la documentación de  OpenCV):

Image:  Es la imagen en donde va a actuar el detector de rostros.

ScaleFactor: Este parámetro especifica que tanto va a ser reducida la imagen. Por ejemplo si se ingresa 1.1, quiere decir que se va a ir reduciendo la imagen en 10%, con 1.3 se reducirá 30%, creando de esta manera una pirámide de imágenes. Hay algo que debemos tener en cuenta y es que si damos un número muy alto, se pierden algunas detecciones. Mientras que para valores muy pequeños como por ejemplo 1,01 (es decir reducir en un 1% la imagen), llevará mayor tiempo de procesamiento, ya que se tendrán más imágenes a analizar, además de que pueden incrementar los falsos positivos (que son detecciones presentadas como objetos u rostros, pero que en realidad no lo son).

![haar-cascade](https://user-images.githubusercontent.com/53346752/102184688-da588300-3e7d-11eb-9b47-16fdc014be7a.jpg)

## Procedimiento para el Reconocimiento Facial
### Faces:
En primera instancia almacenamos rostros de un banco de imágenes (capturandoRostros.py):

![faces](https://user-images.githubusercontent.com/53346752/102184751-f4926100-3e7d-11eb-9d02-b299891c84ef.png)

### Eigen Faces:
Luego entrenamos los rostros obtenidos para generar un modelo de reconocimiento facial lo cuál lo llamaremos EigenFaces.xml donde se guardará los valores de rasgos faciales que presenta la persona (entrenando.py):

![dir](https://user-images.githubusercontent.com/53346752/102186149-2e646700-3e80-11eb-85b5-2ad25dc6e1eb.png)

![eigenfaces](https://user-images.githubusercontent.com/53346752/102184785-096ef480-3e7e-11eb-848e-b05da3536110.png)

### Rogr:
Y finalmente recorremos el modelo entrenado EigenFaces.xml para reconocer a la persona con los datos recopilados (reconocimientoFacial.py):

![rogr](https://user-images.githubusercontent.com/53346752/102184828-1855a700-3e7e-11eb-97c8-683b5657a7f8.png)



