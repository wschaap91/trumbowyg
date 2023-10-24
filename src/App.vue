<script setup lang="ts">

  import { ref } from 'vue'
  import { createInput } from '@formkit/vue'
  import fkVisualEditor from './components/fkVisualEditor.vue';

  const visualEditor = createInput(fkVisualEditor);

  const liveForm = ref({
    content: btoa('<p>hello world</p>')
  })

</script>


<template>
  <FormKit type="form"
           v-model="liveForm">
    <FormKit :type="visualEditor"
             name="content"
             label="De content" />
  </FormKit>
  <pre>{{ liveForm }}</pre>
</template>

<style scoped></style>
