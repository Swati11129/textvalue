<template>
  <v-app>
    <TextValue :propsData="Data" @valueClicked="emitEvent($event)" />
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
        color: 'red',
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
