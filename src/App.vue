<template>
  
  <h1>dealing with compositional API at home page</h1>
  <p>my name is {{name}} and my age is {{ age }}</p>
  <br>
  <button @click="age++">add age + 1</button>
  <br>
  <button @click="handleclick">click me</button>
  <br>
  <lable>Name:</lable>
  <input type="text" v-model="search" >

  <div v-for="namez in matchingNames" :key="namez" >{{namez}}</div>

  <br>
  <label>Serch:</label>
  <input type="text" v-model="search">
  <p>serch value : {{ search }}</p>

  <router-view/>
</template>

<script>
import { computed, ref } from 'vue'


export default {
  //the setup function runs first befor anyother function runs on this component 
  setup() {
   const name1 =computed(() => {
      return 'biralo'
   })

    let name =ref('jovic') // just because it's constant it does not mean the value can't cahange , it can .. it's just the refernce(address) of the value that can't change
    let age =ref(30)

    const names = ref(['mali', 'sadat','omo', 'imelida', 'tumwebaze','biralo', 'patric'])

  const handleclick = () =>{
    name.value ='biralo'
  }

  //computed data ... we are using the available name to return the serched name

  const  search =ref('')
  const  matchingNames = computed(()=>{
    return names.value.filter((namez) => namez.includes(search.value))
  })

    return {name, age,handleclick, names, search, matchingNames}
    // returning the object of the data we want to use in the component 
  },
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>
