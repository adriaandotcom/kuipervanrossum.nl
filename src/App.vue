<template>
  <header>
    <h1>Curaçaostraat 35, Amsterdam</h1>
    <p>
      Media from Curaçaostraat. Click on an image to enlarge it. See text below
      images for more information.
    </p>
  </header>

  <div
    style="
      display: flex;
      margin: 0 auto;
      margin-top: -1rem;
      margin-bottom: 0.5rem;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
    "
  >
    <p style="margin: 0">Select:</p>
    <ul class="labels">
      <li>
        <a @click="tag = null" :class="{ active: !tag }">Alles/All</a>
      </li>
      <li>
        <a @click="tag = 'tekeningen'" :class="{ active: tag === 'tekeningen' }"
          >Tekeningen/Plans</a
        >
      </li>
      <li>
        <a @click="tag = 'ramen'" :class="{ active: tag === 'ramen' }"
          >Ramen/Windows</a
        >
      </li>
      <li>
        <a @click="tag = 'riolering'" :class="{ active: tag === 'riolering' }"
          >Riolering/Sewerage</a
        >
      </li>
      <li>
        <a @click="tag = 'rapporten'" :class="{ active: tag === 'rapporten' }"
          >Rapporten/Reports</a
        >
      </li>
    </ul>
  </div>

  <PhotoAlbum :tag="tag" />

  <section class="description">
    <details>
      <summary>Keuringsrapport riolering in woning/kruipruimte</summary>

      <p>
        De riolering is van PVC/PE. Beide zijn een materiaal wat bijvoorbeeld
        ook in nieuwbouwwoningen wordt toegepast.
      </p>
      <ul>
        <li>
          De beoordeling van de riolering welke hierna volgt betreft altijd
          alleen datgene wat visueel waarneembaar is.
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
        Er is onvoldoende afschot in de riolering (of een verzakking). Hierdoor
        is er geen onbelemmerde afvoer en wegstroming mogelijk van afvalwater en
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
        verzakking van de riolering zal kunnen gaan ontstaan of al reeds
        aanwezig is. Dit zal weer problemen gaan opleveren met het functioneren
        van de riolering. De ophanging dient te worden verbeterd.
      </p>
      <p>
        De riolering ligt 'los' op de bodem van de kruipruimte, dit is niet
        gebruikelijk! Wellicht kan de riolering op deze wijze toch nog goed
        functioneren, echter een wijziging of verandering in de bodemstructuur
        zal ervoor zorgen dat bijvoorbeeld het afschot niet meer goed
        functioneert. Beter is om de riolering op afschot aan fundering of
        onderzijde van de vloer te monteren. Vanaf de doorvoeren door de vloer
        zal de riolering dan vervangen moeten worden.
      </p>

      <h3>Gietijzeren riolering</h3>
      <p>
        Er is een gietijzeren riolering aangetroffen. Gietijzeren (metalen)
        rioleringen zijn in het verleden vaak gebruikt voor de aanleg van
        rioleringstelsels. Er is dan ook niets mis met dergelijk materiaal,
        echter wordt tegenwoordig meestal gekozen voor kunststof rioleringen.
        Indien de riolering functioneert is er nog geen reden om deze te
        vervangen. Bijna alle gietijzeren riolering zijn echter op dit moment
        aan het einde van de levensduur. Gietijzer wordt namelijk vanaf de jaren
        ́70 niet meer gebruikt. Als u een gietijzeren riool met problemen heeft,
        zal de gietijzeren riolering (op korte termijn) vervangen moeten worden.
        Ook wanneer u geen rioolproblemen heeft, kunt u overwegen de riolering
        preventief te laten vervangen door een modern materiaal als PVC, op enig
        moment moet de riolering zeker worden vervangen, een gebrek aan de
        riolering kan door materiaal spanningen en roest of gebreken van
        binnenuit van de ene op de andere dag ontstaan.
      </p>

      <ul>
        <li>
          Hoewel gietijzer een sterk materiaal is, kent het een groot aantal
          nadelen bij het gebruik ervan voor het riool. Het grootste probleem
          van gietijzeren riolering is dat het gietijzer roest. Het materiaal
          staat continu bloot aan water en zuurstof (de twee factoren waardoor
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
          De beoordeling van de riolering welke hierna volgt betreft altijd
          alleen datgene wat visueel waarneembaar is.
        </li>
        <li>
          We merken op dat een riolering altijd beperkt zichtbaar is, niet alle
          zijde's zijn gezien, ook een doorvoer door een vloer of fundering of
          onderdelen welke deels in het zand liggen en/of delen van de riolering
          in andere niet bekeken of bereikbare compartimenten zijn vanzelf niet
          geïnspecteerd.
        </li>
      </ul>
    </details>
  </section>
</template>

<script setup>
import { ref, watch } from "vue";
import PhotoAlbum from "./components/PhotoAlbum.vue";

let tag = ref("");

const urlParams = new URLSearchParams(window.location.search);
const tagParam = urlParams.get("tag");
if (tagParam) tag.value = tagParam;

watch(tag, (value) => {
  if (value) urlParams.set("tag", value);
  else urlParams.delete("tag");
  window.history.replaceState(
    {},
    "",
    `${window.location.pathname}?${urlParams}`,
  );
});
</script>

<style>
header {
  margin: 1rem;
  text-align: center;
}
.description {
  max-width: 700px;
  margin: 1rem auto;
  line-height: 180%;
  padding-bottom: 3rem;
}
ul.labels {
  display: flex;
  justify-content: center;
  list-style: none;
  padding: 0;
  flex-wrap: wrap;
  margin: 0;
}
ul.labels li {
  margin: 0.5rem;
}
ul.labels li a {
  cursor: pointer;
  padding: 0.2rem 0.5rem;
  border-radius: 0.5rem;
  background-color: #eee;
}
ul.labels li a.active {
  background-color: #13c287;
  color: white;
}
@media (hover: hover) {
  ul.labels li a:hover {
    background-color: #ddd;
  }
  ul.labels li a.active:hover {
    background-color: #09875d;
  }
}
</style>
