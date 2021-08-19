<template>
  <div class="page-wrapper">
    <!-- LINES AND BOXES -->
    <div class="line left-line"></div>
    <div class="box left-blue-box"></div>
    <div class="box left-purple-box"></div>
    <!-- MAIN PAGE CONTENT -->
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
    <!-- LINES AND BOXES -->
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
.page-wrapper {
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
    z-index: -1;
    width: 100%;
  }

  .page-content {
    max-width: 542px;
    width: 90%;
    margin: auto;
    border: 1px dashed var(--borderColor);
    border-top: none;
    border-bottom: none;

    // LOGO
    .stripe-logo {
      padding: 50px 30px;
    }

    // LOGIN FORM
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
        color: var(--grayEight);
      }

      // Single Label plus Input
      .form-wrapper {
        margin-bottom: 32px;
        position: relative;

        label {
          display: flex;
          justify-content: space-between;
          align-items: center;
          margin-bottom: 12px;
          color: var(--grayEight);
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
          color: var(--grayNine);
        }

        input:focus {
          outline: none;
        }

        .password-toggler {
          position: absolute;
          top: 50px;
          right: 15px;
          font-size: 18px;
          color: #a3acb9;
        }
      }

      // Submit button
      .submit {
        width: 100%;
        display: block;
        background: var(--purpleColor);
        border-radius: 5px;
        padding: 13.5px 10px;
        color: #fff;
        margin: 28px 0;
      }

      // SSO signin button
      .sso-button {
        display: block;
        width: 100%;
        color: var(--purpleColor);
        text-align: center;
        font-size: 14px;
      }

      @media screen and (max-width: 420px) {
        padding: 48px 28px 72px 28px;
      }
    }

    // LOGIN FOOTER
    .footer {
      padding: 30px;

      // SIGN UP INSTEAD BUTTON
      .signup {
        font-size: 14px;
        color: var(--graySeven);
        margin-bottom: 15px;

        a {
          color: var(--purpleColor);
          text-decoration: none;
          outline: none;
        }
      }

      // COPYRIGHT AND LINKS
      .copyright-links {
        display: flex;
        align-items: center;
        gap: 26px;

        .copyright {
          color: var(--graySix);
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
              background: var(--graySix);
            }

            a {
              text-decoration: none;
              color: var(--graySix);
              font-size: 14px;
            }
          }
        }
      }

      @media screen and (max-width: 414px) {
        padding: 30px 10px;
      }
    }
  }
}

// LEFT AND RIGHT LINES IN BACKGROUND
.line {
  position: fixed;
  // height: 100%;
  min-height: 100vh;
  opacity: 0.7;
  width: 1px;
  background: var(--borderColor);

  @media screen and (max-width: 940px) {
    display: none;
  }
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
  top: calc(50% + 130px);
  left: 30px;
  clip-path: polygon(6% 0, 100% 0%, 94% 100%, 0% 100%);

  @media screen and (max-width: 1440px) {
    top: calc(50% - 25px);
  }

  @media screen and (max-width: 1368px) {
    top: calc(50% - 30px);
  }

  @media screen and (max-width: 1281px) {
    top: calc(50% - 40px);
  }

  @media screen and (max-width: 992px) {
    top: calc(50% - 75px);
  }

  @media screen and (max-width: 768px) {
    top: calc(50% - 90px);
  }
}

.left-purple-box {
  height: 50px;
  width: 399px;
  top: calc(50% + 155px);
  left: -50px;
  clip-path: polygon(3% 0, 100% 0%, 97% 100%, 0% 100%);

  @media screen and (max-width: 1440px) {
    top: calc(50% + 5px);
  }

  @media screen and (max-width: 1368px) {
    top: calc(50% + 0px);
  }

  @media screen and (max-width: 1281px) {
    top: calc(50% - 10px);
  }

  @media screen and (max-width: 992px) {
    top: calc(50% - 50px);
  }

  @media screen and (max-width: 768px) {
    top: calc(50% - 60px);
  }
}

.right-purple-box {
  height: 50px;
  width: 399px;
  top: calc(10% + 140px);
  right: -50px;
  clip-path: polygon(3% 0, 100% 0%, 97% 100%, 0% 100%);

  @media screen and (max-width: 1440px) {
    top: calc(30% - 85px);
  }

  @media screen and (max-width: 1368px) {
    top: calc(30% - 75px);
  }

  @media screen and (max-width: 1281px) {
    top: calc(30% - 65px);
  }

  @media screen and (max-width: 992px) {
    top: calc(30% - 40px);
  }

  @media screen and (max-width: 768px) {
    top: calc(30% - 15px);
  }
}
</style>
