<template>
  <v-app>
    <v-main>
      <v-app-bar color="pink-darken-4">
        <v-app-bar-title>Alexandre Saillet</v-app-bar-title>

        <v-spacer />

        <v-btn icon="mdi-twitter" href="https://twitter.com/Moutard3" target="_blank"></v-btn>
        <v-btn icon="mdi-linkedin" href="https://linkedin.com/in/alexandresaillet" target="_blank"></v-btn>
      </v-app-bar>

      <v-container>
        <ProjectsGrid @project-clicked="onProjectClicked" :projects="projects" />
        <ProjectDialog @close-dialog="isProjectDialogActive = false" :project="projects[activeProject]" :active="isProjectDialogActive" />
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import {ref} from "vue";
import ProjectsGrid from "/@/components/ProjectsGrid.vue";
import ProjectDialog from "/@/components/ProjectDialog.vue";
import allProjects from "/@/assets/projects.json";

const activeProject = ref(0);
const isProjectDialogActive = ref(false);

const projects = allProjects.filter(project => project.display);

function onProjectClicked(projectId: number) {
  activeProject.value = projectId;
  isProjectDialogActive.value = true;
}
</script>
