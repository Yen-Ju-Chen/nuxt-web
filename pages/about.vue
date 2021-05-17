
<script>
export default {
  head() {
    return {
    title: this.title,
    meta: [
      {
        hid: 'description',
        name: 'description',
        content: '關於頁面'
      }
    ],
    };
  },
  data(){
    return{
    title: "Cyn"
    };
  }
}
</script>
<template>
  <div>
      <h1>About</h1>
  </div>
</template>
<style>

</style>
