<template>
  <div id="app">
    <!-- formulario -->
    <form class="formulario">
      <div>
        <label>Título de la tarjeta:</label>
        <input v-model="tituloTarjeta" disabled />
      </div>

      <div>
        <label>Chip SRC: </label>
        <input placeholder="Chip no modificable" disabled />
      </div>

      <div>
        <label>Número: </label>
        <input v-model="nTarjeta" />
      </div>

      <div>
        <label>Fecha de expiración:</label>
        <input v-model="fechaExpiracion" />
      </div>

      <div>
        <label>Propietario:</label>
        <input v-model="propietario" />
      </div>
      <div>
        <label>Tipo de tarjeta SRC: </label>
        <select name="credit" id="credit" v-model="tipoTarjeta">
        <!-- cantidad de opciones n veces -->
          <option
            v-for="credit in credits"
            :key="credit.id"
            :value="credit.path"
          >
            {{ credit.texto }}
          </option>
        </select>
      </div>
    </form>
    <!-- tarjeta -->

    <div class="tarjeta">
      <h3>{{ tituloTarjeta }}</h3>
      <img width="40" :src="chip" alt="" />
      <div>
        <h2>{{ nTarjeta }}</h2>
        <span class="expiracion">Fecha Exp:{{ fechaExpiracion }}</span>
      </div>
      <footer>
        <span>{{ propietario }}</span>
        <img :src="tipoTarjeta" width="60" />
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      tituloTarjeta: "PLOPBANK",
      chip: "/img/chip.png",
      nTarjeta: "",
      fechaExpiracion: "",
      propietario: "",
      tipoTarjeta: "/img/visa.png",
      credits: [
        { id: 1, path: "/img/visa.png", texto: "Visa" },
        { id: 2, path: "/img/mastercard.png", texto: "Mastercard" },
        { id: 3, path: "/img/americanexpress.png", texto: "American Express" },
      ],
    };
  },
};
</script>
<style>
* {
  margin: 0;
}
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60vh;
  font-size: 10px;
  font-family: sans-serif;
  background-image: url(/public/img/fondo.jpg);
}

#app {
  display: flex;
  gap: 40px;
  
}
h1{
  display: flex;
  color: aliceblue;
  justify-content: center;
  }
form {
  padding: 18px;
  border-radius: 20px;
  border: ridge 1px;
  box-shadow: 1px 1px 1px 1px gray;
  font-weight: bold;
  display: flex;
  flex-direction: column;
  gap: 15px;
  justify-content: center;
  color: aliceblue;
}
form div {
  display: grid;
  grid-template-columns: 100px 200px;
  align-items: center;
  gap: 5px;
}

form div label {
  text-align: right;
}

.tarjeta {
  width: 500px;
  height: 230px;
  background-image: url("/public/img/condiplop.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  color: #9a969f;
  border-radius: 20px;
  padding: 20px;
  box-shadow: 0px 0px 10px 2px black;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  font-family: "Moirt Personal Use", sans-serif;
}

.expiracion {
  color: #5c5a5f;
}

h3 {
  font-size: 20px;
}

h2 {
  font-size: 30px;
  letter-spacing: 10px;
  margin-bottom: 15px;
  text-shadow: 0px 0px 1px gold;
}

b {
  font-size: 16px;
}

footer {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  font-weight: bold;
  font-size: 18px;
  text-transform: uppercase;
  font-style: italic;
}
</style>