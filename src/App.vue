<template>
  <v-app>
    <v-main>
      <VowGuide />
    </v-main>
  </v-app>
</template>

<script>
import VowGuide from './components/VowGuide';

export default {
  name: 'App',

  components: {
    VowGuide,
  },

  data: () => ({
    //
  }),
};
</script>
