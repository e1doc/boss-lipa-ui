<template>
  <div class="admin-container">
    <div class="admin-page-title flex-center">
      <font-awesome-icon icon="calendar" class="admin-icon" />
      Statement of Accounts
    </div>
    <div class="admin-body flex-wrap">
      <soa-table-menu />
      <div class="admin-content">
        <admin-soa-table />
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import SoaTableMenu from "@/components/admin/SoaTableMenu";
import AdminSoaTable from "@/components/admin/AdminSoaTable";
export default {
  name: "AdminSoa",
  components: {
    SoaTableMenu,
    AdminSoaTable,
  },
  computed: {
    ...mapGetters(["appointmentStatus"]),
  },
  data() {
    return {};
  },
  methods: {
    handleEventClick(info) {
      console.log(info);
    },
  },
  mounted() {
    window.scrollTo(0, 0);
  },
};
</script>

<style lang="scss" scoped>
div.admin-container {
  width: 100%;
  div.admin-page-title {
    color: #e8726f;
    font-size: 30px;
    font-weight: bold;
    line-height: 29px;
    text-transform: capitalize;
    margin-bottom: 90px;
    .admin-icon {
      color: #e8726f;
      font-size: 35px;
      margin-right: 15px;
    }
  }
  div.admin-body {
    max-width: 1200px;
    margin-left: auto;
    margin-right: auto;
    div.admin-search {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      justify-content: flex-end;
    }
    div.admin-content {
      width: 100%;
      margin-top: 35px;
    }
  }
}

@media only screen and (max-width: 1380px) {
  div.admin-container div.admin-page-title {
    font-size: 28px;
    margin-bottom: 40px;
  }
}
</style>
