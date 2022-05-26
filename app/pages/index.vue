<template>
  <div class="h-full flex justify-center items-center container mx-auto">
  <div class="grid grid-row-2 md:grid-rows-1 md:grid-cols-2 gap-4 md:gap-8 mx-4 md:mx-6">
    <MainButton 
      id="fruit" 
      title="Fruit" 
      icon="fruit"
      @category-selected="setCategory" 
    />
    <MainButton 
      id="vegetable" 
      title="Vegetable" 
      icon="vegetables"
      @category-selected="setCategory" 
    />
    {{category}}
  </div>
  </div>
</template>

<script>
import MainButton from '../components/main-button.vue';

export default {
    name: "fruit-veg-calculator",
    data() {
        return {
            category: null
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