

<script lang="ts">

import { defineComponent, defineProps } from 'vue';

export default defineComponent({
    component: 'Input',
});

</script>

<template>
    <div class="container">
        <label>Label Text</label>
        <input>
    </div>
</template>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
}
</style>