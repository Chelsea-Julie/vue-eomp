<template>
    <div class="container-fluid">
      <section class="row min-vh-100" id="landing">
        <LandingSection /> 
      </section>
      <section class="row min-vh-100" id="about">
        <AboutSection /> 
      </section>
      <section class="row min-vh-100" id="resume">
        <Education />
      </section>
      <section class="row min-vh-100" id="project">
        <Projects />
      </section>
      <section class="row min-vh-100" id="testimonials">
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
import Projects from '@/components/ProjectsSection.vue'

export default {
name: 'HomeView',
components: {
    LandingSection, AboutSection, Education, Testimonials, Projects
}
}
</script>


<style scoped>
.container-fluid{
  padding-inline: 0px !important;
}
</style>
