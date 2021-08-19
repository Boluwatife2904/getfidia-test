<template>
  <li>
    <div class="check">
      <!-- CUSTOM CHECKBOX -->
      <custom-check
        :id="item.description"
        :checked="item.checked"
      ></custom-check>
    </div>
    <div class="amount">
      US${{ item.amount }}
      <span class="status"
        >Succeeded <img src="@/assets/images/checkmark.svg" alt="checkmark"
      /></span>
    </div>
    <div class="description">
      {{ item.description }}
    </div>
    <div class="customer">{{ item.customer }}</div>
    <div class="date">{{ item.date }}</div>
    <div class="actions">
      <button class="button">
        <img src="@/assets/images/dots.svg" alt="dots" />
      </button>
    </div>
  </li>
</template>

<script>
import CustomCheck from "./CustomCheck.vue";
export default {
  components: { CustomCheck },
  name: "TableItem",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
// TABLE ITEM
li {
  display: flex;
  gap: 10px;
  align-items: center;
  padding: 14px 0 14px 4px;
  width: 100%;
  border-bottom: 1px solid var(--borderColor);

  .check {
    width: 20px;
    flex-shrink: 0;
  }

  .amount {
    width: 195px;
    flex-shrink: 0;
  }

  .description {
    flex: 0 0 50%;
    max-width: 50%;
    width: 100%;
    flex-shrink: 0;
  }

  .customer {
    width: 170px;
    flex-shrink: 0;
  }

  .date {
    width: 120px;
    flex-shrink: 0;
  }

  .actions {
    margin-left: auto;
    flex-shrink: 0;
    text-align: right;
    padding-right: 8px;
  }

  div {
    font-size: 14px;
    line-height: 17px;
    color: #3c4257;
  }

  .amount {
    font-weight: 500;
    font-size: 14px;
    line-height: 17px;
    display: flex;
    align-items: center;
    justify-content: flex-end;
    padding-right: 16px;
    gap: 8px;
    text-align: right;
    color: var(--grayNine);
  }

  .description {
    font-size: 13px;
    line-height: 16px;
    color: var(--graySeven);
  }
}

// SUCCEEDED STATUS
.status {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  padding: 1px 4px 1px 6px;
  background: #cbf4c9;
  border-radius: 4px;
  font-weight: 500;
  font-size: 12px;
  line-height: 14px;
  color: #0e6245;
}
</style>