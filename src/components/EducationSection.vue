<template>
    <div class="container-fluid " about>

        <h1>Resume</h1>
        <div id="carouselExample" class="carousel slide" >
            <div class="carousel-inner">

                <div class="carousel-item active">
                    <div class="wrap">
                        <div class="row">
                            <div class="col-3 text-lg-start ">
                                <h2>My Education</h2>
                                <hr>
                                <div class="d-flex flex-row align-items-center">
                                        <ul>
                                            <li v-for="edu in education" :key="edu.id">
                                                {{edu.institution}}
                                            </li>
                                        </ul>
                                    </div>
                                </div>
                
                            <div class="col-9  d-flex flex-row justify-content-end">
                                <div class="cont d-flex flex-column justify-content-evenly">
                                    <div v-for="edu in education" :key="edu.id" :class="{first : edu.institution == 'Mondale High School', second : edu.institution != 'Mondale High School'}">
                                        <div class="card-body">
                                            <h3 class="card-title">{{edu.institution}}</h3>
                                            <p class="card-text">{{edu.Qualification}}</p>
                                            <div class="col d-flex flex-row justify-content-center">
                                                <hr >
                                            </div>
                                            <p class="card-text"><small class="text-muted">{{edu.paragraph}}</small></p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="carousel-item">
                    <div class="wrap">
                        <div class="row ">
                        <div class="col-3 text-lg-start ">
                        <h2>My Experience</h2>
                        <hr>
                            <div v-for="(exp, index) in experience" :key="exp.id">
                                <p>{{exp.company}} {{ index }}</p>
                            </div>
                        </div>
            
                        <div class="col-9  d-flex flex-row justify-content-end">
                            <div class="cont d-flex flex-column justify-content-evenly">
                                <div v-for="(exp, index) in experience" :key="index" class="second" >
                                    <div class="card-body" >
                                        <h3 class="card-title">{{exp.company}}</h3>
                                        <p class="card-text">{{exp.title}}</p>
                                        <div class="col d-flex flex-row justify-content-center">
                                            <hr >
                                        </div>
                                        <p class="card-text"><small class="text-muted">{{ exp.paragraph}}</small></p>
                                    </div>
                                </div>
                            </div>
                        </div>
                        </div>
                    </div>
                </div>

        </div>
            <button class="carousel-control-prev" type="button" data-bs-target="#carouselExample" data-bs-slide="prev">
                <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#carouselExample" data-bs-slide="next">
                <span class="carousel-control-next-icon" aria-hidden="true"></span>
                <span class="visually-hidden">Next</span>
            </button>
        </div>
    </div>
</template>

<script setup>
  
    import {computed, onMounted } from 'vue'
    import {useStore} from 'vuex'
  

    const education = computed(() => store.state.education, add)
    const store = useStore()
    const experience = computed(() => store.state.experience)

  
    onMounted(() => {store.dispatch('fetchEducation')})
    onMounted(() => {store.dispatch('fetchExperience')})
    const spans = document.querySelectorAll("[span]")


    function add(){
        spans.value.forEach((span, idx) => {
            span.addEventListener('click', (value) => {
                value.target.classList.add('active');
            });
            span.addEventListener('animationend', (value) => {
                value.target.classList.remove('active');
            });
    
            setTimeout(() => {
                span.classList.add('active');
            }, 750 * (idx+1))
        });
    }
    


  
</script>

<style scoped>
    @import url('https://fonts.googleapis.com/css?family=Anton|Roboto');
    @import url('https://fonts.googleapis.com/css2?family=Yeseva+One&display=swap');

    :is(h2, h3){
        font-family: "Yeseva One", serif;
        font-weight: 500;
        font-style: normal;
    }
    h2{
        color: white !important;;
    }
    .row{
        width: 70%;
    }
    .wrap{
        display: flex;
        justify-content: center;
        height: 80%;
    }
    .first{
        background-image: url('https://chelsea-julie.github.io/all-images/images/vue-eomp/library.jpg');
        background-position: center;
        background-size: cover;      
    } 
    .second{
        background-image: url('https://chelsea-julie.github.io/all-images/images/vue-eomp/edu1.jpg');
        background-position: center;
        background-size: cover;
    }
    :is(.first, .second){
        height: 40%;
        width: 100;
        
    }


    .card-body{
        opacity: 0.1;
    }

    
    :is(.first,.second):hover{
        background: rgba(255, 255, 255, 0.548);
        transition: 1s;
    }

    :is(.first,.second):hover .card-body{
        opacity: 1;

    }

    .cont{
        width: 70%;

    }

    #carouselExample{
        height: 85%;
    }

    .carousel-inner{
        height: 100% !important;
    }

    .carousel-item{
        height: 100%;
    }

    hr {
        width: 70%;
        border: 2px solid white;
        border-radius: 5px;
        color: white !important;
    }

    .card-text{
        padding: 0 !important;
        margin: 0 !important;
    }
    li{
        color: white !important;
    }
    /* animation  */


    .word {
        font-family: 'Anton', sans-serif;
    }

    .word span {
        cursor: pointer;
        display: inline-block;
        font-size: 100px;
        user-select: none;
        line-height: .8;
    }

    .word span:nth-child(1).active {
        animation: balance 1.5s ease-out;
        transform-origin: bottom left;
    }

    @keyframes balance {
        0%, 100% {
            transform: rotate(0deg);
        }
        
        30%, 60% {
            transform: rotate(-45deg);
        }
    }

    .word span:nth-child(2).active {
        animation: shrinkjump 1s ease-in-out;
        transform-origin: bottom center;
    }

    @keyframes shrinkjump {
        10%, 35% {
            transform: scale(2, .2) translate(0, 0);
        }
        
        45%, 50% {
            transform: scale(1) translate(0, -150px);
        }
        
        80% {
            transform: scale(1) translate(0, 0);
        }
    }

    .word span:nth-child(3).active {
        animation: falling 2s ease-out;
        transform-origin: bottom center;
    }

    @keyframes falling {
        12% {
            transform: rotateX(240deg);
        }
        
        24% {
            transform: rotateX(150deg);
        }
        
        36% {
            transform: rotateX(200deg);
        }
        
        48% {
            transform: rotateX(175deg);
        }
        
        60%, 85% {
            transform: rotateX(180deg);
        }
        
        100% {
            transform: rotateX(0deg);
        }
    }

    .word span:nth-child(4).active {
        animation: rotate 1s ease-out;
    }

    @keyframes rotate {
        20%, 80% {
            transform: rotateY(180deg);
        }
        
        100% {
            transform: rotateY(360deg);
        }
    }

    .word span:nth-child(5).active {
        animation: toplong 1.5s linear;
    }

    @keyframes toplong {
        10%, 40% {
            transform: translateY(-48vh) scaleY(1);
        }
        
        90% {
            transform: translateY(-48vh) scaleY(4);
        }
    }

    
</style>