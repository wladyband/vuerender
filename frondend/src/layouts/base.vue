<template>
  <div>
    <v-header>
      <v-toolbar>
        <v-nav-icon @click.native="toggleDrawer" />
        <v-toolbar-title>Music DB</v-toolbar-title>
        <v-toolbar-actions>
          <v-toolbar-action>
            <v-icon>exit_to_app</v-icon>
          </v-toolbar-action>
        </v-toolbar-actions>
      </v-toolbar>
      <transition name="slide-left">
        <v-drawer v-if="drawerActive">
          <v-drawer-header>
            <v-nav-icon
              variant="green"
              @click.native="toggleDrawer"
            />
            <v-drawer-title>Music DB</v-drawer-title>
          </v-drawer-header>
          <v-drawer-body>
            <v-navigation>
              <v-navigation-item>
                <v-navigation-link :route="{ name: 'artists.index' }">
                  <v-navigation-content>Artists</v-navigation-content>
                </v-navigation-link>
                <v-navigation-link :route="{ name: 'albums.index' }">
                  <v-navigation-content>Albums</v-navigation-content>
                </v-navigation-link>
                <v-navigation-link :route="{ name: 'songs.index' }">
                  <v-navigation-content>Songs</v-navigation-content>
                </v-navigation-link>
              </v-navigation-item>
            </v-navigation>
          </v-drawer-body>
          <v-drawer-footer>For educational purposes only</v-drawer-footer>
        </v-drawer>
      </transition>
    </v-header>
    <v-content>
      <!-- The content of the page will be placed here -->
      <router-view></router-view>
    </v-content>
    <transition name="fade">
      <v-overlay
        v-show="drawerActive"
        @click.native="hideDrawer"
      />
    </transition>
  </div>
</template>
<script>
  export default {
    /**
     * The name of the layout.
     */
    name: 'base-layout',

    data() {
      return {
        drawerActive: false,
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
    },
  };
</script>
