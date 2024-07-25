<template>
  <main>
    <Formulario :produto="produto" @submit="mostrarResultado" />
    <Resultados v-if="validate" :resultado="resultado" />
  </main>
</template>

<script setup>
import { ref, reactive } from 'vue';
import Formulario from './components/FormularioComp.vue';
import Resultados from './components/ResultadosComp.vue';

const produto = reactive({
  nome: '',
  email: '',
  senha: '',
  confirmarsenha: '',
  datadenascimento: '',
  endereco: '',
  cidade: '',
  estado: '',
  hobbies: '',
  linguagensdeprogramacao: '',
  biografia: '',
  idade: null
});

const validate = ref(false);
const resultado = ref(null);

function mostrarResultado(produto) {
  if (
    produto.nome.length < 3 || produto.nome.length > 20 ||
    produto.idade < 18 || produto.idade > 60 ||
    produto.confirmarsenha !== produto.senha ||
    !produto.email.includes('@') ||
    produto.senha === '' ||
    produto.email === '' ||
    produto.datadenascimento === '' ||
    produto.endereco === '' ||
    produto.cidade === '' ||
    produto.estado === '' ||
    produto.hobbies === '' ||
    produto.linguagensdeprogramacao === '' ||
    produto.biografia === ''
  ) {
    alert('Credenciais inválidas ou campos não preenchidos!');
  } else {
    resultado.value = { ...produto };
    validate.value = true;
  }
}
</script>