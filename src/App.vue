<template>
  <h3>Hey</h3>
  <greeting :age="age"></greeting>
  <user
    :age="age"
    @age-change-increase="updateAge"
    @age-change-decrease="age--"
    :ageChangeFn="updateAgeCB"
  ></user>
</template>

<script>
import Greeting from "./components/GreetingComponent.vue";
import User from "./components/UserComponent.vue";

export default {
  name: "App",
  components: {
    Greeting,
    User,
  },
  data() {
    return {
      age: 20,
    };
  },
  methods: {
    updateAge(num) {
      if (this.age + num > 130) {
        this.age = 130;
        return;
      }
      this.age += num;
    },
    updateAgeCB(num) {
      this.age += num;
    },
  },
};
</script>
