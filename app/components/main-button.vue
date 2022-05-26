<template>
  <button
  v-if="id" 
  @click="$emit('category-selected', id)"
  class="border-black border-2 border-solid rounded p-6 md:p-8 md:max-w-sm">
    <div class="flex flex-col justify-center items-center">
      <svg-icon 
        v-if="icon" 
        :name="`main/${icon}`" 
        :title="`${title} category`"
       />
      <p 
      v-if="title" 
      class="font-bold mt-4 text-lg md:text-xl">
        {{title}}
      </p>
    </div>
  </button>
</template>

<script>
export default {
  name: "MainButton",
  props: {
      id: {
        type: String,
        required: true
      },
      title: {
        type: String
      },
      icon: {
        type: String
      }
  }
}
</script>
