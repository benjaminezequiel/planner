<template>
    <div class="container">
        <label for="input">{{ label }}</label>
        <input 
            :type="HTMLType"
            :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value)"
        /> 
    </div>
</template>

<script lang="ts" setup>

const props = defineProps({
    HTMLType: {
        type: String,
        default: 'text',
    },
    label: {
        type: String,
        default: 'label',
    },
    modelValue: {
        type: [Boolean, String, Number],
        default: '',
    }
})

</script>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
}
</style>