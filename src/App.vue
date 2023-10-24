<script setup lang="ts">

  import { ref } from 'vue'
  import { createInput } from '@formkit/vue'
  import fkVisualEditor from './components/fkVisualEditor.vue';

  const visualEditor = createInput(fkVisualEditor);

  const liveForm = ref({
    content: btoa('<p>hello world</p>')
  })

  const formNode = ref();

</script>


<template>
  <FormKit type="form"
           ref="formNode"
           v-model="liveForm">
  </FormKit>


  <FormKit :type="visualEditor"
           name="content"
           label="De content"
           v-if="formNode?.node"
           :parent="formNode.node" />
  <pre>{{ liveForm }}</pre>
</template>

<style scoped></style>
