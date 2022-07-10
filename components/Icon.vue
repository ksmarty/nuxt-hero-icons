<!-- Icons from https://heroicons.com/ -->
<template>
  <svg aria-hidden="true"
       xmlns="http://www.w3.org/2000/svg"
       v-bind="values">
    <path stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          :d="getPath(name)" />
  </svg>
</template>
<script>
import { defineComponent, ref } from "vue";
import OutlineIcons from "../outline";
import SolidIcons from "../solid";

export default defineComponent({
  name: "Icon",
  props: {
    name: { type: String, default: "annotation", required: true },
    solid: { type: Boolean, default: false },
    size: { type: Number, default: 8, required: true }
  },
  data() {
    return {
      values: {
        stroke: !this.solid ? 'currentColor' : '',
        style: { height: (this.size / 4 + 'rem'), width: (this.size / 4 + 'rem') },
        viewBox: this.solid ? '0 0 19 19' : '0 0 24 24',
        fill: this.solid ? 'currentColor' : 'none',
      }
    }
  },
  methods: {
    getPath(name) {
      return (this.solid ? SolidIcons : OutlineIcons)[name];
    }
  }
});
</script>
