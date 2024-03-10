<template>
    <div>
      <input type="file" @change="handleFileUpload" accept="image/*">
      <div v-if="imageUrl" class="image-preview">
        <img :src="imageUrl" alt="Preview" class="preview" />
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ImageUploader',
    data() {
      return {
        imageUrl: null, // URL per la preview dell'immagine
      };
    },
    methods: {
      handleFileUpload(event) {
        const file = event.target.files[0];
        if (file && file.type.startsWith('image/')) {
          this.previewImage(file);
        }
        this.$emit('image-uploaded', file);
      },
      previewImage(file) {
        // Crea un URL per l'immagine selezionata per mostrarne la preview
        const reader = new FileReader();
        reader.onload = (e) => {
          this.imageUrl = e.target.result;
        };
        reader.readAsDataURL(file);
      }
    }
  }
  </script>
  
  <style>
  .image-preview img {
    width: 100%; /* o qualsiasi altra dimensione */
    max-width: 300px; /* Imposta un limite massimo per la larghezza della preview */
    height: auto;
    border: 1px solid #ddd; /* Opzionale: aggiunge un bordo attorno alla preview */
    border-radius: 4px; /* Opzionale: arrotonda gli angoli della preview */
    padding: 5px; /* Opzionale: aggiunge un padding attorno alla preview */
    margin-top: 10px; /* Opzionale: aggiunge un margine sopra la preview */
  }
  </style>