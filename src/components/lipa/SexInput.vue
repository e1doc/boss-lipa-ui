<template>
  <div class="sex">
    <input
      :type="type"
      :id="idMale"
      v-model="selectedSex"
      value="M"
      @change="handleChange('M')"
    />
    <label :for="idMale">Male</label>

    <input
      :type="type"
      :id="idFemale"
      v-model="selectedSex"
      value="F"
      @change="handleChange('F')"
    />
    <label :for="idFemale">Female</label>
  </div>
</template>

<script>
export default {
  props: {
    value: String,
    type: {
      type: String,
      default: "radio",
    },
  },
  data() {
    return {
      selectedSex: this.value || "M", // Default to 'M' if not provided
    };
  },
  computed: {
    idMale() {
      return `male_${this._uid}`;
    },
    idFemale() {
      return `female_${this._uid}`;
    },
  },
  watch: {
    selectedSex(newSex) {
      this.$emit("input", newSex);
    },
  },
  methods: {
    handleChange(sex) {
      this.selectedSex = sex;
    },
  },
};
</script>

<style scoped>
.sex {
  margin-bottom: 15px;
}

input[type="radio"] {
  width: 15px;
  height: 15px;
  border-radius: 50%;
  margin-right: 5px;
  cursor: pointer;
}

label {
  margin-right: 15px;
}
</style>
