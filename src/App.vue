<template>
  <v-app>
    <v-toolbar app class="elevation-3">
      <v-toolbar-title class="headline text-uppercase">
        <span>Jeremy Poole</span>
        <span class="font-weight-light ml-2">Resumé</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        flat
        href="https://jeremypoole.ca"
        title="Back to JeremyPoole.ca"
        target="_blank"
        icon
        large
      >
        <!-- <span class="mr-2">JeremyPoole.ca</span> -->
        <v-img
          :src="require('./assets/resume.png')"
          alt="Cartoon icon of Jeremy Poole"
        >
        </v-img>
      </v-btn>
    </v-toolbar>

    <v-content>
      <Resume />

      


    </v-content>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
import Resume from './components/resume.vue'

export default {
  name: 'App',
  components: {
    Resume
    
  },
  data () {
    return {
      //
    }
  }
}
</script>

<style>
body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>
