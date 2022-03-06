<template>
  <button type="button" @click="onClickIncreaseAge">Increase age</button>
  <button type="button" @click="ageChangeFn(3)">Increase age</button>
  <button type="button" @click="onClickDecreaseAge">Decrease age</button>
  <p>The user is {{ age }} years old</p>
  <p>{{ ageDoubled }}</p>
</template>

<script>
export default {
  name: "UserComponent",
  props: {
    age: {
      type: Number,
      //required: true,
      //   default: 20,
      validator(value) {
        return value < 130;
      },
    },
    ageChangeFn: Function,
  },
  emits: ["age-change-increase", "age-change-decrease"],
  computed: {
    ageDoubled() {
      return this.age * 2;
    },
  },
  methods: {
    onClickIncreaseAge() {
      this.$emit("age-change-increase", 3);
    },
    onClickDecreaseAge() {
      this.$emit("age-change-decrease");
    },
  },
};
</script>
