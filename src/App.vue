<template>
  <v-app>
    <TextValue :propsData="Data" @valueClicked="valueClick($event)" @textClicked="textClick($event)" />
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
      Data: {
        value: '1,838',
        text: 'Low coverage: Under 75% code coverage',
        valueColor: '',
        textColor: 'green',
        valueClickable: true,
        textClickable:true,
        valueFontSize:'30px',
        tooltip:'tooltip info',
      }
    };
  },
  methods:{
    valueClick(value){
      console.log(value);
    },
    textClick(text){
      console.log(text);
    }
  }
  
};
</script>
