<template>
  <button class="base-button" :style="{ ...buttonStyle }" :variant="variant" :disabled="disabled" @click="handleClick"
  >
    <div class="icon-input" v-if="leftIcon">
      <BaseIcon
        :name="leftIcon"
        :sizeIcon="sizeIcon"
        :width="widthIcon"
        :height="heightIcon"
        :cursor="cursor"
      />
    </div>
    {{ text }}
    <div class="icon-input" v-if="rightIcon">
      <BaseIcon
        :name="rightIcon"
        :sizeIcon="sizeIcon"
        :width="widthIcon"
        :height="heightIcon"
        :cursor="cursor"
      />
    </div>
  </button>
</template>
<script setup>
import BaseIcon from "../base-components/BaseIcon.vue";

const props = defineProps({
  variant: {
    type: String,
    default: "primary",
    validator: (value) => {
      return ["primary", "outline"].includes(value);
    },
  },
  text: {
    type: String,
    default: "Text",
  },
  type: {
    type: String,
    default: "button",
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  width: {
    type: [String, Number],
    default: "100%",
  },
  height: {
    type: [String, Number],
    default: "100%",
  },
  cursor: {
    type: String,
    default: "pointer",
  },
  radius: {
    type: [String, Number],
  },
  backgroundColor: {
    type: String,
  },
  color: {
    type: String,
  },
  borderColor: {
    type: String,
  },
  icon: {
    type: String,
    default: "",
  },
  sizeIcon: {
    type: [String, Number],
  },
  widthIcon: {
    type: [String, Number],
  },
  heightIcon: {
    type: [String, Number],
  },
  leftIcon: {
    type: String,
  },
  rightIcon: {
    type: String,
  },
});

const buttonStyle = computed(() => ({
  width: props.width,
  height: props.height,
  backgroundColor: props.backgroundColor,
  color: props.color,
  borderColor: props.borderColor,
  borderRadius: props.radius,
}));

const emit = defineEmits(["click"]);

const handleClick = () => {
    if (!props.disabled) {
    emit("click");
  }
};
</script>
<style scoped src="@/assets/styles/components/BaseButton.scss"></style>
