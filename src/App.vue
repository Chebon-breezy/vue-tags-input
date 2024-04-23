<script>
import { ref, reactive, toRef, toRefs } from 'vue'

export default {
  setup() {
    const message = ref("Hello");
    const quantity = ref(1);
    const item = reactive({
      name: "product 1",
      price: 100,
    })

    const increment = () => quantity.value++;
    const decrement = () => quantity.value--;

    const swapProduct = () => {
      item.name = "product A"
      item.price = 200
    }

    // const nameRef = toRef(item, 'name');
    // console.log('nameRef:', nameRef.value);

    // item.name = "New Product"
    // console.log('nameRef:', nameRef.value);

    const itemRefs = toRefs(item)
    console.log('Name:', itemRefs.name.value);
    console.log('Price:', itemRefs.price.value);

    item.name = "Hot Product"
    item.price = 200

    console.log('Name:', itemRefs.name.value);
    console.log('Price:', itemRefs.price.value);


    return {
      message,
      quantity,
      increment,
      decrement,
      item,
      swapProduct
    };
  }
}

</script>

<template>
  <h1>{{ item.name }} : {{ item.price }}</h1>
  <button @click="swapProduct">Swap Product</button>
  <h2>{{ quantity }}</h2>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>
</template>

<style scoped></style>