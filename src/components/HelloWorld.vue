<script lang="tsx">
  import { VNode } from 'vue'
  import { Vue } from 'vue-class-component'
  

  export default class HelloWorld extends Vue {
    msg = "Calc App"
    val = 0
    inputdata = new Array<number>()
    

    doChange(event:Event):void {
      const ob = event.target as HTMLInputElement
      const re = Number(ob.value)
      this.val = re
    }

    doAction() : void {
      this.doCalc()
    }


    doCalc():void{
      const arr:number[] = []
      for (let item of this.inputdata)
        arr.push(item)
      arr.push(this.val)
      this.inputdata = arr
      this.val = 0
    }

    doType(event:KeyboardEvent):void {
      if(event.code == 'Enter'){
        const ob = event.target as HTMLInputElement
        const re = Number(ob.value)
        this.val = re
        this.doCalc()
      }
    }

    render():VNode{
      let total = 0
      return(<div>
        <h1 class="bg-info text-white p-2">{this.msg}</h1>
        <div class="container">
          <h2 class="my-3">数字を入力してね</h2>
          <div class="alert alert-info">
            <div class="row px-2">
              <input type="number" class="col" onChange={this.doChange} onKeypress={this.doType} value={this.val} />
              <button onClick={this.doAction} class="btn btn-ingo col-2">
                Click
              </button>
            </div>
          </div>
          <table class="table">
            <thead><tr><th>値</th><th>合計</th></tr></thead>
          <tbody>
            {this.inputdata.map((v, k) => {
              total += v
              return <tr key={k}><td>{v}</td><td>{total}</td></tr>
            })}
          </tbody>
          </table>
        </div>       
    </div>)
  }
}
</script>