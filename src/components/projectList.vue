<template>
  <div id="project-list">
    <div v-for="p in projects" :key="p.title">
      <b-row>
        <b-col>{{ p.title }}</b-col>
        <b-col>{{ p.category }}</b-col>
        <b-col
          ><div class="float-right">{{ p.year }}</div></b-col
        >
      </b-row>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'projectList',
  data: () => ({
    projects: []
  }),
  async created () {
    const pl = await axios.get('projects.json')
    pl.data.projects.forEach(p => this.projects.push(p))
  }
}
</script>
