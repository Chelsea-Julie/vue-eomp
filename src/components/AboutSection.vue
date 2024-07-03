<template>
    <div class="container vh-100" about>
        <h1>About me</h1>
        <div class="row align-items-center">
            <div class="col-sm-12 col-md-12 col-lg-6">
                <img class="img-fluid" src="https://chelsea-julie.github.io/all-images/images/Humans/CJ-4.jpg" alt="about" loading="lazy">
            </div>

            <div class="col-sm-12 col-md-12 col-lg-5" v-if="about">
                <p>{{ about[0] }}</p>
                <p>{{ about[1] }}</p>
            </div>

            <div v-else class="row">
                <Spinner />
            </div>
        </div>


    </div>
</template>

<script setup>
  
  import {computed, onMounted } from 'vue'
  import {useStore} from 'vuex'
  import Spinner from '@/components/Spinner.vue'

    const about = computed(() => store.state.about)
    const store = useStore()

  
    onMounted(() => {
        store.dispatch('fetchAbout')
      })
  
</script>

<style scoped>

    [about]{
        background-image: url("https://chelsea-julie.github.io/all-images/images/Brown Grey Creative Modern Online Portfolio/4.png");
        background-size: cover;
        background-repeat: no-repeat;
        
    }

    .row{
        margin-top: 5rem;
    }
    img{
        border-radius: 0 !important;
    }
    
    h1{
        color: aliceblue;
       
    }
    p{
        color: aliceblue;
    }

    .container {
            align-items: center;
            justify-content: center;
            height: 100vh; /* Adjust height as needed */
            text-align: center; /* Center align text */
        }
    img{
        max-width: 27rem;
        height: auto;
    }
</style>