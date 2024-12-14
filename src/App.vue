<script setup>
//importar o ref()
import { ref } from "vue"
const tarefas = ref(["Estufar vue.js", "Treinar", "Fazer comida", "Revisar os estudos", "Beber Água"])

// variável pra adicionar novas tarefas
const novaTarefa = ref("");


//função pra remover itens
function removerTarefa(index) {
  tarefas.value.splice(index, 1)
  //remove o item pela posição clicada
}

//função para adicionar
function adicionarTarefa(){
  if(novaTarefa.value.trim() !== "") {
    tarefas.value.push(novaTarefa.value.trim())
    novaTarefa.value = ""
  }
}

</script>


<template>
  <h1> Lista de Tarefas 📝 </h1>
  <div v-if="tarefas.length === 0">
    <p>CONGRATULATIONS</p>
  </div>
  <ul>
    <!--v-for : uma diretiva que serve para fazer loops-->
    <li v-for="(tarefa, index) in tarefas" :key="index"> {{ tarefa }}
      <button @click="removerTarefa(index)"> Remover ❌ </button>
    </li>
  </ul>

  <section>

    <input type="text"
    placeholder="Digite uma nova tarefa"
    v-model="novaTarefa"

    >
    <!--a diretiva v-model sincroniza um valor de uma variável ao input-->

    <button @click="adicionarTarefa">Adicionar Tarefa</button>

  </section>

</template>

<style></style>