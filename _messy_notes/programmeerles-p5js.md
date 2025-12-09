# Programmeerles P5.js (HAN University of Applied Sciences)

Altijd al willen programmeren? Altijd al willen weten hoe software ontwikkelaars
met code programma's maken? Bij de programmeerles gaan we daar een begin mee maken.
Wat gaan we doen? We gaan met behulp van de codetaal JavaScript een klein programma
schrijven dat een aantal dingen kan tekenen op het scherm.

Als dat lukt gaan we ook nog een aantal kleine gebruikersinteracties erbij bouwen.

## Tools en benodigdheden

- Laptop
- Werkende internetverbinding

## Introductie

Wat is programmeren? Kortweg: het aansturen van de computer op basis van een programmeertaal.

- Open de [editor](https://editor.p5js.org): https://editor.p5js.org
- Druk op de ▶️ play-knop
- Verander nu bij `background(220)` de waarden naar: `background(240, 130, 130);`
  <!-- Wat gebeurt hier nou? RGB waarden als er meerdere waarden zijn -->
  <!-- Grijswaarden als er maar 1 waarde is -->

## Opdracht: Rechthoek

- Teken een rechthoek van 100 pixels breed en 200 pixels hoog.
- Kies een leuke kleur

Gebruik daarvoor de volgende functies:

- [`noStroke()`](https://p5js.org/reference/p5/noStroke/)
- [`fill()`](https://p5js.org/reference/p5/fill/)
- [`rect()`](https://p5js.org/reference/p5/rect/).

We maken nu al gebruik van **functies**, samen met variabelen een heel belangrijk onderdeel van programmeren.

## Opdracht: Variabelen

Om goed gebruik te maken van programmeren maken we gebruik van variabelen,
daarin kunnen we waarden opslaan:

```js
const naam = 'Fritz';
const hoogte = 100;
```

Volg nu de onderstaande stappen:

- Maak nu 2 variabelen voor de hoogte en de breedte van de rechthoek
- Gebruik deze variabelen voor het tekenen van de rechthoek

## Opdracht: Nederlandse vlag

Gebruik nu wat je hebt geleerd om de Nederlandse vlag te tekenen

Nodig: variabelen en kleuren en berekenen op welke hoogte de vierkanten komen.

## Opdracht: Nederlandse vlag herschaalbaar

Gebruik de uitwerking van Nederlandse vlag maar verander de bovenste regels naar:

```js
function setup() {
  const cnvWidth = 400;
  const cnvHeight = 300;
  createCanvas(cnvWidth, cnvHeight);
  // .. hier de rest van de code

  console.log('Wat is de waarde van: ', cnvWidth / 2);
}
```

Zorg er nu voor dat wanneer je de grootte van het "canvas" aanpast de vlag meegroeit.

> Hint: je kunt vermenigvuldigen en delen met `*` en `/`, en elkaar optellen en aftrekken met: `+` en `-`.
> Bijvoorbeeld: `const waarde = 340 / 3 + a`.

## Opdracht: Japanse vlag

Teken nu op basis van wat je hebt geleerd met de functie: [`circle()`](https://p5js.org/reference/p5/circle/) de vlag van Japan.

De cirkel wordt altijd vanuit het midden getekend.

‼️ Zorg ervoor dat deze ook herschaalbaar is.

## Bonus: Bewegende beelden

Als het bovenstaande gelukt is gaan we iets proberen met de muis.

```js
function mousePressed() {
  fill(255, 0, 0);
  rect(mouseX, mouseY, 30, 30);
}
```

## Uitwerkingen

De uitwerkingen worden na de les rondgestuurd door de docent.

## Uitwerkingen voor gist

### Opdracht: rechthoek

```js
function setup() {
  createCanvas(300, 200);

  noStroke();
  fill(255, 0, 0);
  rect(0, 0, 100, 200);
}
```

### Opdracht: Variabelen

```js
function setup() {
  createCanvas(300, 200);

  const breedte = 200;
  const hoogte = 100;

  noStroke();
  fill(255, 0, 0);
  rect(0, 0, breedte, hoogte);
}
```

### Nederlandse vlag

```js
function setup() {
  createCanvas(400, 300);
  background(222);

  noStroke();
  // maakt gebruik van hexadecimale kleurcode's
  // voorbeeldkleuren: https://www.color-hex.com/
  fill('#f00');
  rect(0, 0, 400, 100);

  // kleurwaarden kan ook in R G B
  fill(255, 255, 255);
  rect(0, 100, 400, 100);

  // dit is blauw want
  // R     G      B
  // 0     0     255
  // betekent geen rood, geen groen
  // alleen maar blauw
  fill(0, 0, 255);
  rect(0, 200, 400, 100);
}
```

### Nederlandse vlag - herschaalbaar

```js
function setup() {
  const cnvWidth = 400;
  const cnvHeight = 300;
  createCanvas(cnvWidth, cnvHeight);

  noStroke();
  fill(255, 0, 0);

  rect(0, 0, cnvWidth, cnvHeight / 3);

  fill(255);
  rect(0, cnvHeight / 3, cnvWidth, cnvHeight / 3);

  fill(0, 0, 255);
  rect(0, cnvHeight - cnvHeight / 3, cnvWidth, cnvHeight / 3);
}
```

### Japanse vlag - herschaalbaar

```js
function setup() {
  const cnvWidth = 600;
  const cnvHeight = 450;
  createCanvas(cnvWidth, cnvHeight);
  background(255);
  console.log(width);

  noStroke();
  fill(255, 0, 0);
  circle(cnvWidth / 2, cnvHeight / 2, cnvHeight / 2);
}
```

### Bewegend balletje

```js
let circleX, circleY, circleSize, vx, vy;
function setup() {
  createCanvas(500, 300);
  background(222);
  circleX = width / 2;
  circleY = height / 2;
  circleSize = 50;
  vx = 0;
  vy = 0;
}

function draw() {
  background(255);
  fill('#00F');
  circle(circleX, circleY, circleSize);

  if (keyIsDown(LEFT_ARROW)) {
    vx -= 0.1;
  }
  if (keyIsDown(RIGHT_ARROW)) {
    vx += 0.1;
  }
  if (keyIsDown(UP_ARROW)) {
    vy -= 0.1;
  }
  if (keyIsDown(DOWN_ARROW)) {
    vy += 0.1;
  }
  if (keyIsDown(ENTER)) {
    vx = 0;
    vy = 0;
  }

  if (circleX - circleSize / 2 < 0 || circleX + circleSize / 2 > width) {
    vx = vx * -1;
  }
  if (circleY - circleSize / 2 < 0 || circleY + circleSize / 2 > height) {
    vy = vy * -1;
  }

  circleX += vx;
  circleY += vy;
}
```
