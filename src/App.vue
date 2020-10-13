<template>
  <div id="app">
    <div class="flex-item">
      <h2>Ongoing Projects</h2>
      <input type="text" placeholder="Search history    🔍">
    </div>
    <br>
    <br>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
@font-face {
  font-family: circularStd;
  src: url('assets/circular_std.otf');
}

body {
  overflow-x: hidden;
  font-size: 15px;
  background: #eaf5fc;
  color: #27394b;
  font-family: circularStd;
  margin: 0;
  padding: 0;
}

.flex-item {
  display: flex;
  justify-content: space-between;
  background: #ffffff;
  padding: 2%;

}

input {
  border: 1px solid #aabbcc;
  border-radius: 5px;
  margin-top: 2vh;
  height: 5vh;
  text-align: center;
}

input:active {
  height: 5vh;
}
</style>
