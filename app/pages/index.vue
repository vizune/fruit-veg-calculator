<template>
  <div class="h-full flex flex-col justify-center items-center container mx-auto">
    <div v-if="!category" class="grid grid-row-2 md:grid-rows-1 md:grid-cols-2 gap-4 md:gap-8 mx-4 md:mx-6">
      <MainButton 
        id="fruit" 
        title="Fruit" 
        icon="fruit"
        @category-selected="setCategory" 
      />
      <MainButton 
        id="vegetables" 
        title="Vegetables" 
        icon="vegetables"
        @category-selected="setCategory" 
      />
    </div>

    <div v-if="category" class="py-4 md:py-6 px-4 md:px-0 overflow-y-auto overflow-x-hidden h-full">
      <ItemFeed 
        :category="category" 
        :feed="category === 'fruit' ? fruit : vegetables"
        @decrease="decreaseQuantity"
        @increase="increaseQuantity" />
    </div>

    <button v-if="category" @click="clearCategory" class="my-4 ml-4 md:ml-0 self-start border-black border-2 border-solid rounded py-2 md:py-4 px-4">
      <svg-icon name="navigation/back" height="35px" width="35px" class="mb-2" />
      <span>Back</span>
    </button>
  </div>
</template>

<script>
import axios from 'axios';
import MainButton from '../components/main-button.vue';
import ItemFeed from '../components/item-feed.vue';

export default {
    name: "fruit-veg-calculator",
    data() {
        return {
            category: null,
            fruit: null,
            vegetables: null
        };
    },
    async beforeMount() {
      this.fruit = await this.loadData('fruit');
      this.vegetableas = await this.loadData('vegetables');
    },
    methods: {
        async loadData(category) {
          if (process.server) {
            return JSON.parse(require('fs').readFileSync(`../data/${category}.json`, 'utf8'))
          } else {
            return await axios.get(`../data/${category}.json`).then(res => res.data)
          }
        },
        setCategory(category) {
            this.category = category;
        },
        clearCategory() {
          this.category = null;
        },
        decreaseQuantity(title) {
          const selectedCategory = this.category === "fruit" ? this.fruit : this.vegetables;

          const item = selectedCategory.find(x => x.title === title);

          item.count--;
        },
        increaseQuantity(title) {
          const selectedCategory = this.category === "fruit" ? this.fruit : this.vegetables;

          const item = selectedCategory.find(x => x.title === title);

          item.count++;
        }
    },
    components: { MainButton }
}
</script>

<style>
html, body, #__nuxt, #__layout {
  height: 100%;
  width: 100%;
}

</style>