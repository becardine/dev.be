<template>
  <v-col cols="8">
    <h1>Login</h1>
    <p>Tenha o controle de tudo que você precisa simples e rápido.</p>
    <v-form
      ref="form"
      v-model="valid"
      lazy-validation
      @submit.prevent="userLogin"
    >
      <v-text-field
        v-model="login.email"
        :rules="emailRules"
        label="E-mail"
        required
      ></v-text-field>

      <v-text-field
        v-model="login.password"
        :rules="passwordRules"
        label="Senha"
        required
      ></v-text-field>

      <v-btn :disabled="!valid" block color="primary" class="mt-3" type="submit" rounded>
        Entrar
      </v-btn>
      <p class="mt-3 text-caption">
        Para se cadastrar, <nuxt-link to="/cadastre-se">clique aqui</nuxt-link>.
      </p>
    </v-form>
  </v-col>
</template>

<script>
export default {
  name: "Login",
  layout: "auth",
  data: () => ({
    login: {
      email: "",
      password: "",
    },
    valid: true,
    passwordRules: [
      (v) => !!v || "Password is required",
      (v) => (v && v.length >= 6) || "Password must be less than 6 characters",
    ],
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
  }),
  methods: {
    /*     reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    }, */
    async userLogin() {
      this.$refs.form.validate();
      this.$router.push('/dashboard/')
      /* try {
        //let response = await this.$auth.loginWith('local', { data: this.login })
        this.$refs.form.reset();
        console.log(response)
      } catch (err) {
        console.log(err)
      } */
    },
  },
};
</script>
