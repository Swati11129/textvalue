<template>
  <v-container>
    <div class="d-flex"
      :style="{
        fontSize: Data.valueFontSize ||'30px',
        'font-weight': '700',
        color: Data.valueColor,
      }"
    >
      <div
        v-if="Data.valueClickable"
        @click="valueClick"
        :style="{
          cursor: 'pointer',
          color: Data.valueColor || '#0000EE',
        }"
      >
        {{ Data.value }}
      </div>
      <div v-else>
        {{ Data.value }}
      </div>
    </div>
    <div class="d-flex">
      <div
        :style="{
          'font-size': '16px',
          'font-weight': '700',
          color: Data.textColor,
        }"
      >
        <div
          v-if="Data.textClickable"
          @click="textClick"
          :style="{
            cursor: 'pointer',
            color: Data.textColor || '#0000EE',
          }"
        >
          {{ Data.text }}
        </div>
        <div v-else>
          {{ Data.text }}
        </div>
      </div>
      <div
        v-if="Data.tooltip"
        @mouseover="showTooltipContent = true"
        @mouseout="showTooltipContent = false"
        style="cursor:pointer"
      >
        <v-icon v-show="!showTooltipContent">mdi-alpha-i-circle</v-icon>
        <div v-show="showTooltipContent">{{ Data.tooltip }}</div>
      </div>

    </div>
  </v-container>
</template>

<script>
export default {
  name: "TextValue",
  props: {
    Data: {
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
      this.$emit("valueClicked", this.Data.value);
    },
    textClick() {
        this.$emit("textClicked", this.Data.text);
    },
  },
};
</script>
