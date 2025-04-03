## 1
### - ¿Qué es la entrada-salida mapeada a memoria?

En la plataforma Hack, la entrada-salida mapeada a memoria es un método en el que los dispositivos de entrada y salida se controlan a través de la memoria del sistema lo que crea es que se pueda leer una informacion como el teclado y pasarlo a un codigo usando solo la memoria del sistema.


### - ¿Cómo se implementa en la plataforma Hack?

Se implementa en que en la entrada mapeada es quien escribe los datos en la region de la memoria y los de salida mapeada se limita a leerlos y mostrarlos en la menra que se deba mostrar
Y en Hack la entrada es el teclado y al presionar alguna tecla, en la RAM se muestra el valor que equivale a la tecla presionada y el dispositivo de salida es el display, donde de manera lineal se representa la información que escribe el programa en la region de memoria especifica.


### - Inventa un programa que haga uso de la entrada-salida mapeada a memoria.

``` 
(LOOP) @KBD
D=M
@CLEAN
D;JEQ

@SCREEN
M=A

@LOOP 
0;JMP
(CLEAN) @0
D=A
@SCREEN
M=D
@LOOP
0;JMP
 
```
## 3.
### - Vas a implementar y simular una modificación al reto 20 de la unidad anterior. Si se presiona la letra “d” muestras la imagen que diseñaste en el reto 18. Si no se presiona ninguna tecla, borrarás la imagen.

```
(LOOP) @KBD
D=M
@100
D=D-A
@CLEAN
D;JNE

@8184 
D=A 
@16384 
M=D 
@28686 
D=A 
@16416 
M=D 
@16381 
D=-A 
@16448 
M=D 
@32767 
D=-A 
@16480 
M=D 
@17347 
D=-A 
@16512 
M=D 
@19403 
D=-A 
@16544 
M=D 
@19403 
D=-A 
@16576 
M=D 
@17347 
D=-A 
@16608 
M=D 
@26599 
D=-A 
@16640 
M=D 
@32767 
D=-A 
@16672 
M=D 
@32767 
D=-A 
@16704 
M=D 
@15421 
D=-A 
@16736 
M=D 
@28686 
D=A 
@16768 
M=D 
@6168 
D=A 
@16800 
M=D 
@4080 
D=A 
@16832 
M=D 
@0 
D=A 
@16864 
M=D
@LOOP 
0;JMP

(CLEAN) @0
D=A
@16384 
M=D
@16416 
M=D
@16448 
M=D
@16480 
M=D
@16512 
M=D
@16544 
M=D
@16576 
M=D
@16608 
M=D
@16640 
M=D
@16672 
M=D
@16704 
M=D
@16736 
M=D
@16768 
M=D
@16800 
M=D
@16832 
M=D
@16864 
M=D

@LOOP
0;JMP
```

## 4

```
(LOOP) @KBD
D=M
@100
D=D-A
@DRAW
D;JEQ
@KBD
D=M
@101
D=D-A
@CLEAN
D;JEQ
@LOOP
0;JMP

(DRAW)
@8184 
D=A 
@16384 
M=D 
@28686 
D=A 
@16416 
M=D 
@16381 
D=-A 
@16448 
M=D 
@32767 
D=-A 
@16480 
M=D 
@17347 
D=-A 
@16512 
M=D 
@19403 
D=-A 
@16544 
M=D 
@19403 
D=-A 
@16576 
M=D 
@17347 
D=-A 
@16608 
M=D 
@26599 
D=-A 
@16640 
M=D 
@32767 
D=-A 
@16672 
M=D 
@32767 
D=-A 
@16704 
M=D 
@15421 
D=-A 
@16736 
M=D 
@28686 
D=A 
@16768 
M=D 
@6168 
D=A 
@16800 
M=D 
@4080 
D=A 
@16832 
M=D 
@0 
D=A 
@16864 
M=D
@LOOP 
0;JMP

(CLEAN) @0
D=A
@16384 
M=D
@16416 
M=D
@16448 
M=D
@16480 
M=D
@16512 
M=D
@16544 
M=D
@16576 
M=D
@16608 
M=D
@16640 
M=D
@16672 
M=D
@16704 
M=D
@16736 
M=D
@16768 
M=D
@16800 
M=D
@16832 
M=D
@16864 
M=D

@LOOP
0;JMP
```

# Reto
## 1.
Escribe un programa en lenguaje ensamblador que sume los primeros 100 números naturales.
```
int i = 1;
int sum = 0;
While (i <= 100){
   sum += i;
   i++;
}
```

```
@i
M=1       
@sum
M=0       

(LOOP)
    @i
    D=M     
    @100   
    D=D-A
    @END
    D;JGT 


    @i
    D=M      
    @sum
    M=M+D    

    // i++
    @i
    M=M+1   

    @LOOP
    0;JMP    

(END)
    @END
    0;JMP    
```
### - ¿Cómo están implementadas las variables i y sum?

``i`` y ```sum``` se implementan como direcciones de memoria asignadas automáticamente por el ensamblador.
Se accede a ellas con ``@i`` y ``@sum``, y se manipulan con instrucciones de carga.

### - ¿En qué direcciones de memoria están estas variables?

```i``` se almacena en la direccion 16 de la RAM
```sum``` Se almacena en la dirección 17 de la RAM

### - ¿Cómo está implementado el ciclo while?

El ``While`` se imlpementa para comparar al valor de ``ì``

### - ¿Cómo se implementa la variable i?

``i`` funciona como una posicion enjn la RAM

### - ¿En qué parte de la memoria se almacena la variable i?

Se almacena en la Dirección 16 de la RAM

### - Después de todo lo que has hecho, ¿Qué es entonces una variable?

Es algo simbolico que representa una direccion en la memoria 

### - ¿Qué es la dirección de una variable?

Es la ubciacion en donde se almacena un dato

### - ¿Qué es el contenido de una variable?

El valor almecenado en la dirección

## 2
Transforma el programa en alto nivel anterior para que utilice un ciclo ``for`` en vez de un ciclo ``while``.

```
int sum = 0;
for (int i = 1; i <= 100; i++) {
    sum += i;
}
```

## 3

```
@sum
M=0       
@i
M=1     

(LOOP)
    @i
    D=M      
    @100
    D=D-A
    @END
    D;JGT

    @i
    D=M     
    @sum
    M=D+M  

    @i
    M=M+1   

    @LOOP
    0;JMP   

(END)
    @END
    0;JMP    
```

## 4
### -Ahora vamos a acercarnos al concepto de puntero. Un puntero es una variable que almacena la dirección de memoria de otra variable. Observa el siguiente programa escrito en C++:

``` 
int a = 10;
int *p;
p = &a;
*p = 20;
```

#### -¿Cómo se declara un puntero en C++? int *p;. p es una variable que almacenará la dirección de un variable que almacena enteros.

- Colocandole un * al inicio del nombre de la variable 


#### - ¿Cómo se define un puntero en C++? p = &a;. Definir el puntero es inicializar el valor del puntero, es decir, guardar la dirección de una variable. En este caso p contendrá la dirección de a.

- Un puntero de define como cualquier otra variable, se le asigna un valor en especifico, pero en este caso el valor va a indicar una direccion especifica en memoria 

#### - ¿Cómo se almacena en C++ la dirección de memoria de una variable? Con el operador &. p = &a;

-  Se almacena por medio del operador & seguido de la variable 

#### -¿Cómo se escribe el contenido de la variable a la que apunta un puntero? Con el operador . p = 20;. En este caso como p contiene la dirección de a entonces p a la izquierda del igual indica que quieres actualizar el valor de la variable a.

- Con el operador * a esto se le llama derreferenciar 

## 5 Traduce este programa a lenguaje ensamblador:
```
int a = 10;
int *p;
p = &a;
*p = 20;
```


```
@10      // Cargar el valor 10
D=A      // Guardar el valor 10 en el registro D
@a       // Dirección de la variable 'a'
M=D      // Guardar el valor de D (10) en la dirección de 'a'

// Declaración e inicialización del puntero 'p'
@a       // Cargar la dirección de la variable 'a'
D=A      // Guardar la dirección de 'a' en el registro D
@p       // Dirección de la variable 'p'
M=D      // Guardar la dirección de 'a' en 'p'

// Actualizar el valor de 'a' a través del puntero 'p'
@p       // Cargar la dirección de 'p'
D=M      // Obtener la dirección almacenada en 'p' (la dirección de 'a')
@20      // Cargar el valor 20
M=D      // Usar la dirección de 'a' para actualizar el valor a 20

// Fin del programa
(END)   // Etiqueta de fin del programa
@END    // Etiqueta para el final del programa
0;JMP   // Salto incondicional para finalizar la ejecución
```

## 6 Ahora vas a usar un puntero para leer la posición de memoria a la que este apunta, es decir, vas a leer por medio del puntero la variable cuya dirección está almacenada en él.

```
int a = 10;
int b = 5;
int *p;
p = &a;
b = *p;
```

- En este caso, la instrucción b = *p; provoca que el valor de b pase de 5 a 10, ya que p contiene la dirección de la variable a, y al usar *p estás accediendo al valor almacenado en esa dirección, es decir, el contenido de a.

## 7 Traduce este programa a lenguaje ensamblador:
```
int a = 10;
int b = 5;
int *p;
p = &a;
b = *p;
```

```
// int a = 10;
@a
M=10        // Guarda el valor 10 en la variable 'a'

// int b = 5;
@b
M=5         // Guarda el valor 5 en la variable 'b'

// int *p; p = &a;
@a
D=A         // D = dirección de 'a'
@p
M=D         // Guarda la dirección de 'a' en 'p'

// b = *p;
@p
A=M         // A = dirección almacenada en 'p' (es decir, 'a')
D=M         // D = valor contenido en 'a'
@b
M=D         // b = valor apuntado por 'p' (que es 10)

```

## 8 Vas a parar un momento y tratarás de recodar de memoria lo siguiente. Luego verifica con un compañero o con el profesor
- ¿Qué hace esto `int *pvar;`?

 Declara un puntero

- ¿Qué hace esto `pvar = var;`?

 Le asigna a `pvar` el valor de `var`

- ¿Qué hace esto `var2 = *pvar`?

 Le asigna a `var2`el valor de la variable a la que está apuntando `pvar`

- ¿Qué hace esto `pvar = &var3`?

 Le asigna direccion de `var3` a `pvar`

## 9 Considera que el punto de entrada del siguiente programa es la función main, es decir, el programa inicia llamando la función main. Vas a proponer una posible traducción a lenguaje ensamblador de la función suma, cómo llamar a suma y cómo regresar a std::cout << "El valor de c es: " << c << std::endl; una vez suma termine.

```
#include <iostream>

int suma(int a, int b) {
   int var = a + b;
   return var;
}


int main() {
   int c = suma(6, 9);
   std::cout << "El valor de c es: " << c << std::endl;
   return 0;
}
```


```
// La funcion suma se llama por medio de las siguientes instrucciones
@SUMA
0;JMP

// La funcion suma se define asi
(SUMA)
// R1 almacena el primer termino (la variable a)
@R1
D=M
// R2 almacena el segundo termino (la variable b)
@R2
// a + b
D=D+M
// R0 sera donde se espera el resultado cuando se llama a la funcion suma
@R0
M=D
// R3 tendra la direccion de la siguiente instruccion a ejecutar
@R3
0;JMP
```
