<template>
    <div class="container">
        <div class="info-container">
            <span>{{ name }}</span>
            <span>{{ semester }}</span>
            <span>{{ startTime }}</span>
            <span>{{ endTime }}</span>
            <span v-if="completed">Class Completed</span>
            <span v-else>Class not completed yet</span>
        </div>
        <button class="close-button"@click="$emit('deleteItem', id)"> X </button>
    </div>
</template>

<script lang="ts" setup>

const props = defineProps({
    name: {
        type: String,
        default: 'no class name',
    },
    semester: {
        type: Number,
        default: 0,
    },
    startTime : {
        type: String,
        default: 'WTF',
    },
    endTime : {
        type: String,
        default: '',
    },
    id : {
        type: Number,
        default: 0,
    },
    completed : {
        tpye: Boolean,
        default: false,
    },
    req : {
        tpye: Array,
        default: [],
    }
})

</script>

<style scoped>

/* .info-container > span {
    flex: 1;
} */

.small-item {
    max-width: fit-content;
}

.info-container {
    width: 100%;
    display: flex;
    gap: 24px;
    align-items: stretch;
    justify-content: stretch;
}
.container {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    background-color: #ffffff30;
    padding: 12px;
    border-radius: 8px;
}

button {
    all: unset;
    color: white;
    cursor: pointer;
}
</style>