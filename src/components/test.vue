<template>
    <div class="hello">
        <h3>AA分账</h3>
        <label><input type="text" :placeholder = "'条目名称'" :value="template.data.name"/>
            <button @click="addNewItem">Add</button>
        </label><br>
        <solt v-for="(item,index) in group" :is="item.componentName" :key="index" :data="item.data">

        </solt>
        <br>
        <br>
        <clac-input :data="canhe"></clac-input>
        <clac-input :data="yunfei"></clac-input>
        <clac-input :data="youhui"></clac-input>
        <p>结果：{{result}}</p>
        <button @click="heji"> 计算</button><br>
    </div>
</template>

<script>
  //TODO 当keyUp时将输入框中的数据，写入到对象中
  import clacInput from "./input.vue";
  export default {
    name: 'HelloWorld',
    components:{
      clacInput
    },
    data () {
      return {
        canhe:{
          name:"餐盒费",
          value:5
        },
        yunfei:{
          name:"运费",
          value:5
        },
        youhui:{
          name:"优惠",
          value:20
        },
        template:{
          componentName:"clacInput",
          data:{
            name:"宋飞",
            value:0,
            percent:0,
            total:0
          }
        },
        group:[

        ],
        result:0,
        index:0,
      }
    },
    methods:{
      heji(){
        this.result = 0;
        for(let item of this.group){
          this.result =  this.result + parseFloat(item.data.value);
        }
        let other = parseInt(this.canhe.value) + parseInt(this.yunfei.value);
        let all1 = this.result + other;
        let all = this.result + other - parseInt(this.youhui.value);

        this.result = all;

        if(this.group.length <= 0){
          return "暂无数据";
        }

        let fenTan = parseFloat((other/this.group.length).toFixed(1));
        console.log(all,fenTan);
        for(let item of this.group){
            console.log("value",item.data.value);
          let percent = parseFloat(((parseFloat(item.data.value) + fenTan)/all1).toFixed(2));
          item.data.percent = percent;
          console.log(all,percent,percent*all);
          item.data.total = parseFloat(percent*all).toFixed(1);
        }
      },
      addNewItem(){
        this.index++;
        this.template.data.name = "宋飞" + this.index;
        let temp = JSON.parse(JSON.stringify(this.template));
        this.group.push(temp);
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
