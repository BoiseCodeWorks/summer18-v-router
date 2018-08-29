<template>
  <div class="dragons">
     <div class="loading" v-if="dragons.length == 0">beware here be dragons</div>
      <div class="dragon" v-else v-for="dragon in dragons" :key="dragon.id" @click="setDragon(dragon)">
        {{dragon.name}}
      </div>
  </div>
</template>

<script>
export default {
  beforeCreate() {
    console.log("before create");
  },
  created() {
    console.log("created");
  },
  mounted() {
    console.log("mounted");
    this.$store.dispatch("getDragons");
  },
  beforeDestroy() {
    console.log("about to die");
  },
  destroyed() {
    console.log("dragons are dead what is this?");
  },
  computed: {
    dragons() {
      return this.$store.state.dragons;
    }
  },
  methods: {
    setDragon(dragon) {
      this.$store.dispatch("setDragon", dragon);
    }
  }
};
</script>
