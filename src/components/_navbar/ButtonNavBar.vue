<template>
  <div :class="componentClass">
    <component style="display: block;" :is="is" :to="to" :href="href">
      <icon v-if="icon" :path="icon" />
      {{ text }}
    </component>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from "vue";
import Icon from '../Icon.vue'

export default defineComponent({
  components: {
    Icon
  },
  props: {
    id: String,
    text: String,
    color: String,
    hoverColor: String,
    href: String,
    to: String,
    icon: String,
  },
  name: "ButtonNavBar",
  setup(props) {
    const componentClass = computed(() => {
      const base = [
        "w-full",
        "h-full",
        props.color ? "text-" + props.color + "-300" : "text-gray-300",
        props.hoverColor
          ? "hover:text-" + props.hoverColor + "-400"
          : "hover:text-yellow-400",
        "transform",
        "hover:scale-110",
        "transition",
        "duration-300",
        "ease-in",
        "cursor-pointer",
      ];
      return base;
    });

    const is = computed(() => {
      if (props.href) {
        return "a";
      }
      if (props.to) {
        return "router-link";
      }

      return "div";
    });

    return { componentClass, is };
  },
});
</script>

<style scoped>
.teste {
  border: 1px solid red;
}
</style>