/* eslint-disable */
<template>
  <div>
    <v-layout>
      {{ pageName }}
    </v-layout>
  </div>
</template>
<script>
  import VLayout from '@/layouts/base.vue';

  export default {

    components: {
      'v-layout': VLayout
    },

    data() {
      return {
        pageName: 'albums.index',
      };
    },
  };
</script>
