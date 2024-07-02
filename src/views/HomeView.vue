<template>
    <div class="container-fluid">
      <section class="row" id="landing">
        <LandingSection /> 
      </section>
      <section class="row" id="about">
        <AboutSection /> 
      </section>
      <section class="row" id="resume"></section>
      <section class="row" id="project"></section>
      <section class="row" id="testimonials"></section>
      <section class="row" id="reachme"></section>
    </div>
</template>
  
<script >
import LandingSection from '../components/LandingSection.vue'
import AboutSection from '../components/AboutSection.vue'
export default {
name: 'HomeView',
components: {
    LandingSection, AboutSection
}
}
</script>


<style scoped>
.container-fluid{
  padding-inline: 0px !important;
}
</style>
