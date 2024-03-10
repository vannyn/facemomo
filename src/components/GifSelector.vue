<!-- GifSelector.vue -->
<template>
  <div>
    <select v-model="selectedGif" @change="showPreview">
      <option disabled value="">1. Select the MEME</option>
      <option v-for="(gif, index) in gifs" :key="index" :value="gif.url">{{ index + ') ' + gif.title }}</option>
    </select>

    <div v-if="selectedGif" class="preview">
      <img :src="selectedGif" alt="GIF preview" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'GifSelector',
  data() {
    return {
      gifs: [], // Qui dovrai inserire o caricare dinamicamente l'elenco delle GIF
      selectedGif: ''
    };
  },
  methods: {
    showPreview() {
      // Logica per mostrare l'anteprima può essere aggiunta qui se necessario
      // In questo esempio, l'anteprima viene mostrata automaticamente tramite il binding di Vue.js
    }
  },
  mounted() {
    // Esempio di come potresti caricare dinamicamente le GIF (qui dovresti sostituire con la tua logica/API)
    this.loadGifs();
  },
  methods: {
    loadGifs() {
      // Simulazione del caricamento delle GIF
      this.gifs = [
        {
          url:"/GIFs/applause.webp",
          title: "Applause"
        },
        {
          url:"/GIFs/baby_crying.webp",
          title: "Crying!"
        },
        {
          url:
          "/GIFs/cheers.gif",
          title: "Cheers"
        },
        {
          url:
        "/GIFs/dawson.webp",
          title: "Dawson?"
        },
        {
          url:"/GIFs/dont_know_her.webp",
          title: "I don't know her"
        },
        {
          url:"/GIFs/girls.webp",
          title: "Girlfriends"
        },
        {
          url:"/GIFs/oh_gosh.webp",
          title: "Oh Gosh"
        },
        {
          url:"/GIFs/pizza_guy.webp",
          title: "What's happening?"
        },
        {
          url:"/GIFs/please_god.webp",
          title: "Please!"
        },
        {
          url:"/GIFs/proud_yes.webp",
          title: "Proud yes"
        },
        {
          url:"/GIFs/really.webp",
          title: "Really?"
        },
        {
          url:"/GIFs/under_the_rain.webp",
          title: "Under the rain"
        },
        {
          url:"/GIFs/what_kid.webp",
          title: "What?"
        },
        {
          url:"/GIFs/yes_please.gif",
          title: "Yes Please!"
        },
        {
          url:"/GIFs/yummy.webp",
          title: "Yummi"
        },
        
      ];
    },
    showPreview() {
      // Questo metodo può essere utilizzato per logica aggiuntiva quando viene selezionata una GIF
    }
  }
};
</script>

<style>
.preview img {
  max-width: 100%;
  height: auto;
}
</style>