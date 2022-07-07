<template>
  <v-row>
    <template v-for="(project, i) of props.projects" :key="i">
      <v-col cols="12" md="6" lg="4">
        <v-hover v-slot="{ isHovering, props }">
          <v-card :elevation="isHovering ? 12 : 2" v-bind="props">
            <v-img :src="`/img/projets/${project.img}`" cover />

            <v-overlay
                :model-value="isHovering"
                contained
                scrim="pink-darken-4"
                class="align-center justify-center"
                scroll-strategy="none"
            >
              <v-btn flat @click.stop="emits('project-clicked', i)">
                En savoir plus
              </v-btn>
            </v-overlay>
          </v-card>
        </v-hover>
      </v-col>
    </template>
  </v-row>
</template>

<script setup lang="ts">
const props = defineProps<{
  projects: any,
}>();

const emits = defineEmits<{
  (event: 'project-clicked', projectId: number): void
}>();
</script>
