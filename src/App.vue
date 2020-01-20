<template>
  <div id="app">
    <h1>Computed Properties</h1>
    <button @click="a++">Add to A</button>
    <button @click="b++">Add to B</button>
    <p>A = {{a}}</p>
    <p>B = {{b}}</p>
    <p>Age + A = {{addToAbyM()}}</p>
    <p>Age + B = {{addToBbyM()}}</p>
    <p>Age + A = {{addToAbyC}}</p>
    <p>Age + B = {{addToBbyC}}</p>
    <button @click="watchme">Watch Me</button>
    <p>Age = {{age}}</p>
    <hr>
    <input v-model="name"/>
    <p>{{"Method : " + lowerCase()}}</p>
    <p>{{"Computed : " + lowerCaseName}}</p>
    <p>{{"Watch : " + lcName}}</p>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return{
      age:20,
      a:0,
      b:0,
      name :'NENCY',
      lcName : 'nency'
    }
  },

  methods: {
    addToAbyM(){
      console.log('method:addToA')
      return this.a + this.age
    },
    addToBbyM(){
      console.log('method:addToB')
      return this.b + this.age
    },
    watchme(){ 
       this.age++;
    },
    lowerCase(){
      return this.name.toLowerCase();
    }
  },

  computed: {
    addToAbyC(){
      console.log('computed:addToA')
      return this.a + this.age
    },
    addToBbyC(){
      console.log('computed:addToB')
      return this.b + this.age
    },
    lowerCaseName(){
      return this.name.toLowerCase();
    }

  },

  watch: {
    age: function(newValue,oldValue){
      console.log('watch:age changed')
      console.log(newValue,oldValue)
    },
    name: function(){
      this.lcName = this.name.toLowerCase();
      console.log(this.lcName)
    }
  }
}
</script>

<style>

button{
  margin : 2px;
}

p{
  margin-left: 2px;
}
</style>
