<template>
  <div class="page-wrapper">
    <div class="line left-line"></div>
    <div class="box left-blue-box"></div>
    <div class="box left-purple-box"></div>
    <div class="page-content">
      <div class="stripe-logo">
        <img src="@/assets/images/stripe.svg" alt="" />
      </div>
      <div class="login-form">
        <h1 class="title">Sign in to your account</h1>
        <form>
          <div class="form-wrapper">
            <label for="email">Email</label>
            <input
              type="email"
              name="email"
              id="email"
              placeholder="Enter your email address"
            />
          </div>
          <div class="form-wrapper">
            <label for="password">
              <span>Password</span>
              <span>
                <router-link to="/" class="forgot-password"
                  >Forgot your password?</router-link
                >
              </span>
            </label>
            <input
              :type="passwordType"
              name="password"
              id="password"
              placeholder="Enter your password"
            />
            <button
              class="button password-toggler"
              type="button"
              @click="togglePasswordVisibility"
            >
              <i class="fa fa-eye"></i>
            </button>
          </div>
          <div class="custom-checkbox">
            <label for="data" class="checkbox">
              <input type="checkbox" class="input" id="data" checked />
              <div class="custom-check"></div>
              Stay signed in for a week
            </label>
          </div>
          <button type="submit" class="button submit">Continue</button>
          <button type="button" class="button sso-button">
            Use single sign-on (SSO) instead
          </button>
        </form>
      </div>

      <div class="footer">
        <p class="signup">
          Don't have an account?
          <span><router-link to="/">Sign up</router-link></span>
        </p>
        <div class="copyright-links">
          <p class="copyright">&copy; Stripe</p>
          <ul class="links">
            <li>
              <router-link to="/">Contact</router-link>
            </li>
            <li>
              <router-link to="/">Privacy & terms</router-link>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class="line right-line"></div>
    <div class="box right-purple-box"></div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "Login",
  setup() {
    const passwordType = ref("password");
    const togglePasswordVisibility = () => {
      passwordType.value =
        passwordType.value === "password" ? "text" : "password";
      console.log(passwordType.value);
    };

    return { passwordType, togglePasswordVisibility };
  },
};
</script>

<style lang="scss" scoped>
// LEFT AND RIGHT LINES IN BACKGROUND
.line {
  position: fixed;
  min-height: 100vh;
  opacity: 0.7;
  width: 1px;
  background: #e3e8ee;
}

.left-line {
  top: 0;
  left: 220px;
}

.right-line {
  top: 0;
  right: 200px;
}

.box {
  position: fixed;
  background: rgba(12, 0, 250, 0.5);
  z-index: 1;
  transform: rotate(168deg);

}

.left-blue-box {
  height: 44px;
  width: 199px;
  background: #81e9ff;
  top: calc(50% + 135px);
  left: 30px;
  clip-path: polygon(6% 0, 100% 0%, 94% 100%, 0% 100%);
}

.left-purple-box {
  height: 50px;
  width: 399px;
  top: calc(50% + 155px);
  left: -50px;
  clip-path: polygon(3% 0, 100% 0%, 97% 100%, 0% 100%);
}

.right-purple-box {
  height: 50px;
  width: 399px;
  top: calc(10% + 140px);
  right: -50px;
  clip-path: polygon(3% 0, 100% 0%, 97% 100%, 0% 100%);
}

.page-wrapper {
  min-height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  z-index: 1;

  &::before {
    position: fixed;
    content: "";
    background: url("../assets/images/gray-background.svg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    top: -200px;
    left: 0;
    height: 800px;
    // background: red;
    z-index: -1;
    width: 100%;
  }

  .page-content {
    min-height: 100vh;
    max-width: 542px;
    width: 90%;
    margin: auto;
    border: 1px dashed #e3e8ee;
    border-top: none;
    border-bottom: none;
    position: relative;
  }
}

.stripe-logo {
  padding: 50px 30px;
}

.login-form {
  padding: 48px 68px 72px 68px;
  background: #fff;
  box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.12),
    0px 15px 35px rgba(60, 66, 87, 0.08);
  border-radius: 4px;
  position: relative;
  z-index: 5;

  .title {
    font-size: 20px;
    line-height: 30px;
    font-weight: 600;
    margin-bottom: 25px;
    color: var(--gray);
  }

  @media screen and (max-width: 420px) {
    padding: 48px 28px 72px 28px;
  }
}

.form-wrapper {
  margin-bottom: 30px;
  position: relative;

  label {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
    color: var(--gray);
    font-size: 14px;
    line-height: 24px;

    .forgot-password {
      text-decoration: none;
      border: none;
      outline: none;
      font-size: 14px;
      line-height: 17px;
      color: var(--purpleColor);
    }
  }

  input {
    font: inherit;
    font-size: 16px;
    display: block;
    width: 100%;
    padding: 13.5px 44px 13.5px 16px;
    border: 1px solid #d9dce1;
    border-radius: 5px;
    color: #1a1f36;
  }

  input:focus {
    outline: none;
  }

  .password-toggler {
    position: absolute;
    top: 46px;
    right: 15px;
    font-size: 18px;
    color: #a3acb9;
  }
}

.custom-checkbox {
  .checkbox {
    display: flex;
    align-items: center;
    cursor: pointer;
    margin-bottom: 15px;
    color: var(--gray);
    font-size: 14px;
    font-weight: normal;

    .input {
      display: none;
    }

    .custom-check {
      width: 16px;
      height: 16px;
      border: 2px solid #dfe3e8;
      border-radius: 4px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-right: 6px;
      flex-shrink: 0;
      transition: all 0.15s linear;

      &::after {
        content: "\2714";
        color: #ffffff;
        transition: all 0.15s;
        transform: scale(0);
        font-size: 12px;
      }
    }
  }

  .input:checked + .custom-check {
    background: var(--purpleColor);
    border-color: var(--purpleColor);
  }

  .input:checked + .custom-check::after {
    transform: scale(1);
  }
}

.submit {
  width: 100%;
  display: block;
  background: var(--purpleColor);
  border-radius: 5px;
  padding: 13.5px 10px;
  color: #fff;
  margin: 30px 0;
}

.sso-button {
  display: block;
  width: 100%;
  color: var(--purpleColor);
  text-align: center;
  font-size: 14px;
}

.footer {
  padding: 30px 30px;

  .signup {
    font-size: 14px;
    color: #4f566b;
    margin-bottom: 15px;

    a {
      color: var(--purpleColor);
      text-decoration: none;
      outline: none;
    }
  }

  .copyright-links {
    display: flex;
    align-items: center;
    gap: 26px;

    .copyright {
      color: #4f566b;
      font-size: 14px;
    }

    .links {
      display: flex;
      align-items: center;
      list-style: none;
      gap: 26px;
      margin: 0;

      li {
        position: relative;

        &::after {
          position: absolute;
          left: -12px;
          top: 8px;
          content: "";
          height: 3px;
          width: 3px;
          border-radius: 50%;
          background: #4f566b;
        }

        a {
          text-decoration: none;
          color: #4f566b;
          font-size: 14px;
        }
      }
    }
  }
}
</style>
