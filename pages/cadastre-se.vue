<template>
  <v-col cols="9">
    <h1>Cadastre-se</h1>
    <p>Tenha o controle de tudo que você precisa simples e rápido.</p>
    <v-form
      ref="form"
      v-model="valid"
      lazy-validation
      @submit.prevent="userSignUp"
    >
      <v-text-field
        v-model="signUp.name"
        :rules="nameRules"
        label="Nome"
        required
      ></v-text-field>
      <v-text-field
        v-model="signUp.email"
        :rules="emailRules"
        label="E-mail"
        required
      ></v-text-field>

      <v-text-field
        v-model="signUp.password"
        :rules="passwordRules"
        label="Senha"
        required
      ></v-text-field>
      <v-checkbox
        v-model="signUp.termAs"
        :rules="termAsRules"
        label="Concordo com os termos de uso"
        required
      ></v-checkbox>
      <v-btn :disabled="!valid" type="submit" block color="primary" class="mt-2" rounded>
        Cadastrar
      </v-btn>
      <p mt-3 text-caption>
      <p class="mt-3 text-caption">
        Caso já tenha se cadastrado, <nuxt-link to="/">clique aqui</nuxt-link>.
      </p>
    </v-form>
  </v-col>
</template>

<script>
export default {
  name: "Login",
  layout: "auth",
  data: () => ({
    signUp: {
      name: "",
      email: "",
      password: "",
      termAs: false,
    },
    valid: true,
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => (v && v.length >= 6) || "Name must be at least 6 characters long",
    ],
    passwordRules: [
      (v) => !!v || "Password is required",
      (v) => (v && v.length >= 6) || "Password must at least 6 characters long",
    ],
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
    termAsRules: [(v) => !!v || "Terms is required"],
  }),
  methods: {
    /*     reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    }, */
    async userSignUp() {
      if (this.$refs.form.validate()) {
        this.$router.push("/");
      }
      /* try {
        console.log(this.signUp);
        this.$refs.form.reset();
      } catch (err) {
        console.log(err)
      } */
    },
  },
};
</script>
