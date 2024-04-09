<script setup>
import { ref } from 'vue';
import { Pen, Trash2 } from 'lucide-vue-next';
const data = ref([])

const addNewIngredient = (item) => {
  console.error(item)
  if (item !== "") {
    data.value.push(item)
  }
  return false
}

const deleteIngredient= (key) => {
  console.error('delete', key)
}
const editIngredient = () => {
  console.error('edit')
}
const title = "Ingredients Tracker"
</script>

<template>

  <div class="max-w-lg bg-slate-300 p-3 mx-auto mt-3 rounded-lg overflow-hidden h-40" v-bind:class="{'!h-96' : data.length}">
    <span class="block text-center font-semibold text-slate-800">{{ title }}</span>
    <div class="flex gap-1 mt-3">
      <input class="w-full rounded-lg px-3" v-model="ingredient" placeholder="Add new ingredients">
      <button type="button" @click="addNewIngredient(ingredient)"
        class="border border-gray-100 p-2 rounded-md whitespace-nowrap">Add
        New</button>
    </div>
    <div class="h-[280px] w-full overflow-y-auto">
      <div v-if="data.length" v-for="(item, index) in data" class="bg-white mt-2 p-3 rounded-lg hover:bg-blue-400">
        <span class="flex justify-between">{{ item }} 
          <div class="flex gap-2">
            <button @click="editIngredient" ><Pen /></button>
            <button @click="deleteIngredient(index)"><Trash2/></button>
          </div>
        </span>
      </div>
      <div v-else class="text-center bg-white mt-2 p-3 rounded-lg">No Data!</div>
    </div>
  </div>

</template>
