<template>
  <header>
    <h1>Curaçaostraat</h1>
    <p>
      Media van de Curaçaostraat. Klik op een afbeelding om deze te vergroten.
      Zie tekst onder afbeeldingen voor meer informatie.
    </p>
  </header>

  <div class="album">
    <div class="thumbnail" v-for="image in images" :key="image.id">
      <div
        class="image"
        :style="`background-image:url('${image.src}')`"
        @click="openImage(image.id)"
        :alt="image.title"
      />
      <p>
        {{ image.title }}
        <span v-if="image.source?.url">
          (source
          <a :href="image.source.url" target="_blank" rel="noopener noreferrer">
            {{ image.source.name }} </a
          >)
        </span>
      </p>
    </div>
  </div>

  <section class="description">
    <h3>Riolering in woning/kruipruimte</h3>
    <p>
      De riolering is van PVC/PE. Beide zijn een materiaal wat bijvoorbeeld ook
      in nieuwbouwwoningen wordt toegepast.
    </p>
    <ul>
      <li>
        De beoordeling van de riolering welke hierna volgt betreft altijd alleen
        datgene wat visueel waarneembaar is.
      </li>
      <li>
        We merken op dat een riolering altijd beperkt zichtbaar is, niet alle
        zijde's zijn gezien, ook een doorvoer door een vloer of fundering of
        onderdelen welke deels in het zand liggen en/of delen van de riolering
        in andere niet bekeken of bereikbare compartimenten zijn vanzelf niet
        geïnspecteerd.
      </li>
    </ul>
    <p>
      Er is een lekkage, breuk of gebrek opgemerkt aan de riolering in de
      kruipruimte. Dit gebrek dient hersteld te worden. Reparatie is meestal
      eenvoudig mogelijk. In het ergste geval moet een deel van de riolering
      worden vervangen en zelfs dat is nog eenvoudig te realiseren.
    </p>
    <p>
      Er is onvoldoende afschot in de riolering (of een verzakking). Hierdoor is
      er geen onbelemmerde afvoer en wegstroming mogelijk van afvalwater en
      blijft vervuiling achter in de riolering. Deze vervuiling 'koekt' verder
      aan, wat zal gaan leiden tot problemen of verstoppingen in het
      afvoersysteem. Het afschot dient te worden verbeterd! De ophanging van
      riolering dient opnieuw of verbeterd aangebracht te worden. Ook
      onvoldoende beugeling aan fundering of onderzijde van de vloer kan de
      oorzaak zijn van verzakkingen tussen ophangpunten.
    </p>
    <p>
      De ophanging aan fundering of onderzijde van de vloer is onvoldoende,
      hieraan zijn gebreken opgemerkt of er zijn onvoldoende ophangpunten
      aanwezig. De afstand tussen de ophangpunten is te groot waardoor
      verzakking van de riolering zal kunnen gaan ontstaan of al reeds aanwezig
      is. Dit zal weer problemen gaan opleveren met het functioneren van de
      riolering. De ophanging dient te worden verbeterd.
    </p>
    <p>
      De riolering ligt 'los' op de bodem van de kruipruimte, dit is niet
      gebruikelijk! Wellicht kan de riolering op deze wijze toch nog goed
      functioneren, echter een wijziging of verandering in de bodemstructuur zal
      ervoor zorgen dat bijvoorbeeld het afschot niet meer goed functioneert.
      Beter is om de riolering op afschot aan fundering of onderzijde van de
      vloer te monteren. Vanaf de doorvoeren door de vloer zal de riolering dan
      vervangen moeten worden.
    </p>

    <p>
      Er is een gietijzeren riolering aangetroffen. Gietijzeren (metalen)
      rioleringen zijn in het verleden vaak gebruikt voor de aanleg van
      rioleringstelsels. Er is dan ook niets mis met dergelijk materiaal, echter
      wordt tegenwoordig meestal gekozen voor kunststof rioleringen. Indien de
      riolering functioneert is er nog geen reden om deze te vervangen. Bijna
      alle gietijzeren riolering zijn echter op dit moment aan het einde van de
      levensduur. Gietijzer wordt namelijk vanaf de jaren ́70 niet meer gebruikt.
      Als u een gietijzeren riool met problemen heeft, zal de gietijzeren
      riolering (op korte termijn) vervangen moeten worden. Ook wanneer u geen
      rioolproblemen heeft, kunt u overwegen de riolering preventief te laten
      vervangen door een modern materiaal als PVC, op enig moment moet de
      riolering zeker worden vervangen, een gebrek aan de riolering kan door
      materiaal spanningen en roest of gebreken van binnenuit van de ene op de
      andere dag ontstaan.
    </p>

    <ul>
      <li>
        Hoewel gietijzer een sterk materiaal is, kent het een groot aantal
        nadelen bij het gebruik ervan voor het riool. Het grootste probleem van
        gietijzeren riolering is dat het gietijzer roest. Het materiaal staat
        continu bloot aan water en zuurstof (de twee factoren waardoor
        roestvorming snel bij gietijzer ontstaat).
      </li>
      <li>
        Door de roestvorming ontstaat een oneffen oppervlak in het gietijzeren
        riool. Hier blijft makkelijk toiletpapier aan vastzitten, waardoor
        verstopping ontstaat.
      </li>
      <li>
        Daarnaast worden de aansluitingen tussen gietijzeren rioolstukken na
        verloop van tijd slecht en kan lekkage ontstaan. Verder slijt het
        gietijzer na jarenlang gebruik sneller dan moderne materialen.
      </li>
      <li>
        De beoordeling van de riolering welke hierna volgt betreft altijd alleen
        datgene wat visueel waarneembaar is.
      </li>
      <li>
        We merken op dat een riolering altijd beperkt zichtbaar is, niet alle
        zijde's zijn gezien, ook een doorvoer door een vloer of fundering of
        onderdelen welke deels in het zand liggen en/of delen van de riolering
        in andere niet bekeken of bereikbare compartimenten zijn vanzelf niet
        geïnspecteerd.
      </li>
    </ul>
  </section>

  <div class="enlarged" v-if="enlarged" v-on-click-outside="closeImage">
    <a class="close-icon" @click="closeImage">×</a>
    <img :src="selectedImage.src" :alt="selectedImage.title" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import { vOnClickOutside } from "@vueuse/components";

const images = [
  {
    id: 1,
    title: "Tekening origineel",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-05-originele-tekening.png",
    source: {
      url: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-05-originele-tekening.fml",
      name: ".fml",
    },
  },
  {
    id: 2,
    title: "Schets uitbouw",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-13-tekening.png",
    source: {
      url: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-13-tekening.fml",
      name: ".fml",
    },
  },
  {
    id: 3,
    title: "Riolering kruipruimte 1",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-08-riolering-kruipruimte-1.png",
  },
  {
    id: 4,
    title: "Riolering kruipruimte 2",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-08-riolering-kruipruimte-2.png",
  },
  {
    id: 5,
    title: "1935 riool tekening",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/1935-riool-tekening.jpg",
  },
];

const enlarged = ref(false);
const selectedImage = ref({});

const openImage = (id) => {
  enlarged.value = true;
  selectedImage.value = images.find((image) => image.id === id);
};

const closeImage = () => {
  enlarged.value = false;
  selectedImage.value = {};
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
}
body {
  background: #fcfefe;
  word-break: break-word;
  display: flex;
  justify-content: center;
  color: #415659;
  font-family: Arial, sans-serif;
  font-weight: 400;
}
h1,
h2,
h3,
p,
ul {
  margin: 0 0 1rem;
}
#app {
  margin: auto;
  display: flex;
  flex-direction: column;
  padding: 2rem;
  flex: 0 1 auto;
}
@media (prefers-color-scheme: dark) {
  body {
    background: #2a3638;
  }
  textarea,
  input {
    background: #232e2f;
  }
  body,
  a,
  textarea,
  input {
    color: #a4bdc0;
  }
}
* {
  box-sizing: border-box;
}
header {
  margin: 1rem;
  text-align: center;
}
.description {
  margin: 1rem;
}

.album {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;

  --image-width: 200px;
}
.thumbnail {
  display: flex;
  flex-direction: column;
  width: var(--image-width);
  margin: 10px;
  text-align: center;
}
.thumbnail .image {
  width: var(--image-width);
  height: var(--image-width);
  background-size: cover;
  background-position: center;
  border-radius: 5px;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: transform 0.2s ease-in-out;
}
/* on hover, scale to 1.1 */
.thumbnail .image:hover {
  transform: scale(1.1);
}
.enlarged {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.enlarged img {
  max-width: calc(100vw - 2rem);
  max-height: calc(100vh - 2rem);
  border-radius: 1rem;
  box-shadow: 3px 3px 10px rgba(0, 0, 0, 0.1);
}
.close-icon {
  position: absolute;
  top: 5px;
  right: 5px;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  opacity: 0.5;
  font-size: 40px;
  background-color: black;
  color: white;
  border-radius: 1000px;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 40px;
  height: 40px;
  line-height: 40px;
}
.close-icon:hover {
  opacity: 1;
}
</style>
