<template>
  <Layout>
    <v-container><br><br><br><br><br><br>
      <v-row>
        <v-col cols="12" sm="6">
          <v-text-field
            v-model="userid"
            label="ID"
            outlined
            clearable
            ></v-text-field>
        </v-col>

        <v-col cols="12" sm="6">
          <v-text-field
            v-model="password"
            label="PASSWORD"
            outlined
            clearable
            ></v-text-field>
        </v-col>
       <div class="text-center">
         <v-btn type="submit" rounded color="green lighten-2 white--text" style="margin-left: 1050px">SIGN IN</v-btn>
       </div>
      </v-row>
    </v-container>
  </Layout>
</template>

<script>
export default {
  name: 'LoginForm',
  data () {
    return {
      userid: '',
      password: ''
    }
  },
  methods: {
    submit () {
      console.log('LoginForm submit()')
      const { userid, password } = this
      this.$emit('submit', { userid, password })
    }
  }
}
</script>
