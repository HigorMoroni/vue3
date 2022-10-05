<template>
  {{fullName}}
  <img @click="changeName" alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import { ref } from '@vue/reactivity';
import { computed, watch } from '@vue/runtime-core';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  setup() {
    //DATA
    const user = ref({
      first_name: 'Jon',
      last_name: 'Snow'
    });
    
    //COMPUTED
    const fullName = computed(() => `${user.value.first_name} ${user.value.last_name}`);

    //METHOD
    const changeName = () => {
      user.value.first_name = 'Sansa';
    };

    //WATCH
    watch(user, () => {
      console.log('alterou algo no objeto');
    }, {
      deep: true
    });

    watch(() => user.value.first_name, () => {
      console.log('alterou o first name dentro do objeto user')
    });

    //RETURN
    return {
      user,
      changeName,
      fullName
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
