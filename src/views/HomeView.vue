<template>
    <div class="container-fluid">
      <section class="row vh-100" id="landing">
        <LandingSection /> 
      </section>
      <section class="row vh-100" id="about">
        <AboutSection /> 
      </section>
      <section class="row vh-100" id="resume">
        <Education />
      </section>
      <section class="row" id="project">
        
      </section>
      <section class="row" id="testimonials">
        <testimonials/>
      </section>
      <section class="row" id="reachme">
        
      </section>
    </div>
</template>
  
<script >
import LandingSection from '../components/LandingSection.vue'
import AboutSection from '../components/AboutSection.vue'
import Education from '@/components/EducationSection.vue'
import Testimonials from '../components/TestimonialsSections.vue'
export default {
name: 'HomeView',
components: {
    LandingSection, AboutSection, Education, Testimonials
}
}
</script>


<style scoped>
.container-fluid{
  padding-inline: 0px !important;
}
</style>
