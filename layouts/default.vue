<script setup>
// for language - Menu
const language = ref('BM')
const isDropdownOpen = ref(false)
const languages = [
  { code: 'BM', label: 'BM', flag: 'https://flagcdn.com/my.svg' },
  { code: 'EN', label: 'EN', flag: 'https://flagcdn.com/us.svg' }
]
const selectLanguage = (langCode) => {
  language.value = langCode
  isDropdownOpen.value = false
}
const getCurrentFlag = () => {
  return languages.find(lang => lang.code === language.value)?.flag
}

// for navigation - Menu
// Menu list
const maipsMenu = ref([])
const route = useRoute()

// Function to update isSelected based on current route
const updateSelectedMenu = () => {
  maipsMenu.value.forEach(menu => {
    menu.isSelected = menu.path === route.path
  })
}

onMounted(async () => {
  const res = await fetch('/maipsMenu.json')
  maipsMenu.value = await res.json()
  updateSelectedMenu()
})

// Watch for route changes to update selected menu
watch(() => route.path, () => {
  updateSelectedMenu()
})


// Responsive table
const menuVisible = ref(false)
const toggleMenu = () => {
  menuVisible.value= !menuVisible.value;
};

</script>


<template>
  <!-- Desktop (Small and Large) Header -->
 <div class="hidden lg:block xl:block 2xl:block">
    <!-- Top social and language bar -->
          <div class="bg-gray-100 text-sm px-4 py-2 flex justify-around items-center shadow-sm">
            <div class="flex gap-4 items-center text-gray-600">
              <span>Ikuti kami di:</span>
              <div class="flex gap-2">
              <NuxtLink to="https://www.facebook.com/MajlisAgamaIslamPerlis">
                  <div class="w-6 h-6 border-[1px] border-gray-600 rounded-full flex items-center justify-center cursor-pointer">
                  <Icon name="ri:facebook-fill" class="w-4 h-4" />
                  </div>
              </NuxtLink>
              <NuxtLink to="https://www.instagram.com/maips_official/">
                  <div class="w-6 h-6 border border-[1px] border-gray-600 rounded-full flex items-center justify-center cursor-pointer">
                  <Icon name="fa6-brands:instagram" class="w-4 h-4" />
                  </div>
              </NuxtLink>
              <NuxtLink to="https://www.tiktok.com/@maips_official">
                  <div class="w-6 h-6 border border-[1px] border-gray-600 rounded-full flex items-center justify-center cursor-pointer">
                  <Icon name="ri:tiktok-fill" class="w-4 h-4" />
                  </div>
              </NuxtLink>
              <NuxtLink to="https://www.youtube.com/@maipsofficial6767">
                  <div class="w-6 h-6 border border-[1px] border-gray-600 rounded-full flex items-center justify-center cursor-pointer">
                  <Icon name="ri:youtube-fill" class="w-4 h-4" />
                  </div>
              </NuxtLink>
              </div>
            </div>
            <div class="flex gap-4 items-center">
              <NuxtLink to="https://www.maips.gov.my/soalan-lazim/">
                  <Icon name="ri:question-line" class="w-6 h-6 text-gray-500" />
              </NuxtLink>
              <NuxtLink to="https://www.maips.gov.my/maklumat-perhubungan/">
                  <Icon name="ri:phone-line" class="w-6 h-6 text-gray-500" />
              </NuxtLink>
              <NuxtLink to="">
                <Icon name="ph-chat-centered-dots" class="w-6 h-6 text-gray-500" />
              </NuxtLink>
              <NuxtLink to="https://www.maips.gov.my/peta-laman/">
                  <Icon name="mdi-sitemap-outline" class="w-6 h-6 text-gray-500" /> 
              </NuxtLink>
              <div class="mx-4 border-[1px] border-gray-400 h-6"></div>
              <div class="relative inline-block text-left">
                <NuxtButton
                  @click="isDropdownOpen = !isDropdownOpen"
                  class="flex items-center gap-2 px-2 py-1 bg-transparent hover:opacity-80 cursor-pointer"
                >
                  <NuxtImg :src="getCurrentFlag()" width="20" height="14" class="rounded-sm" />
                  <span class="text-sm text-gray-700">{{ language }}</span>
                  <Icon name="mdi:chevron-down" class="w-5 h-5 text-gray-500" />
                </NuxtButton>

                <!-- Dropdown Language -->
                <div
                  v-if="isDropdownOpen"
                  class="absolute right-0 mt-2 w-32 bg-white border border-gray-200 rounded shadow-lg z-50"
                >
                  <ul class="py-1">
                    <li
                      v-for="lang in languages"
                      :key="lang.code"
                      @click="selectLanguage(lang.code)"
                      class="flex items-center gap-2 px-3 py-2 cursor-pointer hover:bg-gray-100"
                    >
                      <NuxtImg :src="lang.flag" width="20" height="14" class="rounded-sm" alt="language" />
                      <span class="text-sm text-gray-700">{{ lang.label }}</span>
                    </li>
                  </ul>
                </div>
              </div>
              <div class="mx-4 border-[1px] border-gray-400 h-6"></div>
              <NuxtLink to="https://www1.maips.gov.my/index.php?option=com_users&view=login&lang=img&Itemid=402" class="flex items-center gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16" fill="none"><g id="Group"><path id="Vector" d="M14.5479 0.01C14.5313 0.00866667 14.5173 0 14.4999 0H7.33325C6.23059 0 5.33325 0.897333 5.33325 2V2.66667C5.33325 3.03467 5.63192 3.33333 5.99992 3.33333C6.36792 3.33333 6.66659 3.03467 6.66659 2.66667V2C6.66659 1.63267 6.96592 1.33333 7.33325 1.33333H10.4393L10.2359 1.40133C9.69592 1.588 9.33325 2.09667 9.33325 2.66667V12.6667H7.33325C6.96592 12.6667 6.66659 12.3673 6.66659 12V10.6667C6.66659 10.2987 6.36792 10 5.99992 10C5.63192 10 5.33325 10.2987 5.33325 10.6667V12C5.33325 13.1027 6.23059 14 7.33325 14H9.33325V14.6667C9.33325 15.402 9.93125 16 10.6666 16C10.8093 16 10.9446 15.9793 11.0913 15.934L15.0966 14.5987C15.6373 14.412 15.9999 13.9033 15.9999 13.3333V1.33333C15.9999 0.556 15.3299 -0.0533333 14.5479 0.01Z" fill="#0054A5"></path><path id="Vector_2" d="M7.138 6.19513L4.47133 3.52847C4.28067 3.3378 3.994 3.28047 3.74467 3.3838C3.496 3.48713 3.33333 3.73047 3.33333 3.9998V5.9998H0.666667C0.298667 5.9998 0 6.29847 0 6.66647C0 7.03447 0.298667 7.33313 0.666667 7.33313H3.33333V9.33313C3.33333 9.60247 3.496 9.8458 3.74467 9.94913C3.994 10.0525 4.28067 9.99513 4.47133 9.80447L7.138 7.1378C7.39867 6.87713 7.39867 6.4558 7.138 6.19513Z" fill="#0054A5"></path></g></svg>
                <span class="text-[#0054A5] font-semibold">Warga MAIPs</span>
              </NuxtLink>
            </div>
        </div>

          <!-- Logo + Banner -->
        <div class="bg-white px-4 py-4 flex justify-around items-center flex-wrap gap-4">
        <div class="flex items-center gap-4 flex-wrap">
          <!-- Use static provider or regular img if from /public -->
          <NuxtImg src="/MAIPs-logo.png"  width="150" height="150" alt="MAIPs logo" class="w-24 h-24 object-contain" />
          <div class="max-w-2xl">
            <h2 class="text-sm font-semibold">LAMAN WEB RASMI</h2>
            <h2 class="text-sm font-semibold ">
              مجليس اڬام اسلام دان عادة ايستيعادة ملايو ڤرليس
            </h2>
            <h2 class="text-sm font-semibold ">
              MAJLIS AGAMA ISLAM DAN ADAT ISTIADAT MELAYU PERLIS
            </h2>
            <p class="text-sm text-gray-500 italic">
              Perlis Islamic Religious Custom and Malay Council
            </p>
          </div>
        </div>
        <NuxtLink to="/" class="w-48 h-auto object-contain"> 
            <NuxtImg src="/zakat-promo.png" alt="Promosi Zakat MAIPs"  />    
        </NuxtLink>
        </div>

          <!-- Decorative Border -->
          <NuxtImg
            src="decorate.png"
            alt="Decorative"
            class="w-full py-1"
          />

    <!-- Navigation -->
  <nav class="bg-[#0054A5] text-white px-10 py-3">
    <div class="w-full max-w-screen-xl mx-auto flex items-center justify-between">
      <ul class="flex gap-8 font-semibold relative">
        <li 
          v-for="menu in maipsMenu"
          :key="menu.title"
          class="relative cursor-pointer group hover:text-[#FDF600]"
          :class="{ 'text-[#FDF600]': menu.isSelected }"
        >
          <NuxtLink :to="menu.path" class="flex items-center gap-1">
            {{ menu.title }}
            <Icon 
              v-if="menu.items.length" 
              name="mdi:chevron-down" 
              class="w-6 h-6 group-hover:text-[#FDF600]"
            />
          </NuxtLink>
          
          <!-- Dropdown Menu -->
          <ul 
            v-if="menu.items.length"
            class="absolute top-full left-0 bg-white text-gray-500 mt-2 min-w-[220px] z-50 hidden group-hover:block"
          >
            <li 
              v-for="item in menu.items" 
              :key="item"
              class="px-4 py-2 hover:text-[#0054A5]"
            >
              {{ item }}
            </li>
          </ul>
        </li>
      </ul>

      <!-- Search Icon -->
      <div>
        <Icon name="ri:search-line" class="w-5 h-5 text-white cursor-pointer" />
      </div>
    </div>
  </nav>
  </div>


  <!-- Tablet Header -->
<div class="hidden md:block lg:hidden xl:hidden 2xl:hidden sticky top-0 bg-white z-50 shadow-md w-full">
  <!-- Logo + Hamburger -->
  <div class="flex items-center justify-between gap-4 flex-wrap">
    <!-- Logo -->
    <div class="flex items-center gap-4 flex-wrap px-6">
      <NuxtImg src="/MAIPs-logo.png" width="150" height="150" alt="MAIPs logo" class="w-16 h-16 object-contain" />
      <div class="max-w-2xl">
        <h2 class="text-sm font-semibold">LAMAN WEB RASMI</h2>
        <h2 class="text-sm font-semibold">
          مجليس اڬام اسلام دان عادة ايستيعادة ملايو ڤرليس
        </h2>
      </div>
    </div>
    <!-- Hamburger button -->
    <button @click="toggleMenu" class="p-4 bg-[#FDF600]">
      <svg v-if="!menuVisible" xmlns="http://www.w3.org/2000/svg" class="w-7 h-7 text-[#374151]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
      </svg>
      <svg v-else xmlns="http://www.w3.org/2000/svg" class="w-7 h-7 text-[#374151]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>
  </div>

  <!-- Decorative Border -->
  <NuxtImg
    src="https://s3-alpha-sig.figma.com/img/7029/11b9/15fc0f14085a273c51e9c176d1685510?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=ZIfEJ9-nCEZVqkYG9NKkX1yHgn4KNt8Bm2WR6PVjxlaoDexHCcGslMk1MU7Vy-U7hKXo3GnmGXI~JYVJC6tIk5We3wb46GQjkTtgQ0l1dkwU~a7AFPxfyTTtT7P9u6mAa5vtV62QlwvTE2y-GfAe~Wxitde8ZzYmBNHBP74MdRpLlporW9bDznKRpGyEDWsaeiHgAcfsSgGwSi5wFGjcovXT-VYGe6v63L8HMPrezoAUHMfC5DbdATNX5NSmGrkHZhAjs0p-qawrOe66mJvvjsqQaFMRtmmhjFFgWOOVXjOxnHjOX2uNBfqyqWpno~SevMvklmIKb6WoUf3SUSG0xA__"
    alt="Decorative"
    class="w-full"
  />
</div>

  <!-- Menu Section: Hidden by default, displayed when the button is clicked -->
  <div v-if="menuVisible" class="fixed inset-0 bg-white z-50 shadow-md p-6 hidden md:block lg:hidden xl:hidden 2xl:hidden">
    <!-- Close button -->
    <button @click="toggleMenu" class="absolute top-4 right-4 p-2 text-black">
      <svg xmlns="http://www.w3.org/2000/svg" class="w-8 h-8 text-black" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>

    <!-- Content in a Column Layout -->
    <div class="flex flex-col gap-6">
      <!-- Search Function -->
      <div>
        <input type="text" placeholder="Search..." class="w-full p-2 border border-gray-300 rounded-lg" />
      </div>

      <!-- Navigation -->
      <nav class="flex flex-col gap-4">
        <a href="#" class="text-black font-semibold">Home</a>
        <a href="#" class="text-black font-semibold">About</a>
        <a href="#" class="text-black font-semibold">Services</a>
        <a href="#" class="text-black font-semibold">Contact</a>
      </nav>

      <!-- Information Section -->
      <div class="text-black">
        <h3 class="text-xl font-semibold">Information</h3>
        <p>This is some information content.</p>
      </div>
    </div>
  </div>

 <!-- Phone Header -->
<div class="block md:hidden lg:hidden xl:hidden 2xl:hidden sticky top-0 bg-white z-50 shadow-md w-full">
  <!-- Logo + Hamburger -->
  <div class="flex items-center justify-between gap-2 ">
    <!-- Logo -->
    <div class="flex items-center gap-2 flex-grow py-2">
      <NuxtImg src="/MAIPs-logo.png" width="150" height="150" alt="MAIPs logo" class="w-16 h-16 object-contain" />
      <div class="flex flex-col text-left">
        <h2 class="text-[10px] font-semibold">LAMAN WEB RASMI</h2>
        <h2 class="text-[10px] font-semibold">
          مجليس اڬام اسلام دان عادة ايستيعادة ملايو ڤرليس
        </h2>
        <h2 class="text-[10px] font-semibold">
          MAJLIS AGAMA ISLAM DAN ADAT ISTIADAT MELAYU PERLIS
        </h2>
        <p class="text-[10px] text-gray-500 italic">
          Perlis Islamic Religious Custom and Malay Council
        </p>
      </div>
    </div>
    <!-- Hamburger button -->
    <button @click="toggleMenu" class="px-6 py-10 bg-[#FDF600] ">
      <svg v-if="!menuVisible" xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-[#374151]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
      </svg>
      <svg v-else xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-[#374151]" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>
  </div>
  <!-- Decorative Border -->
  <NuxtImg
    src="https://s3-alpha-sig.figma.com/img/7029/11b9/15fc0f14085a273c51e9c176d1685510?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=ZIfEJ9-nCEZVqkYG9NKkX1yHgn4KNt8Bm2WR6PVjxlaoDexHCcGslMk1MU7Vy-U7hKXo3GnmGXI~JYVJC6tIk5We3wb46GQjkTtgQ0l1dkwU~a7AFPxfyTTtT7P9u6mAa5vtV62QlwvTE2y-GfAe~Wxitde8ZzYmBNHBP74MdRpLlporW9bDznKRpGyEDWsaeiHgAcfsSgGwSi5wFGjcovXT-VYGe6v63L8HMPrezoAUHMfC5DbdATNX5NSmGrkHZhAjs0p-qawrOe66mJvvjsqQaFMRtmmhjFFgWOOVXjOxnHjOX2uNBfqyqWpno~SevMvklmIKb6WoUf3SUSG0xA__"
    alt="Decorative"
    class="w-full"
  />
</div>







    <!-- Main Page Content -->
    <div>
        <slot />
    </div>

    <!-- Desktop (Small and Large) Footer -->
  <footer class="hidden lg:block xl:block 2xl:block bg-[#0054A5] text-white text-sm">
    <div class="max-w-screen-xl mx-auto px-6 py-16 grid grid-cols-1 lg:grid-cols-4 gap-8">
      <!-- Logo & Contact -->
      <div>
        <NuxtImg src="https://www.maips.gov.my/wp-content/uploads/2024/11/MAIPs-logo-footer.png"  alt="MAIPs Logo" class="w-full"/>
        <div class="flex items-start space-x-3">
          <Icon name="ri:map-pin-line" class="w-6 h-6 mt-4"/>
          <p class="text-base mt-4 leading-5">
          A2, Taman Pengkalan Asam,<br />
          Jalan Tuanku Syed Putra,<br />
          01000 Kangar, Perlis<br />
        </p>
        </div>

        <NuxtImg src="https://www.maips.gov.my/wp-content/uploads/2024/11/Footer-jawi.png" alt="Jawi Location" width="150" class="mx-8 my-4"/>
        <div class="flex items-center space-x-3">
          <Icon name="fontisto:email" class="w-5 h-5 "/>
          <p class="text-base">korporat@maips.gov.my</p>
        </div>
        <div class="flex items-center space-x-2 my-3">
          <Icon name="akar-icons:phone" class="w-5 h-5"/>
          <p class="text-base">+604 979 4439</p>
        </div>
        <div class="flex items-center space-x-2 my-3">
          <Icon name="mdi:fax" class="w-5 h-5"/>
          <p class="text-base">+604 978 2400</p>
        </div>
        <div class="flex items-start space-x-3 my-3">
          <Icon name="bi:clock" class="w-5 h-5 mt-1"/>
            <p class="text-base">Isnin - Jumaat:<br/> 8.30 pagi - 4.30 petang</p>
        </div>
        <div class="flex items-start space-x-3 my-3">
          <Icon name="bi:hourglass" class="w-5 h-5 mt-1"/>
            <p class="text-base">Rehat (Isnin - Khamis): <br />1.00 tengah hari - 2.00 petang </p>
        </div>
        <div class="flex items-start space-x-3 my-3">
          <Icon name="bi:hourglass" class="w-5 h-5 mt-1"/>
          <p class="text-base">Rehat (Jumaat): <br/> 12.15 tengah hari - 2.45 petang</p>
        </div>
        <div class="flex gap-3 mt-8">
        <NuxtLink to="https://www.facebook.com/MajlisAgamaIslamPerlis">
            <div class="w-8 h-8 border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="ri:facebook-fill" class="w-6 h-6" />
            </div>
        </NuxtLink>
        <NuxtLink to="https://www.instagram.com/maips_official/">
            <div class="w-8 h-8 border border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="fa6-brands:instagram" class="w-6 h-6" />
            </div>
        </NuxtLink>
        <NuxtLink to="https://www.tiktok.com/@maips_official">
            <div class="w-8 h-8 border border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="ri:tiktok-fill" class="w-6 h-6" />
            </div>
        </NuxtLink>
        <NuxtLink to="https://www.youtube.com/@maipsofficial6767">
            <div class="w-8 h-8 border border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="ri:youtube-fill" class="w-6 h-6" />
            </div>
        </NuxtLink>
        </div>
      </div>

      <!-- Tentang MAIPs -->
      <div>
        <h3 class="text-base font-semibold mb-3">Tentang MAIPs</h3>
        <ul class="space-y-3 text-base">
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/tentang-maips/dymm-tuanku-raja-perlis/">
              DYMM Tuanku Raja Perlis
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/tentang-maips/dytm-tuanku-yang-dipertua/">
             DYTM Tuanku Yang DiPertua
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/tentang-maips/perutusan-ketua-pegawai-eksekutif/">
              Perutusan Ketua Pegawai Eksekutif
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/tentang-maips/mengenai-maips/">
              Mengenai MAIPs
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/tentang-maips/ahli-majlis/">
             Ahli Majlis
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/tentang-maips/carta-organisasi/">
             Carta Organisasi
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/tentang-maips/agensi-bersama/">
             Agensi Bersama
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/tentang-maips/subsidiari/">
              Subsidiari
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/tentang-maips/piagam-pelanggan/">
              Piagam Pelanggan
          </NuxtLink>
          </li>
        </ul>
      </div>

      <!-- Perkhidmatan -->
      <div>
        <h3 class="text-base font-semibold mb-3">Perkhidmatan</h3>
        <ul class="space-y-3 text-base">
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/jenis-jenis-zakat/">
              Jenis-jenis Zakat
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/skim-bantuan-zakat/">
             Skim Bantuan Zakat
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/wakaf/">
              Wakaf
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/sumber-am/">
              Sumber Am
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/fasiliti/">
             Fasiliti
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/pusat-warisan/">
             Pusat Warisan
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/adat-istiadat-melayu/">
             Adat Istiadat Melayu
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/hebahan-warta/">
              Hebahan Warta
          </NuxtLink>
          </li>
        </ul>
      </div>

      <!-- Berita & Media + Hubungi Kami -->
      <div>
        <h3 class="text-base font-semibold mb-3">Berita & Media</h3>
        <ul class="space-y-3 text-base">
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/hebahan-media/">
              Hebahan Media
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/pusat-berita/">
             Pusat Berita
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/pusat-media/">
              Pusat Media
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/acara/">
              Acara
          </NuxtLink>
          </li>
        </ul>
        <h3 class="text-base font-semibold mt-8 mb-3">Hubungi Kami</h3>
        <ul class="space-y-3 text-base">
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/maklumat-perhubungan/">
              Maklumat Perhubungan
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/kerjaya/">
             Kerjaya
          </NuxtLink>
          </li>
          <li class="cursor-pointer">         
            <NuxtLink to="https://www.maips.gov.my/perolehan/">
              Perolehan
          </NuxtLink>
          </li>
        </ul>
      </div>
    </div>

    <div class="bg-[#004C7D] text-white py-4">
      <div class="max-w-screen-xl mx-auto flex flex-row justify-between items-center gap-2">
        <div class="text-sm leading-7">
            <NuxtLink to="https://www.maips.gov.my/penafian/">
            Penafian
          </NuxtLink> | 
          <NuxtLink to="https://www.maips.gov.my/dasar-privasi-dan-keselamatan/">
            Dasar Privasi & Keselamatan 
          </NuxtLink>|
          <NuxtLink to="https://www.maips.gov.my/notis-hak-cipta/">
            Notis Hak Cipta
          </NuxtLink>
          <p>Hakcipta Terpelihara © 2024 Majlis Agama Islam dan Adat Istiadat Melayu Perlis (MAIPs).</p>
          <p>Paparan terbaik mengunakan pelayar internet Chrome dengan resolusi minimum 1366x768.</p>
        </div>
        <div class="text-sm leading-7">
            <p>Pelawat Hari Ini: <span class="font-bold">121</span></p>
            <p>Jumlah pelawat: <span class="font-bold">222742</span></p>
            <p>Tarikh kemaskini: <span class="font-bold">21/10/24</span></p>
        </div>
      </div>
    </div>
    
    <NuxtImg
      src="https://s3-alpha-sig.figma.com/img/7029/11b9/15fc0f14085a273c51e9c176d1685510?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=ZIfEJ9-nCEZVqkYG9NKkX1yHgn4KNt8Bm2WR6PVjxlaoDexHCcGslMk1MU7Vy-U7hKXo3GnmGXI~JYVJC6tIk5We3wb46GQjkTtgQ0l1dkwU~a7AFPxfyTTtT7P9u6mAa5vtV62QlwvTE2y-GfAe~Wxitde8ZzYmBNHBP74MdRpLlporW9bDznKRpGyEDWsaeiHgAcfsSgGwSi5wFGjcovXT-VYGe6v63L8HMPrezoAUHMfC5DbdATNX5NSmGrkHZhAjs0p-qawrOe66mJvvjsqQaFMRtmmhjFFgWOOVXjOxnHjOX2uNBfqyqWpno~SevMvklmIKb6WoUf3SUSG0xA__"
      alt="Decorative"
      class="w-full"
    />
  </footer>


  <!-- Tablet Footer -->
   <footer class="md:block hidden lg:hidden xl:hidden 2xl:hidden bg-[#0054A5] text-white " >
      <div class="p-16">
            <!-- Logo & Contact -->
      <div class="pb-6">
        <NuxtImg src="https://www.maips.gov.my/wp-content/uploads/2024/11/MAIPs-logo-footer.png"  alt="MAIPs Logo" class="w-2/3"/>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <!-- Left Column: Location -->
        <div class="flex flex-col space-y-4">
          <div class="flex items-start space-x-3">
            <Icon name="ri:map-pin-line" class="w-6 h-6 mt-4"/>
            <p class="text-base mt-4 leading-5">
              A2, Taman Pengkalan Asam,<br />
              Jalan Tuanku Syed Putra,<br />
              01000 Kangar, Perlis<br />
            </p>
          </div>
          <NuxtImg src="https://www.maips.gov.my/wp-content/uploads/2024/11/Footer-jawi.png" alt="Jawi Location" width="150" class="mx-8 my-4"/>
        </div>
        <!-- Right Column: Contact Information -->
        <div class="flex flex-col space-y-3">
          <div class="flex items-center space-x-3">
            <Icon name="fontisto:email" class="w-5 h-5"/>
            <p class="text-base">korporat@maips.gov.my</p>
          </div>
          <div class="flex items-center space-x-2">
            <Icon name="akar-icons:phone" class="w-5 h-5"/>
            <p class="text-base">+604 979 4439</p>
          </div>
          <div class="flex items-center space-x-2">
            <Icon name="mdi:fax" class="w-5 h-5"/>
            <p class="text-base">+604 978 2400</p>
          </div>
          <div class="flex items-start space-x-3">
            <Icon name="bi:clock" class="w-5 h-5 mt-1"/>
            <p class="text-base">Isnin - Jumaat:<br/> 8.30 pagi - 4.30 petang</p>
          </div>
          <div class="flex items-start space-x-3">
            <Icon name="bi:hourglass" class="w-5 h-5 mt-1"/>
            <p class="text-base">Rehat (Isnin - Khamis): <br />1.00 tengah hari - 2.00 petang </p>
          </div>
          <div class="flex items-start space-x-3">
            <Icon name="bi:hourglass" class="w-5 h-5 mt-1"/>
            <p class="text-base">Rehat (Jumaat): <br/> 12.15 tengah hari - 2.45 petang</p>
          </div>
        </div>
      </div>
    </div>

<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
  <!-- Tentang MAIPs -->
  <div>
    <h3 class="text-base font-semibold mb-3">Tentang MAIPs</h3>
    <ul class="space-y-3 text-base">
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/dymm-tuanku-raja-perlis/">
          DYMM Tuanku Raja Perlis
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/dytm-tuanku-yang-dipertua/">
          DYTM Tuanku Yang DiPertua
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/perutusan-ketua-pegawai-eksekutif/">
          Perutusan Ketua Pegawai Eksekutif
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/mengenai-maips/">
          Mengenai MAIPs
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/ahli-majlis/">
          Ahli Majlis
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/carta-organisasi/">
          Carta Organisasi
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/agensi-bersama/">
          Agensi Bersama
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/subsidiari/">
          Subsidiari
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/piagam-pelanggan/">
          Piagam Pelanggan
        </NuxtLink>
      </li>
    </ul>
  </div>

  <!-- Perkhidmatan -->
  <div>
    <h3 class="text-base font-semibold mb-3">Perkhidmatan</h3>
    <ul class="space-y-3 text-base">
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/jenis-jenis-zakat/">
          Jenis-jenis Zakat
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/skim-bantuan-zakat/">
          Skim Bantuan Zakat
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/wakaf/">
          Wakaf
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/sumber-am/">
          Sumber Am
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/fasiliti/">
          Fasiliti
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/pusat-warisan/">
          Pusat Warisan
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/adat-istiadat-melayu/">
          Adat Istiadat Melayu
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/hebahan-warta/">
          Hebahan Warta
        </NuxtLink>
      </li>
    </ul>
  </div>

  <!-- Berita & Media + Hubungi Kami -->
  <div>
    <h3 class="text-base font-semibold mb-3">Berita & Media</h3>
    <ul class="space-y-3 text-base">
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/hebahan-media/">
          Hebahan Media
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/pusat-berita/">
          Pusat Berita
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/pusat-media/">
          Pusat Media
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/acara/">
          Acara
        </NuxtLink>
      </li>
    </ul>
    <h3 class="text-base font-semibold mt-8 mb-3">Hubungi Kami</h3>
    <ul class="space-y-3 text-base">
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/maklumat-perhubungan/">
          Maklumat Perhubungan
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/kerjaya/">
          Kerjaya
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/perolehan/">
          Perolehan
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="">
          Aduan Jejak Asnaf
        </NuxtLink>
      </li>
    </ul>
  </div>
</div>

           <div class="flex gap-3 mt-8">
        <NuxtLink to="https://www.facebook.com/MajlisAgamaIslamPerlis">
            <div class="w-8 h-8 border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="ri:facebook-fill" class="w-6 h-6" />
            </div>
        </NuxtLink>
        <NuxtLink to="https://www.instagram.com/maips_official/">
            <div class="w-8 h-8 border border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="fa6-brands:instagram" class="w-6 h-6" />
            </div>
        </NuxtLink>
        <NuxtLink to="https://www.tiktok.com/@maips_official">
            <div class="w-8 h-8 border border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="ri:tiktok-fill" class="w-6 h-6" />
            </div>
        </NuxtLink>
        <NuxtLink to="https://www.youtube.com/@maipsofficial6767">
            <div class="w-8 h-8 border border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="ri:youtube-fill" class="w-6 h-6" />
            </div>
        </NuxtLink>
        </div>
      </div>

      <div class="bg-[#004C7D] text-white py-4">
      <div class="px-16 flex flex-col justify-evenly items-start gap-2">
        <div class="text-sm leading-7">
            <NuxtLink to="https://www.maips.gov.my/penafian/">
            Penafian
          </NuxtLink> | 
          <NuxtLink to="https://www.maips.gov.my/dasar-privasi-dan-keselamatan/">
            Dasar Privasi & Keselamatan 
          </NuxtLink>|
          <NuxtLink to="https://www.maips.gov.my/notis-hak-cipta/">
            Notis Hak Cipta
          </NuxtLink>
          <p>Hakcipta Terpelihara © 2024 Majlis Agama Islam dan Adat Istiadat Melayu Perlis (MAIPs).</p>
          <p>Paparan terbaik mengunakan pelayar internet Chrome dengan resolusi minimum 1366x768.</p>
        </div>
        <div class="flex flex-row gap-8 text-sm leading-7">
          <p>Pelawat Hari Ini: <span class="font-bold">121</span></p>
            <p>Jumlah pelawat: <span class="font-bold">222742</span></p>
            <p>Tarikh kemaskini: <span class="font-bold">21/10/24</span></p>
        </div>
      </div>
    </div>
          <NuxtImg
      src="https://s3-alpha-sig.figma.com/img/7029/11b9/15fc0f14085a273c51e9c176d1685510?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=ZIfEJ9-nCEZVqkYG9NKkX1yHgn4KNt8Bm2WR6PVjxlaoDexHCcGslMk1MU7Vy-U7hKXo3GnmGXI~JYVJC6tIk5We3wb46GQjkTtgQ0l1dkwU~a7AFPxfyTTtT7P9u6mAa5vtV62QlwvTE2y-GfAe~Wxitde8ZzYmBNHBP74MdRpLlporW9bDznKRpGyEDWsaeiHgAcfsSgGwSi5wFGjcovXT-VYGe6v63L8HMPrezoAUHMfC5DbdATNX5NSmGrkHZhAjs0p-qawrOe66mJvvjsqQaFMRtmmhjFFgWOOVXjOxnHjOX2uNBfqyqWpno~SevMvklmIKb6WoUf3SUSG0xA__"
      alt="Decorative"
      class="w-full"
    />
   </footer>

   <!-- Phone Footer -->
    <footer class="block md:hidden  lg:hidden xl:hidden 2xl:hidden bg-[#0054A5] text-white " >
      <div class="p-16">
            <!-- Logo & Contact -->
      <div class="pb-6">
        <NuxtImg src="https://www.maips.gov.my/wp-content/uploads/2024/11/MAIPs-logo-footer.png"  alt="MAIPs Logo" class="w-2/3"/>
        <!-- Left Column: Location -->
      <div class="flex flex-row space-x-4 items-center">
        <div class="flex items-start space-x-3">
          <Icon name="ri:map-pin-line" class="w-4 h-4 mt-1"/>
          <p class="text-xs leading-5">
            A2, Taman Pengkalan Asam,<br />
            Jalan Tuanku Syed Putra,<br />
            01000 Kangar, Perlis<br />
          </p>
        </div>
        <NuxtImg src="https://www.maips.gov.my/wp-content/uploads/2024/11/Footer-jawi.png" alt="Jawi Location" width="90" class="my-4"/>
      </div>

        <!-- Right Column: Contact Information -->
        <div class="flex flex-col space-y-3">
          <div class="flex items-center space-x-3">
            <Icon name="fontisto:email" class="w-5 h-5"/>
            <p class="text-xs">korporat@maips.gov.my</p>
          </div>
          <div class="flex items-center space-x-2">
            <Icon name="akar-icons:phone" class="w-5 h-5"/>
            <p class="text-xs">+604 979 4439</p>
          </div>
          <div class="flex items-center space-x-2">
            <Icon name="mdi:fax" class="w-5 h-5"/>
            <p class="text-xs">+604 978 2400</p>
          </div>
          <div class="flex items-start space-x-3">
            <Icon name="bi:clock" class="w-5 h-5 mt-1"/>
            <p class="text-xs">Isnin - Jumaat:<br/> 8.30 pagi - 4.30 petang</p>
          </div>
          <div class="flex items-start space-x-3">
            <Icon name="bi:hourglass" class="w-5 h-5 mt-1"/>
            <p class="text-xs">Rehat (Isnin - Khamis): <br />1.00 tengah hari - 2.00 petang </p>
          </div>
          <div class="flex items-start space-x-3">
            <Icon name="bi:hourglass" class="w-5 h-5 mt-1"/>
            <p class="text-xs">Rehat (Jumaat): <br/> 12.15 tengah hari - 2.45 petang</p>
          </div>
        </div>
      
    </div>

<div class="grid grid-cols-2 gap-8">
  <!-- Tentang MAIPs -->
  <div>
    <h3 class="text-sm font-semibold mb-3">Tentang MAIPs</h3>
    <ul class="space-y-3 text-xs">
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/dymm-tuanku-raja-perlis/">
          DYMM Tuanku Raja Perlis
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/dytm-tuanku-yang-dipertua/">
          DYTM Tuanku Yang DiPertua
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/perutusan-ketua-pegawai-eksekutif/">
          Perutusan Ketua Pegawai Eksekutif
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/mengenai-maips/">
          Mengenai MAIPs
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/ahli-majlis/">
          Ahli Majlis
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/carta-organisasi/">
          Carta Organisasi
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/agensi-bersama/">
          Agensi Bersama
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/subsidiari/">
          Subsidiari
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/tentang-maips/piagam-pelanggan/">
          Piagam Pelanggan
        </NuxtLink>
      </li>
    </ul>
  </div>

  <!-- Perkhidmatan -->
  <div>
    <h3 class="text-xs font-semibold mb-3">Perkhidmatan</h3>
    <ul class="space-y-3 text-xs">
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/jenis-jenis-zakat/">
          Jenis-jenis Zakat
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/skim-bantuan-zakat/">
          Skim Bantuan Zakat
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/wakaf/">
          Wakaf
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/sumber-am/">
          Sumber Am
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/fasiliti/">
          Fasiliti
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/pusat-warisan/">
          Pusat Warisan
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/adat-istiadat-melayu/">
          Adat Istiadat Melayu
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/hebahan-warta/">
          Hebahan Warta
        </NuxtLink>
      </li>
    </ul>
  </div>

  <!-- Berita & Media  -->
  <div>
    <h3 class="text-xs font-semibold mb-3">Berita & Media</h3>
    <ul class="space-y-3 text-xs">
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/hebahan-media/">
          Hebahan Media
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/pusat-berita/">
          Pusat Berita
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/pusat-media/">
          Pusat Media
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/acara/">
          Acara
        </NuxtLink>
      </li>
    </ul>
  </div>
   
  <div>
    <h3 class="text-xs font-semibold mb-3">Hubungi Kami</h3>
    <ul class="space-y-3 text-xs">
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/maklumat-perhubungan/">
          Maklumat Perhubungan
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/kerjaya/">
          Kerjaya
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="https://www.maips.gov.my/perolehan/">
          Perolehan
        </NuxtLink>
      </li>
      <li class="cursor-pointer">         
        <NuxtLink to="">
          Aduan Jejak Asnaf
        </NuxtLink>
      </li>
    </ul>
  </div>
</div>

 <div class="flex gap-3 mt-8">
        <NuxtLink to="https://www.facebook.com/MajlisAgamaIslamPerlis">
            <div class="w-8 h-8 border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="ri:facebook-fill" class="w-6 h-6" />
            </div>
        </NuxtLink>
        <NuxtLink to="https://www.instagram.com/maips_official/">
            <div class="w-8 h-8 border border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="fa6-brands:instagram" class="w-6 h-6" />
            </div>
        </NuxtLink>
        <NuxtLink to="https://www.tiktok.com/@maips_official">
            <div class="w-8 h-8 border border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="ri:tiktok-fill" class="w-6 h-6" />
            </div>
        </NuxtLink>
        <NuxtLink to="https://www.youtube.com/@maipsofficial6767">
            <div class="w-8 h-8 border border-[2px] border-white rounded-full flex items-center justify-center cursor-pointer">
            <Icon name="ri:youtube-fill" class="w-6 h-6" />
            </div>
        </NuxtLink>
        </div>
      </div>

<div class="bg-[#004C7D] text-white py-6">
  <div class="px-8 flex flex-col justify-evenly items-start gap-4">
    <div class="text-xs leading-6">
      <NuxtLink to="https://www.maips.gov.my/penafian/" class="hover:underline">
        Penafian
      </NuxtLink> |
      <NuxtLink to="https://www.maips.gov.my/dasar-privasi-dan-keselamatan/" class="hover:underline">
        Dasar Privasi & Keselamatan
      </NuxtLink> |
      <NuxtLink to="https://www.maips.gov.my/notis-hak-cipta/" class="hover:underline">
        Notis Hak Cipta
      </NuxtLink>
      <p class="mt-2">Hakcipta Terpelihara © 2024 Majlis Agama Islam dan Adat Istiadat Melayu Perlis (MAIPs).</p>
      <p class="mt-1">Paparan terbaik mengunakan pelayar internet Chrome dengan resolusi minimum 1366x768.</p>
    </div>
    <div class="flex flex-row gap-5 text-xs leading-6">
      <p>Pelawat Hari Ini: <span class="font-bold">121</span></p>
      <p>Jumlah pelawat: <span class="font-bold">222742</span></p>
      <p>Tarikh kemaskini: <span class="font-bold">21/10/24</span></p>
    </div>
  </div>
</div>

          <NuxtImg
      src="https://s3-alpha-sig.figma.com/img/7029/11b9/15fc0f14085a273c51e9c176d1685510?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=ZIfEJ9-nCEZVqkYG9NKkX1yHgn4KNt8Bm2WR6PVjxlaoDexHCcGslMk1MU7Vy-U7hKXo3GnmGXI~JYVJC6tIk5We3wb46GQjkTtgQ0l1dkwU~a7AFPxfyTTtT7P9u6mAa5vtV62QlwvTE2y-GfAe~Wxitde8ZzYmBNHBP74MdRpLlporW9bDznKRpGyEDWsaeiHgAcfsSgGwSi5wFGjcovXT-VYGe6v63L8HMPrezoAUHMfC5DbdATNX5NSmGrkHZhAjs0p-qawrOe66mJvvjsqQaFMRtmmhjFFgWOOVXjOxnHjOX2uNBfqyqWpno~SevMvklmIKb6WoUf3SUSG0xA__"
      alt="Decorative"
      class="w-full"
    />
   </footer>
</template>