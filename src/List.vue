<script setup>
import { ref } from 'vue';

const items = ref([
  { status: false, name: 'Cras justo odio' },
  { status: true, name: 'Dapibus ac facilisis in' },
  { status: false, name: 'Morbi leo risus' },
  { status: false, name: 'Porta ac consectetur ac ' },
  { status: true, name: 'Vestibulum at eros' },
  { status: false, name: 'Morbi leo risus' }
]);

const newTask = ref('');

const handleAddTask = () => {
  let text = newTask.value.trim();
  if (text !== '') {
    items.value.push({ name: text, status: false });
    newTask.value = '';
  }
};

const handleRemoveTask = () => {
  items.value = items.value.filter((item) => !item.status);
};

</script>

<template>
  <div class="row row-cols-lg-auto g-3 justify-content-center align-items-center mb-4 pb-2">
    <div class="col-12">
      <div class="form-outline">
        <input v-model="newTask" type="text" id="form1" class="form-control form-control-lg" style="width: 800px;" />
        <label class="form-label" for="form1">What do you need to do today?</label>
      </div>
    </div>

    <div class="col-12">
      <button type="submit" class="btn btn-primary" @click="handleAddTask">Add</button>
      <button type="submit" class="btn btn-danger" @click="handleRemoveTask">Remove</button>
    </div>
  </div>
  <table class="table mb-4">
    <tbody>
    <tr v-for="(item, id) of items" :key="id">
      <td>
        <input v-model="item.status" type="checkbox" />
      </td>
      <td :class="{ 'text-decoration-line-through': item.status }">{{ item.name }}</td>
    </tr>
    </tbody>
  </table>
</template>






