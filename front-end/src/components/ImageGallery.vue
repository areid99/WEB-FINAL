<template>
<div>
  <section class="image-gallery">
    <div class="image" v-for="photo in photos" v-bind:key="photo._id">
      <div class="photoInfo">
        <p> Name:  {{photo.name}}</p>
        <p> Owner: {{photo.user.firstName}} {{photo.user.lastName}}</p>
      </div>
      <img :src="photo.path" />

      <router-link :to="{name: 'Private', params: { id: photo._id }}"><button>Visit!</button></router-link>
      <button>Delete</button>
    </div>
  </section>
</div>
</template>

<script>


export default {
  name: 'ImageGallery',
  props: {
    photos: Array
  },
  methods: {
  }
}
</script>

<style scoped>
.photoInfo {
  background: #37FEE7;
  color: #000;
  padding: 0px;
  height: 80px;
  font-size: 20px;
  margin: 0px;
  justify-content: center;
}

.photoInfo p {
  margin: 0px;
}

p {
  margin: 0px;
}

/* Masonry */
*,
*:before,
*:after {
  box-sizing: inherit;
}

.image-gallery {
  column-gap: 1em;
  text-align: center;
}

.image {
  margin: 0 0 1.5em;
  display: inline-block;
  width: 100%;
}

.image img {
  width: 100%;
}

button {
  height: 50px;
  margin: 10px;
  background: #37DEFE;
  color: black;
  border: none;
  width: 95%
}

/* Masonry on large screens */
@media only screen and (min-width: 1024px) {
  .image-gallery {
    column-count: 3;
  }
}

/* Masonry on medium-sized screens */
@media only screen and (max-width: 1023px) and (min-width: 768px) {
  .image-gallery {
    column-count: 2;
  }
}

/* Masonry on small screens */
@media only screen and (max-width: 767px) and (min-width: 540px) {
  .image-gallery {
    column-count: 1;
  }
}
</style>
