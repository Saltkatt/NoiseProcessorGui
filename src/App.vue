<template>
  <div id="app">
    <ProcessingForm />
  </div>

</template>

<script>

import ProcessingForm from "./components/forms/ProcessingForm.vue";


export default {
  name: 'App',
  components: {
    ProcessingForm,
    
  }
}
</script>

<style>
#app {
  display: center;
  flex-direction: column;
  text-align: center;
}
body {
  margin: 0;
  background: #eee;
}

</style>
