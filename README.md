# Documentación Python 

&nbsp;
# 1. Detalles de bucle For
&nbsp;
### Recorriendo los elementos de una lista utilizando While
~~~
numeros = [1,2,3,4,5,6,7,8,9,10]
indice = 0
while indice < len(numeros):
    print(numeros[indice])
    indice+=1
~~~
~~~
> 
1
2
3
4
5
6
7
8
9
10
~~~
&nbsp;
### Sentencia For (Para) con listas
~~~
numeros = [1,2,3,4,5,6,7,8,9,10]
for numero in numeros:  # Para [variable] en [lista]
    print(numero)
~~~
~~~
> 
1
2
3
4
5
6
7
8
9
10
~~~
&nbsp;
### Modificar ítems de la lista al vuelo
Para asignar un nuevo valor a los elementos de una lista mientras la recorremos, podríamos intentar asignar al número el nuevo valor:
~~~
numeros = [1,2,3,4,5,6,7,8,9,10]
for numero in numeros:
    numero *= 10
numeros
~~~~
~~~~
> 
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
~~~~
Sin embargo, ésto no funciona. La forma correcta de hacerlo es haciendo referencia al índice de la lista en lugar de la variable:
~~~
indice = 0
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
for numero in numeros:
    numeros[indice] *= 10
    indice+=1
numeros
~~~
~~~
> 
[10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
~~~
Podemos utilizar la función enumerate() para conseguir el índice y el valor en cada iteración fácilmente:
~~~
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
for indice,numero in enumerate(numeros):
    numeros[indice] *= 10
numeros
~~~
~~~
> 
[10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
~~~
&nbsp;
### For con cadenas
~~~
cadena = "Hola amigos"
for caracter in cadena:
    print(caracter)
~~~
~~~
> 
H
o
l
a
 
a
m
i 
g
o
s
~~~
Pero debemos recordar que las cadenas son inmutables:
~~~
cadena = "Hola amigos"
for i,c in enumerate(cadena):
    cadena[i] = "*"
~~~
~~~
> 
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-9-8ba888c46579> in <module>()
      1 for i,c in enumerate(cadena):
----> 2     cadena[i] = "*"

TypeError: 'str' object does not support item assignment
~~~
Sin embargo siempre podemos generar una nueva cadena:
~~~
cadena = "Hola amigos"
cadena2 = ""
for caracter in cadena:
    cadena2 += caracter * 2
cadena
~~~
~~~
> 
'Hola amigos'
~~~
~~~
cadena2
~~~
~~~
> 
'HHoollaa  aammiiggooss'
~~~
&nbsp;
# 2. Las Tuplas
&nbsp;

Son unas colecciones parecidas a las listas, con la peculiaridad de que son inmutables.
~~~
tupla = (100,"Hola",[1,2,3,4],-50)
tupla
~~~
~~~
>
(100, 'Hola', [1, 2, 3, 4], -50)
~~~
&nbsp;
### Indexación y slicing
~~~
tupla = (100,"Hola",[1, 2, 3, 4],-50)
tupla[0]
~~~
~~~
>
100
~~~
~~~
tupla[-1]
~~~
~~~
>
-50
~~~
~~~
tupla[2:]
~~~
~~~
>
([1, 2, 3, 4], -50)
~~~
~~~
tupla[2][-1]
~~~
~~~
>
4
~~~
&nbsp;
### Inmutabilidad
~~~
tupla[0] = 50
~~~
~~~
>
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-9-b45433b4cee9> in <module>()
----> 1 tupla[0] = 50

TypeError: 'tuple' object does not support item assignment
~~~
&nbsp;
### Función len()
~~~
len(tupla)
~~~
~~~
>
4
~~~
~~~
len(tupla[2])
~~~
~~~
>
3
~~~
&nbsp;
### Métodos integrados
**index()**

Sirve para buscar un elemento y saber su posición en la tupla. Da error si no se encuentra.
~~~
tupla = (100,"Hola",[1, 2, 3, 4],-50)
tupla.index(100)
~~~
~~~
>
0
~~~
~~~
tupla
~~~
~~~
>
(100, 'Hola', [1, 2, 3], -50)
~~~
~~~
tupla.index('Hola')
~~~
~~~
1
~~~
~~~
tupla.index('Otro')
~~~
~~~
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-18-640d616163a2> in <module>()

----> 1 tupla.index('Otro')

ValueError: tuple.index(x): x not in tuple
~~~
&nbsp;
**count()**

Sirve para contar cuantas veces aparece un elemento en una tupla.
~~~
tupla = (100,"Hola",[1, 2, 3, 4],-50)
tupla.count(100)
~~~
~~~
>
1
~~~
~~~
tupla.count('Algo')
~~~
~~~
>
0
~~~
~~~
tupla = (100,100,100,50,10)
tupla.count(100)
~~~
~~~
>
3
~~~
&nbsp;
**append() ?**

Al ser inmutables, las tuplas no disponen de métodos para modificar su contenido.
~~~
tupla.append(10)
~~~
~~~
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
<ipython-input-23-758d195ec9d7> in <module>()
----> 1 tupla.append(10)

AttributeError: 'tuple' object has no attribute 'append'
~~~
&nbsp;
# 3. Los conjuntos
&nbsp;

Son colecciones desordenadas de elementos únicos utilizados para hacer pruebas de pertenencia a grupos y eliminación de elementos duplicados.
~~~
conjunto = set()
conjunto
~~~
~~~
>
set()
~~~
~~~
conjunto = {1,2,3}
conjunto
~~~
~~~
>
{1, 2, 3}
~~~
&nbsp;
###Método add()
Sirve para añadir elementos al conjunto. Si un elemento ya se encuentra, no se añadirá de nuevo.
~~~
conjunto = {1,2,3}
conjunto.add(4)
conjunto
~~~
~~~
>
{1, 2, 3, 4}
~~~
~~~
conjunto.add(0)
conjunto
~~~
~~~
>
{0, 1, 2, 3, 4}
~~~
&nbsp;
### Colecciones desordenadas
Se dice que son desordenados porque gestionan automáticamente la posición de sus elementos, en lugar de conservarlos en la posición que nosotros los añadimos.
~~~
conjunto.add('H')
conjunto
~~~
~~~
>
{0, 1, 2, 3, 4, 'H'}
~~~
~~~
conjunto.add('A')
conjunto.add('Z')
conjunto
~~~
~~~
>
{0, 1, 2, 3, 4, 'A', 'Z', 'H'}
~~~
&nbsp;
### Pertenencia a grupos con in
~~~
grupo = {'Hector','Juan','Mario'}
'Hector' in grupo
~~~
~~~
>
True
~~~
~~~
'Maria' in grupo
~~~
~~~
>
False
~~~
~~~
'Hector' not in grupo
~~~
~~~
>
False
~~~
&nbsp;
### Auto-eliminación de elementos duplicados
~~~
test = {'Hector','Hector','Hector'}
test
~~~
~~~
>
{'Hector'}
~~~
&nbsp;
### Cast de lista a conjunto y viceversa
Es muy útil transformar listas a conjuntos para borrar los elementos duplicados automáticamente.
~~~
l = [1,2,3,3,2,1]
l
~~~
~~~
>
[1, 2, 3, 3, 2, 1]
~~~
~~~
c = set(l)
c
~~~
~~~
>
{1, 2, 3}
~~~
~~~
l = list(c)
l
~~~
~~~
>
[1, 2, 3]
~~~
~~~
l = [1,2,3,3,2,1]
~~~
&nbsp;
### En una línea
~~~
l = list( set( l ) )
l
~~~
~~~
>
[1, 2, 3]
~~~
&nbsp;
### Cast de cadena a conjunto
Sirve para crear un conjunto con todos los caracteres de la cadena.
~~~
s = "Al pan pan y al vino vino"
set(s)
~~~
~~~
>
{' ', 'A', 'a', 'i', 'l', 'n', 'o', 'p', 'v', 'y'}
~~~
&nbsp;
# 4. Los diccionarios
&nbsp;

Son junto a las listas las colecciones más utilizadas. Se basan en una estructura mapeada donde cada elemento de la colección se encuentra identificado con una clave única. Por tanto, no puede haber dos claves iguales. En otros lenguajes se conocen como arreglos asociativos.
~~~
vacio = {}
vacio
~~~
~~~
>
{}
~~~
&nbsp;
### Tipo de una variable
~~~
type(vacio)
~~~
~~~
>
dict
~~~
&nbsp;
### Definición
Para cada elemento se define la estructura -> clave:valor
~~~
colores = {'amarillo':'yellow','azul':'blue'}
~~~
También se pueden añadir elementos sobre la marcha
~~~
colores['verde'] = 'green'
colores
~~~
~~~
>
{'amarillo': 'yellow', 'azul': 'blue', 'verde': 'green'}
~~~
~~~
colores['azul']
~~~
~~~
>
'blue'
~~~
~~~
colores['amarillo']
~~~
~~~
>
'yellow'
~~~
Las claves también pueden ser números, pero son un poco confusas
~~~
numeros = {10:'diez',20:'veinte'}
numeros[10]
~~~
~~~
>
'diez'
~~~
&nbsp;
### Modificación de valor a partir de la clave
~~~
colores['amarillo'] = 'white'
colores
~~~
~~~
>
{'amarillo': 'white', 'azul': 'blue', 'verde': 'green'}
~~~
&nbsp;
### Función del()
Sirve para borrar un elemento del diccionario.
~~~
del(colores['amarillo'])
colores
~~~
~~~
>
{'azul': 'blue', 'verde': 'green'}
~~~
&nbsp;
### Trabajando directamente con registros
~~~
edades = {'Hector':27,'Juan':45,'Maria':34}
edades
~~~
~~~
>
{'Hector': 27, 'Juan': 45, 'Maria': 34}
~~~
~~~
edades['Hector']+=1
edades
~~~
~~~
>
{'Hector': 28, 'Juan': 45, 'Maria': 34}
~~~
~~~
edades['Juan'] + edades['Maria']
~~~
~~~
>
79
~~~
&nbsp;
### Lectura secuencial con for .. in ..
Es posible utilizar una iteraciín for para recorrer los elementos del diccionario:
~~~
for edad in edades:
    print(edad)
~~~
~~~
>
Maria
Hector
Juan
~~~
El problema es que se devuelven las claves, no los valores
Para solucionarlo deberíamos indicar la clave del diccionario para cada elemento.
~~~
for clave in edades:
    print(edades[clave])
~~~
~~~
>
34
28
45
~~~
~~~
for clave in edades:
    print(clave,edades[clave])
~~~
~~~
Maria 34
Hector 28
Juan 45
~~~
&nbsp;
### El método .items()
Nos facilita la lectura en clave y valor de los elementos porque devuelve ambos valores en cada iteración automáticamente:
~~~
for c,v in edades.items():
    print(c,v)
~~~
~~~
>
Maria 34
Hector 28
Juan 45
~~~
&nbsp;
### Ejemplo utilizando diccionarios y listas a la vez
Podemos crear nuestras propias estructuras avanzadas mezclando ambas colecciones. Mientras los diccionarios se encargarían de manejar las propiedades individuales de los registros, las listas nos permitirían manejarlos todos en conjunto.
~~~
personajes = []
p = {'Nombre':'Gandalf','Clase':'Mago','Raza':'Humano'}  # No sé si era un humano pero lo parecía jeje
personajes.append(p)
personajes
~~~
~~~
>
[{'Clase': 'Mago', 'Nombre': 'Gandalf', 'Raza': 'Humano'}]
~~~
~~~
p = {'Nombre':'Legolas','Clase':'Arquero','Raza':'Elfo'}
personajes.append(p)
p = {'Nombre':'Gimli','Clase':'Guerrero','Raza':'Enano'}
personajes.append(p)
personajes
~~~
~~~
>
[{'Clase': 'Mago', 'Nombre': 'Gandalf', 'Raza': 'Humano'},
 {'Clase': 'Arquero', 'Nombre': 'Legolas', 'Raza': 'Elfo'},
 {'Clase': 'Guerrero', 'Nombre': 'Gimli', 'Raza': 'Enano'}]
~~~
~~~
for p in personajes:
    print(p['Nombre'], p['Clase'], p['Raza'])
~~~
~~~
>
Gandalf Mago Humano
Legolas Arquero Elfo
Gimli Guerrero Enano
~~~
&nbsp;
# Las pilas y colas en listas
&nbsp;

### Las pilas
Son colecciones de elementos ordenados que únicamente permiten dos acciones:
- Añadir un elemento a la pila
- Sacar un elemento de la pila
La peculiaridad es que el último elemento en entrar es el primero en salir. En inglés se conocen como estructuras LIFO (Last In First Out).
**Las podemos crear como listas normales y añadir elementos al final con el append():**
~~~
pila = [3,4,5]
pila.append(6)
pila.append(7)
pila
~~~
~~~
>
[3, 4, 5, 6, 7]
~~~
**Para sacar los elementos utilizaremos el método .pop():**
Al utilizar pop() devolveremos el último elemento, pero también lo borraremos. Si queremos trabajar con él deberíamos asignarlo a una variable o lo perderemos:
~~~
pila.pop()
~~~
~~~
>
7
~~~
~~~
pila
~~~
~~~
>
[3, 4, 5, 6]
~~~
~~~
n = pila.pop()
n
~~~
~~~
>
6
~~~
~~~
pila
~~~
~~~
>
[3, 4, 5]
~~~
~~~
pila.pop()
pila.pop()
pila.pop()
~~~
~~~
>
3
~~~
~~~
pila
~~~
~~~
>
[]
~~~
**Si hacemos pop() de una pila vacía, devolverá un error:**
Debemos asegurarnos siempre de que la len() de la pila sea mayor que 0 antes de extraer un elemento automáticamente.
~~~
pila.pop()
~~~
~~~
>
---------------------------------------------------------------------------
IndexError                                Traceback (most recent call last)
<ipython-input-14-3900970cfbef> in <module>()
----> 1 pila.pop()

IndexError: pop from empty list
~~~
&nbsp;
## Las colas
Son colecciones de elementos ordenados que únicamente permiten dos acciones:
- Añadir un elemento a la cola
- Sacar un elemento de la cola
La peculiaridad es que el primer elemento en entrar es el primero en salir. En inglés se conocen como estructuras FIFO (First In First Out).

**Debemos importar la colección deque manualmente para crear una cola:**
~~~
from collections import deque
cola = deque()
cola
~~~
~~~
>
deque([])
~~~
**Podemos añadir elemento directamente pasando una lista a la cola al crearla:**
~~~
cola = deque(['Hector','Juan','Miguel'])
cola
~~~
~~~
>
deque(['Hector', 'Juan', 'Miguel'])
~~~
**Y también utilizando el método .append():**
~~~
cola.append('Maria')
cola.append('Arnaldo')
cola
~~~
~~~
deque(['Hector', 'Juan', 'Miguel', 'Maria', 'Arnaldo'])
~~~
**popleft() en lugar de pop()**
A la hora de sacar los elementos utilizaremos el método popleft() para extraerlos por la parte izquierda (el principio de la cola). Al igual que antes, debemos asegurarnos de almacenar los elementos al sacarlos o los perderemos.
~~~
cola.popleft()
~~~
~~~
>
'Hector'
~~~
~~~
cola
~~~
~~~
>
deque(['Juan', 'Miguel', 'Maria', 'Arnaldo'])
~~~
~~~
p = cola.popleft()
p
~~~
~~~
>
'Juan'
~~~
~~~
cola
~~~
~~~
>
deque(['Miguel', 'Maria', 'Arnaldo'])
~~~
