<template>
  <v-container>
    <v-row>
      <v-col>
      <v-dialog
          v-model="addDialog"
          width="500"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
              color="purple lighten-2"
              dark
              v-bind="attrs"
              v-on="on"
          >
            Add new movie
          </v-btn>
        </template>

        <v-card>
          <v-card-title class="text-h5 grey lighten-2">
            Add new movie
          </v-card-title>

          <v-card-text>
            <new-form></new-form>
          </v-card-text>

          <v-divider></v-divider>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="primary"
              text
              @click="addDialog = false"
            >
              Submit
            </v-btn>
          </v-card-actions>
         </v-card>
      </v-dialog>>
    </v-col>
      <v-alert type="success">
        Successfuly saved.
      </v-alert>
    </v-row>
    <v-row>
      <v-col cols="12" md="4">
        <v-text-field
            v-model="search"
            append-icon="mdi-magnify"
            label="Search by byline"
            single-line
            hide-details
            :loading="isLoading"
        ></v-text-field>
      </v-col>
        <v-col cols="12" md="4">
          <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search by summary_short"
              single-line
              hide-details
              :loading="isLoadingSummary_short"
          ></v-text-field>
      </v-col>
      <v-col cols="12" md="4">
        <v-text-field
            v-model="summary_short"
            append-icon="mdi-magnify"
            label="Search by display_title"
            single-line
            hide-details
            :loading="isLoadingDisplay_title"
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col
          v-for="movie in movies"
          :key="movie.byline"
          cols="12"
          md="3"
      >
        <movie :movie="movie"></movie>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols='12'>
        <v-pagination
            v-model="page"
            :length="totalMovies/perPage"
            circle
        ></v-pagination>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  //import HelloWorld from '../components/HelloWorld'
  import Movie from "../components/Movie";
  import NewForm from '../components/NewForm.vue';
  export default {
    name: 'Home',

    components: {
      Movie,
      NewForm
    },

    data() {
      return {
        test: 'Testna varijabla',
        movies: [],
        page: 1,
        totalMovies: 0,
        perPage: 20,
        search: '',
        summary_short: '',
        display_title: '',
        isLoading: false,
        isLoadingSummary_short: false,
        isLoadingDisplay_title: false,
        addDialog: false
      }
    },

    created() {
      console.log('created')
      this.getData();
    },
    methods: {
      getData() {
        let api = "https://api.nytimes.com/svc/movies/v2/reviews/all.json"
        this.axios.get(api,  {
          params: {
            'api-key': 'xLDQGV1MWD5HVxMMvcsyp4cGXG289Te2',
            'offset': 20 * (this.page - 1),
            'byline': this.search,
            'summary_short': this.summary_short,
            'display_title': this.display_title
          }
        }).then((response) => {
          console.log(response.data)
          this.movies = response.data.results
          this.totalMovies = response.data.num_results
          this.isLoading = false
          this.isLoadingSummary_short = false
          this.isLoadingDisplay_title = false
        })
      },
      fetchEntriesDebounced() {
        clearTimeout(this._searchTimerId)
        this._searchTimerId = setTimeout(  () => {
          this.getData()
        }, 500) /* 500ms throttle */
      },
    },

    watch: {
      search (val) {
        if (!val) {
          return
        }

        this.movies = []
        this.page = 1
        this.siLoading = true
        this.searchEntries()
      },
      summary_short (val) {
        if (!val) {
          return
        }

        this.movies = []
        this.page = 1
        this.siLoadingSummary_short = true
        this.searchentries();
      },
      display_title (val) {
        if (!val) {
          return
        }

        this.movies = []
        this.page = 1
        this.siLoadingDisplay_title = true
        this.searchentries();
      }
    }


    //components: {
    //  HelloWorld,
    //},



  }
</script>
