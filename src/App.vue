<script setup lang="ts">
import { ref } from 'vue';
import Input from './components//Input.vue'
import ClassItem from './components/ClassItem.vue'

let id = 0;

interface ClassInterface {
  name: string,
  semester: string,
  startTime: string,
  endTime: string,
  completed: boolean,
  id: number,
}

const className = ref('');
const semester = ref(1);
const startTime = ref('');
const endTime = ref('');
const completed = ref();

const classes = ref<object[]>([])

function removeItem(id : number) {
  classes.value = (classes.value as ClassInterface[]).filter((item) => item.id != id)
}

function addData() {
  classes.value.push({
    name: className.value,
    semester: semester.value,
    startTime: startTime.value,
    endTime: endTime.value,
    completed: completed.value,
    id: id++,
  })
}

</script>

<template>
  <div class="section-container">
    <div class="header-container">
      <Input label="Course Name"></Input>
      <Input HTMLType="number" label="Default Semesters"></Input>
    </div>
    <div class="inputs-container">
      <Input HTMLType="text" label="Class" v-model="className"/>
      <Input HTMLType="number" label="Recomended Semester" v-model="semester"/>
      <Input HTMLType="time" label="Start Time" v-model="startTime"/>
      <Input HTMLType="time" label="End Time" v-model="endTime"/>
      <input type="checkbox" v-model="completed">
      <p>Done?</p>
      <button @click='addData'>Add Class</button>
    </div>
      <div class="classes-container">
        <ClassItem 
          v-for="c in (classes as ClassInterface[])"
          @deleteItem='removeItem' 
          :name="c.name" 
          :semester="Number(c.semester)"
          :startTime="c.startTime"
          :endTime="c.endTime"
          :completed="c.completed"
          :id="c.id"
        />
      </div>
    </div>
</template>

<style scoped>

.header-container {
  display: flex;
  flex-direction: row;
  gap: 8px;
}

.section-container {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.inputs-container {
  display: flex;
  gap: 8px;
  align-items: flex-end;
}

.classes-container {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

button {
  white-space: nowrap;
  text-transform: uppercase;
  font-weight: 800;
}

</style>
