<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
   <div>{{num}}</div>
   <div>{{double1}}</div>
   <input v-model="double2" />
   <el-input v-model="demo.name"></el-input>
    {{value}}
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      num:20,
      demo: {
          name: ''
        },
        value: ''
    }
  },
    watch: {
      newName(val) {
        this.value = val;
      }
    },
  computed:{
     newName() {
        return this.demo.name;
      },
    double1(){
     return this.num*2
    },
    double2:{
       get(){
      return this.num*2
    },
    set(val){
      this.num=val/2
    }

    }
   
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
