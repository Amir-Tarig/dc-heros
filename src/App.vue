<template>
<AppHeader/>
 <div class="w-full flex">
    <div class="m-auto">
      <h1 class="text-2xl">Dc Heros</h1>
        <ul>
          <li class="flex justify-between" v-for="(hero, index) in Heros" :key="hero.id">
            <div>{{hero.name}} </div>
            <button @click="removeHero(index)">X</button>
          </li>
        </ul>

        <form class="mt-10" @submit.prevent="addHero">
          <input class="border rounded-lg" type="text" v-model="newHero" placeholder="add heros">
          <button class="border rounded bg-gradient-to-r from-red-700 to-pink-500 text-sm text-white" type="submit" >Add Hero</button>
        </form>
    </div>
 </div>
</template>

<script>
import { reactive ,ref} from 'vue'
import AppHeader from '@/components/AppHeader'

export default {
  name: 'App',
  components: {
    AppHeader,
  },

  setup () {
    const newHero = ref('')

    let Heros = reactive([
        {name: 'SuperGirl', id: 0},
        { name: 'Flash', id: 1},
        { name: 'Arrow', id: 2},
        { name: 'Batman', id:3},
        {name: 'Superman', id: 4}
    ])

    const addHero = () => {
      if(newHero.value !== '') {
        Heros.push({name: newHero.value})
        newHero.value = ''
      }
    }

    const removeHero = (index) => {
      Heros.splice(index,1)
    }


    return { Heros , newHero, addHero, removeHero}
  }
}
</script>

<style scoped>
</style>
