<template>
  <div id="app">
    <input type="number" v-model="limit" />
    <Numbers :limit="limit"/>
  </div>
</template>

<script>
import Numbers from '@/components/Numbers';

export default {
  name: 'App',
  components: {Numbers},
  data()
  {
    return {
      limit: 100
    }
  }
}
</script>

<style scoped>
#app{
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px 40px;
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
  align-items: center;
}
input{
  padding: 5px 15px;
  border: 1px solid hsl(0, 0%, 85%);
  font-size: 90%;
  border-radius: 4px;
  outline: none;
  margin-bottom: 20px;
  /* max-width: 200px; */
}
input:hover{
  border-color: hsl(0, 0%, 75%);
}

input:focus{
  border-color: hsl(0, 0%, 65%);
}
</style>
