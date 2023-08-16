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
      <a class="close" @click="closeImage">
        <svg
          clip-rule="evenodd"
          fill-rule="evenodd"
          stroke-linejoin="round"
          stroke-miterlimit="2"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="m12.002 2.005c5.518 0 9.998 4.48 9.998 9.997 0 5.518-4.48 9.998-9.998 9.998-5.517 0-9.997-4.48-9.997-9.998 0-5.517 4.48-9.997 9.997-9.997zm0 8.933-2.721-2.722c-.146-.146-.339-.219-.531-.219-.404 0-.75.324-.75.749 0 .193.073.384.219.531l2.722 2.722-2.728 2.728c-.147.147-.22.34-.22.531 0 .427.35.75.751.75.192 0 .384-.073.53-.219l2.728-2.728 2.729 2.728c.146.146.338.219.53.219.401 0 .75-.323.75-.75 0-.191-.073-.384-.22-.531l-2.727-2.728 2.717-2.717c.146-.147.219-.338.219-.531 0-.425-.346-.75-.75-.75-.192 0-.385.073-.531.22z"
            fill-rule="nonzero"
          />
        </svg>
      </a>
      <img :src="selectedImage.src" :alt="selectedImage.title" />
      <a class="arrow left" @click="prevImage">
        <svg
          clip-rule="evenodd"
          fill-rule="evenodd"
          stroke-linejoin="round"
          stroke-miterlimit="2"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="m12.012 2c5.518 0 9.997 4.48 9.997 9.998 0 5.517-4.479 9.997-9.997 9.997s-9.998-4.48-9.998-9.997c0-5.518 4.48-9.998 9.998-9.998zm-1.523 6.21s-1.502 1.505-3.255 3.259c-.147.147-.22.339-.22.531s.073.383.22.53c1.753 1.754 3.254 3.258 3.254 3.258.145.145.335.217.526.217.192-.001.384-.074.531-.221.292-.293.294-.766.003-1.057l-1.977-1.977h6.693c.414 0 .75-.336.75-.75s-.336-.75-.75-.75h-6.693l1.978-1.979c.29-.289.287-.762-.006-1.054-.147-.147-.339-.221-.53-.222-.19 0-.38.071-.524.215z"
            fill-rule="nonzero"
          />
        </svg>
      </a>
      <a class="arrow right" @click="nextImage">
        <svg
          clip-rule="evenodd"
          fill-rule="evenodd"
          stroke-linejoin="round"
          stroke-miterlimit="2"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="m12.007 2c-5.518 0-9.998 4.48-9.998 9.998 0 5.517 4.48 9.997 9.998 9.997s9.998-4.48 9.998-9.997c0-5.518-4.48-9.998-9.998-9.998zm1.523 6.21s1.502 1.505 3.255 3.259c.147.147.22.339.22.531s-.073.383-.22.53c-1.753 1.754-3.254 3.258-3.254 3.258-.145.145-.335.217-.526.217-.192-.001-.384-.074-.531-.221-.292-.293-.294-.766-.003-1.057l1.977-1.977h-6.693c-.414 0-.75-.336-.75-.75s.336-.75.75-.75h6.693l-1.978-1.979c-.29-.289-.287-.762.006-1.054.147-.147.339-.221.53-.222.19 0 .38.071.524.215z"
            fill-rule="nonzero"
          />
        </svg>
      </a>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import { vOnClickOutside } from "@vueuse/components";

const images = ref([
  {
    id: 0,
    title: "Tekening origineel",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-05-originele-tekening.png",
    source: {
      url: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-05-originele-tekening.fml",
      name: "FML",
    },
  },
  {
    id: 1,
    title: "Schets uitbouw",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-13-tekening.png",
    source: {
      url: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-13-tekening.fml",
      name: "FML",
    },
  },
  {
    id: 2,
    title: "Riolering kruipruimte 1",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-08-riolering-kruipruimte-1.png",
  },
  {
    id: 3,
    title: "Riolering kruipruimte 2",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-08-riolering-kruipruimte-2.png",
  },
  {
    id: 4,
    title: "Riolering kruipruimte 3",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-08-riolering-kruipruimte-3.jpg",
  },
  {
    id: 5,
    title: "1935 riool tekening",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/1935-riool-tekening.jpg",
  },
  {
    id: 6,
    title: "Bouwtechnische keuring",
    src: "https://files.adriaanvanrossum.nl/curacaostraat/2023-08-09-bouwtechnische-keuring-cover.png",
    source: {
      url: "https://files.adriaanvanrossum.nl/curacaostraat/bouwtechnische-keuring.pdf",
      name: "PDF 66mb",
    },
  },
]);

const enlarged = ref(false);
const selectedImageId = ref(null);

const selectedImage = computed(() => {
  return images.value.find((image) => image.id === selectedImageId.value);
});

const openImage = (id) => {
  enlarged.value = true;
  selectedImageId.value = images.value.find((image) => image.id === id).id;
};

const closeImage = () => {
  enlarged.value = false;
  selectedImageId.value = null;
};

const prevImage = () => {
  const index = images.value.findIndex(
    (image) => image.id === selectedImageId.value,
  );
  if (index > 0) {
    selectedImageId.value = images.value[index - 1].id;
  } else {
    selectedImageId.value = images.value[images.value.length - 1].id;
  }
};

const nextImage = () => {
  const index = images.value.findIndex(
    (image) => image.id === selectedImageId.value,
  );
  console.log({
    date: new Date(),
    index,
    nextImage: selectedImageId.value,
    imagesLength: images.value.length,
  });
  if (index < images.value.length - 1) {
    selectedImageId.value = images.value[index + 1].id;
  } else {
    selectedImageId.value = images.value[0].id;
  }
};

onMounted(() => {
  const handleKeyDown = (event) => {
    if (enlarged.value) {
      if (event.code === "ArrowLeft") {
        prevImage();
      } else if (event.code === "ArrowRight") {
        nextImage();
      }
    }
  };
  window.addEventListener("keydown", handleKeyDown);
  return () => window.removeEventListener("keydown", handleKeyDown);
});
</script>

<style>
.album {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  --image-width: 200px;
  margin-left: -1rem;
  margin-right: -1rem;
}
@media screen and (max-width: 600px) {
  .album {
    --image-width: calc(100vw / 2 - 3rem);
  }
}
.thumbnail {
  display: flex;
  flex-direction: column;
  width: var(--image-width);
  margin: 1rem;
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
.enlarged .arrow,
.enlarged .close {
  position: absolute;
  top: 50%;
  width: 50px;
  height: 50px;
  background-size: 30px 30px;
  background-repeat: no-repeat;
  cursor: pointer;
  transform: translateY(-50%);
  opacity: 0.5;
}
@media (hover: hover) {
  .enlarged .arrow:hover,
  .enlarged .close:hover {
    opacity: 1;
    background-color: transparent;
  }
}
.enlarged .close {
  top: 32px;
  right: 10px;
}
.enlarged .arrow.left {
  left: 10px;
}
.enlarged .arrow.right {
  right: 10px;
}
</style>
