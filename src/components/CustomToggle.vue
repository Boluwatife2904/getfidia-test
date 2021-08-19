<template>
  <div class="toggle">
    <label :for="name" class="switch">
      <input type="checkbox" :name="name" :id="name" />
      <span class="slider round"></span>
    </label>
    <label :for="name">View test data</label>
  </div>
</template>

<script>
export default {
  name: "CustomToggle",
  props: ["name"],
};
</script>

<style lang="scss" scoped>
// CUSTOM TOGGLE
.toggle {
  display: flex;
  align-items: center;
  gap: 6px;

  label {
    cursor: pointer;
    font-size: 14px;
    line-height: 17px;
    color: var(--grayNine);
  }

  .switch {
    position: relative;
    display: inline-block;
    width: 26px;
    height: 16px;

    input {
      opacity: 0;
      width: 0;
      height: 0;
      outline: none;

      &:focus {
        outline: none;
      }
    }

    .slider {
      position: absolute;
      cursor: pointer;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: var(--borderColor);
      -webkit-transition: 0.4s;
      transition: 0.4s;

      &::before {
        position: absolute;
        content: "";
        height: 14px;
        width: 14px;
        left: 0px;
        top: 0px;
        background-color: white;
        border: 1px solid #c2c7cf;
        -webkit-transition: 0.4s;
        transition: 0.4s;
      }
    }
  }

  input:checked + .slider {
    background-color: var(--purpleColor);
  }

  input:checked + .slider:before {
    -webkit-transform: translateX(12px);
    -ms-transform: translateX(12px);
    transform: translateX(12px);
  }

  .slider.round {
    border-radius: 26px;
  }

  .slider.round:before {
    border-radius: 50%;
  }
}
</style>