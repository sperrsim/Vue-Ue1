<template>
  <div :class="{ dynamic: subjects.length > 3 }">
    <h3>{{ title }}</h3>
    <form @submit.prevent="addNewSubject">
      <label>Enter new subject:</label>
      <input v-model="newSubject" />
      <button>Add subject</button>
    </form>
    <hr />
    <ul>
      <li v-for="(item, index) in subjects" :key="index">
        {{ item.content }}
        <button @click="deleteSubject(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from 'vue';
export default {
  props: {
    title: { type: String, required: true },
  },
  setup() {
    const newSubject = ref('lask');
    const subjects = ref([]);

    function addNewSubject() {
      //console.log('addNewSubject: ' + newSubject.value );
      subjects.value.push({
        content: newSubject.value,
      });
      newSubject.value = '';
      //console.log(subjects.value);
    }

    function deleteSubject(index) {
      console.log('Delete .....');
      subjects.value.splice(index, 1);
    }
    return { newSubject, addNewSubject, subjects, deleteSubject };
  },
};
</script>

<style scoped>
h3 {
  margin-bottom: 20px;
}
hr {
  margin-top: 20px;
  margin-bottom: 20px;
}
.dynamic {
  color: red;
}
</style>
