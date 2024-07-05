<template >
    <div id="mainCoantiner">
        <h1>Testimonials</h1>
        <div class="margin-body">
            <div class="row flex-sm-column flex-md-column flex-lg-row " v-if="testimonials">
                <div class="col-sm-3 col-md-3 pricing-column-wrapper" v-for="(testimonial, index) in testimonials" :key="index" >
                <div class="pricing-column" cont v-if="testimonial.name != 'Valhatiem Raynard'" maincont>
                        <div class="pricing-price-row">
                            <div class="pricing-price-wrapper">
                              <img class="img-fluid" :src="testimonials[index].img_url" :alt="testimonials[index].name"  >
                            </div>
                        </div>
                        <div class="pricing-row-title">
                            <div class="pricing_row_title">{{testimonial.name}}</div>
                        </div>
                        <div para>
                          <p>{{testimonial.paragraph}}</p>
                        </div>

                        <div class="pricing-footer">
                              <div class="gem-button-container gem-button-position-center d-flex flex-row"><P></P></div>
                        </div>    
                        </div>
                </div>
            </div>
        </div>
    </div>
</template>


<script setup>
    import {computed, onMounted } from 'vue'
    import {useStore} from 'vuex'
  

    const testimonials = computed(() => store.state.testimonial)
    const store = useStore()

    onMounted(() => {store.dispatch('fetchTestimonials')})


</script>


<style scoped>
    #mainCoantiner {
  height: 100%;
  width: 100%;
  padding-bottom: 3.125rem; /* Changed from 50px to equivalent rem */
  
}
.main-header {
  top: 0;
  left: 0;
  z-index: 20;
  -webkit-transform: translate3d(0, 0, 0);
  height: 4.375rem; /* Changed from 70px to equivalent rem */
  width: 100%;
  bottom: inherit;
  text-align: center;
  overflow: hidden;
  border: 1px solid #2e344d;
  -webkit-transition: all 0.3s ease-in-out 0s;
  -moz-transition: all 0.3s ease-in-out 0s;
  -ms-transition: all 0.3s ease-in-out 0s;
  -o-transition: all 0.3s ease-in-out 0s;
  transition: all 0.3s ease-in-out 0s;
  box-shadow: 0.625rem 0.625rem 2.25rem rgba(0, 0, 0, 0.5), -0.8125rem -0.8125rem 1.4375rem rgba(255, 255, 255, 0.03);
  border-width: 1px 0px 0 1px;
}

.folio-btn {
  position: absolute;
  bottom: 0;
  background: rgba(255, 255, 255, 0.03);
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  right: 0;
  height: 4.375rem; /* Changed from 70px to equivalent rem */
  width: 4.375rem; /* Changed from 70px to equivalent rem */
}

.folio-btn-item {
  position: absolute;
  width: 2.5rem; /* Changed from 40px to equivalent rem */
  height: 2.5rem; /* Changed from 40px to equivalent rem */
  left: 0.9375rem; /* Changed from 15px to equivalent rem */
  top: 0.9375rem; /* Changed from 15px to equivalent rem */
}

.folio-btn-dot {
  float: left;
  width: 33.3%;
  height: 33.3%;
  position: relative;
}

.folio-btn-dot:before {
  content: '';
  position: absolute;
  left: 50%;
  top: 50%;
  width: 0.25rem; /* Changed from 4px to equivalent rem */
  height: 0.25rem; /* Changed from 4px to equivalent rem */
  margin: -0.125rem 0 0 -0.125rem;
  border-radius: 50%;
  transition: all 300ms linear;
  transform: scale(1.0);
}

[para]{
  height: 12rem;
}



.folio-btn:hover .folio-btn-dot:first-child:before,
.folio-btn:hover .folio-btn-dot:nth-child(3):before,
.folio-btn:hover .folio-btn-dot:nth-child(4):before,
.folio-btn:hover .folio-btn-dot:nth-child(8):before {
  transform: scale(1.8);
  opacity: 0.5;
}

ul,
li {
  border: none;
  outline: 0;
  font-weight: inherit;
  font-style: inherit;
  font-size: 100%;
  font-family: inherit;
  vertical-align: baseline;
  text-decoration: none;
  margin: 0;
  padding: 0;
}

ol,
ul {
  list-style: none;
}

.title-h1 {
  margin-top: 0.3125em; /* Changed from 0.5em to equivalent rem */
  margin-bottom: 0.875em; /* Changed from 1.4em to equivalent rem */
  letter-spacing: 0.05em;
  text-transform: uppercase;
  line-height: inherit;
  color: #ffffff;
  font-size: 2.375rem; /* Changed from 38px to equivalent rem */
}

.title-h1 .light {
  font-weight: normal;
}

.pricing-price-wrapper {
  background-color: rgba(71, 71, 72, 0.2);
  border-top-right-radius: 50%;
  border-top-left-radius: 50%;
  padding-top: 2.8125rem; /* Changed from 45px to equivalent rem */
  padding-bottom: 2.125rem; /* Changed from 34px to equivalent rem */
  text-align: center;
  box-shadow: 1.25rem 1.25rem 3.75rem rgba(0, 0, 0, 0.13), -1.25rem -1.25rem 3.75rem rgba(29, 29, 29, 0.08);
}



.pricing-cost {
  font-size: 3.125rem; /* Changed from 50px to equivalent rem */
  font-weight: 300;
  line-height: 1;
}

.time {
  font-size: 1.5rem; /* Changed from 24px to equivalent rem */
  font-weight: 300;
}

.pricing-row-title {
  background-color: #303241;
  padding: 1.625rem 0.625rem; /* Changed from 26px and 10px to equivalent rem */
  text-align: center;
}

.pricing_row_title {
  color: #ff994e;
  line-height: 2.375rem; /* Changed from 38px to equivalent rem */
  font-size: 1.5rem; /* Changed from 24px to equivalent rem */
  font-weight: 700;
  text-transform: uppercase;
}





figure {
  margin: 0;
  display: block;
}

.pricing-row:before {
  vertical-align: middle;
  content: "\f058";
  font-family: "Font Awesome 5 Free";
  text-align: center;
  padding-right: 0.625rem; /* Changed from 10px to equivalent rem */
}

.strike:before {
  content: none;
}



.pricing-column {
  float: none;
  display: inline-block;
  text-align: left;
  vertical-align: top;
  margin-bottom: 2.625rem; /* Changed from 42px to equivalent rem */
  -webkit-transition: all 0.3s ease-in-out 0s;
  -moz-transition: all 0.3s ease-in-out 0s;
  -ms-transition: all 0.3s ease-in-out 0s;
  -o-transition: all 0.3s ease-in-out 0s;
  transition: all 0.3s ease-in-out 0s;
}

.pricing-column-wrapper {
  min-width: 4.21875rem; /* Changed from 271px to equivalent rem */
  text-align: center;
}

.pricing-row-title {
  background-color: rgba(48, 50, 65, 0.2);
}

.margin-body {
  position: relative;
  width: 90%;
  box-sizing: border-box;
  margin: auto;
}

.pricing-row {
  border-top: 1px solid #7273723b;
}

.pricing-price-wrapper {
  border-top-right-radius: 50%;
  border-top-left-radius: 50%;
  padding-top: 2.8125rem; /* Changed from 45px to equivalent rem */
}

.pricing-column-wrapper + .pricing-column-wrapper .pricing-price {
  background-color: #ff994e;
  -webkit-box-shadow: 0px 0px 0px 1.5625rem rgba(255, 153, 78, 0.31);
  -moz-box-shadow: 0px 0px 0px 1.5625rem rgba(255, 153, 78, 0.31);
  box-shadow: 0px 0px 0px 1.5625rem rgba(255, 153, 78, 0.31);
}

.pricing-column-wrapper + .pricing-column-wrapper .pricing_row_title {
  color: #ff994e;
}

.pricing-column-wrapper + .pricing-column-wrapper + .pricing-column-wrapper .pricing_row_title {
  color: #ff994e;
}

.pricing-column-wrapper +  .pricing-price {
    background-color: #ff994e;
  -webkit-box-shadow: 0px 0px 0px 1.5625rem rgba(255, 153, 78, 0.31);
  -moz-box-shadow: 0px 0px 0px 1.5625rem rgba(255, 153, 78, 0.31);
  box-shadow: 0px 0px 0px 1.5625rem rgba(255, 153, 78, 0.31);
}

.pricing-column-wrapper + .pricing-column-wrapper + .pricing-column-wrapper + .pricing-column-wrapper .pricing_row_title {
  color: #ff994e;
}



[cont]{
  
  width: 90%
}

.pricing-column-wrapper .pricing-row:before {
    color: #ff994e;

}


.gem-button {
  cursor: pointer;
  border-width: 0.125rem; /* Changed from 2px to equivalent rem */
  line-height: 2.25rem; /* Changed from 36px to equivalent rem */
  border-style: solid;
  background: transparent;
  height: 2.5rem; /* Changed from 40px to equivalent rem */
  line-height: 2.5rem; /* Changed from 40px to equivalent rem */
  padding: 0 1.0625rem; /* Changed from 17px to equivalent rem */
  font-size: 0.875rem; /* Changed from 14px to equivalent rem */
  margin: 1.5625rem; /* Changed from 25px to equivalent rem */
  position: relative;
  display: inline-block;
  text-align: center;
  text-transform: uppercase;
  white-space: nowrap;
  vertical-align: middle;
  border-radius: 0px;
  border-color: #ff994e;
  color: #ff994e !important;
}





.gem-button:hover {
    background-color: #ff994e;
    color: rgb(255, 255, 255) !important;
}

.gem-button-position-center {
  text-align: center;
  display: block;
  background-color: rgba(0, 0, 0, 0.16862745098039217);
  border-radius: 0px 0px 0.625rem 0.625rem; /* Changed from 10px to equivalent rem */
}

.pricing-column:hover .pricing-price-wrapper {
  box-shadow: 0px 2.1875rem 5rem rgba(241, 139, 2, 0.34), 0px 0px 0px rgba(21, 21, 20, 0.79);
  -webkit-transition: all 0.3s ease-in-out 0s;
  -moz-transition: all 0.3s ease-in-out 0s;
  -ms-transition: all 0.3s ease-in-out 0s;
  -o-transition: all 0.3s ease-in-out 0s;
  transition: all 0.3s ease-in-out 0s;
}

.pricing-column:hover {
  overflow: hidden;
}

p{
  color: white !important;
}





</style>