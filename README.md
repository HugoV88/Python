# Documentación Python 

&nbsp;
## 1. Fundamentos de Programación
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
