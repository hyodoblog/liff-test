<template lang="pug">
  v-app(dark)
    | {{ profile }}
    v-main
      nuxt
</template>

<script lang="ts">
import liff from '@line/liff'
import { Component, Vue } from 'nuxt-property-decorator'

@Component
export default class extends Vue {
  private profile: any

  async mounted() {
    try {
      const liffId = '1654961912-qa6xmKz1'
      await liff.init({ liffId })
      this.profile = await liff.getProfile()
    } catch (err) {
      this.profile = err
      console.error(err)
    }
  }
}
</script>
