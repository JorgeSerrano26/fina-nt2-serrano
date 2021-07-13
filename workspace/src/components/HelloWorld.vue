<template>
  <div class="hello">
    <input v-model="text" />
    <div v-if="text.length > 0">
      <p>Largo {{ text.length }}</p>
      <p>{{code()}}</p>
      <p>{{mayus()}}</p>
      <p>{{min()}}</p>
      <p>{{intercalado(true)}}</p>
      <p>{{intercalado(false)}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      text: ''
    }
  },
  methods: {
    code(){
      return this.text.toLowerCase().split('').map(letra => {
        if(letra === 'a') {
          return 'u';
        }else if(letra === 'e'){
          return 'o';
        } else if(letra === 'o'){
          return 'e';
        } else if(letra === 'u'){
          return 'a';
        }
        return letra;
      }).join('')
    },
    mayus(){
      return this.text.toUpperCase();
    },
    min(){
      return this.text.toLowerCase();
    },
    intercalado(par){
      return this.text.split('').map((letra, indice) => {
        if( (indice % 2 === 0) === par){
          return letra.toUpperCase()
        }
        return letra;
      }).join('');
    }
  },
}
</script>
