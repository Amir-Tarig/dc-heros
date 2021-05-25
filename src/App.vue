<template>
  <h1>Dc Heros</h1>
    <ul>
      <li v-for="(hero, index) in Heros" :key="index">{{hero.name}}</li>
    </ul>
    <form @submit.prevent="addHero">
      <input type="text" v-model="newHero">
      <button type="submit" >Add Hero</button>
    </form>
</template>

<script>
import { reactive ,ref} from 'vue'

export default {
  name: 'App',
  components: {},

  setup () {
    // const isDisabled = ref(false)
    const newHero = ref('')

    const Heros = reactive([
        {name: 'SuperGirl'},
        { name: 'Flash'},
        { name: 'Arrow'},
        { name: 'Batman'},
        {name: 'Superman'}
    ])

    const addHero = () => {
      if(newHero.value !== '') {
        Heros.push({name: newHero.value})
        newHero.value = ''
      }
    }


    return { Heros , newHero, addHero}
  }
}
</script>

<style scoped>
</style>
