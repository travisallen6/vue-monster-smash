<template>
  <div id="app">
    <button @click='toggle(true)'>Create</button>
    <button @click='toggle(false)'>Monsters</button>
    <div v-if='createView'>
      <create
        :gimme='submit'></create>
    </div>
    <div v-else >
      <monsters
        :monsters='monsters'
        :repeatReceiveEdits='editMonster'></monsters>

    </div>
  </div>
</template>

<script>
import Create from './components/Create'
import Monsters from './components/Monsters'

export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      createView: true,
      monsters: []
    }
  },
  methods: {

    toggle(bool){
      this.createView = bool
    },

    submit(monster){
      this.monsters.push(monster)
    },

    editMonster(i, newMonster){
      this.monsters.splice(i, 1, newMonster)
    }
  },
  components: {
    create: Create,
    monsters: Monsters
  }
}
</script>

<style>

</style>
