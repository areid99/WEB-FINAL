<template>
<div class = "page">
 <img :src="photo.path" />
 <p> Name:  {{photo.name}}</p>
 <p> Age:  {{photo.age}}</p>
 <p> Owner:  {{photo.user.firstName}} {{photo.user.lastName}}</p>
 <p> Description:  {{photo.description}}</p>
</div>

</template>

<script>
import axios from 'axios';
export default {

  data() {
    return {
      photo: "",
    }
  },
methods: {
  async getPhoto() {
      try {
        let response = await axios.get("/api/photos/" + this.$route.params.id);
        this.photo = response.data;
        return true;
      } catch (error) {
        //console.log(error);
      }
    },
  },
  created() {
    this.getPhoto();
  },
}


</script>

<style scoped>
.dashboard {
  padding-top: 10px;
}
.page {
  text-align: center;
}
img {
  border: 2px solid #333;
  height: 500px;
  width: 60%;
  object-fit: cover;
}
</style>
