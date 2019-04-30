# Herramientas de lógica computacional - Politécnico Grancolombiano
## Retos Foro Semanas 5 y 6
### Gabriel Garnica Gutiérrez - Ingeniería de Software

#### 1. *¿Por qué es importante para todo profesional en carreras relacionadas con computación dominar los fundamentos básicos de lógica proposicional? Dar ejemplos de aplicación (Diagramas de flujo y/o programación).*

En las ciencias de la computación, la lógica proposicional forma parte fundamental durante el diseño y programación de una aplicación. Todo comienza con un flujo de trabajo establecido de forma verbal, el cual determina qué comportamiento tendrá la aplicación de acuerdo a ciertas condiciones que se van dando durante su ejecución. Estas condiciones, llamadas algoritmos, evalúan el estado actual de los datos que la aplicación tiene en determinados momentos y de acuerdo a la respuesta se realizan unas u otras acciones subsecuentes.

Como ejemplo un sencillo algoritmo que evalúa las condiciones necesarias para aplicar a un subsidio:

##### Premisas de ejemplo

Calculadora de subsidios para empleados de bajos ingresos.

1- Si la persona tiene un salario menor a $1'000.000 tiene derecho a un subsidio por el 10% de su salario

2- Si además tiene un hijo menor de 15 años recibirá un 5% adicional, Esto aplica por cada uno de los hijos que cumplan cada una de estas condiciones.

3- Si tiene a otras personas a cargo como padres o hermanos, recibirá un 3% adicional.

4- Si es de estrato 1 recibirá un 10% adicional.

5- Si tiene vivienda propia no tendrá derecho a dichos subsidios.

Para conveniencia se usarán los símbolos de los operadores lógicos de acuerdo a la sintaxis de los lenguajes Java o JavaScript:

```
&& para "AND" o "^"
|| para "OR" o "v"
== para "EQUIVALENCIA"
!= para "NO EQUIVALENCIA"
!  para "NOT" o negación
```

```javascript
var salario = '500000';
var salarioMaximo = '1000000'
var poseeVivienda = false;
var hijosMenores = 3;
var subsidio = 0;
var estrato = 1;
var personasACargo = true;

if (salario < salarioMaximo && poseeVivienda == false) {
  subsidio = 10;

  if (hijosMenores) {
    subsidio += hijosMenores * 5;
  }

  if (personasACargo == true) {
    subsidio += 3;
  }

  if (estratoUno == true) {
    subsidio += 10;
  }
  alert(`Recibe ${subsidio}% de subsidio (\$${(salario * subsidio) / 100})`);
} else {
  alert('No recibe subsidio');
}
```

[En este enlace se puede ver la aplicación funcionando](https://codepen.io/garnicag/pen/axxQQm)

#### 2. *¿Por qué es importante para todo profesional en carreras relacionadas con computación dominar los fundamentos básicos de Inferencia lógica? Dar ejemplos de aplicación (Diagramas de flujo y/o programación).*

La inferencia lógica es importante en las computación para establecer datos que se pueden deducir sin necesidad del uso de preguntas explícitas o del abuso de algoritmos evaluativos. Dadas dos premisas relacionadas entre sí, se puede llegar a concluir una tercera. Esto ayuda a evitar el uso desmedido de recursos y para tener un código más limpio, legible y por ende más fácil de comprender.

##### Premisas de ejemplo:

En un foro de discusión sobre videojuegos, las siguientes premisas aplican a los usuarios según la información suministrada durante el registro para completar su perfil y determinar en que sección se ubicará a continuación:

- En Francia se habla francés
- Un usuario escoge Francia como su país de origen
- *Ese usuario habla francés*

- God of War es un videojuego exclusivo de PS4
- Un usuario escoge God of War como su videojuego favorito
- *Ese usuario tiene como consola una PS4*

- Los videojuegos de disparos están destinados exclusivamente a audiencias adultas
- Un usuario dice tener 23 años
- *Ese usuario no tiene restricciones para jugar videojuegos de disparos*

```javascript
var pais = 'Francia';
var videojuegoFavorito = 'God of War';
var edad = 23;

var idioma;
var consola;
var restricciones;

switch (pais) {
  case 'Francia':
    idioma = 'francés';
  break;
  case 'Reino Unido':
    idioma = 'inglés';
  break;
  case 'España':
    idioma = 'español';
  break;
  case 'Japón':
    idioma = 'japonés';
  break;
  default:
    idioma = 'español';
}

switch (videojuegoFavorito) {
  case 'Super Smash Bros. Ultimate':
    consola = 'Nintendo Switch';
  break;
  case 'Halo 5':
    consola = 'Xbox One';
  break;
  case 'God of War':
    consola = 'PlayStation 4';
  break;
  default:
    consola = 'ninguna, prefieres el PC';
}

switch (Boolean(edad)) {
  case (edad < 18 && edad > 0):
    restricciones = 'no puedes jugar a videojuegos de disparos';
  break;
  case (edad >= 18):
    restricciones = 'puedes jugar a cualquier videojuego';
  break;
  default:
    restricciones = 'como no sabemos tu edad te recomendamos un videojuego para todo público';
}

alert(`Hola usuario. Tu idioma es el ${idioma}, tu consola es ${consola} y ${restricciones}`);

```

Es de notar como también se infiere una respuesta predeterminada que satisfaga los casos que no corresponden a una opción especial.