# Examen Parcial - alejandroportilla-create

**Usuario GitHub:** alejandroportilla-create
**Fecha:** 4 de noviembre de 2025
**Retos tenidos en cuenta:** Reto 001, Reto 002, Reto 003

---

## Instrucciones

A continuación encontrarás fragmentos de código extraídos de tus entregas. Cada fragmento contiene una o más situaciones relacionadas con los conceptos vistos en clase.

Para cada pregunta debes:
1) Identificar a qué se refiere la observación
2) Explicar si es o no un error y por qué
3) Proponer la corrección

Nota: Responde 5 de las 9 preguntas (en función a lo indicado en el examen).


---

## Pregunta 1

Archivo: `Edificio.java` — [Ver archivo](https://github.com/mmasias/25-26-PRG1/blob/a4a32c7cefe2fbbb8310e3d8b6906a453b3ec346/entregas/PortillaAlejandro/reto-003/Edificio.java) (Reto 003)

```java
final double PERSIANA_ABIERTA = 0.7;
final double LUZ_ENCENCIDA = 0.6;
```

¿Qué observas en este código?

En este código se observa la declaración de dos constantes final de tipo double. El problema está en un error ortográfico en el nombre de la constante LUZ_ENCENCIDA, ya que la palabra correcta es ENCENDIDA.
Aunque el programa funciona igual, este error afecta a la claridad y la buena plegibilidad, porque los identificadores tienen que estar correctamente escritos y describir claramente su propósito.

La corrección del código sería:

final double PERSIANA_ABIERTA = 0.7;
final double LUZ_ENCENDIDA = 0.6;


---

## Pregunta 2

Archivo: `Edificio.java` — [Ver archivo](https://github.com/mmasias/25-26-PRG1/blob/a4a32c7cefe2fbbb8310e3d8b6906a453b3ec346/entregas/PortillaAlejandro/reto-003/Edificio.java) (Reto 003)

```java
for (int hora=0; hora<=24; hora++) {
    // ...
}
```

¿Qué observas en este código?

En este código se observa un bucle for que recorre la variable hora desde 0 hasta 24, utilizando la condición hora <= 24. Esto representa un error lógico, ya que como el objetivo es simular las horas de un día, el rango válido va de 0 a 23, porque en el formato de 24 horas no existe la hora 24. Con la condición actual, el bucle se ejecuta 25 veces en lugar de 24.

La corrección sería cambiar la condición para que el bucle se detenga antes de llegar a 24, utilizando el operador < en lugar de <=. De esta forma, el recorrido será de 0 a 23, cumpliendo correctamente las 24 iteraciones esperadas.

La corrección del código sería:

for (int hora = 0; hora < 24; hora++) {
    // ...
}

---

## Pregunta 3

Archivo: `Edificio.java` — [Ver archivo](https://github.com/mmasias/25-26-PRG1/blob/a4a32c7cefe2fbbb8310e3d8b6906a453b3ec346/entregas/PortillaAlejandro/reto-003/Edificio.java) (Reto 003)

```java
for (int planta=1; planta<=7; planta++) {
    for (int columna=1; columna<=6; columna++) {
        abierta = Math.random() < PERSIANA_ABIERTA;
        encendida = Math.random() < LUZ_ENCENCIDA;
        System.out.println(!abierta ? VENTANA_CERRADA : encendida ? VENTANA_ABIERTA_CON_LUZ : VENTANA_ABIERTA_SIN_LUZ);
        if (columna == 3 ) {
            System.out.print( SEPARADOR );
        }
    }
}
```

¿Qué observas en este código?

En este código se observa un doble bucle que recorre las plantas y columnas de un edificio, generando aleatoriamente si una persiana está abierta y si la luz está encendida. La observación principal está en el uso de operadores ternarios anidados dentro del System.out.println, lo que hace el código difícil de leer y mantener. Además, se mezclan System.out.println y System.out.print, lo que puede provocar que el formato del dibujo del edificio no quede bien alineado.

Aunque el código puede funcionar correctamente, yo creo que es mejor separar las condiciones y usar sentencias if normales para mejorar la claridad.

La corrección del código sería:

for (int planta = 1; planta <= 7; planta++) {
    for (int columna = 1; columna <= 6; columna++) {
        abierta = Math.random() < PERSIANA_ABIERTA;
        encendida = Math.random() < LUZ_ENCENDIDA;

        if (!abierta) {
            System.out.print(VENTANA_CERRADA);
        } else {
            if (encendida) {
                System.out.print(VENTANA_ABIERTA_CON_LUZ);
            } else {
                System.out.print(VENTANA_ABIERTA_SIN_LUZ);
            }
        }

        if (columna == 3) {
            System.out.print(SEPARADOR);
        }
    }
    System.out.println();
}

---

## Pregunta 4

Archivo: `CalcularPrecioFinal.java` — [Ver archivo](https://github.com/mmasias/25-26-PRG1/blob/a4a32c7cefe2fbbb8310e3d8b6906a453b3ec346/entregas/PortillaAlejandro/Reto-001/CalcularPrecioFinal.java) (Reto 001)

```java
double descuento = 0.0;
if (cantidad >= 10) {
    descuento = 0.05;
}
if (cantidad >= 50) {
    descuento = 0.10;
}
if (cantidad >= 100) {
    descuento = 0.15;
}
```

¿Qué observas en este código?

En este código se observa que se están utilizando tres sentencias if independientes para asignar el valor del descuento según la cantidad. Esto representa otro error lógico, ya que cuando la variable cantidad es mayor o igual a 100, las tres condiciones se cumplen y el valor de descuento se reasigna varias veces. Aunque finalmente quede en 0.15, la forma en que está estructurado no es correcta.

La solución es usar una estructura if, else if,  else if, de manera que solo se cumpla una condición y se asigne un único valor de descuento. Además, las condiciones deben evaluarse de mayor a menor para que se aplique correctamente el descuento más alto.

El código corregido sería este:

double descuento = 0.0;

if (cantidad >= 100) {
    descuento = 0.15;
} else if (cantidad >= 50) {
    descuento = 0.10;
} else if (cantidad >= 10) {
    descuento = 0.05;
}


---

## Pregunta 5

Archivo: `DevolverCambio.java` — [Ver archivo](https://github.com/mmasias/25-26-PRG1/blob/a4a32c7cefe2fbbb8310e3d8b6906a453b3ec346/entregas/PortillaAlejandro/Reto-001/DevolverCambio.java) (Reto 001)

```java
int pagar = lector.nextInt();
int paga = lector.nextInt();
int cambio = paga - pagar;
// ...
```

¿Qué observas en este código?

---

## Pregunta 6

Archivo: `DevolverCambio.java` — [Ver archivo](https://github.com/mmasias/25-26-PRG1/blob/a4a32c7cefe2fbbb8310e3d8b6906a453b3ec346/entregas/PortillaAlejandro/Reto-001/DevolverCambio.java) (Reto 001, líneas 36-38)

```java
int monedas1 = cambio / 1;
cambio = cambio % 1;
```

¿Qué observas en este código?

En este código se observa que se realiza una división y un módulo por 1. Esto representa una operación innecesaria, ya que dividir o sacar el resto de una división entre 1 no cambia el valor de la variable.
No genera un error en la ejecución, pero es una instrucción redundante que no aporta nada al cálculo del cambio.

La corrección consiste en eliminar esas líneas o en incluirlas solo si se desea mantener la coherencia del algoritmo de monedas, pero sin realizar operaciones inútiles.

La corrección del código sería:

int monedas1 = cambio; 
cambio = 0;


---

## Pregunta 7

Archivo: `BatallaHeroeVampirosextendido.java` — [Ver archivo](https://github.com/mmasias/25-26-PRG1/blob/a4a32c7cefe2fbbb8310e3d8b6906a453b3ec346/entregas/PortillaAlejandro/reto-002/BatallaHeroeVampirosextendido.java) (Reto 002, línea 95)

```java
String elGanador = vidaGuerrero > 0 ? "Guerrero" : "Vampiro";System.out.println("Ganó el "+elGanador);
```

¿Qué observas en este código?

---

## Pregunta 8

Archivo: `BatallaHeroeVampirosextendido.java` — [Ver archivo](https://github.com/mmasias/25-26-PRG1/blob/a4a32c7cefe2fbbb8310e3d8b6906a453b3ec346/entregas/PortillaAlejandro/reto-002/BatallaHeroeVampirosextendido.java) (Reto 002, líneas 31-48)

```java
if(arma == 1){
    if(Math.random()<PROBABILIDAD_ARMA1){
    vidaVampiro = vidaVampiro - ARMA1;
    System.out.println("El vampiro recibe daño");
    }else{
         System.out.println("El vampiro esquiva");
    }

}else if(arma==2){
   if(Math.random()<PROBABILIDAD_ARMA2){
    vidaVampiro = vidaVampiro - ARMA2;
    System.out.println("El vampiro recibe daño");
   }else{
    System.out.println("El vampiro esquiva");
   }
}else if(arma==3){
    if(Math.random()<PROBABILIDAD_ARMA3){
        vidaVampiro = vidaVampiro - ARMA3;
        System.out.println("El vampiro recibe daño");
    }else{
        System.out.println("El vampiro esquiva");
    }
}
```

¿Qué observas en este código?

---

## Pregunta 9

Archivo: `BatallaHeroeVampirosextendido.java` — [Ver archivo](https://github.com/mmasias/25-26-PRG1/blob/a4a32c7cefe2fbbb8310e3d8b6906a453b3ec346/entregas/PortillaAlejandro/reto-002/BatallaHeroeVampirosextendido.java) (Reto 002, líneas 25-27)

```java
boolean algunMuerto = false;
boolean guerreroVivo = true;
boolean vampiroVivo = true;
```

¿Qué observas en este código?

