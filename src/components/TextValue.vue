<template>
  <v-container>
    <div
      style="font-size: 30px; font-weight: 700; cursor: pointer"
      :style="colorValueProps"
      @click="valueClickable"
    >
      {{ propsTextValueData.value }}
    </div>
    <div class="d-flex">
      <div style="font-size: 16px">{{ propsTextValueData.text }}</div>
        <div v-if="propsTextValueData.tooltip">
          <v-icon >mdi-alpha-i-circle</v-icon>
        </div>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "TextValue",
  props: {
    propsTextValueData: {
      type: Object,
    },
  },
  computed: {
    colorValueProps() {
      const valueColor = {
        color: this.propsTextValueData.color,
      };
      if (!this.propsTextValueData.color && this.propsTextValueData.clickable) {
        valueColor.color = "#0000EE";
      }
      return valueColor;
    },
  },
  methods: {
    valueClickable(){
      if(this.propsTextValueData.clickable){
        this.$emit('valueClicked',this.propsTextValueData.value)
      }
    }
  },
};
</script>
<style>
.group {
  display: flex;
  flex: 1;
  justify-content: space-around;
}
</style>