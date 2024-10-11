<template>
    <div class="container-fluid">

        <h1>Projects</h1>
    </div>

    <div class="container-fluid d-flex flex-row justify-content-center">
      
        <div class="concat">
            <ul class="cards">
            <li cont v-for="(project, index) in projects" :key="index">
                <a href="" class="card">
                <div class="card__overlay">
                  <div class="card__header d-flex flex-row justify-content-center">
                    
                    <div class="card__header-text ">
                      <div class="col-12 ">
                        <img :src="project.img_url" :alt="project.name">
                      </div>
                      <div class="col-12">
                        <h3 class="card__title">{{ project.name }}</h3>            

                      </div>
                      <div class="col-12">
                        <span class="card__status">1 month ago</span>
                      </div>
                    </div>
                    </div>
                    <p class="card__description">{{ project.description }}</p>
                    <div class="buttonsThingy">
                      <div class="col d-flex flex-row justify-content-around"><a class="btn" :href="project.github" target="_blank">GitHub</a> <a class="btn" :href="project.vercel" target="_blank">Vercel</a></div>
                    </div>
                </div>
                </a>      
            </li>
            </ul>
        </div>
    </div>
</template>

<script setup>
import AOS from "aos";
import "aos/dist/aos.css";

    import {computed, onMounted } from 'vue'
    import {useStore} from 'vuex'


    const projects = computed(() => store.state.projects)
    const store = useStore()
    console.log(projects);

  
    onMounted(() => {
        store.dispatch('fetchProjects')
      })
      onMounted(async () => {
        AOS.init({ duration: 1500, once: false });
      });
</script>

<style scoped>

/* styling inspired by  */
    :root {
  --surface-color: #fff;
  --curve: 40;
}

[cont]{
    min-height: 20rem;
    max-width: 20rem;
    
    
}

.card{
  background-color: white;
}

.concat{
    width: 80%;
}

* {
  box-sizing: border-box;
}

body {
  font-family: 'Noto Sans JP', sans-serif;
  background-color: #fef8f800;
}

*{
    color: black !important;;
}

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin: 4rem 5vw;
  padding: 0;
  list-style-type: none;
}

.card {
  position: relative;
  display: block;
  height: 100%;  
  border-radius: calc(var(--curve) * 1px);
  overflow: hidden;
  text-decoration: none;
}

.card__image {      
  width: 100%;
  height: auto;
}

.card__overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;      
  border-radius: calc(var(--curve) * 1px);    
  background-color: var(--surface-color);      
  transform: translateY(100%);
  transition: .2s ease-in-out;
}

.card:hover .card__overlay {
  transform: translateY(0);
}

.card__header {
  position: relative;
  display: flex;
  align-items: center;
  gap: 2em;
  padding: 2em;
  border-radius: calc(var(--curve) * 1px) 0 0 0;    
  background-color: var(--surface-color);
  transform: translateY(-100%);
  transition: .2s ease-in-out;
}

.card__arc {
  width: 80px;
  height: 80px;
  position: absolute;
  bottom: 100%;
  right: 0;      
  z-index: 1;
}

.card__arc path {
  fill: var(--surface-color);
}       

.card:hover .card__header {
  transform: translateY(0);

}

.card__thumb {
  flex-shrink: 0;
  width: 50px;
  height: 50px;      
  border-radius: 50%;      
}

.card__title {
  font-size: 1em;
  margin: 0 0 .3em;
  color: #6A515E;
}

.card__tagline {
  display: block;
  margin: 1em 0;
  font-family: "MockFlowFont";  
  font-size: .8em; 
  color: #D7BDCA;  
}

.card__status {
  font-size: .8em;
  color: #D7BDCA;
}

.card__description {
  padding: 0 2em 2em;
  margin: 0;
  color: #90486c;   
  display: block;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  overflow: hidden;
  background-color: #886342;
}  

.buttonsThingy{
  background-color: #886342;

}

*{
    background: rgba(255, 255, 255, 0);
}

h1{
  color: aliceblue !important;
}

img{
  width: 10rem;
}

.btn{
 background-color: #6A515E;
}

@media only screen and (max-width: 935px) {
  .cards {
    display:  flex;
    flex-direction: column;
    align-items: center;



  gap: 2rem;
  margin: 0;
  padding: 0;
  list-style-type: none;
}

      [cont]{
      width: 20rem;
      height: 10rem;
    }
}



</style>