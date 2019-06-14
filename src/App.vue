<template>
  <div id="app">
    <el-row>
      <el-col class="centered" :span="12">
        <claim-request-form/>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import ClaimRequestForm from "./components/ClaimRequestForm.vue";

export default {
  name: "app",
  components: {
    HelloWorld,
    ClaimRequestForm
  },

  data: function() {
    return {};
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.centered {
  margin: auto;
  float: none !important;
  /* important overides the styles */
}
</style>
