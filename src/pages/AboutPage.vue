<template>
  <div class="about">
    <input type="text" v-model="message" />

    <q-btn
      @click="clearMessage"
      style="background: #ff0080; color: white; margin-left: 2px"
      glossy
      unelevated
      icon="clear"
      label="Clear"
    />
    <h3>{{ message }}</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "I Love Quasar",
    };
  },
  methods: {
    clearMessage() {
      return (this.message = "");
    },
  },
  name: "aboutPage",
};
</script>

<style scoped>
.about {
  text-align: center;
}
.about input {
  margin: 20px auto;
  width: 200px;
  height: 33px;
  border: 2px solid rgb(14, 11, 11);
  padding: 10px;
  color: black;
  font-weight: bold;
}
</style>
