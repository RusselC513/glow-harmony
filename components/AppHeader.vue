<script setup>
    import { ref } from 'vue';

    const isMenuOpen = ref(false);

    const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
    };
</script>
<template>
    <header>
        <nav class="bg-white fixed w-full z-20 top-0 start-0 border-b ">
        <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
            <a href="https://flowbite.com/" class="flex items-center space-x-3 rtl:space-x-reverse">
            <NuxtImg 
                src="/logo-cleaning.jpg"
                width="60"
            />
            </a>
            <div class="flex md:order-2 space-x-3 md:space-x-0 rtl:space-x-reverse">
            <button type="button" class="btn-call text-white focus:ring-4 focus:outline-none font-medium rounded-lg text-sm px-4 py-2 text-center">985418423</button>
            <button type="button" class="btn-call text-white focus:ring-4 focus:outline-none font-medium rounded-lg text-sm px-4 py-2 text-center ml-3">GET A QUOTE</button>

            <button @click="toggleMenu" type="button" class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600" aria-controls="navbar-sticky" aria-expanded="false">
                <span class="sr-only">Open main menu</span>
                <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 14">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 1h15M1 7h15M1 13h15"/>
                </svg>
            </button>
            </div>
            <div :class="{'hidden': !isMenuOpen}" class="items-center justify-between w-full md:flex md:w-auto md:order-1" id="navbar-sticky">
            <ul class="flex flex-col p-4 md:p-0 mt-4 md:space-x-8 rtl:space-x-reverse md:flex-row md:mt-0 md:border-0 md:bg-white">
                <li>
                <a href="#" class="" aria-current="page">Home</a>
                </li>
                <li>
                <a href="#" class="">About</a>
                </li>
                <li>
                <a href="#" class="">Services</a>
                </li>
                <li>
                <a href="#" class="">Contact</a>
                </li>
            </ul>
            </div>
        </div>
        </nav>
    </header>
  </template>
  

<style lang="scss">
header{
    ul{
        li{
            font-size :1.3em;
            color: $color-fuente;
            text-transform:uppercase;
        }
    }
    .btn-call{
        background-color: $primary-color;
        cursor: pointer;
    }

}


</style>