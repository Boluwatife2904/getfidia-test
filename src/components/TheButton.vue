<template>
  <button class="button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "Button",
};
</script>

<style lang="scss" scoped>
button {
  background: #ffffff;
  box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
    0px 0px 0px 1px rgba(60, 66, 87, 0.16), 0px 1px 1px rgba(0, 0, 0, 0.12);
  border-radius: 4px;
  font-weight: 500;
  font-size: 14px;
  line-height: 17px;
  color: var(--grayEight);
  padding: 6px 8px;
  display: flex;
  align-items: center;
  gap: 6px;

  &:disabled {
    opacity: 0.5;
    box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
      0px 0px 0px 1px rgba(60, 66, 87, 0.16), 0px 1px 1px rgba(0, 0, 0, 0.12);
  }
}
</style>