<template>
  <div class="blocks" :class="classes">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "s-blocks",

  props: {
    gap: [Number, String, Object]
  },

  computed: {
    classes() {
      const classes = [];

      if (this.gap) {
        if (typeof this.gap === "string") {
          classes.push(`blocks--${this.gap}`);
        } else if (typeof this.gap === "object") {
          for (var key in this.gap) {
            if (key == "phone") {
              classes.push(`blocks--${this.gap[key]}`);
            } else {
              classes.push(`blocks--${this.gap[key]}:${key}`);
            }
          }
        }
      }

      return classes;
    }
  }
};
</script>