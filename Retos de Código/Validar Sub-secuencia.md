El reto consiste en escribir una función que tome como entrada dos arrays (arreglos) no vacíos de números enteros, y determine si el segundo array es una subsecuencia del primero.

Una subsecuencia de un array es un conjunto de números que no necesariamente son adyacentes en el array, pero que están en el mismo orden en que aparecen en el array. 

Por ejemplo, los números [1, 3, 4] forman una subsecuencia del array [1, 2, 3, 4], y también lo hacen los números [2, 4]. Es importante notar que un único número en un array, así como el array completo, son ambos subsecuencias válidas del array.

Por lo tanto, la función debe devolver un valor booleano que indique si el segundo array es una subsecuencia del primero en el mismo orden.


## Explicación

Imagínate que tienes dos listas de números. Queremos saber si la segunda lista es una parte de la primera lista, pero los números pueden estar en diferente orden. 

Por ejemplo, si la primera lista es [1, 2, 3, 4] y la segunda es [2, 4], entonces la segunda lista es una parte de la primera lista porque los números `2` y `4` están en la primera lista en el mismo orden. Pero si la segunda lista fuera [4, 2] entonces no sería una parte de la primera lista porque los números no están en el mismo orden. 

Entonces, tenemos que hacer una función que compare las dos listas y nos diga si la segunda lista es una parte de la primera lista.

## Paso a paso

1. Crea una función que tome como entrada dos arrays no vacíos: el primero que es el array completo y el segundo que es la subsecuencia que queremos buscar.
2. Crea dos variables, una que represente la posición actual en el primer array y otra que represente la posición actual en el segundo array. Inicializa ambas en cero.
3. Inicia un bucle que recorra el primer array mientras la posición actual en el segundo array sea menor que la longitud del segundo array.
4. Dentro del bucle, verifica si el valor actual en el primer array es igual al valor actual en el segundo array. Si es así, incrementa la posición actual en el segundo array.
5. Incrementa la posición actual en el primer array en cada iteración del bucle.
6. Después de salir del bucle, verifica si la posición actual en el segundo array es igual a la longitud del segundo array. Si es así, entonces el segundo array es una subsecuencia del primer array. De lo contrario, no lo es.
7. Devuelve un valor booleano que indique si el segundo array es una subsecuencia del primero en el mismo orden.

## Pseudo-codigo

```c
Función esSubsecuencia(arrayCompleto, subsecuencia)
  posArrayCompleto = 0
  posSubsecuencia = 0
  
  mientras posArrayCompleto < longitud(arrayCompleto) y posSubsecuencia < longitud(subsecuencia) hacer
    si arrayCompleto[posArrayCompleto] es igual a subsecuencia[posSubsecuencia] entonces
      posSubsecuencia = posSubsecuencia + 1
    fin si
    
    posArrayCompleto = posArrayCompleto + 1
  fin mientras
  
  si posSubsecuencia es igual a longitud(subsecuencia) entonces
    devolver verdadero
  sino
    devolver falso
  fin si
Fin Función

```

## Implementación

### Javascript

```js
function isSubsequence(mainArray, subArray) {
  let mainIndex = 0;
  let subIndex = 0;
  
  while (mainIndex < mainArray.length && subIndex < subArray.length) {
    if (mainArray[mainIndex] === subArray[subIndex]) {
      subIndex++;
    }
    
    mainIndex++;
  }
  
  return subIndex === subArray.length;
}

// Para llamar a esta función, simplemente debes pasarle dos arrays como argumentos:

const mainArray = [1, 2, 3, 4];
const subArray = [2, 4];
const isSub = isSubsequence(mainArray, subArray); // true

```

### Python

```python
def is_subsequence(main_list, sub_list):
    main_index = 0
    sub_index = 0
    
    while main_index < len(main_list) and sub_index < len(sub_list):
        if main_list[main_index] == sub_list[sub_index]:
            sub_index += 1
        
        main_index += 1
    
    return sub_index == len(sub_list)


# Puedes llamar a esta función con dos arrays como argumentos para verificar si el segundo array es una subsecuencia del primero en el mismo orden.

main_list = [1, 2, 3, 4]
sub_list = [2, 4]
is_sub = is_subsequence(main_list, sub_list) # True

```