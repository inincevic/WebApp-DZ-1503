<template>
  <div id="app">
    <ul id="example-1">
        <li v-for="commit in this.commits" :key="commit">
            {{ commit.sha }}
        </li>
    </ul>
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
                } catch (error) {
                    console.log(error);
                }
            },
            parseData() {
                console.log(commits);
            }
        },

        created() {
            this.getData();
        }
}
</script>