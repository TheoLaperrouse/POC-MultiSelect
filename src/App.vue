<template>
  <div class="app">
    <MultiSelect title="Simple Select" mode="single" :options="options" />
    <MultiSelect title="Multiple Select" mode="multiple" :options="options" />
    <MultiSelect title="Tags Select" mode="tags" :options="options" />
    <MultiSelect title="Simple Select with Async function" :mode="tags" :options="getOptions" />
  </div>
</template>

<script>
import MultiSelect from './components/MultiSelect.vue'

export default {
  components: {
    MultiSelect
  },
  data() {
    return {
      options: [
        'Apis mellifera',
        'Danaus plexippus',
        'Anopheles gambiae',
        'Bombyx mori',
        'Drosophila melanogaster',
        'Papilio machaon',
        'Formica rufa',
        'Tenebrio molitor',
        'Lepidoptera',
        'Coleoptera'
      ],
      asyncOptions: []
    }
  },
  methods: {
    async getOptions() {
      try {
        const response = await fetch('https://pokeapi.co/api/v2/pokemon?limit=15')
        const data = await response.json()
        return data.results.map((pokemon) => pokemon.name)
      } catch (error) {
        console.error('Error loading Options:', error)
      }
    }
  }
}
</script>

<style scoped>
.app {
  font-family: Arial, sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.MultiSelect {
  width: 400px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px;
}

.title {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 5px;
}

.select-box {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 5px;
  background-color: #f9f9f9;
}

.option {
  padding: 5px;
  cursor: pointer;
}

.option:hover {
  background-color: #e0e0e0;
}
</style>
