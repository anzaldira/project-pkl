<template>
  <div class="dark:text-white">
      <div class="flex">
          <div class="mx-4 w-full xl:max-w-7xl xl:mx-auto">
              <h2 class="text-center text-2xl my-4 font-semibold">
                  
              </h2>
              <div class="bg-gray-100">
    <div class="w-full bg-cover bg-center" style="height:32rem; background-image: url(https://i.pinimg.com/1200x/4d/36/f7/4d36f77ecfbed117a25efbbdcf56cb09.jpg);">
        <div class="flex items-center justify-left h-full w-full bg-gray-900 bg-opacity-50">
            <div class="">
                <h1 class="text-white text-2xl font-extrabold uppercase md:text-3xl ml-10">WELLCOME TO<br>ZALLstore</h1>
                <p class="text-white text-base font-semibold uppercase md:text-base ml-10">selling all premium helmets</p>

                <!-- <a href="/product" class="ml-10 mt-3 relative inline-flex items-center px-12 py-2 overflow-hidden text-lg font-medium text-white border-2 border-white-600 rounded-full hover:text-black group hover:bg-gray-50">
                  <span class="absolute left-0 block w-full h-0 transition-all bg-white opacity-100 group-hover:h-full top-1/2 group-hover:top-0 duration-400 ease"></span>
                  <span class="absolute right-0 flex items-center justify-start w-10 h-10 duration-300 transform translate-x-full group-hover:translate-x-0 ease">
                  <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"></path></svg>
                  </span>
                  <span class="relative">Start Shopping</span>
                </a> -->
            </div>
        </div>
    </div>
    </div>
              <div class="text-center">
                  
              </div>
              <div v-if="products.length != undefined" class="flex flex-wrap justify-center">
                  <div class="m-3 w-[200px] group hover:shadow-md bg-white hover:bg-gray-100 dark:bg-gray-900 dark:hover:bg-gray-500 dark:hover:bg-opacity-[.5] transition-all border cursor-pointer rounded-t-lg rounded-b-lg"
                      v-for="data in products">
                      <RouterLink :to="'/product/' + data.slug">
                          <div class="flex flex-col h-full">
                              <div class="mb-3">
                                  <div class="overflow-hidden w-[200px] h-[200px] rounded-t-lg">
                                      <img class="transition-all group-hover:scale-125 group-hover:opacity-75"
                                          src="/img/placeholder.jpg" :alt="data.name">
                                  </div>
                                  
                                  <div class="px-2" v-if="data.name">
                                      <h3 class="font-semibold text-md" v-if="data.name.length >= 25">{{
                                          data.name.slice(0,
                                              25)
                                          + ' ...' }}</h3>
                                      <h3 class="font-semibold text-md" v-else>{{ data.name }}</h3>
                                  </div>
                              </div>
                              <div class="mt-auto p-2">
                                  <!-- <div>
                                      <p class="font-semibold text-md">
                                          <span class="text-yellow-400 opacity-80 group-hover:opacity-60 transition-all"
                                              v-html="rateToStar((data.rating).rate)">
                                          </span>
                                          <b
                                              class="mx-[12px] bg-blue-400 transition-all group-hover:text-blue-600 group-hover:bg-opacity-[35%] bg-opacity-[50%] px-1 rounded-md text-blue-800">
                                              {{ data.rating.rate }}
                                          </b>
                                      </p>
                                  </div> -->
                                  <div>
                                      <h2 class="font-bold font-mono">Rp.{{ data.base_price }}</h2>
                                  </div>
                                  <div class="text-sm text-gray-500">
                                      {{ data.category }}
                                  </div>
                              </div>
                          </div>
                      </RouterLink>
                  </div>
              </div>
              <!-- {{ products }} -->

              <h2 class="text-center text-xl font-bold my-12" v-if="products == undefined || products.length == 0">
                  Loading ...
              </h2>
          </div>
      </div>
  </div>
</template>

<script>
import { onMounted } from "vue";
import { mapState } from "vuex";

export default {
  mounted() {
      this.$store.dispatch("product/fetchProduct")
  },
  computed: {
      // getProducts(){
      //     return this.$store.getters.product.getProduct
      // },
      // products() {
      //     return this.$store.state.product.products
      // },
      ...mapState('product', ['products'])
  },
  setup(props, context) {
      onMounted(() => {
          try {
              context.emit("id-menu", 2)
          } catch (error) {
              console.log(error)
          }
      })
  }
}
</script>
