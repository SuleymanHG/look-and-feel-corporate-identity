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
Dynamisch Laden van Afbeeldingen via de Pexels API
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

Toegankelijk Hamburger Menu
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
## Bronnen

## Licentie

This project is licensed under the terms of the [MIT license](./LICENSE).
