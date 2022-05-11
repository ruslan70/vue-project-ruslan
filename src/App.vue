<template>
    <div id="app">
      <ul>
      <!-- the list is ordered by putting completed tasks at the end -->
        <li v-for="(todo, index) in todos_after_sort" :key="todo.label">
          <label>
            <input type="checkbox" v-model="todo.done">
            Task {{ index }}: {{todo.label}}
          </label>
            <i>{{todo.done ? "DONE !": "in progress..."}}</i>
        </li>
      </ul>
        <div id="login_form">
          <form>
            <h1>Authentication</h1>
            <option>Fill out this form to login.</option>
            <hr />

            <label :style="{ color: blueColor,'background-color': backColor}" for="email"><b>Email</b></label>
            <input
              type="text"
              placeholder="Enter your email"
              id="email"
              name="email"
              required
            />

            <label :style="{ color: blueColor,'background-color': backColor}" for="psw"><b>Password</b></label>
            <input
              type="password"
              placeholder="Enter your password"
              id="psw"
              name="psw"
              required
            />

            <p><button :style="{ color: primaryColor}" type="submit">Login</button></p>
          </form>
        </div>
        <div>
          <input type="range" min="0" max="40" v-model="temperature" />
          {{ temperature }} °C
          <span v-if="temperature > 30">🥵</span>
          <span v-else-if="temperature < 15">🥶</span>
          <span v-else>😀</span>
        </div>
        
      <h3>Ist das mein Bild?</h3>
      <p :style="{ color: primaryColor}">{{ firstName}}</p>
      
      <img 
        :src="imgLink" 
        :width="logoWidth"
      >
      <p>Nein! Das ist mein Bild:</p>
      <p :style="{ color: blueColor,'background-color': backColor}">{{ firstName}} . Als ich {{age}} Jahre alt war.</p>
      <img 
        v-bind:src="imgLink1" 
        :width="logoWidth1"
      >

      <p :style="{color: greenColor}">Preis für{{ priceTast }} Tastatur ist - <br>Total: {{ price.toFixed(2) + " Fr." }}</p>
      <img 
        :src="imgLink2" 
        :width="logoWidth2"
      >
      <!-- two way binding: v-model -->
      <input
        v-model="number"
        type="text"
      >
    
      <select v-model="number">
        <option value="45"> 45</option>
        <option value="50"> 50</option>
        <option value="55"> 55</option>
      </select>

      <!-- conditional rendering: v-if / v-else -->
      <h2 v-if="number > 50">
        number is greater than 50
      </h2>
      <h2 v-else-if="number < 50">
        number is smaller than 50
      </h2>
      <h2 v-else>
        number is equal 50
      </h2>
      <br>
      <button @click="inStock = !inStock">Toggle</button>

      <h1 v-if="inStock">Vue is in Stock! Hurry up!</h1>
      <h1 v-else>Oh no 😢 no Vue for Opportunity</h1>

      <!-- v-for -->
    <ul>
      <li
        v-for="frucht in fruits"
        :key="frucht"
      >{{ frucht }}</li>
    </ul>

    </div>

</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      firstName: "Ruslan",
      primaryColor: "blue",
      blueColor: "blue",
      backColor: "red",
      imgLink: require("../src/assets/logo.png"),
      logoWidth: 50,
      age:30,
      imgLink1: require("../src/assets/bruce-lee-main_image-fc7f.jpg"),
      logoWidth1: 100,
      priceTast: "QWERTZ",
      greenColor:"green",
      price: 12.345654,
      imgLink2: require("../src/assets/tastatur.jpeg"),
      logoWidth2: 100,
      temperature: 25, 
      number: 30,
      inStock: true,
      fruits: ["apple","kiwi","mango"] 
    };
  }
  
};
  
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#login_form {
  background-color: black;
  text-transform: capitalize;
  color: white;
}
</style>
