<script setup>
import { ref, reactive, watch } from 'vue';

const props = defineProps({
  produto: {
    type: Object,
    required: true
  }
});

const emit = defineEmits(['submit']);

const estados = ref([
  { cod: 'AC', nome: 'Acre' },
  { cod: 'AL', nome: 'Alagoas' },
  { cod: 'AP', nome: 'Amapá' },
  { cod: 'AM', nome: 'Amazonas' },
  { cod: 'BA', nome: 'Bahia' },
  { cod: 'CE', nome: 'Ceará' },
  { cod: 'DF', nome: 'Distrito Federal' },
  { cod: 'ES', nome: 'Espírito Santo' },
  { cod: 'GO', nome: 'Goiás' },
  { cod: 'MA', nome: 'Maranhão' },
  { cod: 'MT', nome: 'Mato Grosso' },
  { cod: 'MS', nome: 'Mato Grosso do Sul' },
  { cod: 'MG', nome: 'Minas Gerais' },
  { cod: 'PA', nome: 'Pará' },
  { cod: 'PB', nome: 'Paraíba' },
  { cod: 'PR', nome: 'Paraná' },
  { cod: 'PE', nome: 'Pernambuco' },
  { cod: 'PI', nome: 'Piauí' },
  { cod: 'RJ', nome: 'Rio de Janeiro' },
  { cod: 'RN', nome: 'Rio Grande do Norte' },
  { cod: 'RS', nome: 'Rio Grande do Sul' },
  { cod: 'RO', nome: 'Rondônia' },
  { cod: 'RR', nome: 'Roraima' },
  { cod: 'SC', nome: 'Santa Catarina' },
  { cod: 'SP', nome: 'São Paulo' },
  { cod: 'SE', nome: 'Sergipe' },
  { cod: 'TO', nome: 'Tocantins' }
]);

const produtoLocal = reactive({ ...props.produto });

watch(props.produto, (newVal) => {
  Object.assign(produtoLocal, newVal);
});

function handleSubmit() {
  emit('submit', produtoLocal);
}
</script>

<template>
  <section class="container d-flex flex-row gap-3 principal">
    <div class="formulario">
      <h2>Cadastro do produto</h2>

      <div class="form-group">
        <label for="">Nome: </label>
        <input class="form-control" v-model="produtoLocal.nome" />
      </div>

      <div class="form-group">
        <label for="">Email: </label>
        <input class="form-control" v-model="produtoLocal.email" />
      </div>

      <div class="form-group">
        <label for="">Senha: </label>
        <input class="form-control" type="password" v-model="produtoLocal.senha" />
      </div>

      <div class="form-group">
        <label for="">Confirmar senha: </label>
        <input class="form-control" type="password" v-model="produtoLocal.confirmarsenha" />
      </div>

      <div class="form-group">
        <label for="">Data de Nascimento: </label>
        <input type="date" v-model="produtoLocal.datadenascimento" />
      </div>

      <div class="form-group">
        <label for="">Endereço: </label>
        <input class="form-control" v-model="produtoLocal.endereco" />
      </div>

      <div class="form-group">
        <label for="">Cidade: </label>
        <input class="form-control" v-model="produtoLocal.cidade" />
      </div>

      <div class="form-group">
        <label for="">Estado: </label>
        <select name="estado" id="estado" v-model="produtoLocal.estado">
          <option v-for="estado in estados" :key="estado.cod" :value="estado.cod">
            {{ estado.nome }}
          </option>
        </select>
      </div>

      <div class="form-group">
        <label for="">Hobbies: </label>
        <input class="form-control" v-model="produtoLocal.hobbies" />
      </div>

      <div class="form-group">
        <label for="">Linguagens de Programação: </label>
        <input class="form-control" v-model="produtoLocal.linguagensdeprogramacao" />
      </div>

      <div class="form-group">
        <label for="">Biografia: </label>
        <input class="form-control" v-model="produtoLocal.biografia" />
      </div>

      <div class="form-group">
        <label for="">Idade: </label>
        <input class="form-control" type="number" v-model="produtoLocal.idade" />
      </div>

      <div class="caixa-btn">
        <button class="btn" @click="handleSubmit">Enviar</button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.formulario {
  background-color: #f9f9f9;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 20px;
  max-width: 800px;
  margin: 20px auto;
}
.formulario h2 {
  font-size: 28px;
  font-weight: 600;
  color: #333;
  margin-bottom: 20px;
  text-align: center;
}
.form-group {
  margin-bottom: 15px;
}
.form-group label {
  font-size: 16px;
  color: #555;
  display: block;
  margin-bottom: 5px;
}
.form-control {
  width: 100%;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  box-sizing: border-box;
  font-size: 16px;
  color: #333;
}
.form-control:focus {
  border-color: #3498db;
  outline: none;
  box-shadow: 0 0 3px rgba(0, 123, 255, 0.5);
}
select.form-control {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  background: #fff url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="10" height="6" viewBox="0 0 10 6"><path fill="none" stroke="%23555" stroke-width="1" d="M1 1l4 4 4-4"/></svg>') no-repeat right 10px center;
  background-size: 12px;
}
.caixa-btn {
  text-align: center;
}
.btn {
  background-color: #3498db;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
.btn:hover {
  background-color: #2980b9;
}
</style>