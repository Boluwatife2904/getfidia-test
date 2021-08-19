<template>
  <div class="page-layout">
    <TheSidebar :visible="showSidebar" />
    <div class="main-content">
      <TheNavbar />
      <div class="content-wrapper">
        <div class="header">
          <h1 @click="toggleSidebar">Payments</h1>
          <ul class="actions">
            <li>
              <the-button>
                <img src="@/assets/images/filter-icon.svg" alt="filter-icon" />
                Filter
              </the-button>
            </li>
            <li>
              <the-button>
                <img src="@/assets/images/export-icon.svg" alt="export-icon" />
                Export
              </the-button>
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
                <div class="column-name check">
                  <!-- CUSTOM CHECKBOX -->
                  <custom-check
                    @perform-action="selectAll"
                    id="checkAll"
                    :checked="false"
                  ></custom-check>
                </div>
                <div class="column-name amount">Amount</div>
                <div class="column-name description">Description</div>
                <div class="column-name customer">Customer</div>
                <div class="column-name date">date</div>
                <div class="column-name actions"></div>
              </div>
              <ul class="table-content">
                <TableItem
                  v-for="item in data"
                  :key="item.description"
                  :item="item"
                />
              </ul>
            </div>
          </div>
        </div>
        <div class="footer">
          <div class="count">
            <p>16 <span>results</span></p>
          </div>
          <div class="actions">
            <the-button :disabled="true">Previous</the-button>
            <the-button>Next</the-button>
          </div>
        </div>
      </div>
    </div>
    <div class="right-checkbox"></div>
  </div>
</template>

<script>
import { ref } from "vue";
import TheNavbar from "../components/TheNavbar.vue";
import TheSidebar from "../components/TheSidebar.vue";
import TableItem from "../components/TableItem.vue";
import CustomCheck from "../components/CustomCheck.vue";
import TheButton from "../components/TheButton.vue";
export default {
  components: { TheSidebar, TheNavbar, TableItem, CustomCheck, TheButton },
  name: "Payments",

  setup() {
    const filter = ref("succeeded");
    const showSidebar = ref(false);
    const changeFilter = (newFilter) => {
      filter.value = newFilter;
    };
    const toggleSidebar = () => {
      showSidebar.value = !showSidebar.value;
    };
    const data = ref([
      {
        amount: "352.22",
        description: "fe3d8216-58f9-4dc1-aaef-2f19463b5258",
        customer: "hefovo87@ereyemind...",
        date: "7 Jul, 14:04",
        checked: false,
      },
      {
        amount: "39.99",
        description: "0d7b6ac7-dbda-4157-bae9-e64749e538f5",
        customer: "john.doe@gmail.com",
        date: "7 Jul, 14:01",
        checked: false,
      },
      {
        amount: "19.99",
        description: "eca84b25-0324-4f31-b9fb-d489048b77ae",
        customer: "jfamosinhoaraca@iseo...",
        date: "7 Jul, 13:28",
        checked: false,
      },
      {
        amount: "19.99",
        description: "9ce0027a-2429-40aa-bca3-eb9fae9829db",
        customer: "gdontdisable@typery...",
        date: "7 Jul, 13:02",
        checked: false,
      },
      {
        amount: "142.17",
        description: "73bb0713-d326-4983-a805-9cef0f15ff3c",
        customer: "psir@typre.com",
        date: "7 Jul, 12:34",
        checked: false,
      },
      {
        amount: "93.76",
        description: "dff08e3b-037e-4fc9-a587-92850d82868e",
        customer: "qomarkhalildubai0@g...",
        date: "7 Jul, 12:16",
        checked: false,
      },
      {
        amount: "931.00",
        description: "3005be4a-6d4d-487c-85c3-d61cfe64ef63",
        customer: "kfouzan.saleemc@yah...",
        date: "7 Jul, 11:31",
        checked: false,
      },
      {
        amount: "19.99",
        description: "7e960154-e2e2-49eb-9252-edd51f421cd0",
        customer: "asaifah@gmx.com",
        date: "7 Jul, 11:18",
        checked: false,
      },
      {
        amount: "41.99",
        description: "88f37e63-c2b2-4c09-aa89-428fc802fe09",
        customer: "5mohamad.hamod.5m...",
        date: "7 Jul, 10:46",
        checked: false,
      },
      {
        amount: "179.98",
        description: "5a9aae47-1d6a-484e-8305-c75107796cd1",
        customer: "7lucyveenstra918@g...",
        date: "7 Jul, 10:12",
        checked: false,
      },
      {
        amount: "15.17",
        description: "48eb8b41-9ff0-4d5d-82cc-4b9b820b5f53",
        customer: "0sajad@yopmail.com",
        date: "7 Jul, 06:03",
        checked: false,
      },
      {
        amount: "41.99",
        description: "02fd1b96-0bba-48aa-8557-81021755b196",
        customer: "feverton78@gmail.com",
        date: "6 Jul, 23:45",
        checked: false,
      },
      {
        amount: "67.83",
        description: "986bdfca-6c8d-4f40-b2ae-ed0abacccfce",
        customer: "lsid.ali_blidi@outlook...",
        date: "6 Jul, 23:32",
        checked: false,
      },
      {
        amount: "35.01",
        description: "c5629140-ea34-40d8-97e4-d2986b33275e",
        customer: "twendel.b@yahoo.com",
        date: "6 Jul, 23:30",
        checked: false,
      },
      {
        amount: "374.93",
        description: "c2194818-1485-437c-a389-6164e605d697",
        customer: "pdevonneq@gmail.com",
        date: "6 Jul, 23:16",
        checked: false,
      },
      {
        amount: "330.91",
        description: "6583691d-4d9f-43ce-8f2f-0d2d95b30ad4",
        customer: "atotspop886@gmx.com",
        date: "6 Jul, 23:08",
        checked: false,
      },
    ]);
    const selectAll = () => {
      data.value.forEach((item) => {
        item.checked = item.checked
          ? (item.checked = false)
          : (item.checked = true);
      });
    };
    return {
      filter,
      changeFilter,
      data,
      selectAll,
      showSidebar,
      toggleSidebar,
    };
  },
};
</script>

<style lang="scss" scoped>
// PAGE LAYOUT
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

      // HEADER SHOWING "PAYMENT" AND THE THREE ACTION BUTTONS
      .header {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 20px;

        h1 {
          font-weight: bold;
          font-size: 28px;
          line-height: 33px;
          color: var(--grayNine);
        }

        .actions {
          list-style: none;
          display: flex;
          gap: 8px;

          li {
            a {
              text-decoration: none;
              background: var(--blueColor);
              box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
                0px 0px 0px 1px var(--blueColor),
                0px 1px 1px rgba(0, 0, 0, 0.12);
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

        @media screen and (max-width: 576px) {
          align-items: flex-start;
          flex-direction: column;

          .actions {
            margin-left: auto;
            margin-top: 8px;
          }
        }
      }

      // TABLE RECORDS
      .payments {
        margin-bottom: 20px;

        // TABS FOR CHANGING TABLE STATUS
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
            color: var(--graySix);
            padding: 0 0 9px 0;

            &.active {
              color: var(--blueColor);
              box-shadow: 0px 2px 0px var(--blueColor);
            }
          }
        }

        // TABLE
        .table {
          border-top: 1px solid var(--borderColor);
          border-bottom: 1px solid var(--borderColor);
          display: block;
          width: 100%;
          overflow-x: auto;
          -webkit-overflow-scrolling: touch;
          -ms-overflow-style: -ms-autohiding-scrollbar;

          /* CUSTOM CSS SCROLLBAR */
          &::-webkit-scrollbar {
            height: 8px;
            display: none;
          }
          &::-webkit-scrollbar-track {
            background: #f1f1f1;
          }
          &::-webkit-scrollbar-thumb {
            background: rgb(182, 182, 182);
            border-radius: 100px;
          }
          &::-webkit-scrollbar-thumb:hover {
            background: rgb(142, 142, 142);
          }

          // TABLE HEADER
          .table-header {
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
              padding-right: 16px;
            }

            .column-name {
              text-transform: uppercase;
              font-weight: 500;
              font-size: 11px;
              line-height: 13px;
              color: var(--grayNine);

              &.amount {
                padding-left: 16px;
              }

              &.description {
                padding-left: 10px;
              }
            }
          }

          // ITEMS WRAPPER
          .table-content {
            list-style: none;
          }
        }
      }

      // FOOTER SHOWING NUMBER OF RECORD WITH PREV AND NEXT BUTTONS
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
            color: var(--grayEight);

            span {
              font-weight: 400;
            }
          }
        }

        .actions {
          display: flex;
          gap: 8px;
        }
      }
    }
  }

  // CHECKBOX AT TOP RIGHT CORNER OF PAGE
  .right-checkbox {
    background: #ffffff;
    height: 14px;
    width: 14px;
    box-shadow: 0px 2px 5px rgba(60, 66, 87, 0.08),
      0px 0px 0px 1px rgba(60, 66, 87, 0.16), 0px 1px 1px rgba(0, 0, 0, 0.12);
    border-radius: 4px;

    @media screen and (max-width: 1200px) {
      display: none;
    }
  }
}
</style>