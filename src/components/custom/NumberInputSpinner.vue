<template>
  <div class="d-flex">
    <BButton v-if="isBlock" squared variant="primary" @click="decrement">-</BButton>
    <button v-else class="minible-input-spinner left-spinner" @click="decrement">
      -
    </button>
    <BFormInput readonly class="minible-custom-number-input" :class="isBlock ? 'minible-custom-number-input-block' : ''" v-model="value" @input="handleInput" />
    <BButton v-if="isBlock" squared variant="primary" @click="increment">+</BButton>
    <button v-else class="minible-input-spinner right-spinner" @click="increment">
      +
    </button>
  </div>
</template>

<script>
export default {
  props: {
    min: { type: Number, default: 0 },
    max: { type: Number, default: 100 },
    modelValue: { type: Number, default: 0 },
    step: { type: Number, default: 1 },
    isBlock: { type: Boolean, default: false }
  },
  computed: {
    value: {
      get() {
        return this.$props.modelValue;
      },
      set(newValue) {
        this.$emit("input", newValue);
      }
    }
  },
  methods: {
    increment() {
      if (this.value < this.$props.max) {
        this.value = this.value + this.$props.step;
      }
    },
    decrement() {
      if (this.value > this.$props.min) {
        this.value = this.value - this.$props.step;
      }
    },
    handleInput(event) {
      // Ensure the input value stays within your desired range
      const newValue = parseInt(event.target.value);
      if (!isNaN(newValue)) {
        this.value = newValue;
      }
    }
  }
};
</script>

<style scoped lang="scss">
.minible-input-spinner {
  background: none; 
  border: 1px solid #e3e3e3;
  width: 50px;
}

.minible-custom-number-input {
  border: 1px solid #e3e3e3;
  width: 55px;
  background: #f3f3f3;
  border-radius: 0 !important;
  text-align: center;
}

.minible-custom-number-input-block {
  width: 100% !important;
}

.left-spinner {
  border-radius: 4px 0 0 4px;
}

.right-spinner {
  border-radius: 0px 4px 4px 0px;
}
</style>
