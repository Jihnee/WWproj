<template>
  <v-form><br><br><br><br><br><br><br><br><br>
    <v-container>
      <v-row>
        <v-col cols="12" sm="3">
          <v-text-field
            value=""
            label="ID "
            input type="text" v-model="userId"
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="3">
          <v-text-field
            value=""
            label="Name "
            input type="text" v-model="userName"
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="3">
          <v-text-field
            value=""
            label="Password "
            input type="password" v-model="userPw"
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="3">
          <v-text-field
            value=""
            label="Confirmation Password "
            input type="password" v-model="userCPw"
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="12">
          <v-text-field
            value=""
            label="가장 인상깊게 본 전시를 적어주세요"
            input type="text" v-model="Fex"
            :rules="[rules.required, rules.counter]"
            counter
            maxlength="50"
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="12">
          <v-text-field
            value=""
            label="좋아하는 아티스트를 적어주세요"
            input type="text" v-model="Fartist"
            :rules="[rules.required, rules.counter]"
            counter
            maxlength="50"
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="12">
          <v-text-field
            value=""
            label="E-mail address"
            input type="email" v-model="userE"
            :rules="[rules.required, rules.email]"
          ></v-text-field>
        </v-col>
      </v-row>
    </v-container>
    <div>
    <v-btn type="submit" color="red white--text">가입하기 </v-btn>
    </div>
  </v-form>
</template>

<script>
export default {
  name: 'AdminSetupForm',
  data () {
    return {
      userId: '',
      userName: '',
      userPw: '',
      userCPw: '',
      Fex: '',
      Fartist: '',
      email: '',
      rules: {
        required: value => !!value || 'Required.',
        counter: value => value.length <= 50 || 'Max 50 characters',
        email: value => {
          const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
          return pattern.test(value) || 'Invalid e-mail.'
        }
      },
      methods: {
        submit (payload) {
          console.log('this: ' + this.userId + ', ' + this.userName + ', ' + this.userPw)
          const { userId, userName, userPw, userCPw, Fex, Fartist } = this
          this.$emit('submit', { userId, userName, userPw, userCPw, Fex, Fartist })
        }
      }
    }
  }
}
</script>
