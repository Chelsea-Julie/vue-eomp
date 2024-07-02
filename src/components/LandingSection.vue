<template>
    <div class="container-fluid">
      <div class="row vh-100 align-items-center">
          <div class="col">
              <div id="details" >
                    <h1>Hello</h1>
                  <h2 class="display-1"> I'm Chelsea Julie</h2>
                  <p v-if="title">
                      I am
                  <span>{{ title }}</span>
                  </p>

                  <Spinner v-else />
              </div>
          </div>
          <div class="col">
                  <img src="https://chelsea-julie.github.io/all-images/images/Humans/CJ-1.jpg" alt="logo" me loading="lazy">
          </div>
      </div>
    </div>
</template>

  <script setup>
  
  import {computed, onMounted, ref } from 'vue'
  import {useStore} from 'vuex'
  import Spinner from '@/components/Spinner.vue'

    const jobtitle = computed(() => store.state.jobtitle)
    const store = useStore()
    const title = ref('a software developer')
    const cnt = ref(-1)
  
    function repeat() {
          try {
              if (cnt.value == jobtitle.value?.length) cnt.value = 0;
              title.value = 
                  jobtitle.value?.at(cnt.value)?.title;
                  setTimeout(repeat, 2000)
                  cnt.value++
          } catch (e) {
              // 
          }
    }
    onMounted(() => {
          store.dispatch('fetchJobtitle')
          repeat()
      })


  </script>

<style scoped>


</style>