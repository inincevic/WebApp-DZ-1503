<template>
  <div class="home">
    <HelloWorld msg="Welcome to an App that shows git commits."/>
    <GetCommits/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import GetCommits from '@/components/GetCommits.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    GetCommits
  }
}

</script>
