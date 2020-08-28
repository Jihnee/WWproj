<template>
  <div>
    <v-app id="layout">
      <v-app-bar
        absolute
        color="#6A76AB"
        dark
        shrink-on-scroll
        prominent
        src="https://t1.daumcdn.net/cfile/blog/9922123D5B39985D0E"
        fade-img-on-scroll
        scroll-target="#scrolling-techniques-4"
      >
        <template v-slot:img="{ props }">
          <v-img
            v-bind="props"
            gradient="to top right, rgba(100,115,201,.7), rgba(25,32,72,.7)"
          ></v-img>
        </template>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title class="text-uppercase white--text">WWEB White Web </v-toolbar-title>
        <slot name="menubar"></slot>
        <v-spacer></v-spacer>
        <v-btn id="home" @click='home'
          text color="white" style="padding: 10px 75px; width: 90px;">HOME</v-btn>
        <v-btn @click='aboutUs' text color="white"
          style="padding: 10px 80px; width: 90px;">ABOUT US</v-btn>
        <v-btn @click="start('wExhibition')" text color="white"
          style="padding: 10px 100px; width: 90px;">WW EXHIBITION</v-btn>
        <v-btn @click="start('information')" text color="white"
          style="padding: 10px 85px; width: 90px;">INFORMATION</v-btn>
        <v-btn @click="start('Bgallery')" text color="white"
          style="padding: 10px 100px; width: 90px;">BOARD GALLERY</v-btn>
        <div class="home">
          <v-btn id="login" @click="$router.push('SignupPage')"
           rounded color="lime darken-2 white--text" style="margin-left: 280px; margin-top: 7px" >
            SIGN UP
          </v-btn>
        </div>
        <v-btn @click="$router.push('LoginPage')"
          rounded color="lime darken-2 white--text" style="margin-right: 65px; margin-left: 10px;
                                                                                   margin-top: 7px">
         LOGIN
        </v-btn>
      </v-app-bar>
      <v-navigation-drawer
        v-model="drawer"
        app
      >
        <v-list dense>
          <v-list-item @click.stop="left = !left">
            <v-list-item-action>
              <v-icon>mdi-exit-to-app</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title @click="home">Home</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-container>
        <v-content id="content">
         <slot name="content" class="font">
          </slot>
        </v-content>
      </v-container>
    </v-app>
  </div>
</template>

<script>
import router from '../router'

export default {
  name: 'Layout',
  data: () => ({
    drawer: false,
    left: false
  }),
  methods: {
    home () {
      (window.location.pathname !== '/') ? router.push('/') : router.go(0)
    },
    aboutUs () {
      (window.location.pathname !== '/AboutUs') ? router.push('/AboutUs') : router.go(0)
    }
  }
}
</script>
