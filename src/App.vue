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
const semester = ref('');
const startTime = ref('');
const endTime = ref('');
const completed = ref();

const classes = ref<object[]>([])

function removeItem(id : number) {
  classes.value = (classes.value as ClassInterface[]).filter((item) => item.id != id)
  console.log(id)
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

  console.log(classes.value)
}

</script>

<template>
  <div class="section-container">
    <div class="inputs-container">
      <Input HTMLType="text" label="Class" v-model="className"/>
      <Input HTMLType="text" label="Recomended Semester" v-model="semester"/>
      <Input HTMLType="time" label="Start Time" v-model="startTime"/>
      <Input HTMLType="time" label="End Time" v-model="endTime"/>
      <input type="checkbox" v-model="completed">
      <p>Done?</p>
      <button @click='addData'>Add Class</button>
    </div>
    <div class="classes-container" v-for="c in (classes as ClassInterface[])">
      <ClassItem 
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
  border-radius: 4px;
  flex-direction: column;
}
button {
  white-space: nowrap;
  text-transform: uppercase;
  font-weight: 800;
}
</style>
