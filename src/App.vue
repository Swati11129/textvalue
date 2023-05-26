<template>
  <v-app>
    <TextValue :prop="prop" @clicked="handleClick($event)" />
  </v-app>
</template>

<script>
import TextValue from './components/TextValue.vue';
export default {
  name: 'App',
  components:{
    TextValue
  },
   data() {
    return {
      prop: {
        value: '7,864',
        text: 'Low coverage: Under 75% code coverage',
        valueColor: 'red',
        textColor: '',
        valueClickable: true,
        textClickable:true,
        fontSize:'24px',
        tooltip:'tooltip info',
      }
    }; 
  },
  methods:{
    handleClick(ele){
      console.log(ele);
    } 
  }
  
};
</script>
