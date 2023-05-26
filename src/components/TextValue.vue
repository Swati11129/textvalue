<template>
  <v-container>
    <div
      :style="{
        'font-weight': '700',
        fontSize: prop.fontSize || '30px',
        color: prop.valueColor,
      }"
    >
      <span
        v-if="prop.valueClickable"
        @click="handleClick"
        class="cursor"
        :style="{
          color: prop.valueColor || '#0000EE',
        }"
      >
        {{ prop.value }}
      </span>
      <span v-else>
        {{ prop.value }}
      </span>
    </div>

    <div
      :style="{
        'font-size': '16px',
        'font-weight': '700',
        color: prop.textColor,
      }"
    >
      <span
        v-if="prop.textClickable"
        @click="handleClick"
        class="cursor"
        :style="{
          color: prop.textColor || '#0000EE',
        }"
      >
        {{ prop.text }}
      </span>
      <span v-else>
        {{ prop.text }}
      </span>
      
      <v-tooltip v-model="showTooltip" top>
        <template v-slot:activator="{ on }">
          <v-icon v-on="on">mdi-alert-circle-outline</v-icon>
        </template>
        <div>{{ prop.tooltip }}</div>
      </v-tooltip>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "TextValue",
  props: {
    prop: {
      type: Object,
    },
  },
  data() {
    return {
      showTooltip: false,
    };
  },
  methods: {
    handleClick() {
      this.$emit("clicked", this.prop);
    },
  },
};
</script>

<style>
.cursor {
  cursor: pointer;
}
</style>
