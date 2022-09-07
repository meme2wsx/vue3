<script lang="ts">
  import { Vue } from 'vue-class-component'

  export default class HelloWorld extends Vue {
    msg = "Vueで羊をかぞえる"
    val = 1

    doAction() : void {
      this.val += 1
    }
  }
</script>

<template>
  <h1 class="bg-info text-white p-2">{{ msg }}</h1>
  <div class="container">
    <h2 class="my-2">枠内をクリックしてください</h2>
    <div class="alert alert-info">
      <h3 v-on:click="doAction">羊が {{ val }} 匹</h3> 
    </div>
    <h5>画面リロードでリセットします</h5>
  </div>
  
</template>