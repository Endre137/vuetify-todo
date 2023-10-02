<template>
  <v-app id="inspire">
    <v-navigation-drawer
        v-model="drawer"
        :mobile-breakpoint="768"
        app
      >
      <v-img
        class="pa-4"
        src="forest.jpg"
        height="170"
      >
        <v-avatar size="70">
          <img
            src="https://cdn.vuetifyjs.com/images/john.jpg"
            alt="John"
          >
        </v-avatar>
        <div class="white--text pt-5 text-subtitle-1 font-weight-bold">John Wick</div>
        <div class="white--text text-subtitle-2">johnny_w</div>
      </v-img>

        <v-list
          dense
          nav
        >
          <v-list-item
            v-for="item in items"
            :key="item.title"
            :to="item.to"
            link>
          
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
        color="teal-darken-4"
        dark
        src="forest.jpg"
        prominent
        :height="$route.path === '/' ?  '240' : '170' "
      >
        <template v-slot:image>
          <v-img
            gradient="to top right, rgba(19,84,122,.9), 
            rgba(128,208,199,.9)"
          ></v-img>
        </template>

        <v-container class="header-container pa-0">
          <v-row>
            <v-app-bar-nav-icon @click="drawer =!drawer"></v-app-bar-nav-icon>
            <v-spacer></v-spacer>
            <search></search>
          </v-row>
          <v-row>
            <v-app-bar-title class="text-h4 ml-5">
              {{ $store.state.appTitle }}</v-app-bar-title>
          </v-row>
          <v-row>
            <live-date-time/>
          </v-row>
          <v-row v-if="$route.path == '/'">
            <field-add-task></field-add-task>
          </v-row>
        </v-container>
        
      </v-app-bar>

    <v-main>
      <router-view></router-view>
      <snackbar/>
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref } from 'vue'

  const drawer = ref(null)
</script>

<script>
  export default {
    data: () => ({ 
      drawer: null,
      items: [
        {title : 'Todo', icon: 'mdi-format-list-checks', to: '/'},
        {title : 'About', icon: 'mdi-help-box', to: '/about'},
      ],
    }),
    components: {
      'search': require('@/components/Tools/Search.vue').default,
      'snackbar': require('@/components/Global/Snackbar.vue').default,
      'live-date-time': require('@/components/Tools/LiveDateTime.vue').default,
      'field-add-task': require('@/components/Todo/FieldAddTask.vue').
      default,
    },
    mounted(){
      this.$store.dispatch('getTasks')
    },
  }
</script>

<style lang="sass">
.header-container
  max-width: none !important
</style>