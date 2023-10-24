<script setup lang="ts">
  import { ref, computed } from 'vue';
  import trumbowyg from './components/trumbowyg.vue';

  // const testString = btoa('<b>This</b> is really awesome');

  const inputVal = ref(btoa('<b>This</b> is really awesome'));

  const computedString = computed(() => {
    return atob(inputVal.value);
  })

  const updateInputVal = (val: string) => {
    inputVal.value = btoa(val);
  }

</script>


<template>
  <trumbowyg :input="computedString"
             @update:input="updateInputVal"
             v-once />
  <pre>{{ inputVal }}</pre>
</template>

<style scoped></style>
