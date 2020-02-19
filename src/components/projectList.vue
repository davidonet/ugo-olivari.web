<template>
  <div id="project-list">
    <b-table :items="projects" :fields="fields" small>
      <template v-slot:cell(title)="row">
        <span @click="row.toggleDetails">
          {{ row.item.title }}
        </span>
      </template>
      <template v-slot:row-details="row">
        <h3>{{ row.item.title }}</h3>
        {{ row.item.description }}
      </template>
      <template v-slot:cell(year)="data">
        <div class="float-right">
          {{ data.item.year }}
        </div>
      </template>
    </b-table>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'projectList',
  data: () => ({
    transProps: {
      name: 'flip-list'
    },
    projects: [],
    fields: ['title', 'category', 'year']
  }),
  async created () {
    const pl = await axios.get('projects.json')
    for (const p in pl.data.projects) {
      pl.data.projects[p]._showDetails = false
      this.$set(this.projects, p, pl.data.projects[p])
    }
  }
}
</script>

<style>
thead {
  display: none;
}
table .flip-list-move {
  transition: transform 1s;
}
</style>
