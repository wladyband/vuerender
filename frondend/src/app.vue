<template>
  <router-view />
</template>

<script>
  /* ============
   * Entry Point
   * ============
   *
   * This is the entry point of the application.
   */
  import store from '@/store';
  import { router } from './bootstrap';

  export default {
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
