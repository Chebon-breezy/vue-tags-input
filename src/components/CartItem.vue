<script>
import { toRefs, reactive, computed } from 'vue'

export default {
  props: {
    cartItem: {
      type: Object,
      required: true
    }
  },

  setup(props) {
    const item = reactive(props.cartItem);

    const increment = () => item.quantity++;
    const decrement = () => {
      if (item.quantity > 0) {
        item.quantity--;
      }
    };

    const total = computed(() => item.price * item.quantity)

    const { name, price, quantity } = toRefs(item);

    return {
      name,
      price,
      quantity,
      increment,
      decrement,
      total
    };
  }
}
</script>

<template>
  <div>
    <h1>{{ name }}: {{ price }}: {{ quantity }}</h1>
    <button @click="increment">+</button>
    <button @click="decrement">-</button>
    <p>Total: {{ total }}</p>
  </div>
</template>

<style scoped></style>
