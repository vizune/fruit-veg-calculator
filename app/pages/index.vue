<template>
  <div class="h-full flex justify-center items-center container mx-auto">
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
    <div class="py-4 md:py-6 overflow-y-auto overflow-x-hidden h-full">
      <ItemFeed v-if="category" :category="category" :feed="category === 'fruit' ? fruit : vegetables " />
    </div>
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
              { title: 'Apple', icon: 'apple'},
              { title: 'Apricot', icon: 'apricot'},
              { title: 'Avocado', icon: 'avocado'},
              { title: 'Banana', icon: 'banana'},
              { title: 'Blueberry', icon: 'blueberry'},
              { title: 'Cherry', icon: 'cherry'},
              { title: 'Coconut', icon: 'coconut'},
              { title: 'Dates', icon: 'dates'},
              { title: 'Dragon fruit', icon: 'dragon-fruit'},
              { title: 'Durian', icon: 'durian'},
              { title: 'Grapefruit', icon: 'grapefruit'},
              { title: 'Grapes', icon: 'grapes'},
              { title: 'Kiwi', icon: 'kiwi'},
              { title: 'Lemon', icon: 'lemon'},
              { title: 'Lime', icon: 'lime'},
              { title: 'Lychee', icon: 'lychee'},
              { title: 'Mango', icon: 'mango'},
              { title: 'Orange', icon: 'orange'},
              { title: 'Papaya', icon: 'papaya'},
              { title: 'Passionfruit', icon: 'passion-fruit'},
              { title: 'Peach', icon: 'peach'},
              { title: 'Pear', icon: 'pear'},
              { title: 'Pineapple', icon: 'pineapple'},
              { title: 'Plum', icon: 'plum'},
              { title: 'Raspberry', icon: 'raspberry'},
              { title: 'Starfruit', icon: 'starfruit'},
              { title: 'Strawberry', icon: 'strawberry'},
              { title: 'Tomato', icon: 'tomato'},
              { title: 'Watermelon', icon: 'Watermelon'},
            ],
            vegetables: [
              { title: 'Asparagus', icon: 'asparagus'},
              { title: 'Aubergine', icon: 'aubergine'},
              { title: 'Beetroot', icon: 'beetroot'},
              { title: 'Broccoli', icon: 'broccoli'},
              { title: 'Butternut Squash', icon: 'squash'},
              { title: 'Cabbage', icon: 'cabbage'},
              { title: 'Red Cabbage', icon: 'red_cabbage'},
              { title: 'Carrot', icon: 'carrot'},
              { title: 'Cauliflower', icon: 'cauliflower'},
              { title: 'Corn', icon: 'corn'},
              { title: 'Courgette', icon: 'courgette'},
              { title: 'Cucumber', icon: 'cucumber'},
              { title: 'Garlic', icon: 'garlic'},
              { title: 'Wild Garlic', icon: 'wild_garlic'},
              { title: 'Leek', icon: 'leek'},
              { title: 'Lettuce', icon: 'lettuce'},
              { title: 'Button Mushrooms', icon: 'mushrooms_button'},
              { title: 'Chestnut Mushrooms', icon: 'mushrooms_chestnut'},
              { title: 'Shimeji (Beech) Mushrooms', icon: 'mushrooms_shimeji'},
              { title: 'Red Onion', icon: 'onion_red'},
              { title: 'Sping (Green) Onions', icon: 'onion_spring'},
              { title: 'White Onion', icon: 'onion_white'},
              { title: 'Parsnip', icon: 'parsnip'},
              { title: 'Bell Pepper', icon: 'pepper_bell'},
              { title: 'Potato', icon: 'potato'},
              { title: 'New potato', icon: 'potatoes_new'},
              { title: 'Sweet Potato', icon: 'potato_sweet'},
              { title: 'Pumpkin', icon: 'pumpkin'},
              { title: 'Radish', icon: 'radish'},
              { title: 'Red Chili Pepper', icon: 'red-chili-pepper'},
              { title: 'Spinach', icon: 'spinach'},
            ]
        };
    },
    methods: {
        setCategory(category) {
            this.category = category;
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