<script setup>

import { ref } from 'vue'
const images = [
    {
        thumb: "images/slide2.jpg"
    },
    {
        thumb: "images/slide3.jpg"
    },
    {
        thumb: "images/slide4.jpg"
    },
    {
        thumb: "images/slide5.jpg"
    },
    {
        thumb: "images/slide6.jpg"
    },
    {
        thumb: "images/slide7.jpg"
    },
    {
        thumb: "images/slide8.jpg"
    },
]

const fullImage = ref('images/slide2.jpg')
const acitveClass = ref(0)

const setfullImage = (image, index) => {
    fullImage.value = image.thumb
    acitveClass.value = index
}

const nextBtn = () => {
    if (images.length - 1 <= acitveClass.value)
        acitveClass.value = 0
    else
        acitveClass.value++
    fullImage.value = images[acitveClass.value].thumb
}

const preBtn = () => {
    if (0 >= acitveClass.value)
        acitveClass.value = images.length - 1
    else
        acitveClass.value--
    fullImage.value = images[acitveClass.value].thumb
}

</script>

<template>
    <section class="container mx-auto pt-0 pl-20 pr-20">
        <section id="default-carousel" class="container mx-auto flex items-center flex-col">
            <h1 class="text-center text-4xl py-10 font-bold">Vue 3 Image Slider</h1>
            <div class=" relative">

                <img class="cursor-pointer w-full rounded-lg" :src="fullImage" alt="">

                <!-- Slider pre next -->
                <button type="button"
                    class="absolute top-0 left-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none"
                    @click="preBtn()" data-carousel-prev>
                    <span
                        class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/30 dark:bg-gray-800/30 group-hover:bg-white/50 dark:group-hover:bg-gray-800/60 group-focus:ring-4 group-focus:ring-white dark:group-focus:ring-gray-800/70 group-focus:outline-none">
                        <svg class="w-4 h-4 text-white dark:text-gray-800" aria-hidden="true"
                            xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
                            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M5 1 1 5l4 4" />
                        </svg>
                        <span class="sr-only">Previous</span>
                    </span>
                </button>
                <button type="button"
                    class="absolute top-0 right-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none"
                    @click="nextBtn()" data-carousel-next>
                    <span
                        class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/30 dark:bg-gray-800/30 group-hover:bg-white/50 dark:group-hover:bg-gray-800/60 group-focus:ring-4 group-focus:ring-white dark:group-focus:ring-gray-800/70 group-focus:outline-none">
                        <svg class="w-4 h-4 text-white dark:text-gray-800" aria-hidden="true"
                            xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
                            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="m1 9 4-4-4-4" />
                        </svg>
                        <span class="sr-only">Next</span>
                    </span>
                </button>

                <div class="absolute z-30 flex space-x-3 -translate-x-1/2 bottom-2 left-1/2">
                    <ol class="navigaet-bullate">
                        <li @click="setfullImage(image, index)" class="cursor-pointer"
                            :class="index === acitveClass ? 'active' : ''" v-for="(image, index) in images"
                            :key="image.thumb" :src="image.thumb"></li>
                    </ol>
                </div>
            </div>
        </section>
    </section>

    <section>

    </section>
</template>

<style scoped>
.navigaet-bullate li {
    padding: 6px;
    float: left;
    background-color: darkgray;
    margin: 5px;
    border-radius: 50%;
}

li.active {
    background-color: aliceblue;
}

@media only screen and (max-width: 526px) {
    .navigaet-bullate li {
        padding: 4px;
        margin: 3px;
        border-radius: 50%;
    }

    button span {
        height: 16px;
        width: 16px;
    }

    button span svg {
        height: 10px;
        width: 10px;
        font-size: 8px;
    }
}
</style>
