<template>
  <header>
    <h1>HTL Wels / {{msg}}</h1>
    <h2>JavaScript / DOM-Manipulation / Dynamic List</h2>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    msg: String, 
  },
};
</script>
