<script>
import { defineComponent } from 'vue'
import PaletteCard from '@/components/PaletteCard.vue'
import { useFavorites } from '@/composables/favorites'

export default defineComponent({
  name: 'FavoritesView',
  components: { PaletteCard },
  setup() {
    const { favorites } = useFavorites();

    return {
      favorites
    }
  }
})
</script>

<template>
  <h2>My Favorites</h2>

  <TransitionGroup name="list" tag="section" class="favorites-view">
    <PaletteCard v-for="item in favorites" :key="item.id" is-favorite is-editable :item="item" />
  </TransitionGroup>
</template>

<style lang="scss" scoped>
.list-move,
.list-enter-active,
.list-leave-active {
  transition: transform 0.3s ease;
}

.list-leave-active {
  display: none;
}

h2 {
  margin-bottom: 3rem;
}

.favorites-view {
  position: relative;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 3em;
}
</style>
