<template>
  <v-container>
    <div
      :style="{
        fontSize: propsData.valueFontSize ||'30px',
        'font-weight': '700',
        color: propsData.valueColor,
      }"
    >
      <div
        v-if="propsData.valueClickable"
        @click="valueClick"
        :style="{
          cursor: 'pointer',
          color: propsData.valueColor || '#0000EE',
        }"
      >
        {{ propsData.value }}
      </div>
      <div v-else>
        {{ propsData.value }}
      </div>
    </div>
    <div class="d-flex">
      <div
        :style="{
          'font-size': '16px',
          'font-weight': '700',
          color: propsData.textColor,
        }"
      >
        <div
          v-if="propsData.textClickable"
          @click="textClick"
          :style="{
            cursor: pointer,
            color: propsData.textColor || '#0000EE',
          }"
        >
          {{ propsData.text }}
        </div>
        <div v-else>
          {{ propsData.text }}
        </div>
      </div>
      <div
        v-if="propsData.tooltip"
        @mouseover="showTooltipContent = true"
        @mouseout="showTooltipContent = false"
      >
        <v-icon v-show="!showTooltipContent">mdi-alpha-i-circle</v-icon>
        <div v-show="showTooltipContent">{{ propsData.tooltip }}</div>
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
  data() {
    return {
      showTooltipContent: false,
    };
  },
  methods: {
    valueClick() {
      this.$emit("valueClicked", this.propsData.value);
    },
    textClick() {
      if (this.propsData.textClickable) {
        this.$emit("textClicked", this.propsData.text);
      }
    },
  },
};
</script>
