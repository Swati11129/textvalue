<template>
  <v-app>
    <TextValue v-bind:propsTextValueData="textValueData" v-on:valueClicked="emitEvent($event)" />
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
      textValueData: {
        value: '1,838',
        text: 'Low coverage: Under 75% code coverage',
        color: '',
        clickable:true,
        tooltip:true,
      }
    };
  },
  methods:{
    emitEvent(capturedValue){
      console.log(capturedValue);
    }
  }
  
};
</script>
