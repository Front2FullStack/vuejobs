<template>
  <div class="app">
    <div class="button-holder">
      <button @click="handleClick('title')">Order by Title</button>
      <button @click="handleClick('salary')">Order by Salary</button>
      <button @click="handleClick('location')">Order by Location</button>
    </div>
  <JobList :jobs="jobs" :order="order"  />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'

import JobList from './components/JobsList.vue'

export default defineComponent({
  name: 'App',
  components :{
    JobList
  },
  setup(){
    const jobs = ref<Job[]>([
      {title : 'Designer', location :'Dubai' , salary :30000 , id: '1'},
      {title : 'Front End Developer', location :'Sharjah' , salary :78000 , id: '2'},
      {title : 'Project Manager', location :'Dubai' , salary :90000 , id: '3'},
      {title : 'Chief Technology Officer', location :'Dubai' , salary :120000 , id: '4'},
      {title : 'Office Administrator', location :'Dubai' , salary :10000 , id: '5'},
    ])
    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }
    return { jobs, handleClick , order}
  }
});
</script>

<style>
  .button-holder{
    display: flex;
    justify-content: center;
    padding: 2rem 1rem 0;
  }
  button {
    margin: 0 10px;
    color: #013c21;
    border: 3px solid #077f49;
    background: #90d481;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
</style>