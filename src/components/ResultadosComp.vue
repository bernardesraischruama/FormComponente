<script setup>
defineProps({
  resultado: {
    type: Object,
    required: true
  }
});
</script>

<template>
  <div class="resultado">
    <h2>Dados do produto</h2>
    <p>Nome: {{ resultado.nome }}</p>
    <p>Email: {{ resultado.email }}</p>
    <p>Data de Nascimento: {{ resultado.datadenascimento }}</p>
    <p>Endereço: {{ resultado.endereco }}</p>
    <p>Cidade: {{ resultado.cidade }}</p>
    <p>Estado: {{ resultado.estado }}</p>
    <p>Hobbies: {{ resultado.hobbies }}</p>
    <p>Linguagens de Programação: {{ resultado.linguagensdeprogramacao }}</p>
    <p>Biografia: {{ resultado.biografia }}</p>
    <p>Idade: {{ resultado.idade }}</p>
  </div>
</template>

<style scoped>
.resultado {
  background-color: #2c3e50;
  color: #ecf0f1;
  padding: 20px;
  border-radius: 12px;
  margin-top: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}

.resultado h2 {
  font-size: 24px;
  font-weight: 600;
  margin-bottom: 16px;
  text-align: center;
}

.resultado p {
  font-size: 16px;
  line-height: 1.6;
  margin-bottom: 10px;
}

.resultado p::before {
  content: "• ";
  color: #3498db;
  font-size: 18px;
  margin-right: 8px;
}
</style>