<template>
  <v-dialog width="50%" :model-value="props.active">
    <v-card>
      <v-card-title class="border-b">
        {{ props.project.name }}
      </v-card-title>
      <v-card-text>
        <div class="d-flex flex-column">
          <p v-html="props.project.description" />
          <v-list>
            <v-list-item v-for="(task, i) in props.project.tasks" :key="i" prepend-icon="mdi-arrow-right">
              <v-list-item-title v-text="task"/>
            </v-list-item>
          </v-list>
          <div>
            <strong>Technologies :</strong> {{ props.project.stack }}
          </div>
        </div>
      </v-card-text>
      <v-card-actions>
        <v-btn @click="emits('close-dialog')">Fermer</v-btn>
        <v-spacer />
        <v-btn color="primary" :href="props.project.link" target="_blank" v-if="props.project.link">Visiter le site</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script setup lang="ts">
const props = defineProps<{
  project: any
  active: boolean
}>();

const emits = defineEmits<{
  (event: 'close-dialog'): void
}>();
</script>

<style scoped>

</style>
