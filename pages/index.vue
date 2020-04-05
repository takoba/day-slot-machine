<template>
  <v-container fluid px-4 py-8>
    <h1>Day Slot Machine</h1>
    <v-row justify="center" align="center">
      <v-col cols="4">
        <span class="display-4 d-block text-center">{{ drawed.year() }}</span>
      </v-col>
      <v-col cols="1">
        <span class="display-4 d-block text-center">/</span>
      </v-col>
      <v-col cols="3">
        <span class="display-4 d-block text-center">{{
          drawed.month() + 1
        }}</span>
      </v-col>
      <v-col cols="1">
        <span class="display-4 d-block text-center">/</span>
      </v-col>
      <v-col cols="3">
        <span class="display-4 d-block text-center">{{ drawed.date() }}</span>
      </v-col>
    </v-row>
    <v-row justify="center" align="center">
      <v-col cols="12">
        <v-btn x-large class="mx-auto d-block" @click="draw">
          Draw
        </v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import dayjs from 'dayjs'

export default {
  data() {
    const start = dayjs('1865-01-01').startOf('day')
    const end = dayjs().startOf('day')
    return {
      start,
      end,
      drawed: null
    }
  },
  created() {
    this.draw()
  },
  methods: {
    draw() {
      const diff = this.end.diff(this.start, 'day')
      const drawing = Math.floor(Math.random() * diff)
      this.drawed = this.start.add(drawing, 'day')
    }
  }
}
</script>
