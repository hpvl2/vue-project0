<template>
  <div class="root">
    <label>
      Введите email:
      <input type="number" :value="products" @input="productsInput($event.target.value)" />
    </label>
    value: {{ products }}
  </div>
</template>

<script>
export default {
  name: "MyComponent",
  data () {
    return {
      products: ''
    };
  },
  methods: {
    productsInput(value) {
      if (value >= 0 && value < 11) {
      this.products = value;
      }
      else alert('Не то число!')
    }
  },
};
</script>
