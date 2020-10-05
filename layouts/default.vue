<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      fixed
      app
      style="
        background-image: url(https://fbi.dek-d.com/27/0352/8102/114445798);
        background-size: cover;
      "
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon class="white--text text--lighten-1">{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title
              class="white--text text--lighten-1"
              v-text="item.title"
            />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      fixed
      app
      style="
        background-image: url(https://fbi.dek-d.com/27/0352/8102/114445798);
        background-size: cover;
      "
    >
      <v-app-bar-nav-icon
        class="white--text text--lighten-1"
        @click.stop="drawer = !drawer"
      />
      <v-toolbar-title class="white--text text--lighten-1" v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer
      style="
        background-image: url(https://fbi.dek-d.com/27/0352/8102/114445798);
        background-size: cover;
      "
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>
<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-account',
          title: 'Napaporn Doklumpoo',
          to: '/',
        },
        {
          icon: 'mdi-music-circle',
          title: 'Music',
          to: '/Music',
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Music',
    }
  },
}
</script>
<style>
#app {
  background-image: url(https://fbi.dek-d.com/27/0352/8102/114445798);
  background-size: cover;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #0a0a0a;
  margin-top: 60px;
}
</style>
