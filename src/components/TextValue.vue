<template>
  <v-container>
    <div
      :style="{
        'font-size' : '30px',
        'font-weight': '700',
        cursor: propsData.clickable ? 'pointer' : 'default',
        color: propsData.color || (propsData.clickable ? '#0000EE' : ''),
      }"
      @click="valueClick"
    >
    {{ propsData.value }}
    </div>
    <div class="d-flex">
      <div style="font-size: 16px">{{ propsData.text }}</div>
      <div v-if="propsData.tooltip">
        <v-icon>mdi-alpha-i-circle</v-icon>
      </div>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "TextValue",
  props: {
    propsData: {
      type: Object,
    },
  },
  methods: {
    valueClick() {
      if (this.propsData.clickable) {
        this.$emit("valueClicked", this.propsData.value);
      }
    },
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
