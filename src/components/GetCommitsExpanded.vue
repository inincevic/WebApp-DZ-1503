<template>
  <div id="app">
    <ul id="example-1">
        <li> {{ commit.sha }} </li>
        <li> {{ commit.commit.author.name }} </li>
        <li> {{ commit.commit.author.email }} </li>
        <li> {{ commit.commit.message }} </li>
        <li> {{ commit.commit.author.date }} </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'GetCommitsExpanded',
  props: {
  },
  data() {
        return { commit: {} }
  },
  methods: {
            async getData() {
            try {
                const response = await axios.get(
                "https://api.github.com/repos/vuejs/vue/commits"
                );
                return response.data;
                } catch (error) {
                    console.log(error);
                }
            },
            parseData() {
                console.log(commits);
            }
  },
  created() {
            //this.getData();
            this.getData().then(
              (data) => {
                this.commit = data.find(
                  (commit) => commit.sha === localStorage.getItem("requestedCommit")
                );
                console.log(this.commit)
              }
            );
  
  }
}
</script>