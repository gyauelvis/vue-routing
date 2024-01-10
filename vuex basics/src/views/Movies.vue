<template>
    <div class="wrapper max-w-screen-xl flex flex-wrap items-center justify-between mx-auto px-4">
        <div class="wrapper-container flex items-center  gap-2 flex-wrap pt-5 md:justify-center">

        </div>
    </div>
</template>
<script setup>

let renderFxn = (data) => {
    let wrapper = document.querySelector('.wrapper-container');
    data.forEach(movie => {
        let element = document.createElement('div');
        let renderElement = `
    <div class="max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 h-[35rem]">
    <a href="#">
        <img class="rounded-t-lg h-[18rem] w-full object-cover" src='${movie.Images[0]}' alt="" />
    </a>
    <div class="p-5">
        <a href="#">
            <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">${movie.Title}</h5>
        </a>
        <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">${movie.Plot}</p>
        <a href="#" class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
            Read more
             <svg class="rtl:rotate-180 w-3.5 h-3.5 ms-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
            </svg>
        </a>
    </div>
    </div>`
        element.innerHTML = renderElement;
        wrapper.appendChild(element);
    })
}

import { onMounted } from 'vue';
onMounted(async () => {
    let url = 'https://gist.githubusercontent.com/saniyusuf/406b843afdfb9c6a86e25753fe2761f4/raw/523c324c7fcc36efab8224f9ebb7556c09b69a14/Film.JSON';
    let response = await fetch(url);
    let data = await response.json();
    renderFxn(data);
})
</script>