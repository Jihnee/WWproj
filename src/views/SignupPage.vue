<template>
  <layout>
    <template #content>
     <AdminSetupForm v-if="isSignUp" @submit="onSubmit"></AdminSetupForm>
    </template>
  </layout>
</template>

<script>
import axios from 'axios'
import Layout from '../components/Layout.vue'
import AdminSetupForm from '../components/AdminSetupForm.vue'
import { mapState, mapGetters } from 'vuex'

export default {
  name: 'SignupPage',
  components: {
    AdminSetupForm,
    Layout
  },
  computed: {
    ...mapState(['isTrueSignUp']),
    ...mapGetters(['isSignUp'])
  },
  methods: {
    onSubmit (payload) {
      console.log('payload: ' + payload.userId + ', ' + payload.userName + ', ' + payload.userPw)
      const { userId, userName, userPw, userCPw, Fex, Fartist } = payload
      axios.post('http://localhost:24688/users/setup', { userId, userName, userPw, userCPw, Fex, Fartist })
        .then(res => {
          alert('성공적으로 가입되었습니다. ')
          this.$router.push({
            name: 'Home'
          })
        })
        .catch(err => {
          alert(err.response.data)
        })
    }
  },
  created () {
    console.log('isTrueSignUp: ' + this.isTrueSignUp)
  }
}
</script>
