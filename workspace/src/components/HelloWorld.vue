<template>
  <div class="hello">
    <input v-model="text" />
    <div v-if="text.length > 0">
      <p>Largo {{ text.length }}</p>
      <p>{{text | code}}</p>
      <p>{{text | mayus}}</p>
      <p>{{text | min}}</p>
      <p>{{text | intercalado(true)}}</p>
      <p>{{text | intercalado(false)}}</p>
    </div>
    <hr>
    <div>
      Respuestas
      <h1>1. B</h1>
      <h1>2. B</h1>
      <h1>3. D</h1>
      <h1>4. B</h1>
      <h1>5. </h1>
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
  filters: {
    code(txt){
      return txt.toLowerCase().split('').map(letra => {
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
    mayus(txt){
      return txt.toUpperCase();
    },
    min(txt){
      return txt.toLowerCase();
    },
    intercalado(txt,par){
      return txt.split('').map((letra, indice) => {
        return ( (indice % 2 === 0) === par) ? letra.toUpperCase() : letra;
      }).join('');
    }
  },
}
</script>
