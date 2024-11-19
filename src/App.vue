<script setup lang="ts">
import { VueFlow, useVueFlow } from '@vue-flow/core'
import DropzoneBackground from '@/components/DropzoneBackground.vue'
import Sidebar from '@/components/Sidebar.vue'
import useDragAndDrop from '@/components/useDnD'
import SpecialNode from '@/components/SpecialNode.vue'
import SpecialEdge from '@/components/SpecialEdge.vue'

const { onConnect, addEdges } = useVueFlow()

const { onDragOver, onDrop, onDragLeave, isDragOver } = useDragAndDrop()

onConnect(addEdges)
</script>

<template>
  <div class="dnd-flow">
    <VueFlow @dragover="onDragOver" @dragleave="onDragLeave" @drop="onDrop">
      <template #node-special="specialNodeProps">
        <SpecialNode v-bind="specialNodeProps" />
      </template>

      <template #edge-special="specialEdgeProps">
        <SpecialEdge v-bind="specialEdgeProps" />
      </template>

      <DropzoneBackground
        :style="{
          backgroundColor: isDragOver ? '#e7f3ff' : 'transparent',
          transition: 'background-color 0.2s ease',
        }"
      >
        <p v-if="isDragOver">Drop here</p>
      </DropzoneBackground>
    </VueFlow>
    <Sidebar />
  </div>
</template>

<style>
/* import the necessary styles for Vue Flow to work */
@import '@vue-flow/core/dist/style.css';

/* import the default theme, this is optional but generally recommended */
@import '@vue-flow/core/dist/theme-default.css';
</style>
