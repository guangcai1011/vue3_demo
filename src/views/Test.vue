<template>
  <div class="home">
    <input v-model="firstName" /><br />
    <input v-model="lastName" /><br />
    <!-- <button @click="handleClick"></button> -->
    <div>{{ fullName }}</div>
  </div>
</template>

<script>
export default {
  name: "Test",
  data() {
    return {
      firstName: "zhang",
      lastName: "san",
      fullName: ""
    };
  },
  // computed:{
  //   fullName(){
  //     return this.firstName + "-" + this.lastName
  //   }
  // }
  watch: {
    firstName(val) {
      this.fullName = val + "-" + this.lastName;
    },
    lastName(val) {
      this.fullName = this.firstName + "-" + val;
    }
  }
};
</script>

<style lang="sass" scoped></style>
