<template>
  <v-app>
    <v-overlay :value="loading" z-index="9999">
      <v-progress-circular
        indeterminate
        size="64"
        width="8"
      ></v-progress-circular>
    </v-overlay>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      title: 'Day Slot Machine',

      loading: true
    }
  },
  mounted() {
    this.loading = false
  }
}
</script>
