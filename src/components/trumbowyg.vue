<script setup lang="ts">
    import { onMounted, onBeforeUnmount } from 'vue'

    const props = defineProps({
        input: {
            type: String,
            required: true
        }
    })

    const emit = defineEmits<{
        'update:input': [val: string]
    }>()

    onMounted(() => {
        $('#trumbowyg').trumbowyg()
            .on('tbwchange', () => {
                console.log('tbwchange');
                emit('update:input', $('#trumbowyg').trumbowyg('html'))
            })
            .trumbowyg('html', props.input)
    })

    onBeforeUnmount(() => {
        $('#trumbowyg').trumbowyg('destroy');
    })

</script>

<template>
    <div id="trumbowyg"></div>
</template>