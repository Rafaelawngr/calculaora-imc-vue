<script>


export default {
  name: 'HistoricoComponent'
}

</script>

<template>
  <div class="historico">
    <div class="historico-title">
      <h1>Histórico de IMC</h1></div>
    <div class="historico-content">
      <ul>
        <li>valor 01</li>
        <li>valor 02</li>
        <li>valor 03</li>
        <li>valor 04</li>
        <li>valor 05</li>
      </ul>
    </div>
  </div>
</template>

<style>

.historico {
  margin-top: 50px;
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 2px solid #1D1D1D;
  border-radius: 16px;
}

.historico-title h1 {
  font-size: .9rem;
  font-weight: 300;
  border-bottom: 2px solid #1d1d1d;
}

.historico-content li {
  font-size: .75rem;
  font-weight: lighter;
  list-style: none;
  margin-bottom: 5px;
}

</style>