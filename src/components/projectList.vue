<template>
  <div id="project-list" role="tablist">
    <div v-for="p in projects" :key="p.title">
      <b-row role="tab" v-b-toggle="p.uniqueid">
        <b-col>
          <h2>{{ p.title }}</h2>
        </b-col>
        <b-col>
          <h2>{{ p.category }}</h2>
        </b-col>
        <b-col>
          <h2 class="float-right">{{ p.year }}</h2>
        </b-col>
      </b-row>
      <b-collapse
        :id="p.uniqueid"
        accordion="projects-accordeon"
        role="tabpanel"
      >
        <b-img-lazy
          height="30%"
          fluid
          src="https://picsum.photos/3840/1080"
        ></b-img-lazy>
        <p>{{ p.description }}</p>
      </b-collapse>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'projectList',
  data: () => ({
    projects: []
  }),
  async created() {
    const pl = await axios.get('projects.json');
    pl.data.projects.forEach(p => {
      p.uniqueid =
        'id' +
        Math.random()
          .toString(36)
          .substr(2, 9);
      this.projects.push(p);
    });
  }
};
</script>
