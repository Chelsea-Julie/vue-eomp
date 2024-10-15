<template>
  <nav class="navbar navbar-expand-lg sticky-top">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">
        <img src="https://chelsea-julie.github.io/all-images/images/Random/cj.png" alt="logo" class="img-thumbnail" loading="lazy">
      </router-link>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link text-light" aria-current="page" href="#landing">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link text-light" href="#about">About</a>
          </li>
          <li class="nav-item">
            <a class="nav-link text-light" href="#resume">Education&Experience</a>
          </li>
          <li class="nav-item">
            <a class="nav-link text-light" href="#project">Projects</a>
          </li>
          <li class="nav-item">
            <a class="nav-link text-light" href="#reachme">Reach me</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  mounted() {
    // Add an event listener to the window to detect scroll changes
    window.addEventListener("scroll", this.setActiveLink);
  },
  beforeUnmount() {
    // Clean up the event listener when the component is unmounted
    window.removeEventListener("scroll", this.setActiveLink);
  },
  methods: {
    setActiveLink() {
      const sections = document.querySelectorAll("section");
      const navLinks = document.querySelectorAll(".nav-link");
      let currentSection = "";

      // Determine the current section in the viewport
      sections.forEach((section) => {
        const sectionTop = section.offsetTop - 100; // Adjust based on navbar height
        if (window.scrollY >= sectionTop) {
          currentSection = section.getAttribute("id");
        }
      });

      // Update the active class for navigation links
      navLinks.forEach((link) => {
        link.classList.remove("active");
        if (link.getAttribute("href").includes(currentSection)) {
          link.classList.add("active");
        }
      });
    },
  },
};
</script>

<style scoped>
/* Styling for the active link */
.nav-link.active {
  font-weight: bold;
  text-decoration: underline;
}
</style>
