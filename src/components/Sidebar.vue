<script setup>
import useDragAndDrop from './useDnD'

const { onDragStart } = useDragAndDrop()
</script>

<template>
  <aside>
    <div class="description">You can drag these nodes to the pane.</div>

    <div class="nodes">
      <div class="vue-flow__node-input" :draggable="true" @dragstart="onDragStart($event, 'input')">
        Input Node
      </div>

      <div
        class="vue-flow__node-default"
        :draggable="true"
        :data="{ label: 'Node 1' }"
        @dragstart="onDragStart($event, 'default')"
      >
        Default Node
      </div>

      <div
        class="vue-flow__node-output"
        :draggable="true"
        @dragstart="onDragStart($event, 'output')"
      >
        Output Node
      </div>

      <div
        class="vue-flow__node-default"
        :draggable="true"
        :data="{ label: 'Special' }"
        @dragstart="onDragStart($event, 'special')"
      >
        Special Node
      </div>
    </div>
  </aside>
</template>
