<template>
  <div>
    <Message :msg="mensagem" v-show="mensagem"/>
    <form id="burger-form" @submit="createBurger($event)">
      <div class="input-container">
        <label for="nome">Nome do cliente:</label>
        <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
      </div>
      <div class="input-container">
        <label for="pao">Escolha o pão:</label>
        <select name="pao" id="pao" v-model="pao">
          <option value="">Selecione o seu pão</option>
          <option v-for="pao in paesLista" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
        </select>
      </div>
      <div class="input-container">
        <label for="carne">Escolha a carne do seu Burger:</label>
        <select name="carne" id="carne" v-model="carne">
          <option value="">Selecione o tipo da carne</option>
          <option v-for="carne in carnesLista" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
        </select>
      </div>
      <div id="opcionais-container" class="input-container">
        <label id="opcionais-titulo" for="opcionais">Selecione os opcionais:</label>
        <div class="checkbox-container" v-for="opcional in opcionaisLista" :key="opcional.id">
          <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
          <span>{{ opcional.tipo }}</span>
        </div>
      </div>
      <div class="input-container">
        <button type="submit">Criar meu Burger</button>
      </div>
    </form>
  </div>
</template>

<script>
import Message from './Message.vue'

export default {
  name: 'BurgerForm',
  components: {
    Message 
  },
  data() {
    return {
      paesLista: null,
      carnesLista: null,
      opcionaisLista: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      mensagem: null
    }
  },
  methods: {
    async getIngredientes() {
      const response = await fetch('http://localhost:3000/ingredientes')
      const data = await response.json()
      
      this.paesLista = data.paes
      this.carnesLista = data.carnes
      this.opcionaisLista = data.opcionais
    },

    async createBurger(event) {
      event.preventDefault();

      const data = {
        nome: this.nome,
        pao: this.pao,
        carne: this.carne,
        opcionais: Array.from(this.opcionais),
        status: 'Solicitado'
      }

      const response = await fetch('http://localhost:3000/burgers', {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify(data)
      });

      const resobj = await response.json();

      this.mensagem = `Pedido Nº ${resobj.id} realizado com sucesso`;

      setTimeout(() => this.mensagem = '', 3000);

      // limpando os campos
      this.nome = '';
      this.pao = '';
      this.carne = '';
      this.opcionais = '';
    }
  },
  mounted() {
    this.getIngredientes()
  }
}
</script>

<style scoped>
#burger-form {
  max-width: 400px;
  margin: 0 auto;
  border: solid rgba(0, 0, 0, 0.12) 2px;
  border-radius: 5px;
  padding: 30px;
}

.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  padding: 5px 10px;
  border-left: 4px solid #fccf3f;
}

input, select {
  padding: 5px 10px;
  width: 300px;
}

select {
  height: 36px;
  border: solid rgba(0, 0, 0, 0.12) 2px;
  border-radius: 5px;
  background-color: white;
}

input[type=text] {
  height: 22px;
  border: solid rgba(0, 0, 0, 0.12) 2px;
  border-radius: 5px;
  background-color: white;
}

#opcionais-container {
  flex-direction: row;
  flex-wrap: wrap;
}

/* #opcionais-titulo {
  width: 100%;
} */

.checkbox-container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}

.checkbox-container span, input {
  width: auto;
}

.checkbox-container span {
  margin-left: 5px;
}

button {
  /* margin-left: 426px; */
  margin-top: 10px;
  border: solid rgba(0, 0, 0, 0.12) 2px;
  background-color: white;
  height: 36px;
  min-width: 64px;
  max-width: 150px;
  border-radius: 5px;
  padding-left: 16px;
  padding-right: 16px;
  align-self: flex-end;
}

button:hover {
  background-color: rgba(0, 0, 0, 0.05);
}

button:active {
  background-color: rgba(0, 0, 0, 0.15);
}
</style>