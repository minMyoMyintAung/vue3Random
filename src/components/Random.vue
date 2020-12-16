<template>
  <h1>Current Random Value</h1>
  <div> number of time: {{ times.length }} </div>
  <div> total: {{ totalTimes }}</div>
  <div>
        <button @click="generate()">generate random value</button>
        <button @click="init()">init</button>
  </div>
  <div>
      <ol>
          <li v-for="(val ,id) in times" :key="id"> 
              Random value ={{ val }}
          </li>
      </ol>
  </div>
</template>

<script>

import{ ref, computed } from "vue";
export default {
    name: 'Random',
    setup(){
        const randomValues=ref(0);
        const times= ref([]);

        function generate(){
            randomValues.value=Math.floor(Math.random() * Math.floor(9) + 1);
            times.value.push(randomValues.value);
        }

        function init(){
            randomValues.value=0;
            times.value=[];
        }
        const totalTimes=computed(()=>{
            let t=0;
            for(let i=0 ; i<times.value.length; i++){
                t +=times.value[i];
            }
            return t;
        });
        return{
            randomValues,
            times,
            generate,
            init,
            totalTimes
        }
    },

};
</script>

<style>
ol {
    background: #ff9999;
    list-style-position: outside;
    padding: 10px;

}
li {
    background: #ffe5e5;
    padding: 5px;
    margin-left: 35px;
}
div {
    width: 300px;
    margin: auto;
}
</style>