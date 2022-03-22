<template>
  <div class="Details">
    <h1>This is the page on which commit details will be shown.</h1>
    <GetCommitsExpanded/>
    <router-link to="/">Back to home</router-link>
    <router-view />
  </div>
</template>

<script>
// @ is an alias to /src
import GetCommitsExpanded from '@/components/GetCommitsExpanded.vue'

export default {
  props: ['sha'],
  name: 'Details',
  components: {
    GetCommitsExpanded
  }
}

</script>