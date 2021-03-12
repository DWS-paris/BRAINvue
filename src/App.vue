<template>
  <router-view :key="$route.fullPath"></router-view>
</template>

<script>
  export default {
    name: 'App',
    data(){
      return{
        user: undefined
      }
    },
    created(){
      this.$store.dispatch('checkUser')

      this.$store.subscribe((mutations,/*  state */) => {
        // Check mutation*/
        if( mutations.type === "USER" ){
            // Update display
            this.user = mutations.payload.data;
            console.log(this.user)
        }
      })
    }
  }
</script>