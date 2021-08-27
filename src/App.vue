<template>
  <div class="item_1">
    <p style="padding-left: 3%;">Lifegame</p>
    <p style="padding-right: 3%;" class="set" @click="turn">setup</p>
  </div>
  <div></div>
  <div class="grid" >
     <div v-for="c in array" :style="c.style" @click="change(c)"></div> 
  </div>
    
</template>

<script setup>
let array = $ref([]) 
let delta = [-21, -20, -19, -1, 1, 19, 20, 21], ok = 0
let clock = null
for (let i = 0; i < 400; i++) array.push({style: 'background-color: orangered', show: true})
function change(array) {
  array.show = !array.show;
  array.style = array.show ?'background-color: orangered':'background-color: white'
}
function game() {
  for (let i = 0; i < 400; i++) {
    let neigh = 0
    for (let j = 0; j < 8; j++) {
      let x = i + delta[j]
      if (0 <= x && x % 10 != 0 && x % 10 != 9 && x < 400) {
        if (!array[x].show) neigh += 1
      }
    }
    if (neigh == 3 || (neigh == 2 && !array[i].show)) array[i].show = false
    else array[i].show = true
  }
  for (let i = 0; i < 400; i++) {
    if (!array[i].show) array[i].style = 'background-color: white'
    else array[i].style = 'background-color: orangered'
  }
}
function turn() {
  ok = !ok;
  if (ok) clock = setInterval(() => game(), 1000)
  else clearInterval(clock)  
  
  if (!ok) {
    for (let i = 0; i < 400; i++) {
      array[i].show = true
      array[i].style = 'background-color: orangered'
    }
  }
}
  


  

</script>


<style>
  .item_1 {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: black;
    width: 100vw;
    height: 4vw;
    font-size: 120%;
    color: white;
  }
  .set {
    border-style: solid;
    border-color: gold;
    border-radius: 20px;
    background-color: white;
    color: black;
    text-align: center;
    cursor: pointer;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  }
/*  .set:hover {
    padding: 10%;
  }*/
  .grid {
    display: grid;
    width: 100vw;
    height: 96vw;
    grid-template-columns: repeat(20, 4.715vw);
    grid-template-rows: repeat(20, 4.515vw);
    grid-gap: 0.3vw;
    text-align: start ;
  }
  .grid div {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    border-radius: 10%;
  }
  .grid div:hover {
     margin: 10%;
  }
  
</style>