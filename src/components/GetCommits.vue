<template>
  <div id="app">
    {{ this.commits }}
  </div>
</template>

<script>
import axios from 'axios';



export default {
  name: 'GetCommits',
  props: {
    url: URL
  },
  data() {
        return { commits: [] }
    },
        methods: {
            async getData() {
            try {
                const response = await axios.get(
                "https://api.github.com/repos/vuejs/vue/commits"
                );
                this.commits = response.data;
                console.log(this.commits);
            } catch (error) {
                console.log(error);
            }
            },
        },

        created() {
            this.getData();
        }
}
</script>