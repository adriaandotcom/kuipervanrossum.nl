<template>
  <div>
    <div class="album">
      <div class="thumbnail" v-for="image in images" :key="image.id">
        <div
          class="image"
          :style="`background-image:url('${image.src}')`"
          @click="openImage(image.id)"
          :alt="image.title"
        />
        <p style="margin-top: 0.5rem; margin-bottom: 0">
          {{ image.title }}
        </p>
        <p style="font-size: 12px">
          (download
          <a :href="image.src" target="_blank" rel="noopener noreferrer"
            >image</a
          >
          <span v-if="image.source?.url"
            >,
            <a
              :href="image.source.url"
              target="_blank"
              rel="noopener noreferrer"
            >
              {{ image.source.name }}
            </a> </span
          >)
        </p>
      </div>
    </div>

    <div class="enlarged" v-if="enlarged" v-on-click-outside="closeImage">
      <a class="close-icon" @click="closeImage">×</a>
      <img :src="selectedImage.src" :alt="selectedImage.title" />
    </div>
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
      name: "FML",
    },
  },
  {
    id: 2,
    title: "Schets uitbouw",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-13-tekening.png",
    source: {
      url: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-13-tekening.fml",
      name: "FML",
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
    title: "Riolering kruipruimte 3",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-08-riolering-kruipruimte-3.jpg",
  },
  {
    id: 6,
    title: "1935 riool tekening",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/1935-riool-tekening.jpg",
  },
  {
    id: 7,
    title: "Bouwtechnische keuring",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-09-bouwtechnische-keuring-cover.png",
    source: {
      url: "https://files.adriaanvanrossum.nl/curacaostraat/bouwtechnische-keuring.pdf",
      name: "PDF 66mb",
    },
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
@media (hover: hover) {
  .thumbnail .image:hover {
    transform: scale(1.1);
  }
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
