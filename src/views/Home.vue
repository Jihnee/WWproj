<template>
  <div>
    <Layout>
      <template #content>
        <AdminSetupForm v-if="isSignUp" @submit="onSubmit"></AdminSetupForm>
      </template>
    </Layout>
  </div>
</template>

<script>
// import axios from 'axios'
import Layout from '../components/Layout'
import { mapState, mapActions, mapGetters } from 'vuex'

export default {
  data: function () {
    return {
    }
  },
  components: { Layout },
  methods: {
    onClickLogout () {
      this.logout()
      alert('Success Logout')
      this.$router.push({ name: 'Home' })
    },
    ...mapActions(['logout'])
  },
  computed: {
    ...mapState(['myinfo']),
    ...mapGetters(['isAuthorized'])
  }
}
</script>
