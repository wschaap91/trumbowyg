<script setup lang="ts">
    import trumbowyg from './trumbowyg.vue';

    const props = defineProps({
        context: Object,
    })

    const initialVal = atob(props.context._value);

    function updateVal(val) {
        props.context.node.input(btoa(val));
    }

</script>


<template>
    <trumbowyg :input="initialVal"
               @update:input="updateVal"
               v-once />
</template>

<style scoped></style>
