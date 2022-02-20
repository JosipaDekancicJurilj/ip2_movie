<template>
  <div class="about">
    <br><h1 align="center">OVO JE STRANICA O FILMOVIMA</h1>
    <br>
    <br><h3 align="center">Josipa Dekančić Jurilj i Evelina Kopić - studentice Informatike iz Orašja</h3>
    <br>
    <v-carousel>
      <v-carousel-item
        v-for="(item,i) in items"
        :key="i"
        :src="item.src"
        reverse-transition="fade-transition"
        transition="fade-transition"
      ></v-carousel-item>
    </v-carousel>
  </div>
</template>

<style>
.about {
  background-color: rgb(184, 132, 184);
}
</style>

<script>
  export default {
    data () {
      return {
        items: [
          {
            src: 'https://cdn.vox-cdn.com/thumbor/_8V9avzpSWPt1TDLG_6bETpiTh8=/0x0:400x400/1200x1200/filters:focal(0x0:400x400):no_upscale()/cdn.vox-cdn.com/uploads/chorus_asset/file/20020623/1a8a99062e9b06a371ceaef3737ce58c3cf77f7f601380d6f442476ef17eacdd83c2803a72555ed28c0342b0583cb5ede20afa229e2909e87349b46b24cbe8da.0.jpeg',   
          },
          {
            src: 'https://s3-us-west-2.amazonaws.com/prd-rteditorial/wp-content/uploads/2018/03/13153742/RT_300EssentialMovies_700X250.jpg',
          },
          {
            src: 'https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/fall-movies-index-1628968089.jpg?crop=0.470xw:1.00xh;0.353xw,0&resize=640:*',
          },
          {
            src: 'https://m.media-amazon.com/images/M/MV5BNzU4NWEwNDItMzMzYy00ZDYyLWIxZjMtMDlkYWVjNjQwYzBjXkEyXkFqcGdeQXVyMDM2NDM2MQ@@._V1_FMjpg_UX1000_.jpg',
          },
        ],
      }
    },
  }
</script>