<template>
    <v-card height="200" 
            class="movie pa-2">
        <h3 class="text-center movie-byline">{{ movie.byline }}</h3>
        <h5>{{ movie.summary_short }}</h5>
        <h4>{{ movie.display_title }}</h4>  
        <br>
            <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="purple darken-2"
          dark
          v-bind="attrs"
          v-on="on"
        >
          Details
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="text-h5 grey lighten-2">
          {{ movie.byline }}
        </v-card-title>

        <v-card-text>
            {{ movie.date_updated }}
        </v-card-text>

        <v-divider></v-divider>
      </v-card>
    </v-dialog>      
    </v-card>
</template>

<script>
export default {
    props: ['movie'],
    data () {
        return {
            dialog: false
        }
    }

}   
</script>

<style>
.movie {
    background: #9B59B6 !important;
}

.movie-byline {
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
}
</style>