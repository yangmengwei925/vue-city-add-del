<template>
  <div class="home">
    <HelloWorld />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>
<style scoped >
.home,html,body{
 width:100%;
 height: 100%;
 display: flex;
 flex-direction: column
 
}
</style>
