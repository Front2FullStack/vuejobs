<template>
  <div class="app">
    <button @click="handleClick('title')">Order by Title</button>
    <button @click="handleClick('salary')">Order by Salary</button>
    <button @click="handleClick('location')">Order by Location</button>
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

