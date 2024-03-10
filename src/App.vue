<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    

    <div class="wrapper">
      <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="300"  />
    </div>
  </header>
  <content>
    <div id="app" class="wrapper">
      <div class="wrapper" id="selectVideo">
        <h2>1. Select your favorite MEME</h2>
        <GifSelector></GifSelector>
        
      </div>
      <div class="wrapper" id="uploadImage"></div>
        <h2>2. Upload your picture</h2>
        <image-uploader @image-uploaded="setImage"></image-uploader>

      <div>
        <input type="checkbox" id="terms" v-model="acceptedTerms">
        <label for="terms">Accetto i termini e le condizioni</label>
      </div>

      <button :disabled="!canSubmit" @click="submitForm">Submit</button>
    </div>
  </content>
  <footer>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/momo">What is MOMO</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
  </footer>
</template>

<script>
import ImageUploader from './components/ImageUploader.vue'
import GifSelector from './components/GifSelector.vue'
export default {
  name: 'App',
  components: {
    ImageUploader,
    GifSelector
  },
  data() {
    return {
      videos: [
        { id: 'video1', name: 'Video 1' },
        { id: 'video2', name: 'Video 2' },
        // Aggiungi qui altri video/gif
      ],
      selectedVideo: '',
      uploadedImage: null,
      acceptedTerms: false,
    }
  },
  computed: {
    canSubmit() {
      return this.selectedVideo && this.uploadedImage && this.acceptedTerms;
    }
  },
  methods: {
    setImage(image) {
      this.uploadedImage = image;
    },
    submitForm() {
      // Qui gestisci la logica di invio dei dati, es. tramite Axios a un API
      console.log("Form submitted:", this.selectedVideo, this.uploadedImage);
    }
  }
}
</script>
<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
