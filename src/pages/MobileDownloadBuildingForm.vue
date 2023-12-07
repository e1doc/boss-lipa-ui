<template>
  <div class="meta-parent-box">
    <div class="meta-form-holder">
      <downloadable-building-form />
    </div>
    <div class="meta-message-holder">
      <h3 class="meta-message">{{ message }}</h3>
    </div>
  </div>
</template>

<script>
import DownloadableBuildingForm from "../components/application/DownloadableBuildingForm.vue";
import axios from "axios";

export default {
  name: "MobileDownloadBuildingForm",
  components: { DownloadableBuildingForm },
  mounted() {
    this.getData();
  },
  data() {
    return {
      message: "Please wait, your file is now downloading...",
    };
  },
  methods: {
    async getData() {
      const id = this.$route.params.id;
      const token = this.$route.params.token;
      this.$store.commit("setAuthToken", token);

      const result = await axios.get(
        `${process.env.VUE_APP_API_URL}/api/download-building/?id=${id}`,
        { headers: { Authorization: `jwt ${token}` } }
      );

      console.log(result);

      if (result.data) {
        const { data } = result;
        let application = {
          id: data.id,
          is_draft: data.is_draft,
          is_approve: data.is_approve,
          is_disapprove: data.is_disapprove,
          created_at: data.created,
          application_status: data.application_status,
          last_submitted: data.last_submitted,
          series_number: data.series_number,
        };

        await this.$store.commit("setBuildingApplication", application);

        if (data.buildingbasicinformation !== null) {
          await this.$store.commit(
            "setBuildingBasicInformation",
            data.buildingbasicinformation
          );
        }

        if (data.buildingdetails !== null) {
          await this.$store.commit("setBuildingDetails", data.buildingdetails);
        }

        if (data.buildingotherdetails !== null) {
          await this.$store.commit(
            "setBuildingOtherDetails",
            data.buildingotherdetails
          );
        }

        await this.$store.commit("setPrintProperty", true);
        this.message =
          "Please close this window after successfully downloading your building permit application form. Thank you!";
      }
      try {
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
div.meta-parent-box {
  width: 100%;
  margin-top: 50px;
  padding-bottom: 50px;
  .meta-form-holder {
    position: absolute;
    opacity: 0;
    top: -500px;
    z-index: -1;
  }
  .meta-message-holder {
    display: flex;
    padding: 13px;
    flex: 1;
    .meta-message {
      text-align: center;
    }
  }
}
</style>