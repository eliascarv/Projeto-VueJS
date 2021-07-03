<template>
  <div>
    <p>Componte de Mensagem</p>
    <form id="burger-form">
      <div class="input-container">
        <label for="nome">Nome do cliente:</label>
        <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
      </div>
      <div class="input-container">
        <label for="pao">Escolha o pão:</label>
        <select name="pao" id="pao" v-model="pao">
          <option value="">Selecione o seu pão</option>
          <option value="integral">Integral</option>
        </select>
      </div>
      <div class="input-container">
        <label for="carne">Escolha a carne do seu Burger:</label>
        <select name="carne" id="carne" v-model="carne">
          <option value="">Selecione o tipo da carne</option>
          <option value="maminha">Maminha</option>
        </select>
      </div>
      <div id="opcionais-container" class="input-container">
        <label id="opcionais-titulo" for="opcionais">Selecione os opcionais:</label>
        <div class="checkbox-container">
          <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
          <span>Salame</span>
        </div>
        <div class="checkbox-container">
          <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
          <span>Salame</span>
        </div>
        <div class="checkbox-container">
          <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
          <span>Salame</span>
        </div>
      </div>
      <div class="input-container">
        <button type="submit">Criar meu Burger</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'BurgerForm'
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