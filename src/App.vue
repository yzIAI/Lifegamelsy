<template>
  <div class="item_1">
    <p style="padding-left: 3%;">Lifegame &nbsp</p>
    |
    <p><button>setup</button></p>
  </div>
  <div class="grid" >
     <div v-for="c in array" :style="style" @click="change"></div> 
  </div>
    
       
    
    

    
  
</template>

<script>
 
  export default {
    data() {
      return {
        array,
        style: "background-color: orangered"
      }
    },
    methods: {
      change() {
        if (this.style == "background-color: orangered") this.style = "background-color: white"
        else this.style
      }
    }
  } 
  let array = [], delta = [-21, -20, -19, -1, 1, 19, 20, 21];
  for (let i = 0; i < 400; i++) array.push(0);



  

</script>


<style>
  .item_1 {
    display: flex;
    justify-content: start;
    align-items: center;
    background-color: grey;
    width: 100vw;
    height: 4vw;
    font-size: 120%;
    color: white;
   
    
  }
  .item_1 button {
    background-color: blueviolet;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    border-radius: 20px;

  }
  .grid {
    display: grid;
    width: 100vw;
    height: 100vw;
    grid-template-columns: repeat(25, 4.715vw);
    grid-template-rows: repeat(20, 5vw);
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