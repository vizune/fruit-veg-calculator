<template>
    <div 
    v-if="feed"
    class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-5 gap-4 md:gap-6">
        <div 
            v-for="(item, index) in feed" 
            :key="index"
            class="flex flex-col justify-content items-center border-black border-2 border-solid rounded p-4 md:p-6 md:max-w-xs">
                <svg-icon  
                    :name="`${category}/${item.icon}`" 
                    :title="`${item.title} item`"
                    class="ItemFeed-icon"
                />
                <p class="font-bold mt-6 text-lg text-center">{{item.title}}</p>
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
</style>
