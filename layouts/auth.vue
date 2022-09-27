<template>
  <v-app dark>
    <v-main aling="center" class="my-auto">
      <v-container class="fill-height">
        <v-row justify="center" align="center" class="rounded">
          <v-col v-if="$vuetify.breakpoint.mdAndUp" cols="6" class="fill-height light-blue lighten-1 rounded-l">
          </v-col>
          <v-col :cols="$vuetify.breakpoint.mdAndUp ? '6' : '12'">
            <v-row justify="center" align="center">
                <Nuxt />
            </v-row>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>
<script>
export default {
  name: "Login",
  layout: "auth",
 
}
</script>
<style lang="sass" scoped>
.row
  height: 31.25rem,
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px,

.container 
  max-width: 90vh,
</style>
