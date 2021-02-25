<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      :mobile-breakpoint="768"
      app
    >
       <v-img
         class="pa-4 pt-7"
         src="fondo.jpg"
         height="238"
       >
         <v-avatar size="140" class="mb-2">
      <img
        src="foto.jpg"
        alt="Eduardo Gutierrez"
      >
        </v-avatar>
        <div class="white--text text-subtitle-1 font-weight-bold">Eduardo Gutierrez</div>
        <div class="blue--text text-subtitle-2">EduardoGtz</div>
       </v-img>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="cyan"
      dark
      prominent
      height="238"
    >
      <v-container class="header-container pa-0">
        <v-row>
          <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
          <v-spacer></v-spacer>
          <search />
        </v-row>
        <v-row>
          <v-toolbar-title class="text-h4 ml-4">
            {{ $store.state.appTitle }}
          </v-toolbar-title>
        </v-row>
         <v-row>
          <live-date-time/>
         </v-row>

         <v-row >
        <field-add-task />
         </v-row>
      </v-container>
   
    </v-app-bar>
    
    <v-main>
      <router-view></router-view>
      <snackbar />
    </v-main>
  </v-app>
</template>

<script>
import FieldAddTask from './components/Todo/FieldAddTask.vue'
  export default {
    data: () => ({
      drawer: null,
      items: [
        { title: 'Inicio', icon: 'mdi-format-list-checks', to: '/' },
        { title: 'Historia', icon: 'mdi-help-box', to: '/about' },
      ],
    }),
    computed: {
     appTitle() {
       return process.env.VUE_APP_TITLE
     }
    },
    mounted() {
     this.$store.dispatch('getTasks')
    },
    components: {
      'search': require('@/components/Tools/Search.vue').default,
      'live-date-time': require('@/components/Tools/LiveDateTime.vue').default,
      'field-add-task': require('@/components/Todo/FieldAddTask.vue').default,
      'snackbar': require('@/components/Shared/Snackbar.vue').default,
        FieldAddTask
    }
  }
</script>
       
<style lang="sass" scoped>
 .header-container
  max-width: none !important
</style>