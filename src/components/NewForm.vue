<template>
  <v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col
          cols="12"
        >
          <v-text-field
            v-model="byline"
            :counter="10"
            label="Byline"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
        >
          <v-text-field
            v-model="summary_short"
            :counter="10"
            label="Summary short"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
        >
          <v-text-field
            v-model="display_title"
            :counter="10"
            label="Display title"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
        >
          <v-text-field
            v-model="publication_date"
            label="Publication date"
            type="date"
            required
          ></v-text-field>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
export default {
    data () {
        return {
            byline: '',
            summary_short: '',
            display_title: '',
            publication_date: ''
        }
    }
}
</script>