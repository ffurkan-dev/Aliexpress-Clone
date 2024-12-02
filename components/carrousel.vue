<template>
    <div class="relative w-full max-w-5xl mx-auto p-4 bg-white rounded-lg shadow-lg overflow-hidden">
      <!-- Başlık -->
      <div class="py-4 px-6 bg-yellow-200 rounded-lg">
        <h2 class="text-lg font-bold">Dollar Express</h2>
        <p class="text-sm">3 from $0.99</p>
      </div>
  
      <!-- Carousel Container -->
      <div class="relative mt-2 overflow-hidden">
        <!-- Sol Ok -->
        <button
          class="absolute left-2 top-1/2 transform -translate-y-1/2 z-10 p-2 bg-yellow-300 rounded-full shadow-md hover:bg-yellow-400"
          @click="prevSlide"
        >
          &lt;
        </button>
  
        <!-- Ürünler -->
        <div
          class="flex transition-transform duration-300"
          :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
        >
          <!-- Her bir ürün kartı -->
          <div
            v-for="(item, index) in items"
            :key="index"
            class="w-1/4 flex-shrink-0 px-2 box-border"
          >
            <div
              class="bg-gray-100 p-4 rounded-lg shadow-md flex flex-col items-center h-full"
            >
              <img
                :src="item.image"
                alt="Product"
                class="w-24 h-24 object-cover rounded-md mb-2"
              />
              <h3 class="text-sm font-semibold text-center mb-2">
                {{ item.name }}
              </h3>
              <!-- Eski ve İndirimli Fiyat -->
              <div class="flex items-center space-x-2 mb-2">
                <p class="text-gray-500 text-xs line-through">{{ item.oldPrice }}</p>
                <p class="text-red-500 text-sm font-bold">{{ item.discountedPrice }}</p>
              </div>
              <p class="text-yellow-500 text-xs">{{ item.rating }} ★</p>
            </div>
          </div>
        </div>
  
        <!-- Sağ Ok -->
        <button
          class="absolute right-2 top-1/2 transform -translate-y-1/2 z-10 p-2 bg-yellow-300 rounded-full shadow-md hover:bg-yellow-400"
          @click="nextSlide"
        >
          &gt;
        </button>
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref } from "vue";
  
  export default defineComponent({
    name: "Carousel",
    setup() {
      // Ürün listesi
      const items = ref([
        {
          name: "2/3 in1 Case For Airpods Max",
          oldPrice: "$13.29",
          discountedPrice: "$1.33",
          rating: 4.4,
          image: "https://via.placeholder.com/100",
        },
        {
          name: "French Bread Plush Pillow",
          oldPrice: "$32.92",
          discountedPrice: "$7.99",
          rating: 4.5,
          image: "https://via.placeholder.com/100",
        },
        {
          name: "Luxury Magnetic MagSafe Case",
          oldPrice: "$6.54",
          discountedPrice: "$0.33",
          rating: 4.4,
          image: "https://via.placeholder.com/100",
        },
        {
          name: "Transparent Resin Strap",
          oldPrice: "$5.09",
          discountedPrice: "$0.33",
          rating: 4.7,
          image: "https://via.placeholder.com/100",
        },
        {
          name: "Wireless Bluetooth Headphones",
          oldPrice: "$15.99",
          discountedPrice: "$5.50",
          rating: 4.6,
          image: "https://via.placeholder.com/100",
        },
        {
          name: "Mini USB Desk Fan",
          oldPrice: "$5.50",
          discountedPrice: "$2.99",
          rating: 4.3,
          image: "https://via.placeholder.com/100",
        },
        {
          name: "Portable LED Lamp",
          oldPrice: "$10.99",
          discountedPrice: "$3.99",
          rating: 4.5,
          image: "https://via.placeholder.com/100",
        },
        {
          name: "Travel Organizer Bag",
          oldPrice: "$14.50",
          discountedPrice: "$6.50",
          rating: 4.8,
          image: "https://via.placeholder.com/100",
        },
      ]);
  
      // Carousel için index kontrolü
      const currentIndex = ref(0);
  
      // Ürünlerin bir defada kaç tane görüneceği
      const itemsPerPage = 4;
  
      // Toplam sayfa sayısını hesapla
      const totalPages = Math.ceil(items.value.length / itemsPerPage);
  
      const nextSlide = () => {
        currentIndex.value = (currentIndex.value + 1) % totalPages;
      };
  
      const prevSlide = () => {
        currentIndex.value = (currentIndex.value - 1 + totalPages) % totalPages;
      };
  
      return {
        items,
        currentIndex,
        nextSlide,
        prevSlide,
      };
    },
  });
  </script>
  