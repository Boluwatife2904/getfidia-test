<template>
  <div class="page-wrapper">
    <div class="container">
      <h1>Welcome</h1>
      <p>
        Below, you will find the links to the two pages in the Figma design of
        the task attached in the job opening.
      </p>
      <div class="links">
        <router-link :to="{ name: 'Login' }">Login</router-link>
        <router-link :to="{ name: 'Payments' }">Payments</router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
};
</script>

<style lang="scss" scoped>
.page-wrapper {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #f1f1f1;

  .container {
    max-width: 500px;
    width: 90%;
    background: #fff;
    box-shadow: 0 2px 4px 8px rgba(0, 0, 0, 0.02);
    border-radius: 10px;
    padding: 30px;
    text-align: center;

    h1 {
      font-size: 24px;
      margin-bottom: 10px;
    }

    p {
      color: var(--gray);
      font-size: 14px;
      line-height: 24px;
    }

    .links {
      margin: 30px 0;

      a {
        text-decoration: none;
        border: none;
        outline: none;
        color: #fff;
        background: var(--purpleColor);
        font-size: 14px;
        border-radius: 4px;
        padding: 10px 16px;
        margin: 10px;
      }
    }
  }
}
</style>
