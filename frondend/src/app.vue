<template>
  <base-layout>
    <router-view />
  </base-layout>
</template>

<script>
  /* ============
   * Entry Point
   * ============
   *
   * This is the entry point of the application.
   */
  import Base from './layouts/base.vue';
  import store from '@/store';
  import { router } from './bootstrap';

  export default {
    components: {
      'base-layout': Base
    },
    /**
     * The name of the application.
     */
    name: 'music-db',

    /**
     * The Vuex store.
     */
    store,

    /**
     * The router.
     */
    router,
  };
</script>
