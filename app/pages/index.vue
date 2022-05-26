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
import MainButton from '../components/main-button.vue';
import ItemFeed from '../components/item-feed.vue';

export default {
    name: "fruit-veg-calculator",
    data() {
        return {
            category: null,
            fruit: [
              { title: 'Apple', icon: 'apple', count: 0},
              { title: 'Apricot', icon: 'apricot', count: 0},
              { title: 'Avocado', icon: 'avocado', count: 0},
              { title: 'Banana', icon: 'banana', count: 0},
              { title: 'Blueberry', icon: 'blueberry', count: 0},
              { title: 'Cherry', icon: 'cherry', count: 0},
              { title: 'Coconut', icon: 'coconut', count: 0},
              { title: 'Dates', icon: 'dates', count: 0},
              { title: 'Dragon fruit', icon: 'dragon-fruit', count: 0},
              { title: 'Durian', icon: 'durian', count: 0},
              { title: 'Grapefruit', icon: 'grapefruit', count: 0},
              { title: 'Grapes', icon: 'grapes', count: 0},
              { title: 'Kiwi', icon: 'kiwi', count: 0},
              { title: 'Lemon', icon: 'lemon', count: 0},
              { title: 'Lime', icon: 'lime', count: 0},
              { title: 'Lychee', icon: 'lychee', count: 0},
              { title: 'Mango', icon: 'mango', count: 0},
              { title: 'Orange', icon: 'orange', count: 0},
              { title: 'Papaya', icon: 'papaya', count: 0},
              { title: 'Passionfruit', icon: 'passion-fruit', count: 0},
              { title: 'Peach', icon: 'peach', count: 0},
              { title: 'Pear', icon: 'pear', count: 0},
              { title: 'Pineapple', icon: 'pineapple', count: 0},
              { title: 'Plum', icon: 'plum', count: 0},
              { title: 'Raspberry', icon: 'raspberry', count: 0},
              { title: 'Starfruit', icon: 'starfruit', count: 0},
              { title: 'Strawberry', icon: 'strawberry', count: 0},
              { title: 'Tomato', icon: 'tomato', count: 0},
              { title: 'Watermelon', icon: 'Watermelon', count: 0},
            ],
            vegetables: [
              { title: 'Asparagus', icon: 'asparagus', count: 0},
              { title: 'Aubergine', icon: 'aubergine', count: 0},
              { title: 'Beetroot', icon: 'beetroot', count: 0},
              { title: 'Broccoli', icon: 'broccoli', count: 0},
              { title: 'Butternut Squash', icon: 'squash', count: 0},
              { title: 'Cabbage', icon: 'cabbage', count: 0},
              { title: 'Red Cabbage', icon: 'red_cabbage', count: 0},
              { title: 'Carrot', icon: 'carrot', count: 0},
              { title: 'Cauliflower', icon: 'cauliflower', count: 0},
              { title: 'Corn', icon: 'corn', count: 0},
              { title: 'Courgette', icon: 'courgette', count: 0},
              { title: 'Cucumber', icon: 'cucumber', count: 0},
              { title: 'Garlic', icon: 'garlic', count: 0},
              { title: 'Wild Garlic', icon: 'wild_garlic', count: 0},
              { title: 'Green beans', icon: 'green-beans', count: 0},
              { title: 'Leek', icon: 'leek', count: 0},
              { title: 'Lettuce', icon: 'lettuce', count: 0},
              { title: 'Button Mushrooms', icon: 'mushrooms_button', count: 0},
              { title: 'Chestnut Mushrooms', icon: 'mushrooms_chestnut', count: 0},
              { title: 'Shimeji (Beech) Mushrooms', icon: 'mushrooms_shimeji', count: 0},
              { title: 'Red Onion', icon: 'onion_red', count: 0},
              { title: 'Sping (Green) Onions', icon: 'onion_spring', count: 0},
              { title: 'White Onion', icon: 'onion_white', count: 0},
              { title: 'Parsnip', icon: 'parsnip', count: 0},
              { title: 'Bell Pepper', icon: 'pepper_bell', count: 0},
              { title: 'Potato', icon: 'potato', count: 0},
              { title: 'New potato', icon: 'potatoes_new', count: 0},
              { title: 'Sweet Potato', icon: 'potato_sweet', count: 0},
              { title: 'Pumpkin', icon: 'pumpkin', count: 0},
              { title: 'Radish', icon: 'radish', count: 0},
              { title: 'Red Chili Pepper', icon: 'red-chili-pepper', count: 0},
              { title: 'Spinach', icon: 'spinach', count: 0},
            ]
        };
    },
    methods: {
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