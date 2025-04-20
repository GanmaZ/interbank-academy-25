# Reto Técnico: Procesamiento de Transacciones Bancarias (CLI)

## Introducción:

Desarrolla una aplicación de línea de comandos (CLI) que procese un archivo CSV con transacciones bancarias y genere un reporte que incluya:

- **Balance Final:**  
  Suma de los montos de las transacciones de tipo "Crédito" menos la suma de los montos de las transacciones de tipo "Débito".

- **Transacción de Mayor Monto:**  
  Identificar el ID y el monto de la transacción con el valor más alto.

- **Conteo de Transacciones:**  
  Número total de transacciones para cada tipo ("Crédito" y "Débito").

---

## Instrucciones de ejecución:

1. **Entorno para la ejecución:**  
   Se necesita acceso a un mainframe con Z/OS 3.1 que tenga instalado COBOL 6.4 y la utilidad IEFBR14 para crear el PS de 80 caracteres de largo usando JCL, en este se copiará toda la información del archivo CSV.
   La utilidad IEFBR14 no es obligatoria ya que existen otras formas de crear un PS en MAINFRAME y tambien otras forma de copiar o subir estos datos al MAINFRAME, puedes usar el archivo llamado IEFB14 para crear este PS.
   Deberas tener el MEMBER fuente del programa cobol en tu SOURCE LIBRARY con el nombre de PROCTRAN.

2. **Compilacion y ejecución:**
   Ya en el entorno mainframe deberas hacer SUBMIT al JCL llamado JCLPROCT para que en su primer paso compile el fuente del programa cobol que es el MEMBER llamado PROCTRAN y en el segundo paso ejecute el programa tomando el compilado y el PS creado anteriormente, los 
   datos ya los debes haber copiado a este PS.
   Probablemente debas de cambiar todo lo que diga JALA18 en los JCL porque hace referencia a el nombre de usuario que tengas en el MAINFRAME.
   
3. **Salida del Programa:**  
   Ya que en mainframe trabajas directamente en consola el resultado de la ejecución del programa se podra resivar en el spool.
   La salida que obtuve la podras ver en la imagen Resultado.  

## Enfoque y solución:

   Los 3 requerimientos del reporte tienen en común que necesitaras recorrer todos los datos del archivo para resolverlos.
   Basandome en esa premisa entonces hago una lectura secuencial del archivo CSV o PS, por cada linea de datos exceptuando la primera, se separa los datos y se formatean para poder usarlos luego para el balance final evaluo el tipo de transacción para sumar o 
   restar y además agrego 1 al contador de credito o debito. Luego comparo para saber si el monto de la transacción es más alto que el anterior. Al final de la lectura del archivos CSV o PS hago el display del reporte para poder ver los resultados.

## Estructura del proyecto:

   IEFBR14: Contiene el JCL para crear el PS usando la utilidad IEFBR14.
   JCLPROCT: Contiene el JCL para la compilacion del MEMBER fuente Cobol y la ejecución del programa Cobol compilado.
   PROCTRAN: Contiene el codigo fuente del programa cobol.
   Resultado: Imagen que contiene el reporte osea el resultado de la ejecución.
