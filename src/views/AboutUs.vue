<template>
  <layout>
    <template #content>
      <v-app id="layout">

          absolute
          color="#6A76AB"
          dark
          shrink-on-scroll
          prominent
          src="https://t1.daumcdn.net/cfile/blog/9922123D5B39985D0E"
          fade-img-on-scroll
          scroll-target="#scrolling-techniques-4"
       >
      </v-app>
    </template>
  </layout>
</template>

<script>
import Layout from '../components/Layout'

export default {
  name: 'AboutUs',
  components: {
    Layout
  }
}
</script>
