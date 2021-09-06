<template>
  <div id="app">
    <Converter>
      <Conversion from="Real brasileiro/BRL" to="Dólar americano/USD" />
      <Conversion from="Real brasileiro/BRL" to="Euro/EUR" />
      <Conversion from="Real brasileiro/BRL" to="Dólar canadense/CAD" />  
      <Conversion from="Real brasileiro/BRL" to="Euro/EUR" />
      <Conversion from="Dólar americano/USD" to="Dólar canadense/CAD" />
      <Conversion from="Dólar canadense/CAD" to="Euro/EUR" />
    </Converter>
  </div>
</template>

<script>
import Converter from './components/Converter';
import Conversion from './components/Conversion';

export default {
  name: 'App',
  components: {
    Converter,
    Conversion
  }
}
</script>

<style>

html, body {
  font-family: Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
}

body {
  background-image: linear-gradient(90deg, #74b0ed, #2a6bad);
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  color: #000000;
  overflow-y: hidden;
  width: 100vw;
  max-width: 100%;
  height: 100vh;
}

</style>
