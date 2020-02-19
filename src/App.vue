<template>
  <div id="app">
    <b-container fluid>
      <b-row>
        <b-col>ugo olivari</b-col>
        <b-col><div class="text-center">graphic design</div></b-col>
        <b-col><div class="float-right">contact@ugo-olivari.me</div></b-col>
      </b-row>
      <project-list></project-list>
    </b-container>
  </div>
</template>

<script>
import projectList from './components/projectList'
export default {
  name: 'App',
  components: { projectList }
}
</script>
