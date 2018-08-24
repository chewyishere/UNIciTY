<template>
  <div id="app">
    <img src="./assets/logo.jpg">
    <index></index>
  </div>
</template>

<script>
import index from './components/Index'



export default {
  components: {
    index
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}

img{
    width: 100%;
    height: 100%;
    position: fixed;
    z-index: -1;
    left: 0;
    top: 0;
}

  h1 {
    font-weight: normal;
    font-size: 3em;
    color: red;
    text-transform: capitalize;
    font-family: Impact;
    background: linear-gradient(to right, orange , yellow, green, cyan, blue, violet);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  }

  
  h2 {
    display: inline-block;
    font-family: futura;
    font-size: 2em;
    font-style: italic;
    color: white;

  }


  .block {
    width: 50%;
    height: 400px;
    float: left;
    display: flex;
    flex-direction: column;
  }
  
  input, button {
    width: 70%;
    height: 30px;
    text-align: center;
    border: gray 1px solid;
  }

  button{
    height: 50px;
    margin: 50px 0;
    width: 300px;
    font-weight: normal;
    font-size: 2em;
    text-transform: capitalize;
    font-family: Impact;
     text-shadow: -1px -1px 0 rgba(0,0,0,0.3);
     font-weight:bold; 
     color: #FFFFFF;
     background-color: #A5B8DA; 
     background-image: linear-gradient(to right, orange , yellow, green, cyan, blue, violet);

  }


  button:hover{
      background-image: linear-gradient(to right, violet, blue, yellow, green, cyan,orange );
      border: 2px solid white;
      color: black;
  }


  input{
      font-size: 16px;
      margin: 20px auto;
  }

.block-style{
    color: white;
    width: 50%;
    text-align: center;
    margin: 0 auto;
    position: relative;
    flex-direction: row;
    align-items: center;
    align-content: center;
    height: 150px;
    float: unset;
}

label{
    font-size: 1.5rem;
    font-weight: 400;
    margin-left: -80px;
}

  @media only screen and (max-width: 600px) {
    h2, button{
        font-size: 1em;
    }
    input{
        font-size: 12px;
        width: 85%;
        margin: 10px auto;
    }
    .block{
      width: 100%;
      height: unset;
    }
    button{
      height: 35px;
      width: 70%;
    }

  }


  </style>