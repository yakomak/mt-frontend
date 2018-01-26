<template>
  <v-contaner fluid fill-height>
    <v-layout justify-center aligh-center>
      <v-card>
        <v-card-title>
          <h1>Login</h1>
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
                hint="At least 8 characters"
                v-model="password"
                min="8"
                :append-icon="!showPassword ? 'visibility' : 'visibility_off'"
                :append-icon-cb="() => (showPassword = !showPassword)"
                :type="!showPassword ? 'password' : 'text'"
              ></v-text-field>
            </v-flex>
          </v-layout>
        </v-card-text>
      </v-card>
    </v-layout>
  </v-contaner>
</template>
