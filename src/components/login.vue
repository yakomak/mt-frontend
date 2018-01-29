<template>
  <v-container fluid fill-height >
    <v-layout justify-center aligh-center color="green darken-2">
      <v-flex xs12 sm6>
        <v-card md6 color="green accent-1">
          <v-card-title>
            <v-layout justify-center aligh-center>
              <h2>MAGTOOL LOGIN</h2>
            </v-layout>
          </v-card-title>
          <v-card-text>
            <v-layout row>
              <v-flex xs4>
                <v-subheader>Username</v-subheader>
              </v-flex>
              <v-flex xs8>
                <v-text-field
                  name="username"
                  label="Enter your username"
                  v-model="username"
                ></v-text-field>
              </v-flex>
            </v-layout>
            <v-layout row>
              <v-flex xs4>
                <v-subheader>Password</v-subheader>
              </v-flex>
              <v-flex xs8>
                <v-text-field
                  name="password"
                  label="Enter your password"
                  v-model="password"
                  :append-icon="!showPassword ? 'visibility' : 'visibility_off'"
                  :append-icon-cb="() => (showPassword = !showPassword)"
                  :type="!showPassword ? 'password' : 'text'"
                ></v-text-field>
              </v-flex>
            </v-layout>
          </v-card-text>
          <v-card-actions class="text-xs-center">
            <v-layout justify-center aligh-center>
              <v-btn flat block @click="login">LOGIN</v-btn>
            </v-layout>
          </v-card-actions>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Login',
  data () {
    return {
      username: '',
      password: '',
      showPassword: false
    }
  },
  methods: {
    login () {
      axios.post('http://localhost:3000/login', {
        username: this.username,
        password: this.password
      }).then((res) => {
        if (res.data.status === 'OK') {
          console.log('Login OK', res.data)
          this.$router.push('/')
        } else {
          console.log('Login FAIL', res.data)
        }
      }).catch((err) => {
        console.log('Login FAIL', err)
      })
    }
  }
}
</script>
