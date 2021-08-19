<template>
  <div class="sidebar">
    <div class="store-name">
      <div class="logo">
        <img src="@/assets/images/store-icon.svg" alt="store-icon" />
      </div>
      <div class="name">
        <p>Store name <i class="fa fa-chevron-down"></i></p>
      </div>
    </div>
    <ul class="main">
      <li>
        <router-link :to="{ name: 'Home' }">
          <img src="@/assets/images/home-icon.svg" alt="home-icon" />
          Home
        </router-link>
      </li>
      <li>
        <router-link :to="{ name: 'Payments' }">
          <img src="@/assets/images/payments-icon.svg" alt="payments-icon" />
          Payments
        </router-link>
        <ul class="inner-list">
          <li>
            <router-link :to="{ name: 'Home' }">Reviews</router-link>
          </li>
          <li>
            <router-link :to="{ name: 'Home' }">Disputes</router-link>
          </li>
          <li>
            <router-link :to="{ name: 'Home' }">Top-ups</router-link>
          </li>
          <li>
            <router-link :to="{ name: 'Home' }">Collected fees</router-link>
          </li>
          <li>
            <router-link :to="{ name: 'Home' }">Transfers</router-link>
          </li>
          <li>
            <router-link :to="{ name: 'Home' }">Payouts</router-link>
          </li>
          <li>
            <router-link :to="{ name: 'Home' }">All transactions</router-link>
          </li>
        </ul>
      </li>
      <li>
        <router-link :to="{ name: 'Home' }">
          <img src="@/assets/images/balances-icon.svg" alt="balances-icon" />
          Balances
        </router-link>
      </li>
      <li>
        <router-link :to="{ name: 'Home' }">
          <img src="@/assets/images/customers-icon.svg" alt="customers-icon" />
          Customers
        </router-link>
      </li>
      <li>
        <router-link :to="{ name: 'Home' }">
          <img
            src="@/assets/images/connected-accounts-icon.svg"
            alt="connected-accounts-icon"
          />
          Connected accounts
        </router-link>
      </li>
      <li>
        <router-link :to="{ name: 'Home' }">
          <img src="@/assets/images/products-icon.svg" alt="products-icon" />
          Products
        </router-link>
      </li>
      <li>
        <router-link :to="{ name: 'Home' }">
          <img src="@/assets/images/reports-icon.svg" alt="reports-icon" />
          Reports
        </router-link>
      </li>
    </ul>
    <ul class="secondary">
      <li>
        <router-link :to="{ name: 'Home' }">
          <img
            src="@/assets/images/developers-icon.svg"
            alt="developers-icon"
          />
          Developers
        </router-link>
      </li>
      <li class="toggle">
        <div class="switch">
          <input type="checkbox" name="test" id="test" />
          <span class="slider round"></span>
        </div>
        <label for="test">View test data</label>
      </li>
      <li>
        <router-link :to="{ name: 'Home' }">
          <img src="@/assets/images/settings-icon.svg" alt="settings-icon" />
          Settings
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TheSidebar",
};
</script>

<style lang="scss" scoped>
.sidebar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  max-width: 270px;
  min-height: 100vh;
  height: 100%;
  background: #f7fafc;
  box-shadow: inset -1px 0px 0px var(--borderColor);
  padding: 12px 20px 0px 20px;
  flex-shrink: 0;

  .store-name {
    display: flex;
    align-items: center;
    gap: 8px;
    cursor: pointer;
    margin-bottom: 30px;

    .logo {
      width: 36px;
      height: 36px;
      border-radius: 50%;
    }

    .name {
      p {
        font-weight: 500;
        font-size: 16px;
        line-height: 19px;
        color: var(--grayNine);

        i {
          margin-left: 5px;
          color: var(--graySeven);
          font-size: 14px;
        }
      }
    }
  }

  ul {
    list-style: none;

    li {
      margin-bottom: 12px;

      a {
        display: flex;
        align-items: center;
        gap: 18px;
        outline: none;
        text-decoration: none;
        font-size: 14px;
        line-height: 17px;
        color: var(--grayNine);

        &.router-link-active {
          font-weight: 600;
          color: --var(blueColor);
        }
      }

      .inner-list {
        list-style: none;
        margin: 12px 0 24px 34px;

        li {
          margin-bottom: 8px;
          &:first-child {
            margin-bottom: 8px;
          }
        }
      }
    }

    &.main {
      margin-bottom: 28px;

      li {
        &:first-child {
          margin-bottom: 24px;
        }
      }
    }
  }

  @media screen and (max-width: 1200px) {
    left: 100%;
  }
}

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