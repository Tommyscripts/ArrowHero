# ArrowHero

## Introducci贸n 馃殌
Realizamos un juego basado en HTML, CSS y JavaScripts.

El juego se llama  Arrow Hero, el jugador tendra que presionar la tecla que el juego genere en el tiempo determinado, si dicho jugador pulsa la tecla antes de tiempo perdera una vida, al igual si la pulsa despues del tiempo determinado, al pusar la tecla en el tiempo exacto obtendra puntos,lo cual le regenerar谩 una vida.

### Primeros pasos 馃搵

Para la realizaci贸n del proyecto, primero creamos una idea grupal de como hariamos cada paso de las ideas obtenidas en grupo, una vez cumplido este objetivo, decidimos el orden necesario de la realizaci贸n del proyecto para que funcione lo m谩s b谩sico, tras ello, hemos comenzado las tareas para crear una interfaz visible,  una vez la interfaz es visible, hemos comenzado con la generaci贸n de eventos y la creaci贸n de notas.

### Creaci贸n del c贸digo 馃敡

Tras tener la visualizaci贸n, hemos creado un sistema b谩sico, para poder testear los codigos creados en JavaScript, la versi贸n de prueba de dicho juego.

Al div padre le hemos dado 775px en si height

Dar nombre a las variables y funciones, las cuales son las siguientes:
Arrows = variable dada a las flechas.

Notas = las notas generadas por el juego.

Guitarra = la variable utilizada para crear el camino que recorrera las notas.

Life= es la variable utilizada para mostrar el contador de vidas durante la partida.

function gameOver = Es la funcion que actuara una vez el contador de vidas llegue a 0 donde terminara el juego.

Variable timeup = Creamos un setInterval reutilizable.

variable timerWiner = la variable que se utiliza para cuando ganas el juego.

function cleargame = para en la condicion de ganar o perder, limpie el juego.

Creamos una constante llamada moveNote la cual utilizamos para una funcion, su objetivo es mover la nota a trav茅z de la string.

Una variable llamada direcci贸n = le damos la direcci贸n al objeto.

Funcion activated Arrow = para detectar si ha pulsado bien la nota el usuario, o ha errado.

Addevenlistener (keydown) con un switch, donde detectanos el evento de la pulsaci贸n de las flechas.



```js
window.addEventListener("keydown", function (e) {
    switch (e.code) {
        case 'ArrowLeft':
            arrows.pressed = 'left'
            activatedArrow()
            break;
        case 'ArrowUp':
            arrows.pressed = 'up'
            activatedArrow()
            break;
        case 'ArrowDown':
            arrows.pressed = 'down'
            activatedArrow()
            break;
        case 'ArrowRight':
            arrows.pressed = 'right'
            activatedArrow()
            break;
    }
})
```
El activated arrow

```js
function activatedArrow() {
    if (arrows.pressed === 'left') {
        arrows.sprites[0].style.backgroundColor = "red"
        setTimeout(function() {
            arrows.sprites[0].style.backgroundColor = "transparent"
        },200)
    }else if(arrows.pressed === 'up'){
        arrows.sprites[1].style.backgroundColor = "green"
        setTimeout(function() {
            arrows.sprites[1].style.backgroundColor = "transparent"
        },200)
    }else if(arrows.pressed === 'down'){
        arrows.sprites[2].style.backgroundColor = "blue"
        setTimeout(function() {
            arrows.sprites[2].style.backgroundColor = "transparent"
        },200)
    }else if(arrows.pressed === 'right'){
        arrows.sprites[3].style.backgroundColor = "yellow"
        setTimeout(function() {
            arrows.sprites[3].style.backgroundColor = "transparent"
        },200)
    }
}
```

La generaci贸n de la primera nota.

## Ejecutando las pruebas 鈿欙笍

A cada paso dado se realizan pruebas testeando el codigo las pruebas realizadas han sido las siguientes:

El reconocimiento de eventlistener keydown, en sus relativos puesttos, izquierda, arriba,abajo  y derecha, dando el resultado deseado.

La creacion de una nota, tras crear el generador de notas, nos aseguramos que se genera una nota.

La eliminaci贸n de la nota tras salir de la caja, tras el paso anterior nos aseguramos que la nota es eliminada.

### Refactorizaci贸n del codigo 馃敥

Tras unas pruebas, hemos refactorizado el codigo, antes de refacttorizar, se veia de esta manera: 
```js
function activatedArrow() {
    if (arrows.pressed === 'left') {
        arrows.sprites[0].style.backgroundColor = "red"
        setTimeout(function() {
            arrows.sprites[0].style.backgroundColor = "transparent"
        },200)
    }else if(arrows.pressed === 'up'){
        arrows.sprites[1].style.backgroundColor = "green"
        setTimeout(function() {
            arrows.sprites[1].style.backgroundColor = "transparent"
        },200)
    }else if(arrows.pressed === 'down'){
        arrows.sprites[2].style.backgroundColor = "blue"
        setTimeout(function() {
            arrows.sprites[2].style.backgroundColor = "transparent"
        },200)
    }else if(arrows.pressed === 'right'){
        arrows.sprites[3].style.backgroundColor = "yellow"
        setTimeout(function() {
            arrows.sprites[3].style.backgroundColor = "transparent"
        },200)
    }
}

var guitarra = document.getElementById('guitarra')
var nota = document.createElement('div')
nota.setAttribute('class','notaCSS')
guitarra.appendChild(nota)
console.log(nota)
var notaTop = 10
var direccion = 1

const moveNote = function() {
    if (notaTop == 728) {
        guitarra.removeChild(nota)
    }
    notaTop += 1 * direccion
    nota.style.top = notaTop+'px'
} 
```

Tras refactorizar, el resultado es el siguiente: 

```js
const arrows = {
  sprites: document.getElementsByClassName("botn"),
  colorAndTransparent(id, color) {
    this.sprites[id].style.backgroundColor = color
    setTimeout(() => {
      this.sprites[id].style.backgroundColor = "transparent"
    }, 200)
  },
  activatedArrow(pressed) {
    switch (pressed) {
      case 'ArrowLeft':
        this.colorAndTransparent(0, 'red');
        break;
      case 'ArrowUp':
        this.colorAndTransparent(1, 'green');
        break;
      case 'ArrowDown':
        this.colorAndTransparent(2, 'blue');
        break;
      case 'ArrowRight':
        this.colorAndTransparent(3, 'yellow');
        break;
    }
    if (Nota.top > 582 && Nota.top+Nota.height < 712) {
      console.log('DENTRO PERO CUALQUIER TECLA')
    }
  }
}

window.addEventListener("keydown", function (e) {
  if (['ArrowLeft', 'ArrowUp', 'ArrowDown', 'ArrowRight'].includes(e.code)) {
    arrows.activatedArrow(e.code);
  }
})
```

Tras acabar con la programaci贸n mas b谩sica y necesaria, nos hemos puesto a trabajar con el dise帽o
```
https://www.figma.com/file/iawhL8b86WSC5D4vTU7Pgb/Untitled?node-id=1%3A3
```
### Y las pruebas de estilo de codificaci贸n 鈱笍

Hemos hecho una variedad de pruebas cambiando fondos, estilos, pantalla de inicio, game over, etc.

La razon del porque hemos cambiado dise帽os, es porque al verlo en el juego no nos ha gustado el resultado, hemos cambiado varias veces hasta estar totalmente agusto con el resultado.



## Despliegue 馃摝

Tras la versi贸n m谩s optimizada se realizo el despliegue definitivo del juego.

## Construido con 馃洜锔?

Visual studios code

Terminal ubuntu

* [Developers Mozilla]((https://developer.mozilla.org/es/)) - Hemos sacado la informaci贸n necesaria de esta p谩gina.

## Contribuyendo 馃枃锔?

Javier Cabrera Escoz, Emilio Casado de Galdo, Alejandro Jos茅 Cruz Santiago


## Expresiones de Gratitud 馃巵

* Al buen caf茅.
* A los profes de reboot.
* Y a MDN.
