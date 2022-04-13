<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :clipped="clipped"
      fixed
      color="deep-orange" 
      dark
      app
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
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app color="deep-orange" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      </v-btn>  
      <v-toolbar-title v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-home-modern',
          title: 'Beranda',
          to: '/',
        },
        {
        icon: 'mdi-filmstrip-box-multiple',
          title: 'Film Terpopuler',
          to: '/movieNew',
        },
        {
        icon: 'mdi-filmstrip-box',
          title: 'Yang Akan Datang',
          to: '/upcomingMovie',
        },
        
      ],
      rightDrawer:true ,
      title: 'Ruang Film',
    }
  },
}
</script>