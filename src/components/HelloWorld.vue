<script lang="tsx">
  import { VNode } from 'vue'
  import { Vue } from 'vue-class-component'
  
  export default class HelloWorld extends Vue {
    msg = "カウンター"
    val = 1

    doAction() : void {
      this.val += 1
    }

    get sum(): number {
      let re = 0
      for (let i = 1; i <= this.val; i++) {
        re += i
      }
      return re
    }

    render():VNode{
      return(<div>
        <h1 class="bg-info text-white p-2">{this.msg}</h1>
        <div class="container">
          <h2 class="my-2">枠内をクリックしてください</h2>
          <div class="alert alert-info">
            <h3 onclick={this.doAction}>{this.val} </h3>
             <h8>(合計: {this.sum})</h8>
          </div>
        </div>
      </div>)
  }
}
</script>