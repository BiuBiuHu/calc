<template>
    <div>
        <label>
            <span>{{data.name}}</span>
            <input :placeholder = "data.placeholder" type="Number" v-model = "data.value" v-focus  @blur="getValue"/>
            <span>{{data.total}}</span>
        </label>
    </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  computed:{
    value(){
      return this.$props.data.value
    }
  },
  props: {
    data: {
      type: Object,
      default: function() {
        return {
          name: "default",
          value: "",
          total: "0"
        };
      }
    }
  },
  methods: {
    getValue() {
      this.$emit("newValue", this.$props.data);
    }
  },
  mounted() {
    
  },
};
</script>