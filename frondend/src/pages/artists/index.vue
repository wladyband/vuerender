<template>
  <div>
    <v-layout>
      <v-grid variant="container">
        <v-row variant="xs-center">
          <v-col :variants="['xs-9', 'md-4', 'lg-3']">
            <v-card>
              <v-card-body>
                <v-form @submit.prevent.native="setQuery(query)">
                  <v-input-group>
                    <v-icon variant="signifier">search</v-icon>
                    <v-text-field
                      variant="with-signifier"
                      v-model="query"
                      placeholder="Find artist"
                    />
                  </v-input-group>
                </v-form>
              </v-card-body>
            </v-card>
          </v-col>
          <v-col :variants="['xs-3', 'md-4', 'lg-3', 'md-offset-4', 'lg-offset-6']">
            <v-button
              variant="circle"
              class="pull-right"
              @click.native="redirectToCreatePage"
            >
              <v-icon>add</v-icon>
            </v-button>
          </v-col>
        </v-row>
        <v-row>
          <v-col variant="sm">
            <v-table>
              <v-table-header>
                <v-table-row>
                  <v-table-head>Name</v-table-head>
                  <v-table-head>Birthday</v-table-head>
                </v-table-row>
              </v-table-header>
              <v-table-body>
                <v-table-row
                  v-for="artist in artist.all"
                  :key="artist"
                  variant="body"
                >
                  <v-table-cell>
                    <router-link :to="getArtistRoute(artist.id)">{{ artist.fullName }}</router-link>
                  </v-table-cell>
                  <v-table-cell>{{ artist.birthday }}</v-table-cell>
                </v-table-row>
                <v-table-row v-if="artist.all.length === 0">
                  <v-table-cell colspan="3">Artists not found...</v-table-cell>
                </v-table-row>
              </v-table-body>
            </v-table>
          </v-col>
        </v-row>
        <v-row>
          <v-col variant="xs-justify">
            <v-card variant="inline">
              <v-card-body>
                <v-pagination
                  :pagination="artist.pagination"
                  :switch-page-function="setPage"
                  variant="small"
                />
              </v-card-body>
            </v-card>
            <v-card variant="inline">
              <v-card-body>
                <v-select
                  v-model="artist.pagination.limit"
                  :items="pageNumbers"
                />
              </v-card-body>
            </v-card>
          </v-col>
        </v-row>
      </v-grid>
    </v-layout>
  </div>
</template>
<script>
  import VLayout from '@/layouts/base.vue';

  export default {
    /**
     * The name of the layout.
     */
    name: 'artist-index',

    components: {
      'v-layout': VLayout
    },

    data() {
      return {
        artist: {
          all: [],
          pagination: {
            totalCount: 0,
            totalPages: 0,
            currentPage: 1,
            limit: 5,
          },
        },
        drawerActive: false,
        query: null,
        pageNumbers: [
          5,
          10,
          15,
        ],
      };
    },

    /**
     * The methods which the layout can use.
     */
    methods: {
      /**
       * Method used to hide the drawer.
       */
      hideDrawer() {
        this.drawerActive = false;
      },

      /**
       * Method used to toggle the drawer.
       */
      toggleDrawer() {
        this.drawerActive = !this.drawerActive;
      },

      /**
       * Method used to get the artist route.
       *
       * @param {Number} id The artist identifier.
       *
       * @returns {Object} The artist route.
       */
      getArtistRoute() {
        // todo
      },

      /**
       * Method used to redirect the user to the artist create page.
       */
      redirectToCreatePage() {
        // todo
      },

      /**
       * Method used to go to a different page.
       *
       * @param {Number} page The page number.
       */
      setPage() {
        // todo
      },

      /**
       * Method used to set the limit of the items being displayed.
       *
       * @param {Number} limit The limit of items being displayed.
       */
      setLimit() {
        // todo
      },

      /**
       * Method used to set the query of the search bar.
       * The results will be debounced using the lodash debounce method.
       */
      setQuery() {
        // todo
      },
    },

    /**
     * Available watchers for this page.
     */
    watch: {
      query(query) {
        this.setQuery(query);
      },
    },
  };
</script>
