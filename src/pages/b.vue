<template>
  <div class="relative bg-gray-100">
    <nav class="p-4 max-w-8xl mx-auto">
      <div class="hidden lg:flex lg:justify-between lg:items-center">
        <a href="#" class="flex items-start gap-2 group">
          <div class="bg-blue-600 text-white p-2 rounded-md group-hover:bg-blue-800">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
          </div>
          <p class="text-sm font-light uppercase">
            Dashboard
            <span class="text-base block font-bold tracking-widest">
              Atom
            </span>
          </p>
        </a>
        <ul class="flex items-center space-x-4 text-sm font-semibold">
          <li><a href="#" class="px-2 xl:px-4 py-2 text-gray-800 rounded-md hover:bg-gray-200">My Account</a></li>
          <li class="relative" x-data="{ open: false }">
            <a x-on:click="open = !open" x-on:click.outside="open = false" href="#"
              class="px-2 xl:px-4 py-2 text-gray-600 rounded-md hover:bg-gray-200 flex gap-2 items-center">
              Transactions
              <svg xmlns="http://www.w3.org/2000/svg"
                class="w-4 h-4 stroke-current stroke-2 text-gray-800 transform duration-500 ease-in-out"
                :class="open ? 'rotate-90' : ''" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
              </svg> </a>
            <ul x-cloak x-show="open" x-transition
              class="absolute top-10 left-0 bg-white p-4 rounded-md shadow overflow-hidden w-64">
              <li>
                <a href="#" class="p-4 block text-sm text-gray-600 rounded flex items-center gap-2 hover:bg-gray-100">
                  <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                  </svg>
                  Transaction ABC
                </a>
              </li>
              <li>
                <a href="#" class="p-4 block text-sm text-gray-600 rounded flex items-center gap-2 hover:bg-gray-100">
                  <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                  </svg>
                  Transaction DEF
                </a>
              </li>
              <li>
                <a href="#" class="p-4 block text-sm text-gray-600 rounded flex items-center gap-2 hover:bg-gray-100">
                  <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                  </svg>
                  Transaction GHI
                </a>
              </li>
            </ul>
          </li>
          <li><a href="#" class="px-2 xl:px-4 py-2 text-gray-600 rounded-md hover:bg-gray-200">Cards </a></li>
          <li><a href="#" class="px-2 xl:px-4 py-2 text-gray-600 rounded-md hover:bg-gray-200">Offers</a></li>
        </ul>
        <ul class="flex space-x-2 xl:space-x-4 text-sm font-semibold">
          <li>
            <a href="#">
              <div class="p-2 rounded hover:bg-gray-200">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4 stroke-current text-gray-800" fill="none"
                  viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z" />
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
                </svg>
              </div>
            </a>
          </li>
          <li>
            <a href="#">
              <div class="p-2 rounded hover:bg-gray-200">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4 stroke-current text-gray-800" fill="none"
                  viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                </svg>
              </div>
            </a>
          </li>
          <li>
            <a href="#">
              <div class="p-2 rounded hover:bg-gray-200">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4 stroke-current text-gray-800" fill="none"
                  viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
                </svg>
              </div>
            </a>
          </li>
        </ul>
        <ul class="flex items-center gap-6">
          <li>
            <a href="#" class="text-sm font-sans text-gray-800 font-semibold tracking-wider">
              Derol Hakim
            </a>
          </li>
          <li>
            <a href="#">
              <div class="p-2 rounded hover:bg-gray-200">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 stroke-current text-gray-800" fill="none"
                  viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1" />
                </svg>
              </div>
            </a>
          </li>
        </ul>
      </div>
      <div x-data="{ open: false }" class="lg:hidden relative flex justify-between w-full">
        <a href="#" class="flex items-start gap-2 group">
          <div class="bg-blue-600 text-white p-3 rounded-md group-hover:bg-blue-800">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
            </svg>
          </div>
          <p class="text-sm font-light uppercase">
            Dashboard
            <span class="text-base block font-bold tracking-widest">
              Atom
            </span>
          </p>
        </a>
        <button x-on:click="open = !open" type="button" class="bg-gray-200 p-3 rounded-md">
          <svg x-show="!open" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
            stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h7" />
          </svg>
          <svg x-show="open" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
            stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
        <div x-show="open" x-transition class="absolute top-14 left-0 right-0 w-full bg-white rounded-md border">
          <ul class="p-4">
            <li class="px-4 py-2 rounded hover:bg-gray-200">
              <a href="#" class="flex items-center gap-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-3 h-3" fill="none" viewBox="0 0 24 24"
                  stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
                My Account
              </a>
            </li>
            <li class="px-4 py-2 rounded hover:bg-gray-200">
              <a href="#" class="flex items-center gap-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-3 h-3" fill="none" viewBox="0 0 24 24"
                  stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
                Transactions
              </a>
            </li>
            <li class="px-4 py-2 rounded hover:bg-gray-200">
              <a href="#" class="flex items-center gap-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-3 h-3" fill="none" viewBox="0 0 24 24"
                  stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
                Cards
              </a>
            </li>
            <li class="px-4 py-2 rounded hover:bg-gray-200">
              <a href="#" class="flex items-center gap-4">
                <svg xmlns="http://www.w3.org/2000/svg" class="w-3 h-3" fill="none" viewBox="0 0 24 24"
                  stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
                Offers
              </a>
            </li>
          </ul>

        </div>
      </div>
    </nav>
    <!-- End Nav -->
    <!-- Start Main -->
    <main class="container mx-w-6xl mx-auto py-4">
      <div class="flex flex-col space-y-8">
        <!-- First Row -->
        <div class="grid grid-cols-1 md:grid-cols-4 xl:grid-cols-5 px-4 xl:p-0 gap-y-4 md:gap-6">
          <div class="md:col-span-2 xl:col-span-3 bg-white p-6 rounded-2xl border border-gray-50">
            <div class="flex flex-col space-y-6 md:h-full md:justify-between">
              <div class="flex justify-between">
                <span class="text-xs text-gray-500 font-semibold uppercase tracking-wider">
                  Main Account
                </span>
                <span class="text-xs text-gray-500 font-semibold uppercase tracking-wider">
                  Available Funds
                </span>
              </div>
              <div class="flex gap-2 md:gap-4 justify-between items-center">
                <div class="flex flex-col space-y-4">
                  <h2 class="text-gray-800 font-bold tracking-widest leading-tight">Derol's Savings
                    Account</h2>
                  <div class="flex items-center gap-4">
                    <p class="text-lg text-gray-600 tracking-wider">**** **** *321</p>
                    <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24"
                      stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                        d="M17 8l4 4m0 0l-4 4m4-4H3" />
                    </svg>
                  </div>
                </div>
                <h2 class="text-lg md:text-xl xl:text-3xl text-gray-700 font-black tracking-wider">
                  <span class="md:text-xl">$</span>
                  92,817.45
                </h2>
              </div>
              <div class="flex gap-2 md:gap-4">
                <a href="#"
                  class="bg-blue-600 px-5 py-3 w-full text-center md:w-auto rounded-lg text-white text-xs tracking-wider font-semibold hover:bg-blue-800">
                  Transfer Money
                </a>
                <a href="#"
                  class="bg-blue-50 px-5 py-3 w-full text-center md:w-auto rounded-lg text-blue-600 text-xs tracking-wider font-semibold hover:bg-blue-600 hover:text-white">
                  Link Account
                </a>
              </div>
            </div>
          </div>
          <div
            class="col-span-2 p-6 rounded-2xl bg-gradient-to-r from-blue-500 to-blue-800 flex flex-col justify-between">
            <div class="flex flex-col">
              <p class="text-white font-bold">Lorem ipsum dolor sit amet</p>
              <p class="mt-1 text-xs md:text-sm text-gray-50 font-light leading-tight max-w-sm">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Odio soluta saepe consequuntur
                facilis ab a. Molestiae ad saepe assumenda praesentium rem dolore? Exercitationem, neque
                obcaecati?
              </p>
            </div>
            <div class="flex justify-between items-end">
              <a href="#"
                class="bg-blue-800 px-4 py-3 rounded-lg text-white text-xs tracking-wider font-semibold hover:bg-blue-600 hover:text-white">
                Learn More
              </a>
              <img src="../assets/calendar.png" alt="calendar" class="w-auto h-24 object-cover">
            </div>
          </div>

        </div>
        <!-- End First Row -->
        <!-- Start Second Row -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 px-4 xl:p-0 gap-4 xl:gap-6">
          <div class="col-span-1 md:col-span-2 lg:col-span-4 flex justify-between">
            <h2 class="text-xs md:text-sm text-gray-700 font-bold tracking-wide md:tracking-wider">
              Expenses By Category</h2>
            <a href="#" class="text-xs text-gray-800 font-semibold uppercase">More</a>
          </div>
          <div class="bg-white p-6 rounded-xl border border-gray-50">
            <div class="flex justify-between items-start">
              <div class="flex flex-col">
                <p class="text-xs text-gray-600 tracking-wide">Foods & Beverages</p>
                <h3 class="mt-1 text-lg text-blue-500 font-bold">$ 818</h3>
                <span class="mt-4 text-xs text-gray-500">Last Transaction 3 Hours ago</span>
              </div>
              <div class="bg-blue-500 p-2 md:p-1 xl:p-2 rounded-md">
                <img src="../assets/dish-2.png" alt="icon" class="w-auto h-8 md:h-6 xl:h-8 object-cover">
              </div>
            </div>
          </div>
          <div class="bg-white p-6 rounded-xl border border-gray-50">
            <div class="flex justify-between items-start">
              <div class="flex flex-col">
                <p class="text-xs text-gray-600 tracking-wide">Groceries</p>
                <h3 class="mt-1 text-lg text-green-500 font-bold">$ 8,918</h3>
                <span class="mt-4 text-xs text-gray-500">Last Transaction 3 Days ago</span>
              </div>
              <div class="bg-green-500 p-2 md:p-1 xl:p-2 rounded-md">
                <img src="../assets/grocery.png" alt="icon" class="w-auto h-8 md:h-6 xl:h-8 object-cover">
              </div>
            </div>
          </div>
          <div class="bg-white p-6 rounded-xl border border-gray-50">
            <div class="flex justify-between items-start">
              <div class="flex flex-col">
                <p class="text-xs text-gray-600 tracking-wide">Gaming</p>
                <h3 class="mt-1 text-lg text-yellow-500 font-bold">$ 1,223</h3>
                <span class="mt-4 text-xs text-gray-600">Last Transaction 4 Days ago</span>
              </div>
              <div class="bg-yellow-500 p-2 md:p-1 xl:p-2 rounded-md">
                <img src="../assets/gaming.png" alt="icon" class="w-auto h-8 md:h-6 xl:h-8 object-cover">
              </div>
            </div>
          </div>
          <div class="bg-white p-6 rounded-xl border border-gray-50">
            <div class="flex justify-between items-start">
              <div class="flex flex-col">
                <p class="text-xs text-gray-600 tracking-wide">Trip & Holiday</p>
                <h3 class="mt-1 text-lg text-indigo-500 font-bold">$ 5,918</h3>
                <span class="mt-4 text-xs text-gray-500">Last Transaction 1 Month ago</span>
              </div>
              <div class="bg-indigo-500 p-2 md:p-1 xl:p-2 rounded-md">
                <img src="../assets/holiday.png" alt="icon" class="w-auto h-8 md:h-6 xl:h-8 object-cover">
              </div>
            </div>
          </div>
        </div>
        <!-- End Second Row -->
        <!-- Start Third Row -->
        <div class="grid grid-cols-1 md:grid-cols-5 items-start px-4 xl:p-0 gap-y-4 md:gap-6">
          <div class="col-start-1 col-end-5">
            <h2 class="text-xs md:text-sm text-gray-800 font-bold tracking-wide">Summary Transactions</h2>
          </div>
          <div class="col-span-2 bg-white p-6 rounded-xl border border-gray-50 flex flex-col space-y-6">
            <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 flex justify-between items-center">
              <div class="p-4 cursor-pointer border">
                <span class="text-xs text-gray-500 font-semibold">Daily</span>
                <h2 class="text-gray-800 font-bold tracking-wider">$ 27.80</h2>
              </div>
              <div class="p-4 cursor-pointer border">
                <span class="text-xs text-gray-500 font-semibold">Weekly</span>
                <h2 class="text-gray-800 font-bold tracking-wider">$ 192.92</h2>
              </div>
              <div class="p-4 cursor-pointer border">
                <span class="text-xs text-gray-500 font-semibold">Monthly</span>
                <h2 class="text-gray-800 font-bold tracking-wider">$ 501.10</h2>
              </div>
            </div>
            <canvas id="myChart"></canvas>
          </div>
          <div class="col-span-3 bg-white p-6 rounded-xl border border-gray-50 flex flex-col space-y-6">
            <div class="flex justify-between items-center">
              <h2 class="text-sm text-gray-600 font-bold tracking-wide">Latest Transactions</h2>
              <a href="#"
                class="px-4 py-2 text-xs bg-blue-100 text-blue-500 rounded uppercase tracking-wider font-semibold hover:bg-blue-300">More</a>
            </div>
            <ul class="divide-y-2 divide-gray-100 overflow-x-auto w-full">
              <li class="py-3 flex justify-between text-sm text-gray-500 font-semibold">
                <p class="px-4 font-semibold">Today</p>
                <p class="px-4 text-gray-600">McDonald</p>
                <p class="px-4 tracking-wider">Cash</p>
                <p class="px-4 text-blue-600">Food</p>
                <p class="md:text-base text-gray-800 flex items-center gap-2">
                  16.90
                  <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                  </svg>
                </p>
              </li>
              <li class="py-3 flex justify-between text-sm text-gray-500 font-semibold">
                <p class="px-4 font-semibold">Today</p>
                <p class="px-4 text-gray-600">McDonald</p>
                <p class="px-4 tracking-wider">Cash</p>
                <p class="px-4 text-blue-600">Food</p>
                <p class="md:text-base text-gray-800 flex items-center gap-2">
                  16.90
                  <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                  </svg>
                </p>
              </li>
              <li class="py-3 flex justify-between text-sm text-gray-500 font-semibold">
                <p class="px-4 font-semibold">Today</p>
                <p class="px-4 text-gray-600">McDonald</p>
                <p class="px-4 tracking-wider">Cash</p>
                <p class="px-4 text-blue-600">Food</p>
                <p class="md:text-base text-gray-800 flex items-center gap-2">
                  16.90
                  <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                  </svg>
                </p>
              </li>
              <li class="py-3 flex justify-between text-sm text-gray-500 font-semibold">
                <p class="px-4 font-semibold">Today</p>
                <p class="px-4 text-gray-600">McDonald</p>
                <p class="px-4 tracking-wider">Cash</p>
                <p class="px-4 text-blue-600">Food</p>
                <p class="md:text-base text-gray-800 flex items-center gap-2">
                  16.90
                  <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                  </svg>
                </p>
              </li>
              <li class="py-3 flex justify-between text-sm text-gray-500 font-semibold">
                <p class="px-4 font-semibold">Today</p>
                <p class="px-4 text-gray-600">McDonald</p>
                <p class="px-4 tracking-wider">Cash</p>
                <p class="px-4 text-blue-600">Food</p>
                <p class="md:text-base text-gray-800 flex items-center gap-2">
                  16.90
                  <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                  </svg>
                </p>
              </li>
              <li class="py-3 flex justify-between text-sm text-gray-500 font-semibold">
                <p class="px-4 font-semibold">Today</p>
                <p class="px-4 text-gray-600">McDonald</p>
                <p class="px-4 tracking-wider">Cash</p>
                <p class="px-4 text-blue-600">Food</p>
                <p class="md:text-base text-gray-800 flex items-center gap-2">
                  16.90
                  <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4" fill="none" viewBox="0 0 24 24"
                    stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                  </svg>
                </p>
              </li>
            </ul>
          </div>
        </div>
        <!-- End Third Row -->
      </div>
    </main>
  </div>
</template>
<script setup></script>
