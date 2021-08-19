<template>
  <div class="page-layout">
    <TheSidebar />
    <div class="main-content">
      <TheNavbar />
      <div class="content-wrapper">
        <div class="header">
          <h1>Payments</h1>
          <ul class="actions">
            <li>
              <button class="button">
                <img src="@/assets/images/filter-icon.svg" alt="filter-icon" />
                Filter
              </button>
            </li>
            <li>
              <button class="button">
                <img src="@/assets/images/export-icon.svg" alt="export-icon" />
                Export
              </button>
            </li>
            <li>
              <router-link to="/">
                <img src="@/assets/images/plus-icon.svg" alt="plus-icon" />
                Create payment
              </router-link>
            </li>
          </ul>
        </div>
        <div class="payments">
          <ul class="navigation">
            <li
              @click="changeFilter('all')"
              :class="[filter === 'all' ? 'active' : '']"
            >
              All
            </li>
            <li
              @click="changeFilter('succeeded')"
              :class="[filter === 'succeeded' ? 'active' : '']"
            >
              Succeeded
            </li>
            <li
              @click="changeFilter('refunded')"
              :class="[filter === 'refunded' ? 'active' : '']"
            >
              Refunded
            </li>
            <li
              @click="changeFilter('uncaptured')"
              :class="[filter === 'uncaptured' ? 'active' : '']"
            >
              Uncaptured
            </li>
          </ul>
          <div class="table-wrapper">
            <div class="table">
              <div class="table-header">
                <div class="column-name check"><span></span></div>
                <div class="column-name amount">Amount</div>
                <div class="column-name description">Description</div>
                <div class="column-name customer">Customer</div>
                <div class="column-name date">date</div>
                <div class="column-name actions"></div>
              </div>
              <ul class="table-content">
                <li v-for="item in data" :key="item.description">
                  <div class="check"><span></span></div>
                  <div class="amount">
                    US${{ item.amount }}
                    <span class="status"
                      >Succeeded
                      <img src="@/assets/images/checkmark.svg" alt="checkmark"
                    /></span>
                  </div>
                  <div class="description">
                    {{ item.description }}
                  </div>
                  <div class="customer">{{ item.customer }}</div>
                  <div class="date">{{ item.date }}</div>
                  <div class="actions">
                    <button class="button">
                      <img src="@/assets/images/dots.svg" alt="dots">
                    </button>
                  </div>
                </li>
              </ul>
            </div>
          </div>
        </div>
        <div class="footer">
          <div class="count">
            <p>16 <span>results</span></p>
          </div>
          <div class="actions">
            <button disabled class="button previous">Previous</button>
            <button class="button next">Next</button>
          </div>
        </div>
      </div>
    </div>
    <div class="checkbox"></div>
  </div>
</template>

<script>
import { ref } from "vue";
import TheNavbar from "../components/TheNavbar.vue";
import TheSidebar from "../components/TheSidebar.vue";
export default {
  components: { TheSidebar, TheNavbar },
  name: "Payments",

  setup() {
    const filter = ref("succeeded");
    const changeFilter = (newFilter) => {
      filter.value = newFilter;
    };
    const data = ref([
      {
        amount: "352.22",
        description: "fe3d8216-58f9-4dc1-aaef-2f19463b5258",
        customer: "hefovo87@ereyemind...",
        date: "7 Jul, 14:04",
      },
      {
        amount: "39.99",
        description: "0d7b6ac7-dbda-4157-bae9-e64749e538f5",
        customer: "john.doe@gmail.com",
        date: "7 Jul, 14:01",
      },
      {
        amount: "19.99",
        description: "eca84b25-0324-4f31-b9fb-d489048b77ae",
        customer: "jfamosinhoaraca@iseo...",
        date: "7 Jul, 13:28",
      },
      {
        amount: "19.99",
        description: "9ce0027a-2429-40aa-bca3-eb9fae9829db",
        customer: "gdontdisable@typery...",
        date: "7 Jul, 13:02",
      },
      {
        amount: "142.17",
        description: "73bb0713-d326-4983-a805-9cef0f15ff3c",
        customer: "psir@typre.com",
        date: "7 Jul, 12:34",
      },
      {
        amount: "93.76",
        description: "dff08e3b-037e-4fc9-a587-92850d82868e",
        customer: "qomarkhalildubai0@g...",
        date: "7 Jul, 12:16",
      },
      {
        amount: "931.00",
        description: "3005be4a-6d4d-487c-85c3-d61cfe64ef63",
        customer: "kfouzan.saleemc@yah...",
        date: "7 Jul, 11:31",
      },
      {
        amount: "19.99",
        description: "7e960154-e2e2-49eb-9252-edd51f421cd0",
        customer: "asaifah@gmx.com",
        date: "7 Jul, 11:18",
      },
      {
        amount: "41.99",
        description: "88f37e63-c2b2-4c09-aa89-428fc802fe09",
        customer: "5mohamad.hamod.5m...",
        date: "7 Jul, 10:46",
      },
      {
        amount: "179.98",
        description: "5a9aae47-1d6a-484e-8305-c75107796cd1",
        customer: "7lucyveenstra918@g...",
        date: "7 Jul, 10:12",
      },
      {
        amount: "15.17",
        description: "48eb8b41-9ff0-4d5d-82cc-4b9b820b5f53",
        customer: "0sajad@yopmail.com",
        date: "7 Jul, 06:03",
      },
      {
        amount: "41.99",
        description: "02fd1b96-0bba-48aa-8557-81021755b196",
        customer: "feverton78@gmail.com",
        date: "6 Jul, 23:45",
      },
      {
        amount: "67.83",
        description: "986bdfca-6c8d-4f40-b2ae-ed0abacccfce",
        customer: "lsid.ali_blidi@outlook...",
        date: "6 Jul, 23:32",
      },
      {
        amount: "35.01",
        description: "c5629140-ea34-40d8-97e4-d2986b33275e",
        customer: "twendel.b@yahoo.com",
        date: "6 Jul, 23:30",
      },
      {
        amount: "374.93",
        description: "c2194818-1485-437c-a389-6164e605d697",
        customer: "pdevonneq@gmail.com",
        date: "6 Jul, 23:16",
      },
      {
        amount: "330.91",
        description: "6583691d-4d9f-43ce-8f2f-0d2d95b30ad4",
        customer: "atotspop886@gmx.com",
        date: "6 Jul, 23:08",
      },
    ]);
    return { filter, changeFilter, data };
  },
};
</script>

<style lang="scss" scoped>
.page-layout {
  display: flex;
  align-items: flex-start;

  .main-content {
    margin-left: 270px;
    flex: 1;

    @media screen and (max-width: 1200px) {
      margin-left: 0;
    }

    .content-wrapper {
      padding: 0 40px;

      .header {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 20px;

        h1 {
          font-weight: bold;
          font-size: 28px;
          line-height: 33px;
          color: #1a1f36;
        }

        .actions {
          list-style: none;
          display: flex;
          gap: 8px;

          li {
            button {
              background: #ffffff;
              box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
                0px 0px 0px 1px rgba(60, 66, 87, 0.16),
                0px 1px 1px rgba(0, 0, 0, 0.12);
              border-radius: 4px;
              font-weight: 500;
              font-size: 14px;
              line-height: 17px;
              color: #3c4257;
              padding: 6px 8px;
              display: flex;
              align-items: center;
              gap: 6px;
            }

            a {
              text-decoration: none;
              background: #5469d4;
              box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
                0px 0px 0px 1px #5469d4, 0px 1px 1px rgba(0, 0, 0, 0.12);
              border-radius: 4px;
              display: flex;
              align-items: center;
              gap: 6px;
              color: #ffffff;
              font-weight: 500;
              font-size: 14px;
              line-height: 17px;
              padding: 6px 8px;
            }
          }
        }
      }

      .payments {
        margin-bottom: 20px;

        .navigation {
          list-style: none;
          display: flex;
          gap: 26px;
          margin-bottom: 2px;

          li {
            cursor: pointer;
            font-weight: 500;
            font-size: 14px;
            line-height: 17px;
            color: #697386;
            padding: 0 0 9px 0;

            &.active {
              color: #5469d4;
              box-shadow: 0px 2px 0px #5469d4;
            }
          }
        }

        .table {
          border-top: 1px solid #e3e8ee;
          border-bottom: 1px solid #e3e8ee;
        }
      }

      .footer {
        display: flex;
        justify-content: space-between;
        align-content: center;
        margin-bottom: 27px;

        .count {
          p {
            font-weight: 500;
            font-size: 14px;
            line-height: 17px;
            color: #3c4257;

            span {
              font-weight: 400;
            }
          }
        }

        .actions {
          display: flex;
          gap: 8px;

          button {
            padding: 6px 8px;
            background: #ffffff;
            box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
              0px 0px 0px 1px rgba(60, 66, 87, 0.16),
              0px 1px 1px rgba(0, 0, 0, 0.12);
            border-radius: 4px;
            font-weight: 500;
            font-size: 14px;
            line-height: 17px;
            color: #3c4257;

            &:disabled {
              opacity: 0.5;
              box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
                0px 0px 0px 1px rgba(60, 66, 87, 0.16),
                0px 1px 1px rgba(0, 0, 0, 0.12);
            }
          }
        }
      }
    }
  }

  .checkbox {
    background: #ffffff;
    height: 14px;
    width: 14px;
    box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
      0px 0px 0px 1px rgba(60, 66, 87, 0.16), 0px 1px 1px rgba(0, 0, 0, 0.12);
    border-radius: 4px;

    @media screen and (max-width:1200px) {
      display: none;
    }
  }
}

.table {
  display: block;
  width: 100%;
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
  -ms-overflow-style: -ms-autohiding-scrollbar;
}

.table-header,
.table-content li {
  display: flex;
  gap: 10px;
  align-items: center;
  padding: 14px 0 14px 4px;
  width: 100%;
  border-bottom: 1px solid #e3e8ee;

  .check {
    // flex: 0 0 4%;
    // max-width: 4%;
    // width: 100%;
    // padding-left: 10px;
    width: 20px;
    flex-shrink: 0;

    span {
      cursor: pointer;
      display: block;
      background: #ffffff;
      height: 14px;
      width: 14px;
      box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
        0px 0px 0px 1px rgba(60, 66, 87, 0.16), 0px 1px 1px rgba(0, 0, 0, 0.12);
      border-radius: 4px;
    }
  }

  .amount {
    // flex: 0 0 17%;
    // max-width: 17%;
    width: 195px;
    // width: 100%;
    flex-shrink: 0;
  }

  .description {
    flex: 0 0 50%;
    max-width: 50%;
    width: 100%;
    // width: 550px;
    flex-shrink: 0;
  }

  .customer {
    // flex: 0 0 15%;
    // max-width: 15%;
    // width: 100%;
    width: 170px;
    flex-shrink: 0;
  }

  .date {
    // flex: 0 0 10%;
    // max-width: 10%;
    // width: 100%;
    width: 120px;
    flex-shrink: 0;
  }

  .actions {
    // flex: 1;
    // width: 100%;
    margin-left: auto;
    flex-shrink: 0;
    text-align: right;
    padding-right: 16px;
  }

  .column-name {
    text-transform: uppercase;
    font-weight: 500;
    font-size: 11px;
    line-height: 13px;
    color: #1a1f36;

    &.amount {
      padding-left: 16px;
    }

    &.description {
      padding-left: 10px;
    }
  }
}

.table-content {
  list-style: none;

  li {
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
      color: #1a1f36;
    }

    .description {
      font-size: 13px;
      line-height: 16px;
      color: #4f566b;
    }
  }
}

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