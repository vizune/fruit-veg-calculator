<template>
    <div 
    v-if="feed"
    class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-5 gap-4 md:gap-6">
        <div 
            v-for="(item, index) in feed" 
            :key="index"
            class="flex flex-col justify-content items-center border-black border-2 border-solid rounded p-4 md:p-6 pb-1 md:pb-1 md:max-w-xs">
                <svg-icon  
                    :name="`${category}/${item.icon}`" 
                    :title="`${item.title} item`"
                    class="ItemFeed-icon"
                />
                <p class="font-bold mt-4 mb-2 text-lg text-center">{{item.title}}</p>

                <div class="flex justify-between items-center w-full p-4">
                    <button 
                    @click="$emit('decrease', item.title)" 
                    :disabled="item.count === 0" class="ItemFeed-quantity">
                        <svg-icon  
                        name="navigation/minus"
                        height="35px"
                        width="35px"
                        />
                        <span class="sr-only">Decrease quantity of {{item.title}}</span>
                    </button>

                    <p>{{item.count}}</p>

                    <button @click="$emit('increase', item.title)" >
                        <svg-icon  
                        name="navigation/add" 
                        title="Increase quanity"
                        height="35px"
                        width="35px"
                        />
                        <span class="sr-only">Increase quantity of {{item.title}}</span>
                    </button>
                </div>
        </div>
    </div>
</template>

<script>
export default {
  name: "ItemFeed",
  props: {
      category: {
        type: String,
        required: true
      },
      feed: {
        type: Array,
        required: true
      }
  }
}
</script>

<style>
.ItemFeed-icon {
    max-width: 80%;
}

.ItemFeed-quantity:disabled {
    opacity: .15;
}
</style>
