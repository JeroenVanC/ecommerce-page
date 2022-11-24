<script setup lang="ts">
const test = ref()
</script>

<template>
  <div class="w-full flex flex-row">
    <div class="btn btn-primary max-w-max">
      Dit is een test component
    </div>
    <div class="bg-red-600 flex items-center justify-center px-8 py-2 m-6 rounded-xl transition-all ease-in-out duration-300 hover:shadow-lg hover:shadow-red-100 hover:scale-[1.07]">
      <p class="text-white">
        test
      </p>
    </div>
  </div>
</template>
