<template>
    <div>
        <label>
            <span>{{data.name}}</span>
            <input :placeholder = "data.name" :value = "data.value" @click="getValue"/>
            <span>{{data.total}}</span>
        </label>
    </div>
</template>
<script>
  export default {
    data() {
      return {}
    },
    props:{
      data:{
        type:Object,
        default:function () {
          return {
            name:"default",
            value:"",
            total:'0'
          };
        }
      },
      methods:{
        getValue(){
          console.log(this.$props.data.value);
          this.$emit('newValue',this.$props.data.value);
        }
      }
    }


  }
</script>