<template>
  <div
    v-tooltip="options.simpleBadge ? currentStatus.name : false"
    :class="['badge', 'no-wrap', { simple: options.simpleBadge }]"
    :style="style"
  >
    {{ options.simpleBadge ? null : currentStatus.name }}
  </div>
</template>

<script>
import mixin from "@directus/extension-toolkit/mixins/interface";

export default {
  mixins: [mixin],
  computed: {
    currentStatus() {
      return this.options.status_mapping[this.value];
    },
    style() {
      return {
        backgroundColor: `var(--${this.currentStatus.background_color})`,
        color: `var(--${this.currentStatus.text_color})`
      };
    }
  }
};
</script>

<style lang="scss" scoped>
.badge {
  border-radius: var(--border-radius);
  padding: 5px 10px;
  display: block;
  cursor: default;
  width: max-content;
  max-width: 120px;
}

.simple {
  border-radius: 50%;
  width: 10px;
  height: 10px;
  padding: 0;
}
</style>
