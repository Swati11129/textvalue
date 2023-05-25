<template>
  <v-app>
    <TextValue :props="props" @valueClicked="emitValue($event)" @textClicked="emitText($event)" />
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
      props: {
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
    emitValue(value){
      console.log(value);
    },
    emitText(text){
      console.log(text);
    }
  }
  
};
</script>
