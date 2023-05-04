<template>
    <div v-show="modalActive" style="width:300px;height:300px;position:absolute; background-color: rgb(10, 77, 247);">
       <h2>This Is modal</h2>
       <slot />

       <button @click="$emit('close-modal')"> Close Me</button>
    </div>
</template>

<script setup>
defineEmits(['close-modal'])
defineProps({
    modalActive: {
        type: Boolean,
        default: false
    }
})

</script>

<style lang="scss" scoped>

</style>