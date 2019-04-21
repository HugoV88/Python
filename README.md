# Documentación Python 

&nbsp;
## 1. Detalles de bucle For
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
## 2. Las Tuplas
Son unas colecciones parecidas a las listas, con la peculiaridad de que son inmutables.
~~~
tupla = (100,"Hola",[1,2,3,4],-50)
tupla
~~~
~~~
>
(100, 'Hola', [1, 2, 3, 4], -50)
~~~
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
