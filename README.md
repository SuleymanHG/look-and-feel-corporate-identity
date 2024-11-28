# Corporate Identity

Ontwerp en maak voor een opdrachtgever een website op basis van een bestaande huisstijl.

De instructie vind je in: [INSTRUCTIONS](https://github.com/fdnd-task/look-and-feel-corporate-identity/blob/main/docs/INSTRUCTIONS.md)


# Titel
Qatar museums corporate identity

## Beschrijving
In deze sprint hebben we de opdracht gekregen om ons te richten op de stylesheet en het visuele ontwerp van de website. Het doel was om een samenhangende en toegankelijke gebruikerservaring te creëren die aansluit bij de bestaande huisstijl van Qatar Museums.
<!-- Voeg een mooie poster visual toe 📸 -->
<!-- Voeg een link toe naar Github Pages 🌐-->

## Kenmerken
<h3>Dynamisch Laden van Afbeeldingen via de Pexels API</h3>
Code:

```
const container = document.querySelector('.grid');
const apiKey = 'Id7ZnvcbuagCH5xt4V02lWUJAj4kCakcxGrbfEDiROH4zpHyC8DUI0Oa';
let page = 1;
const query = 'islamic art';
const perPage = 50;

function loadImages() {
  const URL = `https://api.pexels.com/v1/search?query=${query}&per_page=${perPage}&page=${page}`;

  fetch(URL, {
    headers: {
      Authorization: apiKey
    }
  })
    .then(response => response.json())
    .then(data => {
      if (data.photos && data.photos.length > 0) {
        data.photos.forEach(photo => {
          const img = document.createElement('img');
          img.src = photo.src.medium;
          img.alt = photo.photographer;
          container.appendChild(img);
        });
      }
    })
    .catch(error => {
      console.error('Error fetching images from Pexels:', error);
    });

  page++;
}

loadImages();
```
Uitleg:

Deze functie maakt gebruik van de Pexels API om afbeeldingen op te halen op basis van de zoekterm islamic art.
Dynamische inhoud: Voor elke afbeelding wordt een <img>-element aangemaakt en toegevoegd aan de container .grid.
Paginering: Variabele page wordt verhoogd om nieuwe inhoud op te halen bij het scrollen.

<h3>Toegankelijk Hamburger Menu</h3>
Code:

```
const hamburger = document.querySelector('.hamburger');
const nav = document.querySelector('nav');

hamburger.addEventListener('click', () => {
  nav.classList.toggle('active');
  const expanded = hamburger.getAttribute('aria-expanded') === 'true' || false;
  hamburger.setAttribute('aria-expanded', !expanded);
});
```
Uitleg:

Klasse active:
Activeert/deactiveert het menu door de klasse .active aan het <nav>-element toe te voegen.
Toegankelijkheid:
Het aria-expanded-attribuut wordt dynamisch aangepast, wat de toegankelijkheid voor schermlezers verbetert.

<h3>Kleuren en Thema Variabelen</h3>
Code:

```
:root {
  color-scheme: light dark;
  
  --light: white;
  --dark: black;
  --accent-pink: #ED3CBA;
  --accent-yellow: #f9ff1e;
}

* {
  background-color: light-dark(var(--light), var(--dark));
  color: light-dark(var(--dark), var(--light));
}
```
Uitleg:

CSS-variabelen:
Verschillende kleurschema’s (licht en donker) zijn gedefinieerd in de :root.
De functie light-dark() selecteert automatisch de juiste kleur afhankelijk van het thema.

<h3>Dynamisch Grid Layout</h3>
Code:

```
.grid {
  display: grid;
  gap: 1em;
  grid-template-columns: repeat(7, 1fr);
}

@media (max-width: 768px) {
  .grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 576px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
```
Uitleg:

Het grid past zich aan afhankelijk van de schermgrootte:
Desktop: 7 kolommen.
Tablet: 3 kolommen.
Mobiel: 2 kolommen.
Deze flexibele layout zorgt voor een betere gebruikerservaring op verschillende apparaten.

<h3>Knopstijlen in de Styleguide</h3>
Code:

```
.button {
  background-color: light-dark(var(--light-button), var(--dark-button));
  color: light-dark(var(--dark), var(--light));
  padding: 0.5rem;
  border: 2px solid;
}

.button:hover {
  background-color: light-dark(var(--light-hover-button), var(--dark-hover-button));
  color: light-dark(var(--light-hover-button-text), var(--dark-hover-button-text));
}
```
Uitleg:

Knoppen veranderen van kleur bij hover, afhankelijk van het actieve thema.
Herbruikbare stijlen maken het eenvoudig om knoppen consistent te ontwerpen.

## Bronnen

## Licentie

This project is licensed under the terms of the [MIT license](./LICENSE).
