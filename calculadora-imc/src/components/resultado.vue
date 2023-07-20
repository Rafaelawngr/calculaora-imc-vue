<template>
  <div class="content">
    <div class="result-borda">
      <div class="result">
        <div class="valor">
          {{ displayValorImc }}
        </div>
        <div class="classification-title">Classificação:
        </div>
        <div class="classification">
          {{ classificacaoImc }}
        </div>
      </div>
    </div>
    <div>
    </div>
    <button class="btn-voltar" @click="goBack"><span class="material-symbols-outlined">
arrow_back
</span>Voltar
    </button>
  </div>
</template>

<script>

import {ref, watch} from 'vue'
import TitleComponent from "@/components/titulo.vue";

export default {
  name: 'ResultsComponent',

  props: {
    valorimc: Number
  },
  emits: ['go-back'],
  components: {
    TitleComponent
  },
  setup(props, {emit}) {

    const goBack = () => {
      emit("go-back")
    }

    let classificacaoImc = ref("");
    let displayValorImc = ref("")

    console.log(props.valorimc)

    watch(() => props.valorimc, (novoValor, valorAntigo) => {
      if (novoValor !== valorAntigo) {
        if (props.valorimc < 18.5) {
          classificacaoImc.value = "Abaixo do peso";
        } else if (props.valorimc <= 25) {
          classificacaoImc.value = 'Peso normal';
        } else if (props.valorimc <= 30) {
          classificacaoImc.value = 'Sobrepeso';
        } else if (props.valorimc <= 35) {
          classificacaoImc.value = 'Obesidade grau I';
        } else if (props.valorimc <= 40) {
          classificacaoImc.value = 'Obesidade grau II';
        } else {
          classificacaoImc.value = 'Obesidade grau III';
        }

        displayValorImc.value = props.valorimc.toFixed(1)
        console.log(classificacaoImc.value, displayValorImc.value)
      }

    });

    return {
      classificacaoImc,
      displayValorImc,
      goBack
    }
  }
}

</script>

<style scoped>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 50px;
}

.result-borda {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 340px;
  height: 340px;
  border-radius: 340px;
  background: #1D1D1D;
  position: relative;
}

.result {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 300px;
  height: 300px;
  border-radius: 300px;
  background: var(--botoes);
  position: absolute;

}

.valor {
  font-family: 'Trispace', sans-serif;
  font-size: 80px;
  font-weight: 700;
  background-color: transparent;
  padding: 20px;
}

.classification-title {
  font-size: .80rem;
  font-weight: 400;
  background-color: transparent;
}

.classification {
  font-size: 1.2rem;
  font-weight: 500;
  background-color: transparent;
}

.btn-voltar {
  display: flex;
  font-size: 1rem;
  font-weight: 400;
  border: none;
  cursor: pointer;
  gap: 10px;
}

.btn-voltar:hover {
  color: var(--botoes);
  transform: scale(1.05);
  transition: 200ms linear;
}

.material-symbols-outlined {
  font-variation-settings: 'FILL' 0,
  'wght' 400,
  'GRAD' 0,
  'opsz' 16
}

</style>