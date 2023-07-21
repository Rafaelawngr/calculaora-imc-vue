<script>

import {ref} from 'vue'

export default {
  name: 'HistoricoComponent',
  props: {
    historico: {
      type: Array,
      required: true
    }
  },
  setup(props) {
    return {
      props
    }
  }
}

</script>

<template>

  <div class="historico">
    <div class="historico-title">
      <h1>Histórico de IMC</h1></div>
    <div>
      <div class="historico-legend">
        <p>Nome </p>|
        <p>Altura </p>|
        <p>Peso </p>|
        <p>IMC</p>
      </div>
      <div class="historico-content" v-for="user in props.historico" :key="user.id">
        <td> {{ user.nome }} </td> 
        <td> {{ user.altura }} </td>
        <td> {{ user.peso }} </td> 
        <td> {{ user.imc }} </td>
      </div>
    </div>
  </div>
</template>

<style>

.historico {
  margin-top: 50px;
  padding: 8px;
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 2px solid #1D1D1D;
  border-radius: 16px;
  overflow-y: scroll;
  height: 23vh;

}

.historico::-webkit-scrollbar-track {
  background: transparent;
  border-radius: 2px;
}
::-webkit-scrollbar {
  width: 4px;
  background: transparent;
}

::-webkit-scrollbar-thumb {
  background: #575757;
  border-radius: 5px;
}

.historico-title h1 {
  font-size: .9rem;
  font-weight: 300;
  border-bottom: 2px solid #1d1d1d;
}

.historico-content {
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid #1d1d1d;
  font-size: .75rem;
  font-weight: lighter;
  list-style: none;
}

.historico-legend {
  display: flex;
  font-size: .8rem;
  font-weight: 300;
  gap: 20px;
  align-items: center;
}

td {
  padding: 10px 0;
}


</style>