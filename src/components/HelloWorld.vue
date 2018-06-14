<template>
  <div class="hello">
      <label><input type="text" :placeholder = "'条目名称'"/>
          <button>增加新条目</button>
      </label><br>


      <label><input type="text" :value = "a"/></label>
      <label><input type="text" :value = "b"/></label>
      <label><input type="text" :value = "c"/></label>
      <label><input type="text" :value = "d"/></label>
      <label><input type="text" :value = "youhui"/></label>
      <clac-input></clac-input>
      <p>结果：{{result}}</p>
      <button @click="heji"> 计算</button><br>
      <label><span>a: </span><span>{{aPay}}</span></label><br>
      <label><span>b: </span><span>{{bPay}}</span></label><br>
      <label><span>c: </span><span>{{cPay}}</span></label><br>
      <label><span>allPay: </span><span>{{allPay}}</span></label><br>
  </div>
</template>

<script>
    import clacInput from "./input.vue";
export default {
  name: 'HelloWorld',
  components:{
    clacInput
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      a:25,
      b:28,
      c:20,
      d:9.5,
      youhui:25,
      result:'',
      aPay:'',
      bPay:'',
      cPay:'',
      allPay:'',
    }
  },
  methods:{
    heji(){
      let all = parseInt(this.a) + parseInt(this.b) + parseInt(this.c) + parseInt(this.d);
      let all2 = parseInt(this.a) + parseInt(this.b) + parseInt(this.c) + parseInt(this.d) - parseInt(this.youhui);
      let yunfei = parseFloat((parseFloat(this.d) / 3).toFixed(2));

      let a1 = ((this.a + yunfei )/all).toFixed(2);
      let b1 = ((this.b + yunfei )/all).toFixed(2);
      let c1 = ((this.c + yunfei )/all).toFixed(2);
      console.log(a1,b1,c1);
      this.result = all2;
      this.aPay = all2*a1;
      this.bPay = all2*b1;
      this.cPay = all2*c1;
      this.allPay = this.aPay + this.bPay + this.cPay;
    },
    addNewItem(){

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
