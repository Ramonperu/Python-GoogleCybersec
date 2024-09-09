# Python in Cybersec

Bienvenidos a la guía básica de Python realizada gracias al [curso](https://www.coursera.org/learn/automate-cybersecurity-tasks-with-python) de Google de ciberseguridad.

## **Introducción a Python**

Python es un lenguaje de programación de alto nivel, interpretado y de propósito general, conocido por su simplicidad y legibilidad. Esto lo convierte en una excelente opción tanto para principiantes como para desarrolladores experimentados. Su sintaxis clara y estructurada permite escribir código de manera rápida y eficiente.

### ¿Por qué se usa Python en ciberseguridad?

**Facilidad de uso y aprendizaje**:

- Permite escribir scripts rápidamente para automatizar tareas o explotar vulnerabilidades.
- Su sintaxis es simple, lo que facilita concentrarse en resolver problemas de seguridad.

**Amplia disponibilidad de bibliotecas**:

- Herramientas como **Scapy**, **Nmap** o **PyCrypto** permiten realizar análisis de redes, criptografía y escaneo de vulnerabilidades.

**Automatización de tareas**:

- Python simplifica la creación de scripts para automatizar procesos repetitivos como monitoreo de redes o análisis de logs.

**Desarrollo rápido de prototipos**:

- Python facilita el desarrollo y prueba de herramientas y scripts en poco tiempo.

**Compatibilidad multiplataforma**:

- Funciona en sistemas operativos como Windows, Linux y macOS, lo que lo hace versátil en entornos variados.

## Asignación de variables

En Python, las variables se utilizan para almacenar datos, y no requieren una declaración explícita de su tipo, ya que Python lo asigna automáticamente según el valor que le des. En ciberseguridad, las variables nos permiten guardar y manipular información clave como direcciones IP, credenciales, tiempos de respuesta, entre otros. Mas adelante se verán ejemplos de como declarar distintos tipos de datos como variables

#### Sintaxis básica:

Para asignar una variable, simplemente se utiliza el nombre de la variable seguido de un signo igual (`=`) y el valor que se desea almacenar.

```python
variable = valor
```

#### Reasignación de variables:

Las variables en Python pueden ser reasignadas con un nuevo valor en cualquier momento. En ciberseguridad, esto es útil cuando los datos cambian dinámicamente, como al actualizar un contador de intentos fallidos de autenticación.

```python
intentos_fallidos = 3
intentos_fallidos = 4  # Actualiza la variable después de otro intento fallido
```

#### Reglas en los nombres de variables:

Es importante seguir buenas prácticas al nombrar variables para que el código sea fácil de entender. Se recomienda usar nombres descriptivos, con palabras separadas por guiones bajos, por ejemplo: `nombre_usuario`, `intentos_fallidos`.

- No pueden comenzar con números.
- No deben incluir espacios ni caracteres especiales (excepto guiones bajos)

## Tipos de datos

En los ejemplos podemos ver como se asignan distintos valores de distintos tipos de datos a las variables

#### **Enteros (`int`)**:

Los enteros representan números sin decimales. Para contar intentos de acceso o manejar números de puertos, entre otros.

```python
intentos_acceso = 5  # Número de intentos fallidos de inicio de sesión
puerto = 443  # Puerto HTTPS
```

####  **Flotantes (`float`)**:

Los flotantes son números con decimales. Cuando necesitamos manejar valores más precisos, como tiempos de respuesta en análisis de redes.

```python
tiempo_respuesta = 0.347  # Tiempo de respuesta de un servidor en segundos
```

#### **Cadenas de texto (`str`)**:

Las cadenas almacenan texto. Son esenciales para manejar direcciones IP, nombres de usuario, contraseñas, logs, etc.

```python
direccion_ip = "192.168.1.1"  # Dirección IP de un cliente
usuario = "admin"  # Nombre de usuario detectado
```

#### **Booleanos (`bool`)**:

Los booleanos almacenan valores `True` o `False`, útiles para verificar condiciones, como si una conexión es segura o si un escaneo ha detectado vulnerabilidades.

```python
conexion_segura = True  # Indica si una conexión está cifrada
vulnerabilidad_detectada = False  # Indica si se ha encontrado una vulnerabilidad
```

#### **Listas (`list`)**:

Las listas son colecciones ordenadas de elementos. Se utilizan para almacenar múltiples valores como direcciones IP en un escaneo de red o múltiples hashes para comparar.

```python
ips_detectadas = ["192.168.1.1", "10.0.0.5", "172.16.0.3"]  # Lista de direcciones IP escaneadas
hashes = ["5d41402abc4b2a76b9719d911017c592", "e99a18c428cb38d5f260853678922e03"]  # Hashes de archivos
```

#### **Diccionarios (`dict`)**:

Los diccionarios almacenan pares clave-valor. Son útiles para asociar direcciones IP con puertos o almacenar información detallada de ataques.

```python
escaneo_puertos = {"192.168.1.1": [80, 443], "10.0.0.5": [22, 8080]}  # Puertos abiertos por IP
```

#### **Tuplas (`tuple`)**:

Las tuplas son similares a las listas, pero sus elementos son inmutables (no se pueden modificar). Se usan cuando queremos asegurarnos de que ciertos valores no cambien, como coordenadas de un sistema o configuraciones iniciales.

```python
configuracion_inicial = ("admin", "12345", "192.168.1.1")  # Configuración inicial de usuario, pass e Ip
```

## Trabajando con strings y listas

En Python, tanto las **strings** como las **listas** son tipos de datos secuenciales, lo que significa que almacenan colecciones de elementos ordenados. Aunque comparten algunas similitudes, también tienen diferencias clave en cómo se manipulan y las operaciones que se pueden realizar con ellas.

### **Strings en Python**

Las **strings** (cadenas de texto) en Python son **inmutables**, lo que significa que una vez que se crean, no pueden ser modificadas directamente. Puedes acceder a sus caracteres mediante **índices** y manipularlas con operaciones que crean nuevas cadenas.

#### Reglas y Operaciones con Strings:

- ***Inmutabilidad**: No se pueden modificar las cadenas existentes, pero se pueden crear nuevas combinando o manipulando cadenas existentes.*

- Concatenación: Se pueden unir dos o más cadenas usando el operador `+`.

  ```python
  cadena1 = "ciber"
  cadena2 = "seguridad"
  nueva_cadena = cadena1 + cadena2  # Resultado: "ciberseguridad"
  ```

- Repetición: Se puede repetir una cadena usando el operador `*`

  ```python
  cadena = "Hola" * 3  # Resultado: "HolaHolaHola"
  ```

- Longitud: Para obtener la longitud de una cadena, se usa la función `len()`

  ```python
  cadena = "ciberseguridad"
  print(len(cadena))  # Resultado: 14
  ```

#### Accediendo a Caracteres e Índices:

- **Índices**: Los índices en una cadena comienzan en `0` y permiten acceder a caracteres individuales.

  ```python
  cadena = "ciberseguridad"
  print(cadena[0])  # Resultado: "c"
  print(cadena[-1])  # Resultado: "d" (último carácter)
  ```

- **Slices **: Usando la notación `cadena[inicio:fin]`, puedes extraer una subcadena. El índice **`inicio` es inclusivo** y el **índice `fin` es exclusivo**.

  ```python
  cadena = "ciberseguridad"
  subcadena = cadena[0:5]  # Resultado: "ciber"
  ```

  - Omitir inicio: Si no especificas el inicio, se toma desde el principio.

    ```python
    subcadena = cadena[:5]  # Resultado: "ciber"
    ```

  - Omitir fin: Si no especificas el fin, se toma hasta el final.

    ```python
    subcadena = cadena[5:]  # Resultado: "seguridad"
    ```

  - Índices negativos: Puedes usar índices negativos para contar desde el final.

    ```python
    subcadena = cadena[-9:]  # Resultado: "seguridad"
    ```

#### Métodos útiles para Strings:

Mas adelante explicamos lo que son los métodos en otro apartado.

- `upper()` y `lower()`: Convertir una cadena a mayúsculas o minúsculas.

  ```python
  cadena = "ciberseguridad"
  print(cadena.upper())  # Resultado: "CIBERSEGURIDAD"
  ```

- `strip()`: Elimina los espacios en blanco al principio y al final de la cadena.

  ```python
  cadena = "  ciberseguridad  "
  print(cadena.strip())  # Resultado: "ciberseguridad"
  ```

- `split()`: Divide una cadena en una lista basada en un separador.

  ```python
  cadena = "usuario:contraseña:email"
  partes = cadena.split(":")  # Resultado: ['usuario', 'contraseña', 'email']
  ```



### **Trabajando con Listas en Python**

Las **listas** en Python son **mutables**, lo que significa que puedes modificar sus elementos una vez creadas. Pueden contener diferentes tipos de datos (números, strings, otras listas, etc.) y permiten almacenar colecciones de elementos ordenados.

#### Reglas y Operaciones con Listas:

- ***Mutabilidad**: Las listas se pueden modificar después de su creación, lo que permite agregar, eliminar o cambiar elementos.*

- Concatenación: Se pueden combinar dos listas usando el operador `+`

  ```python
  lista1 = [1, 2, 3]
  lista2 = [4, 5, 6]
  nueva_lista = lista1 + lista2  # Resultado: [1, 2, 3, 4, 5, 6]
  ```

- Repetición: Se puede repetir una lista usando el operador `*`

  ```python
  lista = [1, 2, 3] * 2  # Resultado: [1, 2, 3, 1, 2, 3]
  ```

- Longitud: Para obtener la longitud de una lista, se usa `len()`

  ```python
  lista = [1, 2, 3, 4]
  print(len(lista))  # Resultado: 4
  ```

#### Accediendo a Elementos e Índices:

- **Índices**: Los índices funcionan igual que en las cadenas, comenzando en `0` para el primer elemento.

  ```python
  lista = [10, 20, 30, 40]
  print(lista[0])  # Resultado: 10
  print(lista[-1])  # Resultado: 40 (último elemento)
  ```

- **Slices**: Puedes extraer sublistas de la misma manera que con las cadenas.

  ```python
  lista = [1, 2, 3, 4, 5]
  sublista = lista[1:4]  # Resultado: [2, 3, 4]
  ```

#### Métodos útiles para Listas:

Mas adelante explicamos lo que son los métodos en otro apartado

- **`append()`**: Agrega un elemento al final de la lista.

  ```python
  lista = [1, 2, 3]
  lista.append(4)  # Resultado: [1, 2, 3, 4]
  ```

- **`extend()`**: Agrega múltiples elementos de otra lista al final.

  ```python
  lista = [1, 2, 3]
  lista.extend([4, 5, 6])  # Resultado: [1, 2, 3, 4, 5, 6]
  ```

- **`insert()`**: Inserta un elemento en un índice específico.

  ```python
  lista = [1, 2, 4]
  lista.insert(2, 3)  # Resultado: [1, 2, 3, 4]
  ```

- **`remove()`**: Elimina la primera ocurrencia de un elemento en la lista.

  ```python
  lista = [1, 2, 3, 4]
  lista.remove(3)  # Resultado: [1, 2, 4]
  ```

- **`pop()`**: Elimina y devuelve el último elemento o un elemento en un índice específico.

  ```python
  lista = [1, 2, 3]
  lista.pop()  # Resultado: [1, 2] (Devuelve 3)
  lista.pop(0)  # Resultado: [2] (Devuelve 1)
  ```

- **`sort()` y `sorted()`**: Ordenan la lista en orden ascendente.

  ```python
  lista = [3, 1, 2]
  lista.sort()  # Resultado: [1, 2, 3]
  ```

  Si no quieres modificar la lista original, puedes usar `sorted()`, que devuelve una lista ordenada.

  ```python
  nueva_lista = sorted(lista)  # La lista original sigue igual
  ```

#### Otras Operaciones:

- Comprensión de listas: Es una forma compacta de crear listas basadas en una expresión.

  ```python
  cuadrados = [x**2 for x in range(5)]  # Resultado: [0, 1, 4, 9, 16]
  ```

## Condicionales e Iteraciones en Python

En ciberseguridad, es común necesitar que el código tome decisiones y repita tareas. Los **condicionales** permiten que el programa ejecute ciertas acciones en función de si se cumplen determinadas condiciones, mientras que las **estructuras iterativas** permiten repetir bloques de código varias veces.

### Condicionales en Python (`if`, `elif`, `else`)

Los condicionales permiten que Python **evalúe una condición y ejecute un bloque de código si la condición es verdadera.** En ciberseguridad, esto puede ser útil para tomar decisiones como si una conexión es segura o si un usuario tiene los permisos correctos.

##### Sintaxis básica:

```python
if condicion:
    # Código a ejecutar si la condición es verdadera
elif otra_condicion:
    # Código a ejecutar si la segunda condición es verdadera
else:
    # Código a ejecutar si ninguna condición es verdadera
```

##### Ejemplos de uso:

1. **Verificación de un intento de acceso**:

   ```python
   intentos_fallidos = 3
   
   if intentos_fallidos > 5:
       print("Bloquear usuario: demasiados intentos fallidos")
   elif intentos_fallidos > 0:
       print("Advertencia: intentos fallidos detectados")
   else:
       print("Acceso correcto")
   ```

2. **Validación de una conexión segura**:

   ```python
   conexion_segura = True
   
   if conexion_segura:
       print("Conexión cifrada: continuar")
   else:
       print("Conexión insegura: finalizar")
   ```

### Estructuras Iterativas

Las iteraciones permiten repetir un bloque de código varias veces, lo que es esencial en ciberseguridad cuando se trabaja con grandes volúmenes de datos, como escaneos de puertos, análisis de logs, o múltiples intentos de explotación.

#### Bucle `for`

El bucle `for` se utiliza para iterar sobre secuencias, como listas, tuplas o diccionarios. En ciberseguridad, puede ser útil para recorrer listas de direcciones IP, puertos o registros de actividad.

##### Sintaxis básica:

```python
for variable in secuencia:
    # Código a ejecutar en cada iteración
```

1. **Escaneo de puertos**:

   ```python
   puertos_abiertos = [22, 80, 443]
   
   for puerto in puertos_abiertos:
       print(f"Escaneando puerto {puerto}...")
   ```

2. **Revisión de intentos de acceso fallidos**:

   ```python
   intentos_fallidos = ["admin", "root", "guest"]
   
   for usuario in intentos_fallidos:
       print(f"Intento fallido con el usuario: {usuario}")
   ```

#### Bucle `while`

El bucle `while` ejecuta un bloque de código mientras una condición sea verdadera. Es útil cuando no se sabe de antemano cuántas veces se necesita repetir una operación, como en un proceso de monitoreo continuo de redes.

##### Sintaxis básica:

```python
while condicion:
    # Código a ejecutar mientras la condición sea verdadera
while not condicion:
    # Código a ejecutar mientras la condición sea falsa
```

1. **Monitoreo continuo de intentos fallidos**:

   ```python
   intentos_fallidos = 0
   
   while intentos_fallidos < 5:
       print(f"Intentos fallidos: {intentos_fallidos}")
       intentos_fallidos += 1
   ```

2. **Esperar hasta que se detecte una conexión segura**:

   ```python
   conexion_segura = False
   
   while not conexion_segura:
       print("Esperando conexión segura...")
       # Simulación de establecer conexión segura
       conexion_segura = True  # Aquí se simula el establecimiento de la conexión
   print("Conexión segura establecida")
   ```

## Funciones en Python

Las **funciones** son bloques de código reutilizables diseñados para realizar una tarea específica.

### Definir y Llamar Funciones

#### Sintaxis básica para definir una función:

```python
def nombre_funcion(parametros):
    # Bloque de código
    return valor  # (opcional)
```

**`def`**: palabra clave para definir la función.

**`nombre_funcion`**: nombre que damos a la función.

**`parametros`**: opcional, valores que la función puede recibir para operar.

**`return`**: opcional, valor que la función puede devolver tras su ejecución.

##### Ejemplo:

```python
def verificar_ip(ip):
    if ip == "192.168.1.1":
        return "IP conocida"
    else:
        return "IP desconocida"
```

#### Llamar una función:

Para ejecutar una función, solo necesitas llamarla por su nombre y pasarle los argumentos necesarios.

```python
resultado = verificar_ip("192.168.1.1")
print(resultado)  # Imprime: IP conocida
```

### Uso de Argumentos y parámetros.

Las funciones pueden recibir **parámetros** para que trabajen con datos externos, y pueden devolver un valor con **`return`**.

#### Parámetros

Los parámetros son los valores que la función recibe cuando es llamada. Pueden ser cualquier tipo de dato: enteros, cadenas, listas, etc. 

##### Ejemplo:

```python
def escanear_puertos(ip, puertos):
    for puerto in puertos:
        print(f"Escaneando {puerto} en {ip}")
```

Aquí, la función **`escanear_puertos`** recibe una dirección IP y una lista de puertos, luego imprime cada puerto escaneado.

##### Llamada de la función:

```python
escanear_puertos("192.168.1.1", [80, 443, 22])
```

Esto imprimirá:

```python
Escaneando 80 en 192.168.1.1
Escaneando 443 en 192.168.1.1
Escaneando 22 en 192.168.1.1
```

### Funciones ya construidas en Python

Python tiene muchas funciones predefinidas que son útiles para tareas comunes. Estas funciones permiten operar directamente sin tener que reinventar la rueda.

Algunas funciones útiles en ciberseguridad:

- **`len()`**: Para obtener la longitud de una lista o cadena (por ejemplo, contar intentos fallidos).

  ```python
  intentos = ["admin", "root", "guest"]
  print(len(intentos))  # Imprime: 3
  ```

- **`input()`**: Para recibir datos del usuario.

  ```python
  usuario = input("Ingrese su nombre de usuario: ")
  ```

- **`int()`**, **`str()`**, **`float()`**: Para convertir entre tipos de datos.

  ```python
  puerto = "443"
  puerto_entero = int(puerto)  # Convierte la cadena en entero
  ```

- **`sorted()`**

  ```
  puertos = [443, 80, 22, 8080] print(sorted(puertos))  # Imprime: [22, 80, 443, 8080]
  ```

- **`max()` y `min()`**

  ```python
  puertos = [22, 80, 443, 8080]
  print(max(puertos))  # Imprime: 8080
  print(min(puertos))  # Imprime: 22
  ```

## Módulos y Librerías

Python tiene una gran cantidad de **módulos** y **librerías** que proporcionan funcionalidades adicionales. Los módulos son archivos que contienen funciones y variables que puedes importar y usar en tu programa, lo que es particularmente útil en ciberseguridad, donde hay herramientas especializadas como Scapy o Nmap.

### Importar Módulos

Para usar un módulo, simplemente lo importas usando la palabra clave **`import`**. Algunos módulos ya vienen incluidos en Python, mientras que otros deben instalarse.

##### Ejemplo de módulo:

- **`math`**: Para realizar operaciones matemáticas avanzadas.

  ```python
  import math
  print(math.sqrt(16))  # Imprime: 4.0
  ```

- **`os`**: Para interactuar con el sistema operativo, útil en ciberseguridad para operaciones relacionadas con el sistema de archivos.

  ```python
  import os
  directorio_actual = os.getcwd()  # Obtiene el directorio actual
  print(directorio_actual)
  ```

### Librerías Especializadas en Ciberseguridad

1. **Scapy**: Herramienta poderosa para manipulación de paquetes de red.

   ```python
   from scapy.all import *
   paquete = IP(dst="192.168.1.1")/ICMP()
   send(paquete)
   ```

2. **Nmap**: Permite realizar escaneos de puertos y redes.

   ```python
   import nmap
   escaner = nmap.PortScanner()
   escaner.scan('192.168.1.1', '22-443')
   print(escaner.all_hosts())
   ```

3. **Pyshark**: Es un wrapper para **Wireshark** que permite capturar y analizar paquetes de red. Es útil para el análisis forense de red y la detección de intrusiones.

   ```python
   import pyshark
   
   captura = pyshark.LiveCapture(interface='eth0')
   for paquete in captura.sniff_continuously(packet_count=5):
       print(paquete)
   ```

Y podríamos continuar mencionando librerías especializadas en ciberseguridad como **`request`**, **`haslib`**, **`paramiko`**...etc

## Debugging

Tipos de errores y como solucionarlos

### **Errores de Sintaxis**

Ocurren cuando el código no sigue las reglas del lenguaje de programación, impidiendo que el programa se ejecute. Son detectados por el intérprete de Python cuando se analiza el código.

#### Ejemplo:

```python
if True
    print("Error de sintaxis")
```

En este caso, falta el **`:`** al final de la condición del `if`, lo que generará un **`SyntaxError`**.

```Python
SyntaxError: invalid syntax
```

#### Cómo solucionarlos:

- Revisar cuidadosamente el código en la línea indicada.
- Verificar que todas las estructuras de control (if, loops) estén bien escritas.
- Asegurarse de que se utilicen correctamente los paréntesis, comillas y signos de puntuación.

### **Errores en Tiempo de Ejecución (Exceptions)**

Ocurren mientras el programa está en ejecución. A diferencia de los errores de sintaxis, el código puede ejecutarse parcialmente antes de que se produzca el error. Son lanzados como **excepciones** y pueden manejarse mediante bloques `try-except`.



#### Tipos Comunes:

- **`NameError`**: Se produce cuando se intenta usar una variable que no ha sido definida.

  ```python
  print(variable_no_definida)
  ```

  **Solución**: Asegurarse de que todas las variables estén definidas antes de ser usadas.

- **`TypeError`**: Ocurre cuando se intenta operar con tipos de datos incompatibles.

  ```python
  numero = 5
  cadena = "hola"
  print(numero + cadena)  # Error: No se puede sumar un número a una cadena
  ```
  
  **Solución**: Convertir uno de los tipos para que la operación tenga sentido.

  ```python
  print(str(numero) + cadena)  # Conversión del número a string
  ```
  
- **`IndexError`**: Se produce cuando se intenta acceder a un índice que está fuera del rango de una lista o cadena.

  ```python
  lista = [1, 2, 3]
  print(lista[5])  # Error: no hay índice 5 en la lista
  ```

  **Solución**: Comprobar la longitud de la lista antes de acceder al índice.

- **`KeyError`**: Ocurre cuando intentas acceder a una clave inexistente en un diccionario.

  ```python
  diccionario = {"clave1": "valor1"}
  print(diccionario["clave_no_existente"])
  ```
  
  **Solución**: Usar el método `get()` para evitar el error, o verificar la existencia de la clave.

  ```python
  print(diccionario.get("clave_no_existente", "Clave no encontrada"))
  ```
  
- **`ZeroDivisionError`**: Ocurre cuando se intenta dividir un número entre cero.

  ```python
  resultado = 10 / 0
  ```
  
  **Solución**: Verificar que el divisor no sea cero antes de realizar la operación.
  
  ```python
  divisor = 0
  if divisor != 0:
      resultado = 10 / divisor
  else:
      print("No se puede dividir entre cero")
  ```

### **Errores Lógicos**

Ocurren cuando el código se ejecuta correctamente, pero no produce el resultado esperado. Estos errores no generan mensajes de error, lo que hace que sean más difíciles de detectar.

Imagina que quieres verificar si un número es par, pero tu lógica es incorrecta:

```python
numero = 5
if numero % 2 == 1:
    print("El número es par")
```

El programa imprimirá que el número es par cuando no lo es.

#### Cómo identificarlos:

- **Revisar la lógica del programa.**
- Usar **declaraciones `print()`** para verificar el valor de las variables en diferentes puntos del programa.
