<template>
  <v-form
    v-model="valid"
    ref="form"
  >
    <v-container>
      <!-- Form Title -->
      <v-row>
        <v-col>
          <div class="title">Iniciar sesion</div>
        </v-col>
      </v-row>
      <!-- Form Inputs -->
      <v-row>
        <!-- Email input -->
        <v-col cols="12" md="4">
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>
        </v-col>
        <!-- Password input -->
        <v-col cols="12" md="4">
          <v-text-field
            v-model="password"
            :rules="passwordRules"
            label="Password"
            type="password"
            required
          ></v-text-field>
        </v-col>
        <!-- Submit Button -->
        <v-col>
          <v-btn color="indigo" class="mr-4" @click="check()">
            Sign In
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
export default {
  data: () =>  ({
    valid: true,
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+/.test(v) || "E-mail must be valid",
    ],
    password: "",
    passwordRules: [
      (v) => !!v || "Paaasword is required",
      (v) => v.length >= 8 || "Password must be at least than 8 characters",
    ],
  }),
  methods: {
    async check() {
      const valid = await this.$refs.form.validate()
      if (valid) {
        this.$router.push('/home')
      }
      else {
        alert('Invalid form')
      }
    }
  }
};
</script>

<style>
.title {
  font-size: 3rem;
  font-weight: 300;
}
</style>
