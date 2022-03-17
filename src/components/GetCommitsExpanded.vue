<template>
  <div id="app">
    <ul id="example-1">
        <li v-for="commit in this.commits" :key="commit">
            <p>{{ commit.sha }}</p>
            <p>{{ commit.commit.author.name }}</p>
            <p>{{ commit.commit.author.email }}</p>
            <p>{{ commit.commit.message }}</p>
            <p>{{ commit.commit.author.date }}</p>
        </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'GetCommitsExpanded',
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