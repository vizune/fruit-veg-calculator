<template>
    <div 
    v-if="feed"
    class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-4 md:gap-6">
        <div 
            v-for="(item, index) in feed.sort((a, b) => (a.title > b.title) ? 1 : -1)" 
            :key="index"
            class="flex flex-col justify-content items-center border-black border-2 border-solid rounded px-3 md:px-4 pt-4 pb-1 md:max-w-xs md:max-h-xs">
                <svg-icon  
                    :name="`${category}/${item.icon}`" 
                    :title="`${item.title} item`"
                    class="ItemFeed-icon"
                />
                <p class="font-bold mt-2 md:mt-4 mb-2 text-lg text-center">{{item.title}}</p>

                <div class="flex justify-between items-center w-full py-4">
                    <button 
                    @click="$emit('decrease', item.title)" 
                    :disabled="item.count === 0" class="ItemFeed-quantity">
                        <svg-icon  
                        name="navigation/minus"
                        height="32px"
                        width="32px"
                        />
                        <span class="sr-only">Decrease quantity of {{item.title}}</span>
                    </button>

                    <p>{{item.count}}</p>

                    <button @click="$emit('increase', item.title)" class="ItemFeed-quantity">
                        <svg-icon  
                        name="navigation/add" 
                        title="Increase quanity"
                        height="32px"
                        width="32px"
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
        required: true
      }
  }
}
</script>

<style>
.ItemFeed-icon {
    max-width: 65%;
    max-height: 70px;
}

.ItemFeed-quantity:disabled {
    opacity: .15;
}

.ItemFeed-quantity:disabled {
    opacity: .15;
}

@media (min-width: 450px) {
    .ItemFeed-icon {
        max-width: 50%;
        max-height: 95px;
    }
}

@media (min-width: 768px) {
    .ItemFeed-icon {
        max-width: 65%;
        max-height: 125px;
    }
}

@media (min-width: 1440px) {
    .ItemFeed-icon {
        max-width: 50%;
    }
}
</style>
