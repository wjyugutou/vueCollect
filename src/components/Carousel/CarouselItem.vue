<script lang='ts' setup>
import type { PropType } from 'vue'
import { currentIndexKey } from '.'
const props = defineProps({
  data: {
    type: Object as PropType<{
      url: string
      title: string
    }>,
    required: true,
  },
})
const currentIndex = inject(currentIndexKey)
const state = reactive({
  selfIndex: getCurrentInstance()?.vnode.key,
})
</script>

<template>
  <transition name="carousel">
    <div v-show="currentIndex === state.selfIndex" class="carouselItem" w-full h-full absolute origin-top-left>
      <img w-full h-full :src="data.url" :alt="data?.title">
    </div>
  </transition>
</template>

<style scoped>
.carousel-enter-active,
.carousel-leave-active {
  transition: all 0.5s linear;
}

.carousel-enter-active {
  transform: translateX(100%);
}
.carousel-enter-to {
  transform: translateX(0);
}
.carousel-leave-active {
  transform: translateX(-100%);
}
</style>
