<template>
  <AppButton @update="getUpdate">Save</AppButton>

  <br><br><br>

  <AppHook v-if="showAppHook" />

  <button @click="showAppHook = !showAppHook" >Toggle</button>

  <br><br><br>
  {{fullName}}
  <br><br><br>
  <img @click="changeName" alt="Vue logo" src="./assets/logo.png">
</template>

<script>
import AppHook from './components/AppHook.vue';
import AppButton from './components/AppButton.vue';

import { ref } from '@vue/reactivity';
import { computed, watch } from '@vue/runtime-core';

export default {
  name: 'App',

  components: {
    AppHook,
    AppButton
  },

  setup() {
    //DATA
    const user = ref({
      first_name: 'Jon',
      last_name: 'Snow'
    });

    const showAppHook = ref(true);
   
    
    //COMPUTED
    const fullName = computed(() => `${user.value.first_name} ${user.value.last_name}`);


    //METHOD
    const changeName = () => {
      user.value.first_name = 'Sansa';
    };
    
    const getUpdate = data => {
      console.log('getUpdate', data);
    }


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
      fullName,
      showAppHook,
      getUpdate
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
