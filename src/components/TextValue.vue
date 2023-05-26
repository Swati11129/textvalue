<template>
  <v-container>
    <div
      :style="{
        'font-weight': '700',
        fontSize: props.fontSize || '30px',
        color: props.valueColor,
      }"
    >
      <span
        v-if="props.valueClickable"
        @click="handleClick"
        class="cursor"
        :style="{
          color: props.valueColor || '#0000EE',
        }"
      >
        {{ props.value }}
      </span>
      <span v-else>
        {{ props.value }}
      </span>
    </div>

    <div
      :style="{
        'font-size': '16px',
        'font-weight': '700',
        color: props.textColor,
      }"
    >
      <span
        v-if="props.textClickable"
        @click="handleClick"
        class="cursor"
        :style="{
          color: props.textColor || '#0000EE',
        }"
      >
        {{ props.text }}
      </span>
      <span v-else>
        {{ props.text }}
      </span>
      
      <v-tooltip v-model="showTooltip" top>
        <template v-slot:activator="{ on }">
          <v-icon v-on="on">mdi-alert-circle-outline</v-icon>
        </template>
        <div>{{ props.tooltip }}</div>
      </v-tooltip>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "TextValue",
  props: {
    props: {
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
      this.$emit("clicked", this.props);
    },
  },
};
</script>

<style>
.cursor {
  cursor: pointer;
}
</style>
