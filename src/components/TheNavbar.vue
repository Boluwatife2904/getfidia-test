<template>
  <div class="navbar">
    <div class="search-bar">
      <form action="#" autocomplete="off">
        <img src="@/assets/images/search-icon.svg" alt="search-icon" />
        <input
          type="search"
          name="search"
          id="search"
          placeholder="Search..."
        />
      </form>
    </div>
    <ul class="icons">
      <li>
        <router-link to="/">
          <img src="@/assets/images/notification-icon.svg" alt="notification-icon">
        </router-link>
      </li>
      <li>
        <router-link to="/">
          <img src="@/assets/images/help-icon.svg" alt="notification-icon">
        </router-link>
      </li>
      <li>
        <router-link to="/">
          <img src="@/assets/images/account-icon.svg" alt="notification-icon">
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TheNavbar",
};
</script>

<style lang="scss" scoped>
.navbar {
  padding: 20px 40px;
  border-bottom: 1px solid #e3e8ee;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 32px;

  .search-bar {
    form {
      display: flex;
      gap: 10px;
      align-items: center;

      input {
        font: inherit;
        border: none;
        outline: none;
      }
    }
  }

  .icons {
    list-style: none;
    display: flex;
    align-items: center;
    gap: 16px;

    li {
      img {
        height: 16px;
        width: 16px;
      }
    }
  }
}
</style>