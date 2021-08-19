<template>
  <label :for="id" class="checkbox" :class="{ flex: label }">
    <input
      @click.self="$emit('perform-action')"
      type="checkbox"
      class="input"
      :id="id"
      :checked="checked"
    />
    <div class="custom-check"></div>
    <!-- Stay signed in for a week -->
    <div class="label" v-if="label">
      {{ label }}
    </div>
  </label>
</template>

<script>
export default {
  name: "CustomCheck",
  props: ["id", "checked", "label"],
  emits: ["perform-action"],
};
</script>

<style lang="scss" scoped>
// Custom Checkbox
.checkbox {
  cursor: pointer;
  margin-bottom: 15px;
  color: var(--grayEight);
  font-size: 14px;
  font-weight: normal;

  .input {
    display: none;
  }

  .custom-check {
    width: 16px;
    height: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-right: 6px;
    flex-shrink: 0;
    transition: all 0.15s linear;
    background: #ffffff;
    box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
      0px 0px 0px 1px rgba(60, 66, 87, 0.16), 0px 1px 1px rgba(0, 0, 0, 0.12);
    border-radius: 4px;

    &::after {
      content: "\2714";
      color: #ffffff;
      transition: all 0.15s;
      transform: scale(0);
      font-size: 12px;
    }
  }
}

.flex {
  display: inline-flex;
  align-items: center;
}

.input:checked + .custom-check {
  background: var(--purpleColor);
  border-color: var(--purpleColor);
}

.input:checked + .custom-check::after {
  transform: scale(1);
}
</style>