<template>
    <div class="product-display container mx-auto">
        <div class="flex justify-between items-center">
            <div class="my-10 bg-white w-10/12 p-3 rounded-xl">
                <p class="font-bold text-2xl">{{products[curID].title}}</p>
                <p class="text-article text-xs mt-2">Артикул: {{products[curID].article}}</p>
                <div class="flex justify-between items-center mt-4">
                    <div class="w-1/2">
                      <img class="w-full" :src="products[curID].images[0].first" alt="">
                    </div>
                    <div class="w-3/4 pr-2">

                      <div class="flex justify-between items-center">
                        
                          <div class="flex justify-start items-center">
                            <p class="bg-yellow-400 font-bold text-xs py-1 px-3 rounded-md mr-2">{{ products[curID].rating }}</p>
                            <div class="mr-2">
                              <i class="fas fa-star text-ash"></i>
                              <i class="fas fa-star text-ash"></i>
                              <i class="fas fa-star text-ash"></i>
                              <i class="fas fa-star text-ash"></i>
                              <i class="fas fa-star text-ash"></i>
                            </div>
                            <a class="text-link text-xs" href="#">{{ products[curID].reviews }} отзывов</a>
                          </div>

                          <div>
                            <i class="fas fa-check mr-2 text-greeny"></i>
                            <a class="text-link text-xs" href="#">Гарантия низкой цены</a>
                          </div>                        

                      </div>   

                      <div class="block mt-8">
                        <p class="text-2xl font-semibold mb-3">Описание</p> <!-- <mark class="bg-ash">Описание</mark>-->

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Модельный год</p>
                            <p>{{ products[curID].year }}</p>
                          </div>  

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Диагональ дисплея, дюйм</p>
                            <p>{{ products[curID].diagonal }}</p>
                          </div> 

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Разрешение дисплея</p>
                            <p>{{ products[curID].resolution }}</p>
                          </div> 

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Тип матрицы</p>
                            <p>{{ products[curID].matrix }}</p>
                          </div>  

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Частота обновления</p>
                            <p>{{ products[curID].hz }}</p>
                          </div>  

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Объем оперативной памяти, ГБ</p>
                            <p>{{ products[curID].ram }}</p>
                          </div>  

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Объем встроенной памяти, ГБ</p>
                            <p>{{ products[curID].hard }}</p>
                          </div>  

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Модель процессора</p>
                            <p>{{ products[curID].processor }}</p>
                          </div>  

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Операционная система</p>
                            <p>{{ products[curID].OS }}</p>
                          </div>  

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Интерфейсы</p>
                            <p>{{ products[curID].interface }}</p>
                          </div>

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Беспроводная зарядка</p>
                            <p>{{ products[curID].wirelessCharge }}</p>
                          </div>

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Стандарт защиты от пыли и влаги</p>
                            <p>{{ products[curID].dustDefense }}</p>
                          </div>

                          <div class="flex justify-between items-center border-b border-dashed mb-2">
                            <p>Вес, гр</p>
                            <p>{{ products[curID].weight }}</p>
                          </div>                          

                      </div> 

                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      products: [],
      curID: this.$route.params.id - 1,
      baseURL: 'http://localhost:3001/products/'
    };
  },
  async created() {
    try {
      const res = await axios.get(this.baseURL);
      this.products = res.data;
    } catch (e) {
      console.error(e);
    }
  },
};
</script>