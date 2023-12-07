<template>
  <div id="landing">
    <LandingNav />
    <div id="landing-body">
      <ServicesDiv />
      <PermitDiv />
      <VerifyDiv />
    </div>
    <FooterSection />
  </div>
</template>

<script>
import LandingNav from "@/components/lipa/LandingNav";
import ServicesDiv from "@/components/lipa/ServicesDiv";
import PermitDiv from "@/components/lipa/PermitDiv";
import VerifyDiv from "@/components/lipa/VerifyDiv";
import FooterSection from "@/components/FooterSection";

export default {
  name: "Landing",
  components: {
    LandingNav,
    ServicesDiv,
    PermitDiv,
    VerifyDiv,
    FooterSection,
  },
  data() {
    return {
      type: "landing",
    };
  },
};
</script>

<style lang="scss" scoped>
* {
  overflow-x: hidden;
  box-sizing: border-box;
}

#landing {
  width: 100vw;
  height: 100%;
  box-sizing: border-box;
  overflow-x: hidden;
}

#landing-body {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
  overflow-x: hidden;
}
</style>
