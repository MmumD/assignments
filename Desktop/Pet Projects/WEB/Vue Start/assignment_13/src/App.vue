<template>
  <div class="app">
    <Timeform @create="add"/>
    <Timeline v-bind:events="events"/>
  </div>
</template>

<script>
import Timeform from './components/Timeform.vue';
import Timeline from './components/Timeline.vue';
export default{
  components: {
    Timeform,
    Timeline
  },
  data(){
    return{
      events: [
      ]
    }
  },
  methods:{
    add(timeEvent){
      this.events.push(timeEvent);
      this.events = this.events.slice().sort((a, b) => new Date(a.date) - new Date(b.date));
    }
  }
};
</script>
