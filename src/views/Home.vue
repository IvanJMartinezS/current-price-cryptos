<template>
  <div>
    <Data :assets="assets" />
  </div>
</template>

<script>
import api from "../api"; 
import Data from "@/components/Data";
export default {
  name: "Home",
  components: { Data }, 
  data() {
    return {
      assets: []
    };
  },
  created() {
    api.getAssets().then(assets => (this.assets = assets));
  }
};
</script>
