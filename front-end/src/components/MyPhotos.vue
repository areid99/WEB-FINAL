<template>
<div class="main">
  <div class="menu">
    <h2>Logged in as: {{user.firstName}} {{user.lastName}} <button @click="logout"><p>logout</p></button></h2>
    <uploader :show="show" @close="close" @uploadFinished="uploadFinished" />

  </div>
    <div class = "addPhotos">
        <button @click="toggleUpload">Add a new photo</button>
      </div>
      <image-gallery :photos="photos" />
  <p v-if="error">{{error}}</p>
</div>
</template>

<script>
import axios from 'axios';
import Uploader from '@/components/Uploader.vue';
import ImageGallery from '@/components/ImageGallery.vue';
export default {
  name: 'MyPhotos',
  components: {
    Uploader,
    ImageGallery
  },
  data() {
    return {
     show: false,
     photos: [],
     error: '',
   }
  },
  computed: {
    user() {
      return this.$root.$data.user;
    },
  },
  methods: {
    async logout() {
      try {
        await axios.delete("/api/users");
        this.$root.$data.user = null;
      } catch (error) {
        this.$root.$data.user = null;
      }
    },
    async getPhotos() {
      try {
        this.response = await axios.get("/api/photos");
        this.photos = this.response.data;
      } catch (error) {
        this.error = error.response.data.message;
      }
    },
    close() {
      this.show = false;
    },
    toggleUpload() {
      this.show = true;
    },
    async uploadFinished() {
      this.show = false;
      this.getPhotos();
    },
  },
  created() {
    this.getPhotos();
  },
}
</script>

<style scoped>
.menu {
  display: flex;
  justify-content: center;
}

.addPhotos {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px
}
</style>
