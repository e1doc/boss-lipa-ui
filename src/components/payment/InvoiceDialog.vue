<template>
  <section>
    <div class="dialog-holder">
      <div class="dialog-header">
        <div class="store-avatar">
          <font-awesome-icon
            icon="store"
            class="icon"
            v-if="currentSoaType === 'business'"
          />
          <font-awesome-icon
            icon="city"
            class="icon"
            v-if="
              currentSoaType === 'real_property' ||
              currentSoaType === 'building'
            "
          />
        </div>
        <div
          class="text-bold size14 main-title"
          v-if="currentSoaType === 'business'"
        >
          {{
            currentSelectedBusiness.businessdetails.name != ""
              ? currentSelectedBusiness.businessdetails.name
              : currentSelectedBusiness.businessdetails.trade_name
          }}
        </div>
        <div
          class="text-bold size14 main-title"
          v-if="currentSoaType === 'real_property'"
        >
          {{ currentSelectedProperty.buildingdetails.tax_dec_no }}
        </div>
        <div
          class="text-bold size14 main-title"
          v-if="currentSoaType === 'building'"
        >
          {{ currentSelectedBuilding.series_number }}
        </div>
        <div class="triangle">
          <font-awesome-icon icon="caret-down" class="icon" />
        </div>
        <div class="times" @click="closeModal()" v-if="!isPayment">
          <font-awesome-icon icon="times" class="icon" />
        </div>
      </div>
      <div class="dialog-body">
        <!-- <div class="invoice-action" v-if="!isPayment">
          <div class="title mb20">New Invoice</div>
          <div class="mb5">
            <button-full-outline class="btn-reg" :link="{ path: 'payment' }"
              >PAY INVOICE</button-full-outline
            >
          </div>
          <div class="text-later" @click="closeModal()">Pay Later</div>
        </div> -->
        <div class="invoice-details">
          <div class="invoice-title">INVOICE DETAILS</div>
          <div class="details-body">
            <div class="details-item">
              <div class="item-label">Reference No:</div>
              <div class="item-value">
                {{ currentSelectedBill.referenceno }}
              </div>
            </div>
            <div class="details-item">
              <div class="item-label">Year:</div>
              <div class="item-value">
                {{
                  currentSoaType === "business"
                    ? generatedBill.year
                    : currentSelectedBill.year
                }}
              </div>
            </div>
            <div class="details-item">
              <div class="item-label">Due Date:</div>
              <div class="item-value">
                {{ currentSelectedBill.duedate | moment("MMMM DD, YYYY") }}
              </div>
            </div>
            <div class="details-item">
              <div class="item-label">Quarter:</div>
              <div class="item-value">{{ currentSelectedBill.quarter }}</div>
            </div>
          </div>
        </div>
        <div class="invoice-owner">
          <div class="invoice-title">
            {{
              currentSoaType === "business"
                ? "BUSINESS DETAILS"
                : currentSoaType === "real_property"
                ? "Real Property Details"
                : "Building Details"
            }}
          </div>
          <div class="owner-details">
            <div class="item-label">
              {{
                currentSoaType === "business"
                  ? "Business Owner"
                  : currentSoaType === "real_property"
                  ? "Real Property Owner Name"
                  : "Building Owner Name"
              }}
            </div>
            <div class="item-value" v-if="currentSoaType === 'business'">
              {{
                currentSelectedBusiness.businessbasicinformation
                  .owner_first_name
              }}
              {{
                currentSelectedBusiness.businessbasicinformation
                  .owner_middle_name
              }}
              {{
                currentSelectedBusiness.businessbasicinformation.owner_last_name
              }}
            </div>
            <div class="item-value" v-if="currentSoaType === 'real_property'">
              {{
                currentSelectedProperty.buildingbasicinformation
                  .owner_first_name
              }}
            </div>
            <div class="item-value" v-if="currentSoaType === 'building'">
              {{
                currentSelectedBuilding.buildingbasicinformation
                  .owner_first_name
              }}
              {{
                currentSelectedBuilding.buildingbasicinformation.owner_last_name
              }}
            </div>
          </div>
        </div>
        <div class="meta-fees">
          <div class="meta-fees-title">FEES</div>
          <div
            class="meta-fees-details"
            v-for="(item, index) of currentSelectedBill.fees"
            :key="index"
          >
            <div class="meta-label-holder">
              <div class="meta-label">{{ item.fee_description }}</div>
            </div>
            <div class="meta-value-holder">
              <div class="meta-value">
                <div>
                  ₱ {{ formatCurrency(parseFloat(item.amount).toFixed(2)) }}
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="invoice-amount">
          <div class="amount-details">
            <div class="item-label">Total Amount</div>
            <div class="item-value">
              ₱
              {{
                formatCurrency(
                  parseFloat(currentSelectedBill.amount).toFixed(2)
                )
              }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import ButtonFullOutline from "@/components/ButtonFullOutline";
import { mapGetters } from "vuex";
export default {
  name: "InvoiceDialog",
  components: {
    ButtonFullOutline,
  },
  computed: {
    ...mapGetters([
      "currentSelectedBusiness",
      "currentSelectedBill",
      "generatedBill",
      "currentSoaType",
      "currentSelectedProperty",
      "currentSelectedBuilding",
    ]),
  },
  data() {
    return {
      fees: [
        {
          label: "Mayor's Permit",
          value: "₱ 500.00",
        },
        {
          label: "Environmental Fee",
          value: "₱ 1200.00",
        },
        {
          label: "Business Plate Fee",
          value: "₱ 250.00",
        },
        {
          label: "Medical Fee",
          value: "₱ 1.00",
        },
        {
          label: "Business Processing Fee",
          value: "₱ 50.00",
        },
        {
          label: "Security Seal Fee",
          value: "₱ 50.00",
        },
        {
          label: "Sanitary Fee",
          value: "₱ 200.00",
        },
        {
          label: "Zoning Fee",
          value: "₱ 1285.00",
        },
        {
          label: "Building Permit Fee",
          value: "₱ 120.00",
        },
        {
          label: "Electrical Fee",
          value: "₱ 300.00",
        },
        {
          label: "Plumbing Permit Fee",
          value: "₱ 60.00",
        },
        {
          label: "Sign Board Fee",
          value: "₱ 192.00",
        },
        {
          label: "Business Tax",
          value: "₱ 220.00",
        },
      ],
    };
  },
  mounted() {
    console.log(this.generatedBill);
  },
  methods: {
    async payInvoice() {
      this.$store.commit("setCurrentSoa", {
        id: this.currentSelectedBusiness.id,
        type: "business",
      });
      console.log("soa", soa);
      this.$store.commit("setCurrentSoaObj", soa);
      this.$store.commit("setAppointmentAction", "add");
      this.$router.push({ path: "payment" });
    },
    formatCurrency(str) {
      var parts = str.toString().split(".");
      parts[0] = parts[0].replace(/\B(?=(\d{3})+(?!\d))/g, ",");
      if (parts.length < 2) {
        parts.push("00");
      }
      return parts.join(".");
    },
    closeModal() {
      this.$modal.hide("invoiceModal");
    },
  },
  props: {
    isPayment: {
      type: Boolean,
      default: false,
      required: false,
    },
  },
};
</script>

<style lang="scss" scoped>
.meta-fees {
  display: flex;
  flex-direction: column;
  .meta-fees-title {
    margin: 25px 0px;
    color: rgba($color: #2699fb, $alpha: 0.73);
    font-weight: bold;
    font-size: 15px;
  }
  .meta-fees-details {
    display: flex;
    flex-direction: row;
    padding: 10px 5px;
    .meta-label-holder {
      text-align: left;
      flex: 1;
      .meta-label {
        font-size: 14px;
      }
    }
    .meta-value-holder {
      text-align: right;
      flex: 1;
      font-weight: bold;
    }
  }
}
.dialog-holder {
  display: flex;
  flex-direction: column;
  border-radius: 8px;
  width: 100%;
  max-width: 650px;
  margin: 30px auto;
  .dialog-header {
    background: #2699fb;
    position: relative;
    border-radius: 15px 15px 0px 0px;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    color: #ffffff;
    padding: 20px 15px;
    .store-avatar {
      border: 2px #ffffff solid;
      border-radius: 5px;
      padding: 10px 10px;
      margin-bottom: 0;
      margin-right: 15px;
      .icon {
        font-size: 20px;
      }
    }
    .main-title {
      font-size: 24px;
    }
    .triangle {
      position: absolute;
      bottom: -27px;
      left: 0;
      width: 100%;
      text-align: center;
      .icon {
        font-size: 48px;
        color: #2699fb;
      }
    }
    .times {
      position: absolute;
      top: 3px;
      right: 11px;
      padding: 10px;
      cursor: pointer;
      .icon {
        font-size: 28px;
      }
    }
  }
  .dialog-body {
    background: #ffffff;
    border-radius: 0px 0px 15px 15px;
    padding: 40px 30px 30px;
    .invoice-action {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding-bottom: 35px;
      border-bottom: 2px #eaf6ff solid;
      .title {
        font-size: 24px;
      }
      .text-later {
        color: #2699fb;
        font-size: 14px;
        text-decoration: underline;
        padding-top: 10px;
        cursor: pointer;
      }
    }

    .invoice-title {
      margin-bottom: 25px;
      color: rgba($color: #2699fb, $alpha: 0.73);
      font-weight: bold;
      font-size: 15px;
    }
    .invoice-details {
      padding: 0 0 30px 0px;
      border-bottom: 2px #eaf6ff solid;
      .details-body {
        padding-left: 20px;
        display: flex;
        flex-wrap: wrap;
        .details-item {
          width: 50%;
          margin-bottom: 25px;
          .item-label {
            font-weight: bold;
            margin-bottom: 8px;
            font-size: 13px;
          }
          .item-value {
            font-size: 16px;
            font-family: "Proxima Nova Rg";
          }
        }
      }
    }
    .invoice-owner {
      border-bottom: 2px #eaf6ff solid;
      padding: 30px 0px;
      .owner-details {
        .item-label {
          font-weight: bold;
          margin-bottom: 8px;
          font-size: 13px;
        }
        .item-value {
          font-size: 16px;
        }
      }
    }
    .invoice-amount {
      padding: 15px;
      background-color: #f1f9ff;
      .amount-details {
        display: flex;
        flex-wrap: wrap;
        .item-label {
          width: 50%;
          margin: auto 0;
          color: rgba($color: #2699fb, $alpha: 0.73);
          font-weight: bold;
          font-size: 14px;
          font-family: "Proxima Nova Rg";
          text-transform: uppercase;
        }
        .item-value {
          width: 50%;
          color: #2699fb;
          font-weight: bold;
          font-size: 20px;
          font-family: "Proxima Nova Rg";
          text-align: right;
        }
      }
    }
  }
}

.details-item:nth-last-child(-n + 2) {
  margin-bottom: 0 !important;
}
.size14 {
  font-size: 14px;
}

.invoice-title {
  margin-bottom: 25px;
  color: rgba($color: #2699fb, $alpha: 0.73);
  font-weight: bold;
  font-size: 18px;
}

@media only screen and (max-width: 860px) {
  .dialog-holder {
    max-width: 90%;
  }
}

@media only screen and (max-width: 480px) {
  .dialog-holder {
    max-width: 100%;
    margin: 0;
  }

  .dialog-holder .dialog-body .invoice-details {
    padding-top: 0;
  }

  .dialog-holder .dialog-body .invoice-details .details-body {
    padding-left: 0;
  }
  .dialog-holder .dialog-body .invoice-details .details-body .details-item {
    width: 100%;
  }

  .details-item:nth-last-child(-n + 2) {
    margin-bottom: 25px !important;
  }

  .dialog-holder .dialog-body .invoice-amount .amount-details .item-value {
    font-size: 18px;
    text-align: left;
    width: 100%;
    margin-top: 15px;
  }

  .dialog-holder
    .dialog-body
    .invoice-details
    .details-body
    .details-item
    .item-value,
  .dialog-holder .dialog-body .invoice-owner .owner-details .item-value {
    font-size: 14px;
  }
}
</style>
