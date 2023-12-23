<template>
  <div class="app">
    <Accordination :accordionItems="accordionItems" @create="add">
    </Accordination>
  </div>
</template>

<script>
import Accordination from './components/Accordination.vue';

export default {
  components: {
    Accordination
  },
  data() {
    return {
      accordionItems: [
        { name: 'name1', title: 'Section 1', expanded: true},
        { name: 'name2', title: 'Section 2'},
        { name: 'name3', title: 'Section 3'},
        { name: 'name4', title: 'Section 4'},
        { name: 'name1', title: 'Section 5'},
        { name: 'name2', title: 'Section 6'},
        { name: 'name1', title: 'Section 7'},
        { name: 'name2', title: 'Section 8'},
      ]
    };
  },
  methods:{
    add(index){
      this.accordionItems[index].expanded = !this.accordionItems[index].expanded
    }
  }
};
</script>
<style>
.app{
  width: 1200px;
  margin: 0 auto;
}
</style>
