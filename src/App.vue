<script setup>
import { reactive } from 'vue';
import 'bootstrap/dist/css/bootstrap.min.css'
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';

  const estado = reactive({

    primeiroNumeroDigitado: 0,
    segundoNumeroDigitado: 0,
    resultado: 0,
    operacao: '',

  })

  function somar(){
    estado.resultado = Number(estado.primeiroNumeroDigitado) + Number(estado.segundoNumeroDigitado);
  }
  function subtrair(){
    estado.resultado = estado.primeiroNumeroDigitado - estado.segundoNumeroDigitado;
  }
  function multiplicar(){
    estado.resultado = estado.primeiroNumeroDigitado * estado.segundoNumeroDigitado;
  }
  function divisao(){
    estado.resultado = estado.primeiroNumeroDigitado / estado.segundoNumeroDigitado;
  }

  function alteraPrimeiroValor(evento){
    estado.primeiroNumeroDigitado = evento.target.value;
  }

  function alteraSegundoValor(evento){
    estado.segundoNumeroDigitado = evento.target.value
  }

  const operacaoSelecionada = (evento) => {
    estado.operacao = evento.target.value;
    switch (estado.operacao){
      case 'somar':
        somar();
        break;
      case 'subtrair':
        subtrair();
        break;
      case 'multiplicar':
        multiplicar();
        break;
      case 'divisao':
        divisao();
        break;
    }
  }
</script>

<template>

<div class="container bg-light text-center">
<Cabecalho/>

<br>
<br>
<span class="bg-secondary-subtle p-3"><strong>Resultado:</strong> {{ estado.resultado }}</span>
<br>
<br>

<input type="number" @keyup="alteraPrimeiroValor" placeholder="primeiro valor"><br> 
<input type="number" @keyup="alteraSegundoValor" placeholder="segundo valor"><br>
<br>

<Formulario :set-operacao-selecionada="operacaoSelecionada" />




</div>



</template>

<style scoped>

</style>
