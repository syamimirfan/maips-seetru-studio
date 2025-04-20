<script setup>
definePageMeta({
    layout: 'default'
})
const showScrollTop = ref(false);

const handleScroll = () => {
  showScrollTop.value = window.scrollY > 100;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' });
};

// perkembangan
const perkembangan = ref([])
onMounted(async () => {
  const res = await fetch('/perkembangan.json')
  perkembangan.value = await res.json()
})

// aktiviti
const aktiviti = ref([])
onMounted(async () => {
  const res = await fetch('/aktiviti.json')
  aktiviti.value = await res.json()
})

// berita
const berita = ref([])
onMounted(async () => {
  const res = await fetch('/berita.json')
  berita.value = await res.json()
})

// pautan
const showLinks1 = ref(false)
const toggleLinks1 = () => {
  showLinks1.value = !showLinks1.value
}
const showLinks2 = ref(false)
const toggleLinks2 = () => {
  showLinks2.value = !showLinks2.value
}
const showLinks3 = ref(false)
const toggleLinks3 = () => {
  showLinks3.value = !showLinks3.value
}
const pautanMAIPs = ref([])
onMounted(async () => {
  const res = await fetch('/pautanMAIPs.json')
  pautanMAIPs.value = await res.json()
})
const pautanMAIN = ref([])
onMounted(async () => {
  const res = await fetch('/pautanMAIN.json')
  pautanMAIN.value = await res.json()
}) 
const pautanAgensi = ref([])
onMounted(async () => {
  const res = await fetch('/pautanAgensi.json')
  pautanAgensi.value = await res.json()
}) 
</script>

<template>
  <!-- Hero Section  (Desktop - Small And Large)-->
<section class="relative pb-20 overflow-hidden hidden lg:block xl:block 2xl:block">
  <NuxtImg
    src="/hero-section.jpeg"
    alt="MAIPs Background"
    class="absolute inset-0 w-full h-full object-cover brightness-75" />

    <!-- Sticky Icons (Right Edge) -->
    <!-- Sticky Icon Column (Already Present) -->
    <div class="fixed top-1/4 right-0 flex flex-col items-center space-y-4 z-50">
      <div class="bg-[#0054A5] rounded-tl-xl rounded-bl-xl shadow-lg border-none overflow-hidden cursor-pointer">
        <div class="p-3 w-full hover:bg-[#00395E] flex justify-center border-b border-white">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="20" viewBox="0 0 20 24" fill="none"><g id="Group"><path id="Vector" d="M11.9892 1.40625C11.6988 0.587766 10.9167 0 10 0C9.08331 0 8.30125 0.587766 8.01077 1.40625H5.78125C5.39261 1.40625 5.07812 1.72073 5.07812 2.10938V3.51562C5.07812 3.90427 5.39261 4.21875 5.78125 4.21875H14.2188C14.6074 4.21875 14.9219 3.90427 14.9219 3.51562V2.10938C14.9219 1.72073 14.6074 1.40625 14.2188 1.40625H11.9892Z" fill="white"></path><path id="Vector_2" d="M8.59375 16.9219C10.5354 16.9219 12.1094 15.3479 12.1094 13.4062C12.1094 11.4646 10.5354 9.89062 8.59375 9.89062C6.65212 9.89062 5.07812 11.4646 5.07812 13.4062C5.07812 15.3479 6.65212 16.9219 8.59375 16.9219Z" fill="white"></path><path id="Vector_3" d="M0.859375 23.2969C0.859375 23.6855 1.17386 24 1.5625 24H18.4375C18.8261 24 19.1406 23.6855 19.1406 23.2969V3.51562C19.1406 3.12698 18.8261 2.8125 18.4375 2.8125H16.3281V3.51562C16.3281 4.67878 15.3819 5.625 14.2188 5.625H5.78125C4.61809 5.625 3.67188 4.67878 3.67188 3.51562V2.8125H1.5625C1.17386 2.8125 0.859375 3.12698 0.859375 3.51562V23.2969ZM8.59375 8.48438C11.3074 8.48438 13.5156 10.6926 13.5156 13.4062C13.5156 14.5095 13.1374 15.5184 12.5219 16.3401L16.1221 19.9403C16.3968 20.215 16.3968 20.66 16.1221 20.9346C15.8475 21.2093 15.4025 21.2093 15.1278 20.9346L11.5276 17.3344C10.7059 17.9499 9.697 18.3281 8.59375 18.3281C5.88011 18.3281 3.67188 16.1199 3.67188 13.4062C3.67188 10.6926 5.88011 8.48438 8.59375 8.48438Z" fill="white"></path></g></svg>        </div>
        <div class="p-3 w-full hover:bg-[#00395E] flex justify-center border-b border-white">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="20" viewBox="0 0 24 24" fill="none"><g id="writing 1"><g id="Group"><path id="Vector" d="M22.4146 7.58359C21.9011 7.06965 21.0847 7.03735 20.5326 7.48721C20.4527 7.55227 20.5146 7.49494 19.299 8.71055L22.4544 11.866L23.5884 10.7461C24.1367 10.1979 24.1367 9.30573 23.5884 8.75738L22.4146 7.58359Z" fill="white"></path><path id="Vector_2" d="M12.8281 15.2413L10.972 19.2189C10.847 19.4869 10.9029 19.8043 11.112 20.0134C11.321 20.2225 11.6386 20.2784 11.9065 20.1534L15.884 18.2972C16.0414 18.2237 15.565 18.6696 21.4538 12.8543L18.3046 9.70508C12.4659 15.5438 12.903 15.0809 12.8281 15.2413Z" fill="white"></path><path id="Vector_3" d="M17.0686 19.1611C16.8964 19.3312 16.6979 19.4692 16.4787 19.5715L12.5012 21.4277C11.719 21.7927 10.7635 21.6538 10.1177 21.0078C9.49277 20.383 9.32398 19.4251 9.69766 18.6242L11.5539 14.6466C11.6581 14.4232 11.7994 14.2215 11.9737 14.0472L17.9534 8.06747V2.10938C17.9534 0.946266 17.0072 0 15.8441 0H2.10968C0.946571 0 0.000305176 0.946266 0.000305176 2.10938V21.8906C0.000305176 23.0537 0.946571 24 2.10968 24H15.8441C17.0072 24 17.9534 23.0537 17.9534 21.8906V18.2873L17.0686 19.1611ZM3.75035 4.54688H14.2504C14.6387 4.54688 14.9535 4.86169 14.9535 5.25C14.9535 5.63831 14.6387 5.95312 14.2504 5.95312H3.75035C3.36204 5.95312 3.04723 5.63831 3.04723 5.25C3.04723 4.86169 3.36204 4.54688 3.75035 4.54688ZM3.75035 8.29688H12.0004C12.3887 8.29688 12.7035 8.61169 12.7035 9C12.7035 9.38831 12.3887 9.70312 12.0004 9.70312H3.75035C3.36204 9.70312 3.04723 9.38831 3.04723 9C3.04723 8.61169 3.36204 8.29688 3.75035 8.29688ZM3.04723 12.75C3.04723 12.3617 3.36204 12.0469 3.75035 12.0469H9.75035C10.1387 12.0469 10.4535 12.3617 10.4535 12.75C10.4535 13.1383 10.1387 13.4531 9.75035 13.4531H3.75035C3.36204 13.4531 3.04723 13.1383 3.04723 12.75Z" fill="white"></path></g></g></svg>        </div>
        <div class="p-3 w-full hover:bg-[#00395E] flex justify-center">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="20" viewBox="0 0 24 24" fill="none"><g id="Donation"><path id="Vector" d="M2.51817 12.0569C2.55425 13.0492 2.59935 14.1497 2.63541 15.1419C3.29958 14.7913 4.03222 14.5896 4.78229 14.5511C5.03035 12.8327 5.4047 11.0737 7.38019 9.83786C8.37695 9.21094 9.68492 10.5189 9.73454 11.2721C9.77964 12.0073 8.02064 13.3874 6.85249 14.8803C6.65898 15.1243 6.48121 15.3804 6.32028 15.6471C6.16031 15.9076 6.03163 16.1862 5.93691 16.4769C5.77847 16.9335 5.80602 17.4341 6.01359 17.8706C6.16242 18.1683 6.7262 17.9337 7.49745 17.4286C7.72748 17.2798 7.98005 17.1039 8.24615 16.9099C8.47618 16.7385 8.71973 16.5581 8.96779 16.3642C9.60825 15.8726 10.2893 15.3223 10.9433 14.8036C12.0844 13.8971 15.237 12.7154 17.7718 10.0363L14.0057 4.01514C13.8148 4.0669 13.6171 4.08971 13.4194 4.08279C11.3695 3.98766 9.31542 4.03438 7.27194 4.22261C6.88104 4.23797 6.5091 4.39509 6.22557 4.66461C4.59739 6.42812 2.43248 9.61686 2.51817 12.0569Z" fill="white"></path><path id="Vector_2" d="M14.5425 3.1717L14.7996 3.58664L18.3897 9.33269L18.6017 9.67096C18.655 9.75646 18.7252 9.83023 18.8079 9.88778C18.8907 9.94532 18.9842 9.98543 19.0829 10.0057C19.1817 10.0259 19.2835 10.0259 19.3822 10.0056C19.4809 9.98524 19.5744 9.94506 19.6571 9.88745L23.1435 7.47898C23.1913 7.44563 23.2244 7.39525 23.2362 7.33821C23.2479 7.28116 23.2374 7.22178 23.2067 7.17228L18.6558 0.104732C18.6407 0.0801364 18.6209 0.0587573 18.5976 0.0418168C18.5742 0.0248762 18.5478 0.0127066 18.5197 0.00600432C18.4916 -0.000698014 18.4625 -0.00180182 18.434 0.00275619C18.4055 0.00731419 18.3782 0.0174446 18.3536 0.0325679L14.7951 2.13434C14.7095 2.18505 14.6349 2.25235 14.5757 2.33229C14.5165 2.41223 14.4739 2.5032 14.4504 2.59984C14.4268 2.69649 14.4229 2.79687 14.4387 2.89507C14.4545 2.99328 14.4898 3.08733 14.5425 3.1717Z" fill="white"></path><path id="Vector_3" d="M0.759212 19.7242C0.759212 20.8582 1.20969 21.9458 2.01154 22.7476C2.81339 23.5495 3.90093 24 5.03492 24C6.16891 24 7.25646 23.5495 8.05831 22.7476C8.86016 21.9458 9.31063 20.8582 9.31063 19.7242C9.31363 18.9968 9.12543 18.2813 8.76489 17.6495C7.53131 18.5394 6.68729 19.0526 5.92795 18.8628C4.90234 18.5883 4.5949 16.9051 5.39123 15.4666C4.80201 15.4172 4.20896 15.4906 3.64956 15.6822C3.09016 15.8737 2.57657 16.1792 2.14125 16.5793C1.70593 16.9795 1.35835 17.4656 1.12046 18.0069C0.882581 18.5482 0.759573 19.133 0.759212 19.7242Z" fill="white"></path></g></svg>        </div>
      </div>

      <div class="bg-[#FDF600] text-[#00395E] rounded-tl-xl rounded-bl-xl p-3 shadow-lg flex justify-center cursor-pointer">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" fill="currentColor" width="1em">
						<title>Accessibility Tools</title>
						<path d="M50 .8c5.7 0 10.4 4.7 10.4 10.4S55.7 21.6 50 21.6s-10.4-4.7-10.4-10.4S44.3.8 50 .8zM92.2 32l-21.9 2.3c-2.6.3-4.6 2.5-4.6 5.2V94c0 2.9-2.3 5.2-5.2 5.2H60c-2.7 0-4.9-2.1-5.2-4.7l-2.2-24.7c-.1-1.5-1.4-2.5-2.8-2.4-1.3.1-2.2 1.1-2.4 2.4l-2.2 24.7c-.2 2.7-2.5 4.7-5.2 4.7h-.5c-2.9 0-5.2-2.3-5.2-5.2V39.4c0-2.7-2-4.9-4.6-5.2L7.8 32c-2.6-.3-4.6-2.5-4.6-5.2v-.5c0-2.6 2.1-4.7 4.7-4.7h.5c19.3 1.8 33.2 2.8 41.7 2.8s22.4-.9 41.7-2.8c2.6-.2 4.9 1.6 5.2 4.3v1c-.1 2.6-2.1 4.8-4.8 5.1z"></path>					</svg>      </div>
    </div>

        <!-- Scroll to Top Button -->
        <NuxtButton 
          v-show="showScrollTop"
          @click="scrollToTop"
          class="fixed bottom-48 right-16 bg-[#0054A5] rounded-[10px] p-3 shadow-xl z-50 transition flex cursor-pointer">
          <Icon name="heroicons:arrow-up" class="w-5 h-5 text-white" />
        </NuxtButton>

        <!-- Sticky Image Below Scroll Button -->
        <div class="fixed bottom-4 right-8 z-50 cursor-pointer">
            <NuxtLink to="">
                <NuxtImg
                src="/chat-ai.png"
                alt="Sticky Image"
                class="w-42 h-32 object-contain"
            />
            </NuxtLink>
        </div>

  <div class="relative max-w-6xl mx-auto pt-28 text-white"> 
    <h1 class="text-4xl md:text-6xl font-bold leading-tight text-left">
      Selamat Datang Ke<br />
      Laman Web Rasmi MAIPs
    </h1>
    <p class="mt-6 text-xl pt-2 text-left">
      Dapatkan maklumat terkini mengenai MAIPs. Bersama kita membina masyarakat
      <br /> yang sejahtera, berlandaskan syariat Islam.
    </p>
  </div>

    <div class="mt-20 flex justify-around">
    <!-- Carousel Container -->
    <div class="relative md:w-2/3"> <!-- Centered carousel -->
        <!-- Carousel Items -->
        <div class="mt-10 grid grid-cols-2 md:grid-cols-5 gap-4 text-sm font-medium">
        <NuxtButton class="group relative bg-transparent text-[#FDF600]  rounded-lg text-base text-left cursor-pointer ">
            Laman Web Rasmi
            <span class="absolute bottom-0 left-0 w-full h-[2px] bg-[#FDF600] group-hover:bg-white transition-all duration-300"></span>
        </NuxtButton>
        <NuxtButton class="group relative bg-transparent text-gray-400 hover:text-white rounded-lg text-base text-left leading-none cursor-pointer">
            Zakat
            <span class="absolute bottom-0 left-0 w-full h-[2px] bg-gray-400 group-hover:bg-white transition-all duration-300"></span>
        </NuxtButton>
        <NuxtButton class="group relative bg-transparent text-gray-400 hover:text-white rounded-lg text-base text-left leading-none cursor-pointer">
            Wakaf Tunai
            <span class="absolute bottom-0 left-0 w-full h-[2px] bg-gray-400 group-hover:bg-white transition-all duration-300"></span>
        </NuxtButton>
        <NuxtButton class="group relative bg-transparent text-gray-400 hover:text-white rounded-lg text-base text-left leading-none cursor-pointer">
            Premis untuk Disewa
            <span class="absolute bottom-0 left-0 w-full h-[2px] bg-gray-400 group-hover:bg-white transition-all duration-300"></span>
        </NuxtButton>
        <NuxtButton class="group relative bg-transparent text-gray-400 hover:text-white rounded-lg text-base text-left leading-none cursor-pointer">
            Tahun Melawat Perlis
            <span class="absolute bottom-0 left-0 w-full h-[2px] bg-gray-400 group-hover:bg-white transition-all duration-300"></span>
        </NuxtButton>
        </div>

    <!-- Navigation Arrows positioned at the left and right ends -->
    <NuxtButton class="absolute top-3/4 left-[-70px] z-30 flex items-center justify-center h-12 w-12 -translate-y-1/2 cursor-pointer">
    <span class="inline-flex items-center justify-center w-10 h-10 rounded-[10px] bg-transparent border-[1px]">
        <Icon name="mdi:chevron-left" class="w-6 h-6 text-white" />
    </span>
    </NuxtButton>
    <NuxtButton class="absolute top-3/4 right-[-70px] z-30 flex items-center justify-center h-12 w-12 -translate-y-1/2 cursor-pointer">
    <span class="inline-flex items-center justify-center w-10 h-10 rounded-[10px] bg-transparent border-[1px]">
        <Icon name="mdi:chevron-right" class="w-6 h-6 text-white" />
    </span>
    </NuxtButton>
    </div>
    </div>
    <div class="absolute bottom-0 left-0 right-0 w-full bg-[#00395E] text-sm text-white flex items-center">
        <div class="bg-[#FDF600] text-black px-4 py-2 font-bold whitespace-nowrap">
            Pengumuman
        </div>

        <div class="flex-1 px-4 py-2 text-center truncate">
            Waktu Operasi Kaunter MAIPs: (Isnin-Khamis) Pagi 08:30am - 01:00pm, Rehat 01:00pm - 02:00pm, Petang 02:00pm - 04:30pm (Jumaat) Pagi...
        </div>

        <NuxtButton class="px-4 py-2 flex items-center gap-2 bg-[#00395E] text-white whitespace-nowrap cursor-pointer">
            <span>Baca Lagi</span>
            <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
        </NuxtButton>

        <div class="px-4 py-2 flex items-center gap-2 whitespace-nowrap">
            <NuxtButton class="flex justify-center cursor-pointer">
                <Icon name="mdi:chevron-left" class="w-5 h-5" />
            </NuxtButton>
            <span><span class="font-bold">1</span> / 3</span>
            <NuxtButton class="flex justify-center cursor-pointer">
            <Icon name="mdi:chevron-right" class="w-5 h-5" />
            </NuxtButton>
        </div>
    </div>
</section>

  <!-- Hero Section  (Tablet)-->
<section class="relative md:h-[600px] overflow-hidden hidden md:block lg:hidden xl:hidden 2xl:hidden">
  <NuxtImg
    src="/hero-section-tablet.jpeg"
    alt="MAIPs Background"
    class="absolute inset-0 w-full h-full object-cover brightness-75"
     />

    <!-- Sticky Icons (Right Edge) -->
    <!-- Sticky Icon Column (Already Present) -->
    <div class="fixed top-1/4 right-0 flex flex-col items-center space-y-4 z-50">
      <div class="bg-[#0054A5] rounded-tl-xl rounded-bl-xl shadow-lg border-none overflow-hidden cursor-pointer">
        <div class="p-3 w-full hover:bg-[#00395E] flex justify-center border-b border-white">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="20" viewBox="0 0 20 24" fill="none"><g id="Group"><path id="Vector" d="M11.9892 1.40625C11.6988 0.587766 10.9167 0 10 0C9.08331 0 8.30125 0.587766 8.01077 1.40625H5.78125C5.39261 1.40625 5.07812 1.72073 5.07812 2.10938V3.51562C5.07812 3.90427 5.39261 4.21875 5.78125 4.21875H14.2188C14.6074 4.21875 14.9219 3.90427 14.9219 3.51562V2.10938C14.9219 1.72073 14.6074 1.40625 14.2188 1.40625H11.9892Z" fill="white"></path><path id="Vector_2" d="M8.59375 16.9219C10.5354 16.9219 12.1094 15.3479 12.1094 13.4062C12.1094 11.4646 10.5354 9.89062 8.59375 9.89062C6.65212 9.89062 5.07812 11.4646 5.07812 13.4062C5.07812 15.3479 6.65212 16.9219 8.59375 16.9219Z" fill="white"></path><path id="Vector_3" d="M0.859375 23.2969C0.859375 23.6855 1.17386 24 1.5625 24H18.4375C18.8261 24 19.1406 23.6855 19.1406 23.2969V3.51562C19.1406 3.12698 18.8261 2.8125 18.4375 2.8125H16.3281V3.51562C16.3281 4.67878 15.3819 5.625 14.2188 5.625H5.78125C4.61809 5.625 3.67188 4.67878 3.67188 3.51562V2.8125H1.5625C1.17386 2.8125 0.859375 3.12698 0.859375 3.51562V23.2969ZM8.59375 8.48438C11.3074 8.48438 13.5156 10.6926 13.5156 13.4062C13.5156 14.5095 13.1374 15.5184 12.5219 16.3401L16.1221 19.9403C16.3968 20.215 16.3968 20.66 16.1221 20.9346C15.8475 21.2093 15.4025 21.2093 15.1278 20.9346L11.5276 17.3344C10.7059 17.9499 9.697 18.3281 8.59375 18.3281C5.88011 18.3281 3.67188 16.1199 3.67188 13.4062C3.67188 10.6926 5.88011 8.48438 8.59375 8.48438Z" fill="white"></path></g></svg>        </div>
        <div class="p-3 w-full hover:bg-[#00395E] flex justify-center border-b border-white">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="20" viewBox="0 0 24 24" fill="none"><g id="writing 1"><g id="Group"><path id="Vector" d="M22.4146 7.58359C21.9011 7.06965 21.0847 7.03735 20.5326 7.48721C20.4527 7.55227 20.5146 7.49494 19.299 8.71055L22.4544 11.866L23.5884 10.7461C24.1367 10.1979 24.1367 9.30573 23.5884 8.75738L22.4146 7.58359Z" fill="white"></path><path id="Vector_2" d="M12.8281 15.2413L10.972 19.2189C10.847 19.4869 10.9029 19.8043 11.112 20.0134C11.321 20.2225 11.6386 20.2784 11.9065 20.1534L15.884 18.2972C16.0414 18.2237 15.565 18.6696 21.4538 12.8543L18.3046 9.70508C12.4659 15.5438 12.903 15.0809 12.8281 15.2413Z" fill="white"></path><path id="Vector_3" d="M17.0686 19.1611C16.8964 19.3312 16.6979 19.4692 16.4787 19.5715L12.5012 21.4277C11.719 21.7927 10.7635 21.6538 10.1177 21.0078C9.49277 20.383 9.32398 19.4251 9.69766 18.6242L11.5539 14.6466C11.6581 14.4232 11.7994 14.2215 11.9737 14.0472L17.9534 8.06747V2.10938C17.9534 0.946266 17.0072 0 15.8441 0H2.10968C0.946571 0 0.000305176 0.946266 0.000305176 2.10938V21.8906C0.000305176 23.0537 0.946571 24 2.10968 24H15.8441C17.0072 24 17.9534 23.0537 17.9534 21.8906V18.2873L17.0686 19.1611ZM3.75035 4.54688H14.2504C14.6387 4.54688 14.9535 4.86169 14.9535 5.25C14.9535 5.63831 14.6387 5.95312 14.2504 5.95312H3.75035C3.36204 5.95312 3.04723 5.63831 3.04723 5.25C3.04723 4.86169 3.36204 4.54688 3.75035 4.54688ZM3.75035 8.29688H12.0004C12.3887 8.29688 12.7035 8.61169 12.7035 9C12.7035 9.38831 12.3887 9.70312 12.0004 9.70312H3.75035C3.36204 9.70312 3.04723 9.38831 3.04723 9C3.04723 8.61169 3.36204 8.29688 3.75035 8.29688ZM3.04723 12.75C3.04723 12.3617 3.36204 12.0469 3.75035 12.0469H9.75035C10.1387 12.0469 10.4535 12.3617 10.4535 12.75C10.4535 13.1383 10.1387 13.4531 9.75035 13.4531H3.75035C3.36204 13.4531 3.04723 13.1383 3.04723 12.75Z" fill="white"></path></g></g></svg>        </div>
        <div class="p-3 w-full hover:bg-[#00395E] flex justify-center">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="20" viewBox="0 0 24 24" fill="none"><g id="Donation"><path id="Vector" d="M2.51817 12.0569C2.55425 13.0492 2.59935 14.1497 2.63541 15.1419C3.29958 14.7913 4.03222 14.5896 4.78229 14.5511C5.03035 12.8327 5.4047 11.0737 7.38019 9.83786C8.37695 9.21094 9.68492 10.5189 9.73454 11.2721C9.77964 12.0073 8.02064 13.3874 6.85249 14.8803C6.65898 15.1243 6.48121 15.3804 6.32028 15.6471C6.16031 15.9076 6.03163 16.1862 5.93691 16.4769C5.77847 16.9335 5.80602 17.4341 6.01359 17.8706C6.16242 18.1683 6.7262 17.9337 7.49745 17.4286C7.72748 17.2798 7.98005 17.1039 8.24615 16.9099C8.47618 16.7385 8.71973 16.5581 8.96779 16.3642C9.60825 15.8726 10.2893 15.3223 10.9433 14.8036C12.0844 13.8971 15.237 12.7154 17.7718 10.0363L14.0057 4.01514C13.8148 4.0669 13.6171 4.08971 13.4194 4.08279C11.3695 3.98766 9.31542 4.03438 7.27194 4.22261C6.88104 4.23797 6.5091 4.39509 6.22557 4.66461C4.59739 6.42812 2.43248 9.61686 2.51817 12.0569Z" fill="white"></path><path id="Vector_2" d="M14.5425 3.1717L14.7996 3.58664L18.3897 9.33269L18.6017 9.67096C18.655 9.75646 18.7252 9.83023 18.8079 9.88778C18.8907 9.94532 18.9842 9.98543 19.0829 10.0057C19.1817 10.0259 19.2835 10.0259 19.3822 10.0056C19.4809 9.98524 19.5744 9.94506 19.6571 9.88745L23.1435 7.47898C23.1913 7.44563 23.2244 7.39525 23.2362 7.33821C23.2479 7.28116 23.2374 7.22178 23.2067 7.17228L18.6558 0.104732C18.6407 0.0801364 18.6209 0.0587573 18.5976 0.0418168C18.5742 0.0248762 18.5478 0.0127066 18.5197 0.00600432C18.4916 -0.000698014 18.4625 -0.00180182 18.434 0.00275619C18.4055 0.00731419 18.3782 0.0174446 18.3536 0.0325679L14.7951 2.13434C14.7095 2.18505 14.6349 2.25235 14.5757 2.33229C14.5165 2.41223 14.4739 2.5032 14.4504 2.59984C14.4268 2.69649 14.4229 2.79687 14.4387 2.89507C14.4545 2.99328 14.4898 3.08733 14.5425 3.1717Z" fill="white"></path><path id="Vector_3" d="M0.759212 19.7242C0.759212 20.8582 1.20969 21.9458 2.01154 22.7476C2.81339 23.5495 3.90093 24 5.03492 24C6.16891 24 7.25646 23.5495 8.05831 22.7476C8.86016 21.9458 9.31063 20.8582 9.31063 19.7242C9.31363 18.9968 9.12543 18.2813 8.76489 17.6495C7.53131 18.5394 6.68729 19.0526 5.92795 18.8628C4.90234 18.5883 4.5949 16.9051 5.39123 15.4666C4.80201 15.4172 4.20896 15.4906 3.64956 15.6822C3.09016 15.8737 2.57657 16.1792 2.14125 16.5793C1.70593 16.9795 1.35835 17.4656 1.12046 18.0069C0.882581 18.5482 0.759573 19.133 0.759212 19.7242Z" fill="white"></path></g></svg>        </div>
      </div>

      <div class="bg-[#FDF600] text-[#00395E] rounded-tl-xl rounded-bl-xl p-3 shadow-lg flex justify-center cursor-pointer">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" fill="currentColor" width="1em">
						<title>Accessibility Tools</title>
						<path d="M50 .8c5.7 0 10.4 4.7 10.4 10.4S55.7 21.6 50 21.6s-10.4-4.7-10.4-10.4S44.3.8 50 .8zM92.2 32l-21.9 2.3c-2.6.3-4.6 2.5-4.6 5.2V94c0 2.9-2.3 5.2-5.2 5.2H60c-2.7 0-4.9-2.1-5.2-4.7l-2.2-24.7c-.1-1.5-1.4-2.5-2.8-2.4-1.3.1-2.2 1.1-2.4 2.4l-2.2 24.7c-.2 2.7-2.5 4.7-5.2 4.7h-.5c-2.9 0-5.2-2.3-5.2-5.2V39.4c0-2.7-2-4.9-4.6-5.2L7.8 32c-2.6-.3-4.6-2.5-4.6-5.2v-.5c0-2.6 2.1-4.7 4.7-4.7h.5c19.3 1.8 33.2 2.8 41.7 2.8s22.4-.9 41.7-2.8c2.6-.2 4.9 1.6 5.2 4.3v1c-.1 2.6-2.1 4.8-4.8 5.1z"></path>					</svg>      </div>
    </div>

        <!-- Scroll to Top Button -->
        <NuxtButton 
          v-show="showScrollTop"
          @click="scrollToTop"
          class="fixed bottom-48 right-16 bg-[#0054A5] rounded-[10px] p-3 shadow-xl z-50 transition flex cursor-pointer">
          <Icon name="heroicons:arrow-up" class="w-5 h-5 text-white" />
        </NuxtButton>

        <!-- Sticky Image Below Scroll Button -->
        <div class="fixed bottom-4 right-8 z-50 cursor-pointer">
            <NuxtLink to="">
                <NuxtImg
                src="/chat-ai.png"
                alt="Sticky Image"
                class="w-42 h-32 object-contain"
            />
            </NuxtLink>
        </div>

      <div class="absolute top-1/2 left-6 md:left-16 transform -translate-y-1/2 text-white flex flex-col items-start text-left px-4 md:px-0 z-10">
        <h1 class="text-2xl sm:text-4xl md:text-5xl lg:text-6xl font-bold leading-snug md:leading-tight">
          Selamat Datang Ke<br />
          Laman Web Rasmi <br />
          MAIPs
        </h1>
        <p class="mt-4 md:mt-6 text-base g md:text-xl text-white max-w-2xl text-xs">
          Dapatkan maklumat terkini mengenai MAIPs. Bersama kita membina masyarakat yang sejahtera, berlandaskan syariat Islam.
        </p>
      </div>


            <!-- Carousel Container -->
          <div class="absolute bottom-0 left-0 w-full max-w-7xl px-4 pb-10">
            <!-- Carousel Items In Circular-->
            <div class="flex space-x-3 z-10 justify-center pb-7">
              <div class="w-3 h-3 rounded-full bg-white"></div>
              <div class="w-3 h-3 rounded-full bg-gray-400"></div>
              <div class="w-3 h-3 rounded-full bg-gray-400"></div>
              <div class="w-3 h-3 rounded-full bg-gray-400"></div>  
              <div class="w-3 h-3 rounded-full bg-gray-400"></div>
            </div>

            <!-- Navigation Arrows at the very left and right, positioned at the bottom -->
            <NuxtButton class="absolute left-2 bottom-14 z-30 flex items-center justify-center h-10 w-10 rounded-[10px] bg-transparent border-[1px]">
              <Icon name="mdi:chevron-left" class="w-6 h-6 text-white" />
            </NuxtButton>
            <NuxtButton class="absolute right-2 bottom-14 z-30 flex items-center justify-center h-10 w-10 rrounded-[10px] bg-transparent border-[1px]">
              <Icon name="mdi:chevron-right" class="w-6 h-6 text-white" />
            </NuxtButton>
          </div>

    <div class="absolute bottom-0 left-0 right-0 w-full bg-[#00395E] text-sm text-white flex items-center">
        <div class="flex-1 px-4 py-2 text-center truncate">
            Waktu Operasi Kaunter MAIPs: (Isnin-Khamis) Pagi 08:30am - 01:00pm, Rehat 01:00pm - 02:00pm, Petang 02:00pm - 04:30pm (Jumaat) Pagi...
        </div>

        <NuxtButton class="px-4 py-2 flex items-center gap-2 bg-[#00395E] text-white whitespace-nowrap cursor-pointer">
            <span>Baca Lagi</span>
            <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
        </NuxtButton>

        <div class="px-4 py-2 flex items-center gap-2 whitespace-nowrap">
            <NuxtButton class="flex justify-center cursor-pointer">
                <Icon name="mdi:chevron-left" class="w-5 h-5" />
            </NuxtButton>
            <span><span class="font-bold">1</span> / 3</span>
            <NuxtButton class="flex justify-center cursor-pointer">
            <Icon name="mdi:chevron-right" class="w-5 h-5" />
            </NuxtButton>
        </div>
    </div>
</section>

  <!-- Hero Section  (Phone)-->
<section class="relative h-[500px] w overflow-hidden block md:hidden lg:hidden xl:hidden 2xl:hidden">
  <NuxtImg
    src="/hero-section-phone.jpeg"
    alt="MAIPs Background"
    class="absolute inset-0 w-full h-full object-cover brightness-75"
     />

    <!-- Sticky Icons (Right Edge) -->
    <!-- Sticky Icon Column (Already Present) -->
    <div class="fixed top-1/4 right-0 flex flex-col items-center space-y-4 z-50">
      <div class="bg-[#0054A5] rounded-tl-xl rounded-bl-xl shadow-lg border-none overflow-hidden cursor-pointer">
        <div class="p-3 w-full hover:bg-[#00395E] flex justify-center border-b border-white">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="20" viewBox="0 0 20 24" fill="none"><g id="Group"><path id="Vector" d="M11.9892 1.40625C11.6988 0.587766 10.9167 0 10 0C9.08331 0 8.30125 0.587766 8.01077 1.40625H5.78125C5.39261 1.40625 5.07812 1.72073 5.07812 2.10938V3.51562C5.07812 3.90427 5.39261 4.21875 5.78125 4.21875H14.2188C14.6074 4.21875 14.9219 3.90427 14.9219 3.51562V2.10938C14.9219 1.72073 14.6074 1.40625 14.2188 1.40625H11.9892Z" fill="white"></path><path id="Vector_2" d="M8.59375 16.9219C10.5354 16.9219 12.1094 15.3479 12.1094 13.4062C12.1094 11.4646 10.5354 9.89062 8.59375 9.89062C6.65212 9.89062 5.07812 11.4646 5.07812 13.4062C5.07812 15.3479 6.65212 16.9219 8.59375 16.9219Z" fill="white"></path><path id="Vector_3" d="M0.859375 23.2969C0.859375 23.6855 1.17386 24 1.5625 24H18.4375C18.8261 24 19.1406 23.6855 19.1406 23.2969V3.51562C19.1406 3.12698 18.8261 2.8125 18.4375 2.8125H16.3281V3.51562C16.3281 4.67878 15.3819 5.625 14.2188 5.625H5.78125C4.61809 5.625 3.67188 4.67878 3.67188 3.51562V2.8125H1.5625C1.17386 2.8125 0.859375 3.12698 0.859375 3.51562V23.2969ZM8.59375 8.48438C11.3074 8.48438 13.5156 10.6926 13.5156 13.4062C13.5156 14.5095 13.1374 15.5184 12.5219 16.3401L16.1221 19.9403C16.3968 20.215 16.3968 20.66 16.1221 20.9346C15.8475 21.2093 15.4025 21.2093 15.1278 20.9346L11.5276 17.3344C10.7059 17.9499 9.697 18.3281 8.59375 18.3281C5.88011 18.3281 3.67188 16.1199 3.67188 13.4062C3.67188 10.6926 5.88011 8.48438 8.59375 8.48438Z" fill="white"></path></g></svg>        </div>
        <div class="p-3 w-full hover:bg-[#00395E] flex justify-center border-b border-white">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="20" viewBox="0 0 24 24" fill="none"><g id="writing 1"><g id="Group"><path id="Vector" d="M22.4146 7.58359C21.9011 7.06965 21.0847 7.03735 20.5326 7.48721C20.4527 7.55227 20.5146 7.49494 19.299 8.71055L22.4544 11.866L23.5884 10.7461C24.1367 10.1979 24.1367 9.30573 23.5884 8.75738L22.4146 7.58359Z" fill="white"></path><path id="Vector_2" d="M12.8281 15.2413L10.972 19.2189C10.847 19.4869 10.9029 19.8043 11.112 20.0134C11.321 20.2225 11.6386 20.2784 11.9065 20.1534L15.884 18.2972C16.0414 18.2237 15.565 18.6696 21.4538 12.8543L18.3046 9.70508C12.4659 15.5438 12.903 15.0809 12.8281 15.2413Z" fill="white"></path><path id="Vector_3" d="M17.0686 19.1611C16.8964 19.3312 16.6979 19.4692 16.4787 19.5715L12.5012 21.4277C11.719 21.7927 10.7635 21.6538 10.1177 21.0078C9.49277 20.383 9.32398 19.4251 9.69766 18.6242L11.5539 14.6466C11.6581 14.4232 11.7994 14.2215 11.9737 14.0472L17.9534 8.06747V2.10938C17.9534 0.946266 17.0072 0 15.8441 0H2.10968C0.946571 0 0.000305176 0.946266 0.000305176 2.10938V21.8906C0.000305176 23.0537 0.946571 24 2.10968 24H15.8441C17.0072 24 17.9534 23.0537 17.9534 21.8906V18.2873L17.0686 19.1611ZM3.75035 4.54688H14.2504C14.6387 4.54688 14.9535 4.86169 14.9535 5.25C14.9535 5.63831 14.6387 5.95312 14.2504 5.95312H3.75035C3.36204 5.95312 3.04723 5.63831 3.04723 5.25C3.04723 4.86169 3.36204 4.54688 3.75035 4.54688ZM3.75035 8.29688H12.0004C12.3887 8.29688 12.7035 8.61169 12.7035 9C12.7035 9.38831 12.3887 9.70312 12.0004 9.70312H3.75035C3.36204 9.70312 3.04723 9.38831 3.04723 9C3.04723 8.61169 3.36204 8.29688 3.75035 8.29688ZM3.04723 12.75C3.04723 12.3617 3.36204 12.0469 3.75035 12.0469H9.75035C10.1387 12.0469 10.4535 12.3617 10.4535 12.75C10.4535 13.1383 10.1387 13.4531 9.75035 13.4531H3.75035C3.36204 13.4531 3.04723 13.1383 3.04723 12.75Z" fill="white"></path></g></g></svg>        </div>
        <div class="p-3 w-full hover:bg-[#00395E] flex justify-center">
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="20" viewBox="0 0 24 24" fill="none"><g id="Donation"><path id="Vector" d="M2.51817 12.0569C2.55425 13.0492 2.59935 14.1497 2.63541 15.1419C3.29958 14.7913 4.03222 14.5896 4.78229 14.5511C5.03035 12.8327 5.4047 11.0737 7.38019 9.83786C8.37695 9.21094 9.68492 10.5189 9.73454 11.2721C9.77964 12.0073 8.02064 13.3874 6.85249 14.8803C6.65898 15.1243 6.48121 15.3804 6.32028 15.6471C6.16031 15.9076 6.03163 16.1862 5.93691 16.4769C5.77847 16.9335 5.80602 17.4341 6.01359 17.8706C6.16242 18.1683 6.7262 17.9337 7.49745 17.4286C7.72748 17.2798 7.98005 17.1039 8.24615 16.9099C8.47618 16.7385 8.71973 16.5581 8.96779 16.3642C9.60825 15.8726 10.2893 15.3223 10.9433 14.8036C12.0844 13.8971 15.237 12.7154 17.7718 10.0363L14.0057 4.01514C13.8148 4.0669 13.6171 4.08971 13.4194 4.08279C11.3695 3.98766 9.31542 4.03438 7.27194 4.22261C6.88104 4.23797 6.5091 4.39509 6.22557 4.66461C4.59739 6.42812 2.43248 9.61686 2.51817 12.0569Z" fill="white"></path><path id="Vector_2" d="M14.5425 3.1717L14.7996 3.58664L18.3897 9.33269L18.6017 9.67096C18.655 9.75646 18.7252 9.83023 18.8079 9.88778C18.8907 9.94532 18.9842 9.98543 19.0829 10.0057C19.1817 10.0259 19.2835 10.0259 19.3822 10.0056C19.4809 9.98524 19.5744 9.94506 19.6571 9.88745L23.1435 7.47898C23.1913 7.44563 23.2244 7.39525 23.2362 7.33821C23.2479 7.28116 23.2374 7.22178 23.2067 7.17228L18.6558 0.104732C18.6407 0.0801364 18.6209 0.0587573 18.5976 0.0418168C18.5742 0.0248762 18.5478 0.0127066 18.5197 0.00600432C18.4916 -0.000698014 18.4625 -0.00180182 18.434 0.00275619C18.4055 0.00731419 18.3782 0.0174446 18.3536 0.0325679L14.7951 2.13434C14.7095 2.18505 14.6349 2.25235 14.5757 2.33229C14.5165 2.41223 14.4739 2.5032 14.4504 2.59984C14.4268 2.69649 14.4229 2.79687 14.4387 2.89507C14.4545 2.99328 14.4898 3.08733 14.5425 3.1717Z" fill="white"></path><path id="Vector_3" d="M0.759212 19.7242C0.759212 20.8582 1.20969 21.9458 2.01154 22.7476C2.81339 23.5495 3.90093 24 5.03492 24C6.16891 24 7.25646 23.5495 8.05831 22.7476C8.86016 21.9458 9.31063 20.8582 9.31063 19.7242C9.31363 18.9968 9.12543 18.2813 8.76489 17.6495C7.53131 18.5394 6.68729 19.0526 5.92795 18.8628C4.90234 18.5883 4.5949 16.9051 5.39123 15.4666C4.80201 15.4172 4.20896 15.4906 3.64956 15.6822C3.09016 15.8737 2.57657 16.1792 2.14125 16.5793C1.70593 16.9795 1.35835 17.4656 1.12046 18.0069C0.882581 18.5482 0.759573 19.133 0.759212 19.7242Z" fill="white"></path></g></svg>        </div>
      </div>

      <div class="bg-[#FDF600] text-[#00395E] rounded-tl-xl rounded-bl-xl p-3 shadow-lg flex justify-center cursor-pointer">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" fill="currentColor" width="1em">
						<title>Accessibility Tools</title>
						<path d="M50 .8c5.7 0 10.4 4.7 10.4 10.4S55.7 21.6 50 21.6s-10.4-4.7-10.4-10.4S44.3.8 50 .8zM92.2 32l-21.9 2.3c-2.6.3-4.6 2.5-4.6 5.2V94c0 2.9-2.3 5.2-5.2 5.2H60c-2.7 0-4.9-2.1-5.2-4.7l-2.2-24.7c-.1-1.5-1.4-2.5-2.8-2.4-1.3.1-2.2 1.1-2.4 2.4l-2.2 24.7c-.2 2.7-2.5 4.7-5.2 4.7h-.5c-2.9 0-5.2-2.3-5.2-5.2V39.4c0-2.7-2-4.9-4.6-5.2L7.8 32c-2.6-.3-4.6-2.5-4.6-5.2v-.5c0-2.6 2.1-4.7 4.7-4.7h.5c19.3 1.8 33.2 2.8 41.7 2.8s22.4-.9 41.7-2.8c2.6-.2 4.9 1.6 5.2 4.3v1c-.1 2.6-2.1 4.8-4.8 5.1z"></path>					</svg>      </div>
    </div>

        <!-- Scroll to Top Button -->
        <NuxtButton 
          v-show="showScrollTop"
          @click="scrollToTop"
          class="fixed bottom-48 right-16 bg-[#0054A5] rounded-[10px] p-3 shadow-xl z-50 transition flex cursor-pointer">
          <Icon name="heroicons:arrow-up" class="w-5 h-5 text-white" />
        </NuxtButton>

        <!-- Sticky Image Below Scroll Button -->
        <div class="fixed bottom-4 right-8 z-50 cursor-pointer">
            <NuxtLink to="">
                <NuxtImg
                src="/chat-ai.png"
                alt="Sticky Image"
                class="w-42 h-32 object-contain"
            />
            </NuxtLink>
        </div>

        <div class="absolute top-[25%] left-6 md:left-16 transform -translate-y-1/2 text-white flex flex-col items-start text-left px-4 md:px-0 z-10">
          <h1 class="text-3xl font-bold leading-snug md:leading-tight">
            Selamat Datang Ke<br />
            Laman Web Rasmi <br />
            MAIPs
          </h1>
          <p class="mt-4 md:mt-6 text-xs md:text-xl text-white max-w-2xl">
            Dapatkan maklumat terkini mengenai <br/> MAIPs. Bersama kita membina <br/>br>masyarakat yang sejahtera, berlandaskan <br/> syariat Islam.
          </p>
        </div>


            <!-- Carousel Container -->
          <div class="absolute bottom-0 left-0 w-full max-w-7xl px-4 pb-10">
            <!-- Carousel Items In Circular-->
            <div class="flex space-x-3 z-10 justify-center pb-7">
              <div class="w-3 h-3 rounded-full bg-white"></div>
              <div class="w-3 h-3 rounded-full bg-gray-400"></div>
              <div class="w-3 h-3 rounded-full bg-gray-400"></div>
              <div class="w-3 h-3 rounded-full bg-gray-400"></div>  
              <div class="w-3 h-3 rounded-full bg-gray-400"></div>
            </div>

            <!-- Navigation Arrows at the very left and right, positioned at the bottom -->
            <NuxtButton class="absolute left-2 bottom-14 z-30 flex items-center justify-center h-10 w-10 rounded-[10px] bg-transparent border-[1px]">
              <Icon name="mdi:chevron-left" class="w-6 h-6 text-white" />
            </NuxtButton>
            <NuxtButton class="absolute right-2 bottom-14 z-30 flex items-center justify-center h-10 w-10 rrounded-[10px] bg-transparent border-[1px]">
              <Icon name="mdi:chevron-right" class="w-6 h-6 text-white" />
            </NuxtButton>
          </div>

    <div class="absolute bottom-0 left-0 right-0 w-full bg-[#00395E] text-sm text-white flex items-center">
        <div class="flex-1 px-4 py-2 text-center truncate">
            Waktu Operasi Kaunter MAIPs: (Isnin-Khamis) Pagi 08:30am - 01:00pm, Rehat 01:00pm - 02:00pm, Petang 02:00pm - 04:30pm (Jumaat) Pagi...
        </div>

        <NuxtButton class="px-4 py-2 flex items-center gap-2 bg-[#00395E] text-white whitespace-nowrap cursor-pointer">
            <span>Baca Lagi</span>
            <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
        </NuxtButton>

        <div class="px-4 py-2 flex items-center gap-2 whitespace-nowrap">
            <NuxtButton class="flex justify-center cursor-pointer">
                <Icon name="mdi:chevron-left" class="w-5 h-5" />
            </NuxtButton>
            <span><span class="font-bold">1</span> / 3</span>
            <NuxtButton class="flex justify-center cursor-pointer">
            <Icon name="mdi:chevron-right" class="w-5 h-5" />
            </NuxtButton>
        </div>
    </div>
</section>


<!-- Perkembangan Terkini -->
   <section class="pt-32 pb-8 bg-white">
    <div class="mx-auto px-16 max-w-screen-xl max-w-screen-md max-w-screen-sm">
      <!-- Accent line + headings -->
      <span class="block w-[32px] h-[4px] bg-[#0054A5] mb-2 rounded"></span>
      <h2 class="text-4xl font-bold text-[#374151] mb-8 max-w-2xl">Perkembangan Terkini</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 sm:grid-cols-2 lg:grid-cols-3 gap-8 mb-12 ">
        <article
          v-for="(item, index) in perkembangan"
          :key="index"
          class="group bg-gray-50 rounded-xl overflow-hidden shadow-sm border-[1px] border-gray-150"
        >
        <div class="aspect-[16/9] overflow-hidden">
          <img
            :src="item.image"
            alt=""
            class="w-full h-full object-cover scale-125"
          />
        </div>
          <div class="p-6">
            <h3 class="text-xl font-semibold text-gray-800 mb-2 line-clamp-2">
              {{ item.title }}
            </h3>
            <p class="text-gray-600 mb-4 line-clamp-3">
              {{ item.description }}
            </p>
          <div class="flex flex-row sm:flex-col items-start text-xs sm:text-sm text-gray-500 space-x-4 sm:space-x-0 sm:space-y-2">
            <div class="flex items-center space-x-1">
              <Icon name="bi:calendar" class="w-4 h-4 text-[#0054A5]" />
              <span>{{ item.date }}</span>
            </div>
            <div class="flex items-center space-x-1">
              <Icon name="fa-regular:user" class="w-4 h-4 text-[#0054A5]" />
              <span>{{ item.user }}</span>
            </div>
          </div>
          </div>
        </article>
      </div>
      <div class="text-center text-[#0054A5]">
        <NuxtButton
          class="inline-flex items-center space-x-3 px-6 py-3 border-[#0054A5] border-[1px] rounded-[10px] cursor-pointer"
        >
          <p>Lihat Semua</p>
            <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
        </NuxtButton>
      </div>
    </div>
  </section>
  
  <!-- Kemudahan (Desktop - Small And Large) -->
<section
  class="relative pt-32 pb-16 bg-cover bg-center hidden lg-block xl:block 2xl:block"
  style="background-image: url('https://s3-alpha-sig.figma.com/img/2ed4/26c1/b652a53cf78c98f970d20258c5d34d04?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=pb1HWDBM-VYerYAj0KzvHe5tEooVu2YWpgRdtP1l2KNwogoRvjsW8yobYCm8siI4ZLcu2hgN7zKHqw0KadZOJzsJCqODy~Yu-eQNBxON5IwNARzOijezWpj2GfoTseo7kGak1lLmFnBlSCz8sBp2CcFmzKZHdTc2MN8wtyUvmXtTgt16NSYBSItn3n1W-wr9kwz4~DdI41G~88QQQXOiVVt27RAU1NxMuYPJDJpnyz~liBKY~5-3Qd1qwDedhhBkkXGB7UK0vO2k9J1jKme93D85c-Ula-5aKS-LLeuBPyMuoX~rpmHIoUx9kSkOe5Qpl-8wcJX3-fqp9zKONnN38A');"
>
  <!-- Overlay -->
  <div class="absolute inset-0 bg-[#F6FBFF]/90"></div>

  <div class="relative mx-auto px-4 md:px-16 max-w-screen-xl">
    <span class="block w-[32px] h-[4px] bg-[#0054A5] mb-2 rounded"></span>
    <h2 class="text-4xl font-bold text-[#374151] mb-6">
      Kemudahan Anda Adalah Keutamaan Kami
    </h2>
    <p class="text-gray-600 mb-12 max-w-2xl">
      MAIPs komited dalam menyediakan perkhidmatan digital yang memudahkan urusan anda.
    </p>

<div class="relative">
  <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
    <!-- Semak -->
      <div class="relative mx-auto">
        <!-- Third Container (Largest - Bottom) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[335px] h-[560px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(255,254,231,1)_50%,rgba(255,200,180,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-0"></div>

        <!-- Second Container (Medium - Middle) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[340px] h-[550px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(255,254,231,1)_50%,rgba(255,200,180,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-10"></div>

        <!-- Main Container (Normal - Top) -->
      <div class="relative z-20 bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(255,254,231,1)_50%,rgba(255,200,180,1)_100%)] border-[#B6C1DB] border-[1px] rounded-2xl shadow-lg p-8 w-[350px] h-[540px] overflow-hidden">


        <!-- Inline SVG background -->
        <div class="absolute top-[-120px] right-[-230px] z-0 w-[500px] h-[500px] opacity-[0.05] pointer-events-none transfrom scale-x-[-1]">
                        <svg xmlns="http://www.w3.org/2000/svg" width="500" height="500" viewBox="0 0 51 50" fill="none"
                        class="w-full h-full"><g id="Group"><path id="Vector" d="M26.1752 14.6679H33.9067C34.5798 14.6679 35.1274 14.1204 35.1274 13.4472V5.68264C35.1274 5.00948 34.5798 4.46191 33.9067 4.46191H26.1752C25.502 4.46191 24.9545 5.00948 24.9545 5.68264V7.51978C24.9545 7.92437 25.2823 8.25221 25.6869 8.25221C26.0915 8.25221 26.4193 7.92437 26.4193 7.51978V5.92678H33.6625V13.2032H26.4193V11.0439C26.4193 10.6393 26.0915 10.3114 25.6869 10.3114C25.2823 10.3114 24.9545 10.6393 24.9545 11.0439V13.4473C24.9545 14.1204 25.502 14.6679 26.1752 14.6679Z" fill="#FF5A1F"></path><path id="Vector_2" d="M12.5342 13.4844H22.5122C22.9168 13.4844 23.2446 13.1566 23.2446 12.752C23.2446 12.3474 22.9168 12.0195 22.5122 12.0195H12.5342C12.1296 12.0195 11.8018 12.3474 11.8018 12.752C11.8018 13.1566 12.1297 13.4844 12.5342 13.4844Z" fill="#FF5A1F"></path><path id="Vector_3" d="M29.2313 18.9434C29.2313 18.5388 28.9035 18.2109 28.4989 18.2109H18.4302C18.0257 18.2109 17.6978 18.5388 17.6978 18.9434C17.6978 19.348 18.0257 19.6758 18.4302 19.6758H28.4989C28.9034 19.6758 29.2313 19.3479 29.2313 18.9434Z" fill="#FF5A1F"></path><path id="Vector_4" d="M12.5342 10.2969H22.5122C22.9168 10.2969 23.2446 9.96906 23.2446 9.56446C23.2446 9.15987 22.9168 8.83203 22.5122 8.83203H12.5342C12.1296 8.83203 11.8018 9.15987 11.8018 9.56446C11.8018 9.96906 12.1297 10.2969 12.5342 10.2969Z" fill="#FF5A1F"></path><path id="Vector_5" d="M12.5342 7.11038H22.5122C22.9168 7.11038 23.2446 6.78254 23.2446 6.37794C23.2446 5.97335 22.9168 5.64551 22.5122 5.64551H12.5342C12.1296 5.64551 11.8018 5.97335 11.8018 6.37794C11.8018 6.78254 12.1297 7.11038 12.5342 7.11038Z" fill="#FF5A1F"></path><path id="Vector_6" d="M12.5342 27.7803H27.5593C27.9639 27.7803 28.2918 27.4525 28.2918 27.0479C28.2918 26.6433 27.9639 26.3154 27.5593 26.3154H12.5342C12.1296 26.3154 11.8018 26.6433 11.8018 27.0479C11.8018 27.4525 12.1297 27.7803 12.5342 27.7803Z" fill="#FF5A1F"></path><path id="Vector_7" d="M12.5342 23.6826H24.417C24.8216 23.6826 25.1494 23.3548 25.1494 22.9502C25.1494 22.5456 24.8216 22.2178 24.417 22.2178H12.5342C12.1296 22.2178 11.8018 22.5456 11.8018 22.9502C11.8018 23.3548 12.1297 23.6826 12.5342 23.6826Z" fill="#FF5A1F"></path><path id="Vector_8" d="M34.4404 22.2178H27.5918C27.1872 22.2178 26.8594 22.5456 26.8594 22.9502C26.8594 23.3548 27.1872 23.6826 27.5918 23.6826H34.4404C34.845 23.6826 35.1728 23.3548 35.1728 22.9502C35.1728 22.5456 34.8449 22.2178 34.4404 22.2178Z" fill="#FF5A1F"></path><path id="Vector_9" d="M50.0627 45.3059C50.0538 45.2971 50.0446 45.2886 50.0354 45.2803L45.5281 41.2698C46.2403 39.9723 46.6467 38.5185 46.7007 37.0032C46.7151 36.5989 46.3991 36.2596 45.9949 36.2451C45.5899 36.2331 45.2513 36.5468 45.2367 36.951C45.1258 41.2655 41.4714 44.8193 37.1482 44.7761C32.6853 44.7761 29.0543 41.133 29.0543 36.6551C28.9867 32.2666 32.7656 28.4719 37.1482 28.5341C40.5623 28.5341 43.6267 30.7006 44.7735 33.9251C44.909 34.3061 45.3282 34.5055 45.7089 34.3698C46.0901 34.2342 46.2891 33.8154 46.1536 33.4343C44.9303 29.9944 41.8578 27.5751 38.3022 27.1401V1.22072C38.3022 0.547567 37.7546 0 37.0814 0H9.84759C9.17444 0 8.62687 0.547567 8.62687 1.22072V3.86989H5.99255C5.3194 3.86989 4.77183 4.41745 4.77183 5.09061V7.73968H2.13741C1.46425 7.73968 0.916687 8.28724 0.916687 8.9604V45.4987C0.916687 46.1718 1.46425 46.7194 2.13741 46.7194H25.4594C26.1325 46.7194 26.6801 46.1718 26.6801 45.4987V42.8495H29.8597C31.6145 44.9228 34.2306 46.2411 37.1483 46.2411C38.7517 46.2411 40.2995 45.8447 41.6768 45.1L46.2183 49.1674C47.2982 50.2372 49.0479 50.2963 50.1314 49.227C51.2157 48.1907 51.1502 46.3308 50.0627 45.3059ZM10.0917 1.46487H36.8373V27.0753C33.7243 27.1768 30.8955 28.7954 29.2049 31.3231H26.2311C25.8265 31.3231 25.4986 31.6509 25.4986 32.0555C25.4986 32.4601 25.8265 32.7879 26.2311 32.7879H28.3997C28.3016 33.011 28.2113 33.2386 28.1296 33.4712C27.7712 34.4923 27.5896 35.5636 27.5896 36.6551C27.5896 36.9449 27.6033 37.2315 27.6284 37.5149H17.4386C18.4439 36.5518 19.0721 35.1958 19.0721 33.6945V32.788H23.0564C23.461 32.788 23.7888 32.4602 23.7888 32.0556C23.7888 31.651 23.461 31.3232 23.0564 31.3232H18.3396C17.935 31.3232 17.6072 31.651 17.6072 32.0556V33.6945C17.6072 35.8011 15.9011 37.5149 13.8042 37.5149H10.0917V1.46487ZM6.2367 41.3846V31.3726C6.2367 30.968 5.90886 30.6401 5.50426 30.6401C5.09967 30.6401 4.77183 30.968 4.77183 31.3726V41.6287C4.77183 42.3019 5.3194 42.8494 5.99255 42.8494H25.2152V45.2544H2.38155V9.20454H4.77183V28.2767C4.77183 28.6813 5.09967 29.0092 5.50426 29.0092C5.90886 29.0092 6.2367 28.6813 6.2367 28.2767V5.33475H8.62697V38.2473C8.62697 38.6519 8.9548 38.9797 9.3594 38.9797H27.8744C28.087 39.832 28.4132 40.6394 28.8366 41.3847H6.2367V41.3846ZM49.1004 48.1864C48.5935 48.6917 47.7338 48.6401 47.21 48.089L42.9504 44.2739C43.6079 43.7701 44.2143 43.1649 44.7186 42.5101L49.0463 46.361C49.5457 46.8419 49.6036 47.7018 49.1004 48.1864Z" fill="#FF5A1F"></path><path id="Vector_10" d="M37.1484 30.3951C33.7686 30.347 30.8537 33.2723 30.9051 36.6554C30.9051 40.1073 33.7058 42.9155 37.1484 42.9155C40.5908 42.9155 43.3915 40.1073 43.3915 36.6554C43.3915 33.2035 40.5908 30.3951 37.1484 30.3951ZM37.1484 41.4506C34.5136 41.4506 32.37 39.2995 32.37 36.6553C32.3299 34.0642 34.561 31.8233 37.1484 31.8599C39.7831 31.8599 41.9267 34.011 41.9267 36.6553C41.9267 39.2995 39.7832 41.4506 37.1484 41.4506Z" fill="#FF5A1F"></path></g></svg>
          
        </div>
          
        <div class="relative z-10">
      <div class="relative ">
      <div class="absolute left-[-3px] top-[-12px] w-[50px] h-[50px] bg-[#FFE4DA] rounded-full"></div>
        <div class="flex mb-6 px-3">
        <span class="text-2xl mr-3 relative z-10">
              <svg xmlns="http://www.w3.org/2000/svg" width="60" height="60" viewBox="0 0 51 50" fill="none"><g id="Group"><path id="Vector" d="M26.1752 14.6679H33.9067C34.5798 14.6679 35.1274 14.1204 35.1274 13.4472V5.68264C35.1274 5.00948 34.5798 4.46191 33.9067 4.46191H26.1752C25.502 4.46191 24.9545 5.00948 24.9545 5.68264V7.51978C24.9545 7.92437 25.2823 8.25221 25.6869 8.25221C26.0915 8.25221 26.4193 7.92437 26.4193 7.51978V5.92678H33.6625V13.2032H26.4193V11.0439C26.4193 10.6393 26.0915 10.3114 25.6869 10.3114C25.2823 10.3114 24.9545 10.6393 24.9545 11.0439V13.4473C24.9545 14.1204 25.502 14.6679 26.1752 14.6679Z" fill="#FF5A1F"></path><path id="Vector_2" d="M12.5342 13.4844H22.5122C22.9168 13.4844 23.2446 13.1566 23.2446 12.752C23.2446 12.3474 22.9168 12.0195 22.5122 12.0195H12.5342C12.1296 12.0195 11.8018 12.3474 11.8018 12.752C11.8018 13.1566 12.1297 13.4844 12.5342 13.4844Z" fill="#FF5A1F"></path><path id="Vector_3" d="M29.2313 18.9434C29.2313 18.5388 28.9035 18.2109 28.4989 18.2109H18.4302C18.0257 18.2109 17.6978 18.5388 17.6978 18.9434C17.6978 19.348 18.0257 19.6758 18.4302 19.6758H28.4989C28.9034 19.6758 29.2313 19.3479 29.2313 18.9434Z" fill="#FF5A1F"></path><path id="Vector_4" d="M12.5342 10.2969H22.5122C22.9168 10.2969 23.2446 9.96906 23.2446 9.56446C23.2446 9.15987 22.9168 8.83203 22.5122 8.83203H12.5342C12.1296 8.83203 11.8018 9.15987 11.8018 9.56446C11.8018 9.96906 12.1297 10.2969 12.5342 10.2969Z" fill="#FF5A1F"></path><path id="Vector_5" d="M12.5342 7.11038H22.5122C22.9168 7.11038 23.2446 6.78254 23.2446 6.37794C23.2446 5.97335 22.9168 5.64551 22.5122 5.64551H12.5342C12.1296 5.64551 11.8018 5.97335 11.8018 6.37794C11.8018 6.78254 12.1297 7.11038 12.5342 7.11038Z" fill="#FF5A1F"></path><path id="Vector_6" d="M12.5342 27.7803H27.5593C27.9639 27.7803 28.2918 27.4525 28.2918 27.0479C28.2918 26.6433 27.9639 26.3154 27.5593 26.3154H12.5342C12.1296 26.3154 11.8018 26.6433 11.8018 27.0479C11.8018 27.4525 12.1297 27.7803 12.5342 27.7803Z" fill="#FF5A1F"></path><path id="Vector_7" d="M12.5342 23.6826H24.417C24.8216 23.6826 25.1494 23.3548 25.1494 22.9502C25.1494 22.5456 24.8216 22.2178 24.417 22.2178H12.5342C12.1296 22.2178 11.8018 22.5456 11.8018 22.9502C11.8018 23.3548 12.1297 23.6826 12.5342 23.6826Z" fill="#FF5A1F"></path><path id="Vector_8" d="M34.4404 22.2178H27.5918C27.1872 22.2178 26.8594 22.5456 26.8594 22.9502C26.8594 23.3548 27.1872 23.6826 27.5918 23.6826H34.4404C34.845 23.6826 35.1728 23.3548 35.1728 22.9502C35.1728 22.5456 34.8449 22.2178 34.4404 22.2178Z" fill="#FF5A1F"></path><path id="Vector_9" d="M50.0627 45.3059C50.0538 45.2971 50.0446 45.2886 50.0354 45.2803L45.5281 41.2698C46.2403 39.9723 46.6467 38.5185 46.7007 37.0032C46.7151 36.5989 46.3991 36.2596 45.9949 36.2451C45.5899 36.2331 45.2513 36.5468 45.2367 36.951C45.1258 41.2655 41.4714 44.8193 37.1482 44.7761C32.6853 44.7761 29.0543 41.133 29.0543 36.6551C28.9867 32.2666 32.7656 28.4719 37.1482 28.5341C40.5623 28.5341 43.6267 30.7006 44.7735 33.9251C44.909 34.3061 45.3282 34.5055 45.7089 34.3698C46.0901 34.2342 46.2891 33.8154 46.1536 33.4343C44.9303 29.9944 41.8578 27.5751 38.3022 27.1401V1.22072C38.3022 0.547567 37.7546 0 37.0814 0H9.84759C9.17444 0 8.62687 0.547567 8.62687 1.22072V3.86989H5.99255C5.3194 3.86989 4.77183 4.41745 4.77183 5.09061V7.73968H2.13741C1.46425 7.73968 0.916687 8.28724 0.916687 8.9604V45.4987C0.916687 46.1718 1.46425 46.7194 2.13741 46.7194H25.4594C26.1325 46.7194 26.6801 46.1718 26.6801 45.4987V42.8495H29.8597C31.6145 44.9228 34.2306 46.2411 37.1483 46.2411C38.7517 46.2411 40.2995 45.8447 41.6768 45.1L46.2183 49.1674C47.2982 50.2372 49.0479 50.2963 50.1314 49.227C51.2157 48.1907 51.1502 46.3308 50.0627 45.3059ZM10.0917 1.46487H36.8373V27.0753C33.7243 27.1768 30.8955 28.7954 29.2049 31.3231H26.2311C25.8265 31.3231 25.4986 31.6509 25.4986 32.0555C25.4986 32.4601 25.8265 32.7879 26.2311 32.7879H28.3997C28.3016 33.011 28.2113 33.2386 28.1296 33.4712C27.7712 34.4923 27.5896 35.5636 27.5896 36.6551C27.5896 36.9449 27.6033 37.2315 27.6284 37.5149H17.4386C18.4439 36.5518 19.0721 35.1958 19.0721 33.6945V32.788H23.0564C23.461 32.788 23.7888 32.4602 23.7888 32.0556C23.7888 31.651 23.461 31.3232 23.0564 31.3232H18.3396C17.935 31.3232 17.6072 31.651 17.6072 32.0556V33.6945C17.6072 35.8011 15.9011 37.5149 13.8042 37.5149H10.0917V1.46487ZM6.2367 41.3846V31.3726C6.2367 30.968 5.90886 30.6401 5.50426 30.6401C5.09967 30.6401 4.77183 30.968 4.77183 31.3726V41.6287C4.77183 42.3019 5.3194 42.8494 5.99255 42.8494H25.2152V45.2544H2.38155V9.20454H4.77183V28.2767C4.77183 28.6813 5.09967 29.0092 5.50426 29.0092C5.90886 29.0092 6.2367 28.6813 6.2367 28.2767V5.33475H8.62697V38.2473C8.62697 38.6519 8.9548 38.9797 9.3594 38.9797H27.8744C28.087 39.832 28.4132 40.6394 28.8366 41.3847H6.2367V41.3846ZM49.1004 48.1864C48.5935 48.6917 47.7338 48.6401 47.21 48.089L42.9504 44.2739C43.6079 43.7701 44.2143 43.1649 44.7186 42.5101L49.0463 46.361C49.5457 46.8419 49.6036 47.7018 49.1004 48.1864Z" fill="#FF5A1F"></path><path id="Vector_10" d="M37.1484 30.3951C33.7686 30.347 30.8537 33.2723 30.9051 36.6554C30.9051 40.1073 33.7058 42.9155 37.1484 42.9155C40.5908 42.9155 43.3915 40.1073 43.3915 36.6554C43.3915 33.2035 40.5908 30.3951 37.1484 30.3951ZM37.1484 41.4506C34.5136 41.4506 32.37 39.2995 32.37 36.6553C32.3299 34.0642 34.561 31.8233 37.1484 31.8599C39.7831 31.8599 41.9267 34.011 41.9267 36.6553C41.9267 39.2995 39.7832 41.4506 37.1484 41.4506Z" fill="#FF5A1F"></path></g></svg>
            </span>
            <h3 class="text-2xl font-bold text-[#FF5A1F]">Semak</h3>
          </div>
           </div>
          <ul class="space-y-2 text-lg text-gray-700">
            <li class="font-bold">Agihan</li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Skim Bantuan Zakat
              </NuxtLink>
            </li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Status Permohonan
              </NuxtLink>
            </li>
            <li class="font-bold pt-2">Kutipan</li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Kalkulator Zakat 
              </NuxtLink>
            </li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Penyata Zakat
              </NuxtLink>
            </li>
          </ul>
           </div>
        </div>
      </div>

    <!-- Mohon -->
      <div class="relative mx-auto">
        <!-- Third Container (Largest - Bottom) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[335px] h-[560px] bg-[linear-gradient(135deg,_rgba(255,255,255,1)_0%,rgba(1,114,0,1)_250%,rgba(1,114,0,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-0"></div>

        <!-- Second Container (Medium - Middle) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[340px] h-[550px] bg-[linear-gradient(135deg,_rgba(255,255,255,1)_0%,rgba(1,114,0,1)_250%,rgba(1,114,0,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-10"></div>

        <!-- Main Container (Normal - Top) -->
      <div class="relative z-20 bg-[linear-gradient(135deg,_rgba(255,255,255,1)_0%,rgba(1,114,0,1)_250%,rgba(1,114,0,1)_100%)] border-[#B6C1DB] border-[1px] rounded-2xl shadow-lg p-8 w-[350px] h-[540px] overflow-hidden">
        
        <!-- Inline SVG background -->
        <div class="absolute top-[-120px] right-[-230px] z-0 w-[500px] h-[500px] opacity-[0.05] pointer-events-none transfrom scale-x-[-1]">
              <svg xmlns="http://www.w3.org/2000/svg" width="53" height="50" viewBox="0 0 53 50" fill="none"
              class="w-full h-full"><g id="Group"><path id="Vector" d="M8.34294 7.87046H30.3431C30.7658 7.87046 31.1085 7.5279 31.1085 7.10515C31.1085 6.68239 30.7658 6.33984 30.3431 6.33984H8.34294C7.92029 6.33984 7.57764 6.68239 7.57764 7.10515C7.57764 7.5279 7.92029 7.87046 8.34294 7.87046Z" fill="#017200"></path><path id="Vector_2" d="M12.2099 10.0156C11.7872 10.0156 11.4446 10.3582 11.4446 10.7809C11.4446 11.2037 11.7872 11.5462 12.2099 11.5462H25.9892C26.4118 11.5462 26.7545 11.2037 26.7545 10.7809C26.7545 10.3582 26.4118 10.0156 25.9892 10.0156H12.2099Z" fill="#017200"></path><path id="Vector_3" d="M6.0867 42.4853H17.0595C17.4821 42.4853 17.8248 42.1427 17.8248 41.72C17.8248 41.2972 17.4821 40.9547 17.0595 40.9547H6.52353V33.2651H31.2145V40.9547H20.4308C20.0081 40.9547 19.6655 41.2972 19.6655 41.72C19.6655 42.1427 20.0081 42.4853 20.4308 42.4853H31.6541C32.2557 42.4853 32.7451 41.9947 32.7451 41.3916V32.828C32.7451 32.225 32.2557 31.7344 31.6541 31.7344H6.0867C5.48353 31.7344 4.99292 32.225 4.99292 32.828V41.3916C4.99292 41.9947 5.48363 42.4853 6.0867 42.4853Z" fill="#017200"></path><path id="Vector_4" d="M6.10117 28.6641H31.464C32.064 28.6641 32.5521 28.176 32.5521 27.5761V24.4882C32.5521 23.8883 32.064 23.4004 31.464 23.4004H6.10117C5.49964 23.4004 5.01025 23.8883 5.01025 24.4882V27.5761C5.01025 28.176 5.49964 28.6641 6.10117 28.6641ZM6.54087 24.931H31.0215V27.1335H6.54087V24.931Z" fill="#017200"></path><path id="Vector_5" d="M6.10117 20.5332H17.0595C17.4822 20.5332 17.8248 20.1907 17.8248 19.7679C17.8248 19.3452 17.4822 19.0026 17.0595 19.0026H6.54087V16.7972H31.0215V19.0025H20.5807C20.158 19.0025 19.8154 19.3451 19.8154 19.7678C19.8154 20.1906 20.158 20.5331 20.5807 20.5331H31.464C32.064 20.5331 32.5521 20.0438 32.5521 19.4424V16.3546C32.5521 15.7547 32.064 15.2666 31.464 15.2666H6.10117C5.49964 15.2666 5.01025 15.7547 5.01025 16.3546V19.4424C5.01025 20.0439 5.49964 20.5332 6.10117 20.5332Z" fill="#017200"></path><path id="Vector_6" d="M36.1897 0H1.54837C0.832449 0 0.25 0.582347 0.25 1.29827V48.7018C0.25 49.4177 0.832449 50 1.54837 50H36.1897C36.9072 50 37.4909 49.4177 37.4909 48.7017V1.29827C37.4909 0.582347 36.9072 0 36.1897 0ZM35.9603 48.4694H1.78061V1.53061H35.9603V48.4694Z" fill="#017200"></path><path id="Vector_7" d="M52.2468 9.3608C52.0548 8.97387 51.5572 8.32478 50.3839 8.32478H49.21V7.9955C49.21 5.64213 47.2948 3.72754 44.9408 3.72754C42.5868 3.72754 40.6716 5.64213 40.6716 7.9955V16.2999C40.6716 16.7226 41.0143 17.0652 41.4369 17.0652C41.8596 17.0652 42.2022 16.7226 42.2022 16.2999V11.9408H47.6794V23.9858H42.2022V19.8169C42.2022 19.3942 41.8596 19.0516 41.4369 19.0516C41.0143 19.0516 40.6716 19.3942 40.6716 19.8169V36.6157C40.6716 36.7402 40.702 36.8574 40.7548 36.9613C40.7553 36.9623 40.7551 36.9633 40.7556 36.9643L43.8721 43.0566C44.1563 43.6087 44.3807 44.0448 44.9432 44.0448H44.9444C45.5052 44.0441 45.7305 43.604 45.9913 43.0943L49.1261 36.9643C49.1272 36.9621 49.1276 36.9603 49.1285 36.9582C49.1802 36.8551 49.2101 36.7391 49.2101 36.6158V9.8554H50.384C50.8468 9.8554 50.9644 9.93948 50.9644 10.7118V16.395C50.9644 16.8177 51.307 17.1603 51.7297 17.1603C52.1523 17.1603 52.495 16.8177 52.495 16.395V10.7118C52.4949 10.3935 52.4949 9.8605 52.2468 9.3608ZM44.9413 41.7858L42.688 37.381H47.1938L44.9413 41.7858ZM47.6794 35.8504H42.2022V25.5165H47.6794V35.8504ZM47.6794 10.4103H42.2022V7.9956C42.2022 6.48621 43.4308 5.25825 44.9408 5.25825C46.4509 5.25825 47.6794 6.48621 47.6794 7.9956V10.4103Z" fill="#017200"></path></g></svg>
        </div>
          
        <div class="relative z-10">
          <div class="relative ">
          <div class="absolute left-[-3px] top-[-12px] w-[50px] h-[50px] bg-[#E8FDE8] rounded-full"></div>
            <div class="flex mb-6 px-3">
            <span class="text-2xl mr-3 relative z-10">
          <svg xmlns="http://www.w3.org/2000/svg" width="53" height="50" viewBox="0 0 53 50" fill="none"><g id="Group"><path id="Vector" d="M8.34294 7.87046H30.3431C30.7658 7.87046 31.1085 7.5279 31.1085 7.10515C31.1085 6.68239 30.7658 6.33984 30.3431 6.33984H8.34294C7.92029 6.33984 7.57764 6.68239 7.57764 7.10515C7.57764 7.5279 7.92029 7.87046 8.34294 7.87046Z" fill="#017200"></path><path id="Vector_2" d="M12.2099 10.0156C11.7872 10.0156 11.4446 10.3582 11.4446 10.7809C11.4446 11.2037 11.7872 11.5462 12.2099 11.5462H25.9892C26.4118 11.5462 26.7545 11.2037 26.7545 10.7809C26.7545 10.3582 26.4118 10.0156 25.9892 10.0156H12.2099Z" fill="#017200"></path><path id="Vector_3" d="M6.0867 42.4853H17.0595C17.4821 42.4853 17.8248 42.1427 17.8248 41.72C17.8248 41.2972 17.4821 40.9547 17.0595 40.9547H6.52353V33.2651H31.2145V40.9547H20.4308C20.0081 40.9547 19.6655 41.2972 19.6655 41.72C19.6655 42.1427 20.0081 42.4853 20.4308 42.4853H31.6541C32.2557 42.4853 32.7451 41.9947 32.7451 41.3916V32.828C32.7451 32.225 32.2557 31.7344 31.6541 31.7344H6.0867C5.48353 31.7344 4.99292 32.225 4.99292 32.828V41.3916C4.99292 41.9947 5.48363 42.4853 6.0867 42.4853Z" fill="#017200"></path><path id="Vector_4" d="M6.10117 28.6641H31.464C32.064 28.6641 32.5521 28.176 32.5521 27.5761V24.4882C32.5521 23.8883 32.064 23.4004 31.464 23.4004H6.10117C5.49964 23.4004 5.01025 23.8883 5.01025 24.4882V27.5761C5.01025 28.176 5.49964 28.6641 6.10117 28.6641ZM6.54087 24.931H31.0215V27.1335H6.54087V24.931Z" fill="#017200"></path><path id="Vector_5" d="M6.10117 20.5332H17.0595C17.4822 20.5332 17.8248 20.1907 17.8248 19.7679C17.8248 19.3452 17.4822 19.0026 17.0595 19.0026H6.54087V16.7972H31.0215V19.0025H20.5807C20.158 19.0025 19.8154 19.3451 19.8154 19.7678C19.8154 20.1906 20.158 20.5331 20.5807 20.5331H31.464C32.064 20.5331 32.5521 20.0438 32.5521 19.4424V16.3546C32.5521 15.7547 32.064 15.2666 31.464 15.2666H6.10117C5.49964 15.2666 5.01025 15.7547 5.01025 16.3546V19.4424C5.01025 20.0439 5.49964 20.5332 6.10117 20.5332Z" fill="#017200"></path><path id="Vector_6" d="M36.1897 0H1.54837C0.832449 0 0.25 0.582347 0.25 1.29827V48.7018C0.25 49.4177 0.832449 50 1.54837 50H36.1897C36.9072 50 37.4909 49.4177 37.4909 48.7017V1.29827C37.4909 0.582347 36.9072 0 36.1897 0ZM35.9603 48.4694H1.78061V1.53061H35.9603V48.4694Z" fill="#017200"></path><path id="Vector_7" d="M52.2468 9.3608C52.0548 8.97387 51.5572 8.32478 50.3839 8.32478H49.21V7.9955C49.21 5.64213 47.2948 3.72754 44.9408 3.72754C42.5868 3.72754 40.6716 5.64213 40.6716 7.9955V16.2999C40.6716 16.7226 41.0143 17.0652 41.4369 17.0652C41.8596 17.0652 42.2022 16.7226 42.2022 16.2999V11.9408H47.6794V23.9858H42.2022V19.8169C42.2022 19.3942 41.8596 19.0516 41.4369 19.0516C41.0143 19.0516 40.6716 19.3942 40.6716 19.8169V36.6157C40.6716 36.7402 40.702 36.8574 40.7548 36.9613C40.7553 36.9623 40.7551 36.9633 40.7556 36.9643L43.8721 43.0566C44.1563 43.6087 44.3807 44.0448 44.9432 44.0448H44.9444C45.5052 44.0441 45.7305 43.604 45.9913 43.0943L49.1261 36.9643C49.1272 36.9621 49.1276 36.9603 49.1285 36.9582C49.1802 36.8551 49.2101 36.7391 49.2101 36.6158V9.8554H50.384C50.8468 9.8554 50.9644 9.93948 50.9644 10.7118V16.395C50.9644 16.8177 51.307 17.1603 51.7297 17.1603C52.1523 17.1603 52.495 16.8177 52.495 16.395V10.7118C52.4949 10.3935 52.4949 9.8605 52.2468 9.3608ZM44.9413 41.7858L42.688 37.381H47.1938L44.9413 41.7858ZM47.6794 35.8504H42.2022V25.5165H47.6794V35.8504ZM47.6794 10.4103H42.2022V7.9956C42.2022 6.48621 43.4308 5.25825 44.9408 5.25825C46.4509 5.25825 47.6794 6.48621 47.6794 7.9956V10.4103Z" fill="#017200"></path></g></svg>
            </span>
            <h3 class="text-2xl font-bold text-[#017200]">Mohon</h3>
          </div>
           </div>
            <ul class="space-y-2 text-lg ">
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Bantuan Am
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Bantuan Pelajaran
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Sewaan Permis/ Tanah
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Sewaan Bazar Wakaf
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Wakaf Tanah
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-8 h-8 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Panduan Pelaksanaan Perakuan Permastautin
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Potongan Zakat Gaji Bulanan
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-8 h-8 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Kebenaran Potongan Gaji Wakaf Tunai
                </NuxtLink>
              </li>
            </ul>
           </div>
        </div>
      </div>

    <!-- Bayar -->
      <div class="relative mx-auto">
        <!-- Third Container (Largest - Bottom) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[335px] h-[560px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(0,84,165,1)_250%,rgba(0,84,165,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-0"></div>

        <!-- Second Container (Medium - Middle) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[340px] h-[550px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(0,84,165,1)_250%,rgba(0,84,165,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-10"></div>

        <!-- Main Container (Normal - Top) -->
      <div class="relative z-20 bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(0,84,165,1)_250%,rgba(0,84,165,1)_100%)] border-[#B6C1DB] border-[1px] rounded-2xl shadow-lg p-8 w-[350px] h-[540px] overflow-hidden">
        
        <!-- Inline SVG background -->
        <div class="absolute top-[-120px] right-[-230px] z-0 w-[450px] h-[450px] opacity-[0.05] pointer-events-none">
        <svg xmlns="http://www.w3.org/2000/svg" width="59" height="50" viewBox="0 0 49 50" fill="none" class="w-full h-full"><g id="Group"><path id="Vector" d="M40.4752 38.2219C40.8273 37.6107 40.9215 36.8553 40.6682 36.1392C40.2062 34.8406 38.757 34.164 37.4374 34.6309C37.4335 34.6323 37.4297 34.6336 37.4258 34.6351L35.0113 35.5352C35.0288 35.2156 34.9876 34.8899 34.877 34.5758C34.6522 33.9435 34.1932 33.439 33.5847 33.1552C32.9772 32.8719 32.2883 32.8418 31.6451 33.0707C31.6416 33.072 31.6381 33.0733 31.6347 33.0745L27.1353 34.7523C27.1461 34.4566 27.1016 34.1589 26.9998 33.8724C26.788 33.2759 26.3559 32.7974 25.7829 32.5251C25.1989 32.2475 24.5364 32.2162 23.909 32.4399L15.6861 35.4868C15.3688 35.3698 15.0752 35.2481 14.7904 35.1294C12.9435 34.3596 11.5703 33.9336 8.05332 35.1075C7.88086 34.1958 7.07969 33.5037 6.11865 33.5037H2.25498C1.16855 33.5037 0.284668 34.3876 0.284668 35.4741V39.2071C0.284668 39.6147 0.615039 39.9452 1.02266 39.9452C1.43027 39.9452 1.76064 39.6147 1.76064 39.2071V35.4741C1.76064 35.2016 1.98242 34.9798 2.25498 34.9798H6.11855C6.38643 34.9798 6.61279 35.2061 6.61279 35.4741V46.7702C6.61279 47.0382 6.38643 47.2645 6.11855 47.2645H2.25498C1.98252 47.2645 1.76064 47.0428 1.76064 46.7702V42.6034C1.76064 42.1957 1.43027 41.8653 1.02266 41.8653C0.615039 41.8653 0.284668 42.1957 0.284668 42.6034V46.7702C0.284668 47.8567 1.16855 48.7406 2.25498 48.7406H6.11855C7.03389 48.7406 7.80303 48.1122 8.02334 47.265C10.1458 47.3303 11.3314 47.5551 13.8513 48.3091L18.2806 49.6335C19.1039 49.8784 20.2022 50 21.3061 50C22.4628 50 23.6257 49.8663 24.4833 49.6006C26.7521 48.8997 30.3631 47.5233 31.7924 46.9421L40.6246 43.3479C41.2766 43.0815 41.7633 42.5428 41.9948 41.831C42.2649 41.0008 42.1453 40.0203 41.6833 39.2736C41.386 38.7908 40.969 38.437 40.4752 38.2219ZM33.6597 37.6146C33.6929 37.6048 33.7257 37.5926 33.7578 37.578L37.935 36.0206C38.4963 35.8249 39.0852 36.0935 39.277 36.6326C39.465 37.1643 39.1852 37.75 38.6531 37.9382C38.6494 37.9396 38.6456 37.941 38.6419 37.9423L28.0126 41.8968C28.0122 41.6668 27.9885 41.4341 27.937 41.2025C27.8329 40.7333 27.6307 40.3138 27.3526 39.966L33.6597 37.6146ZM32.1444 34.46C32.4186 34.3638 32.7084 34.3755 32.9609 34.4932C33.2084 34.6085 33.3949 34.8136 33.4855 35.0683C33.6358 35.4952 33.4822 35.976 33.1206 36.2402L25.7883 38.9738L22.8013 37.9438L32.1444 34.46ZM24.413 33.8273C24.6601 33.7393 24.9215 33.7501 25.1492 33.8584C25.3657 33.9614 25.529 34.1417 25.6088 34.3664C25.6892 34.593 25.6755 34.839 25.5703 35.0591C25.4648 35.2798 25.2812 35.4459 25.0532 35.5268C25.0366 35.5328 25.0208 35.5399 25.0048 35.5468L20.6063 37.1869L17.8815 36.2474L24.413 33.8273ZM40.5911 41.3744C40.5239 41.581 40.3783 41.854 40.0673 41.9811L31.2361 45.5749C29.8277 46.1477 26.2732 47.5029 24.047 48.1906C22.6276 48.6304 20.1297 48.6434 18.7022 48.2191L14.2742 46.8951C11.6403 46.107 10.3324 45.8611 8.08867 45.7905V36.6563C11.6138 35.407 12.6661 35.8435 14.2224 36.4921C14.6001 36.6495 25.5574 40.4557 25.5574 40.4557C25.5652 40.4584 25.5731 40.461 25.5811 40.4634C26.2395 40.6659 26.4401 41.2715 26.4958 41.5225C26.5892 41.9431 26.525 42.365 26.3297 42.7002C26.3278 42.7034 26.3261 42.7067 26.3243 42.7098C26.2542 42.8281 26.168 42.9355 26.066 43.0278C25.5125 43.5282 24.5365 43.5821 23.3171 43.1794L17.0864 41.1238C16.6995 40.9959 16.282 41.2064 16.1543 41.5934C16.0267 41.9805 16.2369 42.3978 16.624 42.5255L22.8545 44.5811C23.5953 44.8257 24.2305 44.921 24.7707 44.921C25.9475 44.921 26.6732 44.4687 27.0561 44.1226C27.204 43.9888 27.3359 43.8405 27.4513 43.6806L38.283 39.6508C38.2932 39.6474 38.3034 39.6448 38.3135 39.641C39.0424 39.363 39.9806 39.3239 40.427 40.0489C40.6641 40.4319 40.7284 40.9522 40.5911 41.3744Z" fill="#0054A5"></path><path id="Vector_2" d="M48.4851 10.9831L43.2006 1.04512C42.9549 0.581546 42.5421 0.241409 42.0384 0.0873079C41.5354 -0.0665983 41.0033 -0.0158171 40.5416 0.230081L37.1391 2.03848C36.2013 2.53819 35.8356 3.69395 36.3015 4.63995C35.9368 4.83653 35.6023 5.01914 35.2944 5.18711C32.5818 6.66748 31.7631 7.11426 28.1001 7.55078C27.6953 7.59903 27.4064 7.96621 27.4546 8.371C27.4993 8.7461 27.8179 9.02178 28.1865 9.02178C28.2157 9.02178 28.2451 9.02002 28.2748 9.01651C32.2203 8.54629 33.2499 7.98438 36.0015 6.48282C36.3047 6.31739 36.6338 6.1378 36.9916 5.94483L40.4981 12.5406C39.0803 13.3789 38.1651 14.2521 37.4282 15.4457C36.1965 17.4441 34.6786 18.2137 33.2108 18.9579C32.5563 19.2897 31.8796 19.6328 31.2491 20.0741L25.2748 24.2624C25.1151 24.3606 24.9598 24.4362 24.8122 24.489C24.7996 24.4927 24.787 24.4966 24.7746 24.5011C24.5379 24.5799 24.3222 24.5986 24.1439 24.5508C23.9029 24.4862 23.6941 24.2907 23.5234 23.97C23.0981 23.171 23.7354 20.8147 24.8947 19.6743L28.6359 15.9887C28.6513 15.9735 28.666 15.9576 28.68 15.9412C29.3218 15.1869 29.2914 14.5762 29.1529 14.1966C28.9211 13.5612 28.25 13.1463 27.1575 12.9631C24.0476 12.4431 22.8431 13.226 22.1017 14.2542C21.4274 13.8599 20.7008 13.5563 19.9332 13.3487C19.5011 13.2314 19.0619 13.1481 18.6193 13.0974L18.6985 12.9505C20.0296 10.4784 22.0363 9.75362 24.8428 9.38526C25.247 9.33223 25.5316 8.96162 25.4785 8.55752C25.4254 8.15332 25.0545 7.86875 24.6507 7.92178C21.9005 8.28272 19.1186 9.05694 17.3992 12.2501L16.9589 13.0659C15.2412 13.1979 13.5643 13.8407 12.1952 14.9015C10.6602 16.0907 9.58126 17.7123 9.07491 19.5905C7.80245 24.3049 10.6026 29.1756 15.3169 30.448C16.0872 30.6558 16.8642 30.7557 17.6308 30.7556C20.9598 30.7555 24.0897 28.8719 25.5933 25.7623C25.7523 25.6897 25.9119 25.6047 26.0718 25.5051C26.083 25.498 26.0941 25.4907 26.105 25.4831L32.0961 21.2831C32.6404 20.9021 33.2417 20.5972 33.8783 20.2744C35.4517 19.4767 37.235 18.5726 38.6845 16.2206C39.2757 15.2632 40.0276 14.5458 41.1924 13.8464L41.6137 14.6388C41.9665 15.301 42.6481 15.679 43.3523 15.6789C43.6633 15.6789 43.9788 15.6051 44.2722 15.4496L47.6704 13.642C48.1339 13.3962 48.474 12.9834 48.6281 12.4797C48.7819 11.9768 48.7312 11.4452 48.4851 10.9831ZM26.9138 14.419C27.4576 14.5103 27.6747 14.6406 27.7465 14.6967C27.7284 14.743 27.6839 14.8303 27.5751 14.9617L25.1957 17.3058C24.6907 16.4732 24.0499 15.7271 23.3045 15.1024C23.7541 14.4856 24.5209 14.0189 26.9138 14.419ZM15.7014 29.0231C11.773 27.9627 9.43956 23.9038 10.5001 19.975C11.3433 16.847 14.1935 14.6029 17.4304 14.518C18.1442 14.5001 18.8557 14.5858 19.5473 14.7735C20.4018 15.0046 21.194 15.3771 21.9016 15.8808C22.8151 16.531 23.5732 17.3898 24.1089 18.3767L23.8593 18.6226C22.416 20.0421 21.3631 23.0533 22.2205 24.6639C22.6822 25.5312 23.3133 25.8564 23.7614 25.9767C23.766 25.9779 23.7708 25.9787 23.7754 25.9799C22.0468 28.5939 18.8072 29.8607 15.7014 29.0231ZM47.2165 12.0482C47.1779 12.1744 47.0935 12.2773 46.9779 12.3387L43.5797 14.1463C43.3406 14.2731 43.043 14.1828 42.9165 13.9456L37.6313 4.00342C37.5066 3.76924 37.599 3.46592 37.8325 3.34151L41.235 1.53321C41.3053 1.4958 41.3823 1.47676 41.4608 1.47676C41.5093 1.47676 41.5584 1.48409 41.6067 1.49883C41.7328 1.53741 41.8358 1.62188 41.897 1.73731L47.1819 11.6761C47.182 11.6763 47.1821 11.6764 47.1822 11.6766C47.2427 11.7904 47.2549 11.9224 47.2165 12.0482Z" fill="#0054A5"></path></g></svg>
        </div>
          
        <div class="relative z-10">
          <div class="relative ">
          <div class="absolute left-[-3px] top-[-12px] w-[50px] h-[50px] bg-[#E6EEFF] rounded-full"></div>
            <div class="flex mb-6 px-3">
            <span class="text-2xl mr-3 relative z-10">
            <svg xmlns="http://www.w3.org/2000/svg" width="49" height="50" viewBox="0 0 49 50" fill="none"><g id="Group"><path id="Vector" d="M40.4752 38.2219C40.8273 37.6107 40.9215 36.8553 40.6682 36.1392C40.2062 34.8406 38.757 34.164 37.4374 34.6309C37.4335 34.6323 37.4297 34.6336 37.4258 34.6351L35.0113 35.5352C35.0288 35.2156 34.9876 34.8899 34.877 34.5758C34.6522 33.9435 34.1932 33.439 33.5847 33.1552C32.9772 32.8719 32.2883 32.8418 31.6451 33.0707C31.6416 33.072 31.6381 33.0733 31.6347 33.0745L27.1353 34.7523C27.1461 34.4566 27.1016 34.1589 26.9998 33.8724C26.788 33.2759 26.3559 32.7974 25.7829 32.5251C25.1989 32.2475 24.5364 32.2162 23.909 32.4399L15.6861 35.4868C15.3688 35.3698 15.0752 35.2481 14.7904 35.1294C12.9435 34.3596 11.5703 33.9336 8.05332 35.1075C7.88086 34.1958 7.07969 33.5037 6.11865 33.5037H2.25498C1.16855 33.5037 0.284668 34.3876 0.284668 35.4741V39.2071C0.284668 39.6147 0.615039 39.9452 1.02266 39.9452C1.43027 39.9452 1.76064 39.6147 1.76064 39.2071V35.4741C1.76064 35.2016 1.98242 34.9798 2.25498 34.9798H6.11855C6.38643 34.9798 6.61279 35.2061 6.61279 35.4741V46.7702C6.61279 47.0382 6.38643 47.2645 6.11855 47.2645H2.25498C1.98252 47.2645 1.76064 47.0428 1.76064 46.7702V42.6034C1.76064 42.1957 1.43027 41.8653 1.02266 41.8653C0.615039 41.8653 0.284668 42.1957 0.284668 42.6034V46.7702C0.284668 47.8567 1.16855 48.7406 2.25498 48.7406H6.11855C7.03389 48.7406 7.80303 48.1122 8.02334 47.265C10.1458 47.3303 11.3314 47.5551 13.8513 48.3091L18.2806 49.6335C19.1039 49.8784 20.2022 50 21.3061 50C22.4628 50 23.6257 49.8663 24.4833 49.6006C26.7521 48.8997 30.3631 47.5233 31.7924 46.9421L40.6246 43.3479C41.2766 43.0815 41.7633 42.5428 41.9948 41.831C42.2649 41.0008 42.1453 40.0203 41.6833 39.2736C41.386 38.7908 40.969 38.437 40.4752 38.2219ZM33.6597 37.6146C33.6929 37.6048 33.7257 37.5926 33.7578 37.578L37.935 36.0206C38.4963 35.8249 39.0852 36.0935 39.277 36.6326C39.465 37.1643 39.1852 37.75 38.6531 37.9382C38.6494 37.9396 38.6456 37.941 38.6419 37.9423L28.0126 41.8968C28.0122 41.6668 27.9885 41.4341 27.937 41.2025C27.8329 40.7333 27.6307 40.3138 27.3526 39.966L33.6597 37.6146ZM32.1444 34.46C32.4186 34.3638 32.7084 34.3755 32.9609 34.4932C33.2084 34.6085 33.3949 34.8136 33.4855 35.0683C33.6358 35.4952 33.4822 35.976 33.1206 36.2402L25.7883 38.9738L22.8013 37.9438L32.1444 34.46ZM24.413 33.8273C24.6601 33.7393 24.9215 33.7501 25.1492 33.8584C25.3657 33.9614 25.529 34.1417 25.6088 34.3664C25.6892 34.593 25.6755 34.839 25.5703 35.0591C25.4648 35.2798 25.2812 35.4459 25.0532 35.5268C25.0366 35.5328 25.0208 35.5399 25.0048 35.5468L20.6063 37.1869L17.8815 36.2474L24.413 33.8273ZM40.5911 41.3744C40.5239 41.581 40.3783 41.854 40.0673 41.9811L31.2361 45.5749C29.8277 46.1477 26.2732 47.5029 24.047 48.1906C22.6276 48.6304 20.1297 48.6434 18.7022 48.2191L14.2742 46.8951C11.6403 46.107 10.3324 45.8611 8.08867 45.7905V36.6563C11.6138 35.407 12.6661 35.8435 14.2224 36.4921C14.6001 36.6495 25.5574 40.4557 25.5574 40.4557C25.5652 40.4584 25.5731 40.461 25.5811 40.4634C26.2395 40.6659 26.4401 41.2715 26.4958 41.5225C26.5892 41.9431 26.525 42.365 26.3297 42.7002C26.3278 42.7034 26.3261 42.7067 26.3243 42.7098C26.2542 42.8281 26.168 42.9355 26.066 43.0278C25.5125 43.5282 24.5365 43.5821 23.3171 43.1794L17.0864 41.1238C16.6995 40.9959 16.282 41.2064 16.1543 41.5934C16.0267 41.9805 16.2369 42.3978 16.624 42.5255L22.8545 44.5811C23.5953 44.8257 24.2305 44.921 24.7707 44.921C25.9475 44.921 26.6732 44.4687 27.0561 44.1226C27.204 43.9888 27.3359 43.8405 27.4513 43.6806L38.283 39.6508C38.2932 39.6474 38.3034 39.6448 38.3135 39.641C39.0424 39.363 39.9806 39.3239 40.427 40.0489C40.6641 40.4319 40.7284 40.9522 40.5911 41.3744Z" fill="#0054A5"></path><path id="Vector_2" d="M48.4851 10.9831L43.2006 1.04512C42.9549 0.581546 42.5421 0.241409 42.0384 0.0873079C41.5354 -0.0665983 41.0033 -0.0158171 40.5416 0.230081L37.1391 2.03848C36.2013 2.53819 35.8356 3.69395 36.3015 4.63995C35.9368 4.83653 35.6023 5.01914 35.2944 5.18711C32.5818 6.66748 31.7631 7.11426 28.1001 7.55078C27.6953 7.59903 27.4064 7.96621 27.4546 8.371C27.4993 8.7461 27.8179 9.02178 28.1865 9.02178C28.2157 9.02178 28.2451 9.02002 28.2748 9.01651C32.2203 8.54629 33.2499 7.98438 36.0015 6.48282C36.3047 6.31739 36.6338 6.1378 36.9916 5.94483L40.4981 12.5406C39.0803 13.3789 38.1651 14.2521 37.4282 15.4457C36.1965 17.4441 34.6786 18.2137 33.2108 18.9579C32.5563 19.2897 31.8796 19.6328 31.2491 20.0741L25.2748 24.2624C25.1151 24.3606 24.9598 24.4362 24.8122 24.489C24.7996 24.4927 24.787 24.4966 24.7746 24.5011C24.5379 24.5799 24.3222 24.5986 24.1439 24.5508C23.9029 24.4862 23.6941 24.2907 23.5234 23.97C23.0981 23.171 23.7354 20.8147 24.8947 19.6743L28.6359 15.9887C28.6513 15.9735 28.666 15.9576 28.68 15.9412C29.3218 15.1869 29.2914 14.5762 29.1529 14.1966C28.9211 13.5612 28.25 13.1463 27.1575 12.9631C24.0476 12.4431 22.8431 13.226 22.1017 14.2542C21.4274 13.8599 20.7008 13.5563 19.9332 13.3487C19.5011 13.2314 19.0619 13.1481 18.6193 13.0974L18.6985 12.9505C20.0296 10.4784 22.0363 9.75362 24.8428 9.38526C25.247 9.33223 25.5316 8.96162 25.4785 8.55752C25.4254 8.15332 25.0545 7.86875 24.6507 7.92178C21.9005 8.28272 19.1186 9.05694 17.3992 12.2501L16.9589 13.0659C15.2412 13.1979 13.5643 13.8407 12.1952 14.9015C10.6602 16.0907 9.58126 17.7123 9.07491 19.5905C7.80245 24.3049 10.6026 29.1756 15.3169 30.448C16.0872 30.6558 16.8642 30.7557 17.6308 30.7556C20.9598 30.7555 24.0897 28.8719 25.5933 25.7623C25.7523 25.6897 25.9119 25.6047 26.0718 25.5051C26.083 25.498 26.0941 25.4907 26.105 25.4831L32.0961 21.2831C32.6404 20.9021 33.2417 20.5972 33.8783 20.2744C35.4517 19.4767 37.235 18.5726 38.6845 16.2206C39.2757 15.2632 40.0276 14.5458 41.1924 13.8464L41.6137 14.6388C41.9665 15.301 42.6481 15.679 43.3523 15.6789C43.6633 15.6789 43.9788 15.6051 44.2722 15.4496L47.6704 13.642C48.1339 13.3962 48.474 12.9834 48.6281 12.4797C48.7819 11.9768 48.7312 11.4452 48.4851 10.9831ZM26.9138 14.419C27.4576 14.5103 27.6747 14.6406 27.7465 14.6967C27.7284 14.743 27.6839 14.8303 27.5751 14.9617L25.1957 17.3058C24.6907 16.4732 24.0499 15.7271 23.3045 15.1024C23.7541 14.4856 24.5209 14.0189 26.9138 14.419ZM15.7014 29.0231C11.773 27.9627 9.43956 23.9038 10.5001 19.975C11.3433 16.847 14.1935 14.6029 17.4304 14.518C18.1442 14.5001 18.8557 14.5858 19.5473 14.7735C20.4018 15.0046 21.194 15.3771 21.9016 15.8808C22.8151 16.531 23.5732 17.3898 24.1089 18.3767L23.8593 18.6226C22.416 20.0421 21.3631 23.0533 22.2205 24.6639C22.6822 25.5312 23.3133 25.8564 23.7614 25.9767C23.766 25.9779 23.7708 25.9787 23.7754 25.9799C22.0468 28.5939 18.8072 29.8607 15.7014 29.0231ZM47.2165 12.0482C47.1779 12.1744 47.0935 12.2773 46.9779 12.3387L43.5797 14.1463C43.3406 14.2731 43.043 14.1828 42.9165 13.9456L37.6313 4.00342C37.5066 3.76924 37.599 3.46592 37.8325 3.34151L41.235 1.53321C41.3053 1.4958 41.3823 1.47676 41.4608 1.47676C41.5093 1.47676 41.5584 1.48409 41.6067 1.49883C41.7328 1.53741 41.8358 1.62188 41.897 1.73731L47.1819 11.6761C47.182 11.6763 47.1821 11.6764 47.1822 11.6766C47.2427 11.7904 47.2549 11.9224 47.2165 12.0482Z" fill="#0054A5"></path></g></svg>
          </span>
            <h3 class="text-2xl font-bold text-[#0054A5]">Bayar</h3>
          </div>
           </div>
            <ul class="space-y-2 text-lg ">
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                   Bayaran Zakat (Online)
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Bayaran Zakat (Transfer)
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Bayaran Wakaf Tunai
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Bayaran Sewaan
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Fidyah
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Wang Tidak Patuh Syarak
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Kafarah
                </NuxtLink>
              </li>
            </ul>
           </div>
        </div>
      </div>
  </div>
</div>


  </div>
</section>

<!-- Kemudahan (Tablet) -->
<section
  class="relative pt-32 pb-16 bg-cover bg-center hidden md:block lg:hidden xl:hidden 2xl:hidden"
  style="background-image: url('https://s3-alpha-sig.figma.com/img/2ed4/26c1/b652a53cf78c98f970d20258c5d34d04?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=pb1HWDBM-VYerYAj0KzvHe5tEooVu2YWpgRdtP1l2KNwogoRvjsW8yobYCm8siI4ZLcu2hgN7zKHqw0KadZOJzsJCqODy~Yu-eQNBxON5IwNARzOijezWpj2GfoTseo7kGak1lLmFnBlSCz8sBp2CcFmzKZHdTc2MN8wtyUvmXtTgt16NSYBSItn3n1W-wr9kwz4~DdI41G~88QQQXOiVVt27RAU1NxMuYPJDJpnyz~liBKY~5-3Qd1qwDedhhBkkXGB7UK0vO2k9J1jKme93D85c-Ula-5aKS-LLeuBPyMuoX~rpmHIoUx9kSkOe5Qpl-8wcJX3-fqp9zKONnN38A');"
>
  <!-- Overlay -->
  <div class="absolute inset-0 bg-[#F6FBFF]/90"></div>

  <div class="relative mx-4 px-4 ">
    <span class="block w-[32px] h-[4px] bg-[#0054A5] mb-2 rounded"></span>
    <h2 class="text-4xl font-bold text-[#374151] mb-6">
      Kemudahan Anda Adalah Keutamaan Kami
    </h2>
    <p class="text-gray-600 mb-12 text-md">
      MAIPs komited dalam menyediakan perkhidmatan digital yang memudahkan urusan anda.
    </p>

<div class="relative">
  <div class="grid grid-cols-2 gap-10 ">
    <!-- Semak -->
      <div class="relative mx-auto">
        <!-- Third Container (Largest - Bottom) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[335px] h-[560px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(255,254,231,1)_50%,rgba(255,200,180,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-0"></div>

        <!-- Second Container (Medium - Middle) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[340px] h-[550px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(255,254,231,1)_50%,rgba(255,200,180,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-10"></div>

        <!-- Main Container (Normal - Top) -->
      <div class="relative z-20 bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(255,254,231,1)_50%,rgba(255,200,180,1)_100%)] border-[#B6C1DB] border-[1px] rounded-2xl shadow-lg p-8 w-[350px] h-[540px] overflow-hidden">


        <!-- Inline SVG background -->
        <div class="absolute top-[-120px] right-[-230px] z-0 w-[500px] h-[500px] opacity-[0.05] pointer-events-none transfrom scale-x-[-1]">
                        <svg xmlns="http://www.w3.org/2000/svg" width="500" height="500" viewBox="0 0 51 50" fill="none"
                        class="w-full h-full"><g id="Group"><path id="Vector" d="M26.1752 14.6679H33.9067C34.5798 14.6679 35.1274 14.1204 35.1274 13.4472V5.68264C35.1274 5.00948 34.5798 4.46191 33.9067 4.46191H26.1752C25.502 4.46191 24.9545 5.00948 24.9545 5.68264V7.51978C24.9545 7.92437 25.2823 8.25221 25.6869 8.25221C26.0915 8.25221 26.4193 7.92437 26.4193 7.51978V5.92678H33.6625V13.2032H26.4193V11.0439C26.4193 10.6393 26.0915 10.3114 25.6869 10.3114C25.2823 10.3114 24.9545 10.6393 24.9545 11.0439V13.4473C24.9545 14.1204 25.502 14.6679 26.1752 14.6679Z" fill="#FF5A1F"></path><path id="Vector_2" d="M12.5342 13.4844H22.5122C22.9168 13.4844 23.2446 13.1566 23.2446 12.752C23.2446 12.3474 22.9168 12.0195 22.5122 12.0195H12.5342C12.1296 12.0195 11.8018 12.3474 11.8018 12.752C11.8018 13.1566 12.1297 13.4844 12.5342 13.4844Z" fill="#FF5A1F"></path><path id="Vector_3" d="M29.2313 18.9434C29.2313 18.5388 28.9035 18.2109 28.4989 18.2109H18.4302C18.0257 18.2109 17.6978 18.5388 17.6978 18.9434C17.6978 19.348 18.0257 19.6758 18.4302 19.6758H28.4989C28.9034 19.6758 29.2313 19.3479 29.2313 18.9434Z" fill="#FF5A1F"></path><path id="Vector_4" d="M12.5342 10.2969H22.5122C22.9168 10.2969 23.2446 9.96906 23.2446 9.56446C23.2446 9.15987 22.9168 8.83203 22.5122 8.83203H12.5342C12.1296 8.83203 11.8018 9.15987 11.8018 9.56446C11.8018 9.96906 12.1297 10.2969 12.5342 10.2969Z" fill="#FF5A1F"></path><path id="Vector_5" d="M12.5342 7.11038H22.5122C22.9168 7.11038 23.2446 6.78254 23.2446 6.37794C23.2446 5.97335 22.9168 5.64551 22.5122 5.64551H12.5342C12.1296 5.64551 11.8018 5.97335 11.8018 6.37794C11.8018 6.78254 12.1297 7.11038 12.5342 7.11038Z" fill="#FF5A1F"></path><path id="Vector_6" d="M12.5342 27.7803H27.5593C27.9639 27.7803 28.2918 27.4525 28.2918 27.0479C28.2918 26.6433 27.9639 26.3154 27.5593 26.3154H12.5342C12.1296 26.3154 11.8018 26.6433 11.8018 27.0479C11.8018 27.4525 12.1297 27.7803 12.5342 27.7803Z" fill="#FF5A1F"></path><path id="Vector_7" d="M12.5342 23.6826H24.417C24.8216 23.6826 25.1494 23.3548 25.1494 22.9502C25.1494 22.5456 24.8216 22.2178 24.417 22.2178H12.5342C12.1296 22.2178 11.8018 22.5456 11.8018 22.9502C11.8018 23.3548 12.1297 23.6826 12.5342 23.6826Z" fill="#FF5A1F"></path><path id="Vector_8" d="M34.4404 22.2178H27.5918C27.1872 22.2178 26.8594 22.5456 26.8594 22.9502C26.8594 23.3548 27.1872 23.6826 27.5918 23.6826H34.4404C34.845 23.6826 35.1728 23.3548 35.1728 22.9502C35.1728 22.5456 34.8449 22.2178 34.4404 22.2178Z" fill="#FF5A1F"></path><path id="Vector_9" d="M50.0627 45.3059C50.0538 45.2971 50.0446 45.2886 50.0354 45.2803L45.5281 41.2698C46.2403 39.9723 46.6467 38.5185 46.7007 37.0032C46.7151 36.5989 46.3991 36.2596 45.9949 36.2451C45.5899 36.2331 45.2513 36.5468 45.2367 36.951C45.1258 41.2655 41.4714 44.8193 37.1482 44.7761C32.6853 44.7761 29.0543 41.133 29.0543 36.6551C28.9867 32.2666 32.7656 28.4719 37.1482 28.5341C40.5623 28.5341 43.6267 30.7006 44.7735 33.9251C44.909 34.3061 45.3282 34.5055 45.7089 34.3698C46.0901 34.2342 46.2891 33.8154 46.1536 33.4343C44.9303 29.9944 41.8578 27.5751 38.3022 27.1401V1.22072C38.3022 0.547567 37.7546 0 37.0814 0H9.84759C9.17444 0 8.62687 0.547567 8.62687 1.22072V3.86989H5.99255C5.3194 3.86989 4.77183 4.41745 4.77183 5.09061V7.73968H2.13741C1.46425 7.73968 0.916687 8.28724 0.916687 8.9604V45.4987C0.916687 46.1718 1.46425 46.7194 2.13741 46.7194H25.4594C26.1325 46.7194 26.6801 46.1718 26.6801 45.4987V42.8495H29.8597C31.6145 44.9228 34.2306 46.2411 37.1483 46.2411C38.7517 46.2411 40.2995 45.8447 41.6768 45.1L46.2183 49.1674C47.2982 50.2372 49.0479 50.2963 50.1314 49.227C51.2157 48.1907 51.1502 46.3308 50.0627 45.3059ZM10.0917 1.46487H36.8373V27.0753C33.7243 27.1768 30.8955 28.7954 29.2049 31.3231H26.2311C25.8265 31.3231 25.4986 31.6509 25.4986 32.0555C25.4986 32.4601 25.8265 32.7879 26.2311 32.7879H28.3997C28.3016 33.011 28.2113 33.2386 28.1296 33.4712C27.7712 34.4923 27.5896 35.5636 27.5896 36.6551C27.5896 36.9449 27.6033 37.2315 27.6284 37.5149H17.4386C18.4439 36.5518 19.0721 35.1958 19.0721 33.6945V32.788H23.0564C23.461 32.788 23.7888 32.4602 23.7888 32.0556C23.7888 31.651 23.461 31.3232 23.0564 31.3232H18.3396C17.935 31.3232 17.6072 31.651 17.6072 32.0556V33.6945C17.6072 35.8011 15.9011 37.5149 13.8042 37.5149H10.0917V1.46487ZM6.2367 41.3846V31.3726C6.2367 30.968 5.90886 30.6401 5.50426 30.6401C5.09967 30.6401 4.77183 30.968 4.77183 31.3726V41.6287C4.77183 42.3019 5.3194 42.8494 5.99255 42.8494H25.2152V45.2544H2.38155V9.20454H4.77183V28.2767C4.77183 28.6813 5.09967 29.0092 5.50426 29.0092C5.90886 29.0092 6.2367 28.6813 6.2367 28.2767V5.33475H8.62697V38.2473C8.62697 38.6519 8.9548 38.9797 9.3594 38.9797H27.8744C28.087 39.832 28.4132 40.6394 28.8366 41.3847H6.2367V41.3846ZM49.1004 48.1864C48.5935 48.6917 47.7338 48.6401 47.21 48.089L42.9504 44.2739C43.6079 43.7701 44.2143 43.1649 44.7186 42.5101L49.0463 46.361C49.5457 46.8419 49.6036 47.7018 49.1004 48.1864Z" fill="#FF5A1F"></path><path id="Vector_10" d="M37.1484 30.3951C33.7686 30.347 30.8537 33.2723 30.9051 36.6554C30.9051 40.1073 33.7058 42.9155 37.1484 42.9155C40.5908 42.9155 43.3915 40.1073 43.3915 36.6554C43.3915 33.2035 40.5908 30.3951 37.1484 30.3951ZM37.1484 41.4506C34.5136 41.4506 32.37 39.2995 32.37 36.6553C32.3299 34.0642 34.561 31.8233 37.1484 31.8599C39.7831 31.8599 41.9267 34.011 41.9267 36.6553C41.9267 39.2995 39.7832 41.4506 37.1484 41.4506Z" fill="#FF5A1F"></path></g></svg>
          
        </div>
          
        <div class="relative z-10">
      <div class="relative ">
      <div class="absolute left-[-3px] top-[-12px] w-[50px] h-[50px] bg-[#FFE4DA] rounded-full"></div>
        <div class="flex mb-6 px-3">
        <span class="text-2xl mr-3 relative z-10">
              <svg xmlns="http://www.w3.org/2000/svg" width="60" height="60" viewBox="0 0 51 50" fill="none"><g id="Group"><path id="Vector" d="M26.1752 14.6679H33.9067C34.5798 14.6679 35.1274 14.1204 35.1274 13.4472V5.68264C35.1274 5.00948 34.5798 4.46191 33.9067 4.46191H26.1752C25.502 4.46191 24.9545 5.00948 24.9545 5.68264V7.51978C24.9545 7.92437 25.2823 8.25221 25.6869 8.25221C26.0915 8.25221 26.4193 7.92437 26.4193 7.51978V5.92678H33.6625V13.2032H26.4193V11.0439C26.4193 10.6393 26.0915 10.3114 25.6869 10.3114C25.2823 10.3114 24.9545 10.6393 24.9545 11.0439V13.4473C24.9545 14.1204 25.502 14.6679 26.1752 14.6679Z" fill="#FF5A1F"></path><path id="Vector_2" d="M12.5342 13.4844H22.5122C22.9168 13.4844 23.2446 13.1566 23.2446 12.752C23.2446 12.3474 22.9168 12.0195 22.5122 12.0195H12.5342C12.1296 12.0195 11.8018 12.3474 11.8018 12.752C11.8018 13.1566 12.1297 13.4844 12.5342 13.4844Z" fill="#FF5A1F"></path><path id="Vector_3" d="M29.2313 18.9434C29.2313 18.5388 28.9035 18.2109 28.4989 18.2109H18.4302C18.0257 18.2109 17.6978 18.5388 17.6978 18.9434C17.6978 19.348 18.0257 19.6758 18.4302 19.6758H28.4989C28.9034 19.6758 29.2313 19.3479 29.2313 18.9434Z" fill="#FF5A1F"></path><path id="Vector_4" d="M12.5342 10.2969H22.5122C22.9168 10.2969 23.2446 9.96906 23.2446 9.56446C23.2446 9.15987 22.9168 8.83203 22.5122 8.83203H12.5342C12.1296 8.83203 11.8018 9.15987 11.8018 9.56446C11.8018 9.96906 12.1297 10.2969 12.5342 10.2969Z" fill="#FF5A1F"></path><path id="Vector_5" d="M12.5342 7.11038H22.5122C22.9168 7.11038 23.2446 6.78254 23.2446 6.37794C23.2446 5.97335 22.9168 5.64551 22.5122 5.64551H12.5342C12.1296 5.64551 11.8018 5.97335 11.8018 6.37794C11.8018 6.78254 12.1297 7.11038 12.5342 7.11038Z" fill="#FF5A1F"></path><path id="Vector_6" d="M12.5342 27.7803H27.5593C27.9639 27.7803 28.2918 27.4525 28.2918 27.0479C28.2918 26.6433 27.9639 26.3154 27.5593 26.3154H12.5342C12.1296 26.3154 11.8018 26.6433 11.8018 27.0479C11.8018 27.4525 12.1297 27.7803 12.5342 27.7803Z" fill="#FF5A1F"></path><path id="Vector_7" d="M12.5342 23.6826H24.417C24.8216 23.6826 25.1494 23.3548 25.1494 22.9502C25.1494 22.5456 24.8216 22.2178 24.417 22.2178H12.5342C12.1296 22.2178 11.8018 22.5456 11.8018 22.9502C11.8018 23.3548 12.1297 23.6826 12.5342 23.6826Z" fill="#FF5A1F"></path><path id="Vector_8" d="M34.4404 22.2178H27.5918C27.1872 22.2178 26.8594 22.5456 26.8594 22.9502C26.8594 23.3548 27.1872 23.6826 27.5918 23.6826H34.4404C34.845 23.6826 35.1728 23.3548 35.1728 22.9502C35.1728 22.5456 34.8449 22.2178 34.4404 22.2178Z" fill="#FF5A1F"></path><path id="Vector_9" d="M50.0627 45.3059C50.0538 45.2971 50.0446 45.2886 50.0354 45.2803L45.5281 41.2698C46.2403 39.9723 46.6467 38.5185 46.7007 37.0032C46.7151 36.5989 46.3991 36.2596 45.9949 36.2451C45.5899 36.2331 45.2513 36.5468 45.2367 36.951C45.1258 41.2655 41.4714 44.8193 37.1482 44.7761C32.6853 44.7761 29.0543 41.133 29.0543 36.6551C28.9867 32.2666 32.7656 28.4719 37.1482 28.5341C40.5623 28.5341 43.6267 30.7006 44.7735 33.9251C44.909 34.3061 45.3282 34.5055 45.7089 34.3698C46.0901 34.2342 46.2891 33.8154 46.1536 33.4343C44.9303 29.9944 41.8578 27.5751 38.3022 27.1401V1.22072C38.3022 0.547567 37.7546 0 37.0814 0H9.84759C9.17444 0 8.62687 0.547567 8.62687 1.22072V3.86989H5.99255C5.3194 3.86989 4.77183 4.41745 4.77183 5.09061V7.73968H2.13741C1.46425 7.73968 0.916687 8.28724 0.916687 8.9604V45.4987C0.916687 46.1718 1.46425 46.7194 2.13741 46.7194H25.4594C26.1325 46.7194 26.6801 46.1718 26.6801 45.4987V42.8495H29.8597C31.6145 44.9228 34.2306 46.2411 37.1483 46.2411C38.7517 46.2411 40.2995 45.8447 41.6768 45.1L46.2183 49.1674C47.2982 50.2372 49.0479 50.2963 50.1314 49.227C51.2157 48.1907 51.1502 46.3308 50.0627 45.3059ZM10.0917 1.46487H36.8373V27.0753C33.7243 27.1768 30.8955 28.7954 29.2049 31.3231H26.2311C25.8265 31.3231 25.4986 31.6509 25.4986 32.0555C25.4986 32.4601 25.8265 32.7879 26.2311 32.7879H28.3997C28.3016 33.011 28.2113 33.2386 28.1296 33.4712C27.7712 34.4923 27.5896 35.5636 27.5896 36.6551C27.5896 36.9449 27.6033 37.2315 27.6284 37.5149H17.4386C18.4439 36.5518 19.0721 35.1958 19.0721 33.6945V32.788H23.0564C23.461 32.788 23.7888 32.4602 23.7888 32.0556C23.7888 31.651 23.461 31.3232 23.0564 31.3232H18.3396C17.935 31.3232 17.6072 31.651 17.6072 32.0556V33.6945C17.6072 35.8011 15.9011 37.5149 13.8042 37.5149H10.0917V1.46487ZM6.2367 41.3846V31.3726C6.2367 30.968 5.90886 30.6401 5.50426 30.6401C5.09967 30.6401 4.77183 30.968 4.77183 31.3726V41.6287C4.77183 42.3019 5.3194 42.8494 5.99255 42.8494H25.2152V45.2544H2.38155V9.20454H4.77183V28.2767C4.77183 28.6813 5.09967 29.0092 5.50426 29.0092C5.90886 29.0092 6.2367 28.6813 6.2367 28.2767V5.33475H8.62697V38.2473C8.62697 38.6519 8.9548 38.9797 9.3594 38.9797H27.8744C28.087 39.832 28.4132 40.6394 28.8366 41.3847H6.2367V41.3846ZM49.1004 48.1864C48.5935 48.6917 47.7338 48.6401 47.21 48.089L42.9504 44.2739C43.6079 43.7701 44.2143 43.1649 44.7186 42.5101L49.0463 46.361C49.5457 46.8419 49.6036 47.7018 49.1004 48.1864Z" fill="#FF5A1F"></path><path id="Vector_10" d="M37.1484 30.3951C33.7686 30.347 30.8537 33.2723 30.9051 36.6554C30.9051 40.1073 33.7058 42.9155 37.1484 42.9155C40.5908 42.9155 43.3915 40.1073 43.3915 36.6554C43.3915 33.2035 40.5908 30.3951 37.1484 30.3951ZM37.1484 41.4506C34.5136 41.4506 32.37 39.2995 32.37 36.6553C32.3299 34.0642 34.561 31.8233 37.1484 31.8599C39.7831 31.8599 41.9267 34.011 41.9267 36.6553C41.9267 39.2995 39.7832 41.4506 37.1484 41.4506Z" fill="#FF5A1F"></path></g></svg>
            </span>
            <h3 class="text-2xl font-bold text-[#FF5A1F]">Semak</h3>
          </div>
           </div>
          <ul class="space-y-2 text-lg text-gray-700">
            <li class="font-bold">Agihan</li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Skim Bantuan Zakat
              </NuxtLink>
            </li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Status Permohonan
              </NuxtLink>
            </li>
            <li class="font-bold pt-2">Kutipan</li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Kalkulator Zakat 
              </NuxtLink>
            </li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Penyata Zakat
              </NuxtLink>
            </li>
          </ul>
           </div>
        </div>
      </div>

    <!-- Mohon -->
      <div class="relative mx-auto">
        <!-- Third Container (Largest - Bottom) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[335px] h-[560px] bg-[linear-gradient(135deg,_rgba(255,255,255,1)_0%,rgba(1,114,0,1)_250%,rgba(1,114,0,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-0"></div>

        <!-- Second Container (Medium - Middle) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[340px] h-[550px] bg-[linear-gradient(135deg,_rgba(255,255,255,1)_0%,rgba(1,114,0,1)_250%,rgba(1,114,0,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-10"></div>

        <!-- Main Container (Normal - Top) -->
      <div class="relative z-20 bg-[linear-gradient(135deg,_rgba(255,255,255,1)_0%,rgba(1,114,0,1)_250%,rgba(1,114,0,1)_100%)] border-[#B6C1DB] border-[1px] rounded-2xl shadow-lg p-8 w-[350px] h-[540px] overflow-hidden">
        
        <!-- Inline SVG background -->
        <div class="absolute top-[-120px] right-[-230px] z-0 w-[500px] h-[500px] opacity-[0.05] pointer-events-none transfrom scale-x-[-1]">
              <svg xmlns="http://www.w3.org/2000/svg" width="53" height="50" viewBox="0 0 53 50" fill="none"
              class="w-full h-full"><g id="Group"><path id="Vector" d="M8.34294 7.87046H30.3431C30.7658 7.87046 31.1085 7.5279 31.1085 7.10515C31.1085 6.68239 30.7658 6.33984 30.3431 6.33984H8.34294C7.92029 6.33984 7.57764 6.68239 7.57764 7.10515C7.57764 7.5279 7.92029 7.87046 8.34294 7.87046Z" fill="#017200"></path><path id="Vector_2" d="M12.2099 10.0156C11.7872 10.0156 11.4446 10.3582 11.4446 10.7809C11.4446 11.2037 11.7872 11.5462 12.2099 11.5462H25.9892C26.4118 11.5462 26.7545 11.2037 26.7545 10.7809C26.7545 10.3582 26.4118 10.0156 25.9892 10.0156H12.2099Z" fill="#017200"></path><path id="Vector_3" d="M6.0867 42.4853H17.0595C17.4821 42.4853 17.8248 42.1427 17.8248 41.72C17.8248 41.2972 17.4821 40.9547 17.0595 40.9547H6.52353V33.2651H31.2145V40.9547H20.4308C20.0081 40.9547 19.6655 41.2972 19.6655 41.72C19.6655 42.1427 20.0081 42.4853 20.4308 42.4853H31.6541C32.2557 42.4853 32.7451 41.9947 32.7451 41.3916V32.828C32.7451 32.225 32.2557 31.7344 31.6541 31.7344H6.0867C5.48353 31.7344 4.99292 32.225 4.99292 32.828V41.3916C4.99292 41.9947 5.48363 42.4853 6.0867 42.4853Z" fill="#017200"></path><path id="Vector_4" d="M6.10117 28.6641H31.464C32.064 28.6641 32.5521 28.176 32.5521 27.5761V24.4882C32.5521 23.8883 32.064 23.4004 31.464 23.4004H6.10117C5.49964 23.4004 5.01025 23.8883 5.01025 24.4882V27.5761C5.01025 28.176 5.49964 28.6641 6.10117 28.6641ZM6.54087 24.931H31.0215V27.1335H6.54087V24.931Z" fill="#017200"></path><path id="Vector_5" d="M6.10117 20.5332H17.0595C17.4822 20.5332 17.8248 20.1907 17.8248 19.7679C17.8248 19.3452 17.4822 19.0026 17.0595 19.0026H6.54087V16.7972H31.0215V19.0025H20.5807C20.158 19.0025 19.8154 19.3451 19.8154 19.7678C19.8154 20.1906 20.158 20.5331 20.5807 20.5331H31.464C32.064 20.5331 32.5521 20.0438 32.5521 19.4424V16.3546C32.5521 15.7547 32.064 15.2666 31.464 15.2666H6.10117C5.49964 15.2666 5.01025 15.7547 5.01025 16.3546V19.4424C5.01025 20.0439 5.49964 20.5332 6.10117 20.5332Z" fill="#017200"></path><path id="Vector_6" d="M36.1897 0H1.54837C0.832449 0 0.25 0.582347 0.25 1.29827V48.7018C0.25 49.4177 0.832449 50 1.54837 50H36.1897C36.9072 50 37.4909 49.4177 37.4909 48.7017V1.29827C37.4909 0.582347 36.9072 0 36.1897 0ZM35.9603 48.4694H1.78061V1.53061H35.9603V48.4694Z" fill="#017200"></path><path id="Vector_7" d="M52.2468 9.3608C52.0548 8.97387 51.5572 8.32478 50.3839 8.32478H49.21V7.9955C49.21 5.64213 47.2948 3.72754 44.9408 3.72754C42.5868 3.72754 40.6716 5.64213 40.6716 7.9955V16.2999C40.6716 16.7226 41.0143 17.0652 41.4369 17.0652C41.8596 17.0652 42.2022 16.7226 42.2022 16.2999V11.9408H47.6794V23.9858H42.2022V19.8169C42.2022 19.3942 41.8596 19.0516 41.4369 19.0516C41.0143 19.0516 40.6716 19.3942 40.6716 19.8169V36.6157C40.6716 36.7402 40.702 36.8574 40.7548 36.9613C40.7553 36.9623 40.7551 36.9633 40.7556 36.9643L43.8721 43.0566C44.1563 43.6087 44.3807 44.0448 44.9432 44.0448H44.9444C45.5052 44.0441 45.7305 43.604 45.9913 43.0943L49.1261 36.9643C49.1272 36.9621 49.1276 36.9603 49.1285 36.9582C49.1802 36.8551 49.2101 36.7391 49.2101 36.6158V9.8554H50.384C50.8468 9.8554 50.9644 9.93948 50.9644 10.7118V16.395C50.9644 16.8177 51.307 17.1603 51.7297 17.1603C52.1523 17.1603 52.495 16.8177 52.495 16.395V10.7118C52.4949 10.3935 52.4949 9.8605 52.2468 9.3608ZM44.9413 41.7858L42.688 37.381H47.1938L44.9413 41.7858ZM47.6794 35.8504H42.2022V25.5165H47.6794V35.8504ZM47.6794 10.4103H42.2022V7.9956C42.2022 6.48621 43.4308 5.25825 44.9408 5.25825C46.4509 5.25825 47.6794 6.48621 47.6794 7.9956V10.4103Z" fill="#017200"></path></g></svg>
        </div>
          
        <div class="relative z-10">
          <div class="relative ">
          <div class="absolute left-[-3px] top-[-12px] w-[50px] h-[50px] bg-[#E8FDE8] rounded-full"></div>
            <div class="flex mb-6 px-3">
            <span class="text-2xl mr-3 relative z-10">
          <svg xmlns="http://www.w3.org/2000/svg" width="53" height="50" viewBox="0 0 53 50" fill="none"><g id="Group"><path id="Vector" d="M8.34294 7.87046H30.3431C30.7658 7.87046 31.1085 7.5279 31.1085 7.10515C31.1085 6.68239 30.7658 6.33984 30.3431 6.33984H8.34294C7.92029 6.33984 7.57764 6.68239 7.57764 7.10515C7.57764 7.5279 7.92029 7.87046 8.34294 7.87046Z" fill="#017200"></path><path id="Vector_2" d="M12.2099 10.0156C11.7872 10.0156 11.4446 10.3582 11.4446 10.7809C11.4446 11.2037 11.7872 11.5462 12.2099 11.5462H25.9892C26.4118 11.5462 26.7545 11.2037 26.7545 10.7809C26.7545 10.3582 26.4118 10.0156 25.9892 10.0156H12.2099Z" fill="#017200"></path><path id="Vector_3" d="M6.0867 42.4853H17.0595C17.4821 42.4853 17.8248 42.1427 17.8248 41.72C17.8248 41.2972 17.4821 40.9547 17.0595 40.9547H6.52353V33.2651H31.2145V40.9547H20.4308C20.0081 40.9547 19.6655 41.2972 19.6655 41.72C19.6655 42.1427 20.0081 42.4853 20.4308 42.4853H31.6541C32.2557 42.4853 32.7451 41.9947 32.7451 41.3916V32.828C32.7451 32.225 32.2557 31.7344 31.6541 31.7344H6.0867C5.48353 31.7344 4.99292 32.225 4.99292 32.828V41.3916C4.99292 41.9947 5.48363 42.4853 6.0867 42.4853Z" fill="#017200"></path><path id="Vector_4" d="M6.10117 28.6641H31.464C32.064 28.6641 32.5521 28.176 32.5521 27.5761V24.4882C32.5521 23.8883 32.064 23.4004 31.464 23.4004H6.10117C5.49964 23.4004 5.01025 23.8883 5.01025 24.4882V27.5761C5.01025 28.176 5.49964 28.6641 6.10117 28.6641ZM6.54087 24.931H31.0215V27.1335H6.54087V24.931Z" fill="#017200"></path><path id="Vector_5" d="M6.10117 20.5332H17.0595C17.4822 20.5332 17.8248 20.1907 17.8248 19.7679C17.8248 19.3452 17.4822 19.0026 17.0595 19.0026H6.54087V16.7972H31.0215V19.0025H20.5807C20.158 19.0025 19.8154 19.3451 19.8154 19.7678C19.8154 20.1906 20.158 20.5331 20.5807 20.5331H31.464C32.064 20.5331 32.5521 20.0438 32.5521 19.4424V16.3546C32.5521 15.7547 32.064 15.2666 31.464 15.2666H6.10117C5.49964 15.2666 5.01025 15.7547 5.01025 16.3546V19.4424C5.01025 20.0439 5.49964 20.5332 6.10117 20.5332Z" fill="#017200"></path><path id="Vector_6" d="M36.1897 0H1.54837C0.832449 0 0.25 0.582347 0.25 1.29827V48.7018C0.25 49.4177 0.832449 50 1.54837 50H36.1897C36.9072 50 37.4909 49.4177 37.4909 48.7017V1.29827C37.4909 0.582347 36.9072 0 36.1897 0ZM35.9603 48.4694H1.78061V1.53061H35.9603V48.4694Z" fill="#017200"></path><path id="Vector_7" d="M52.2468 9.3608C52.0548 8.97387 51.5572 8.32478 50.3839 8.32478H49.21V7.9955C49.21 5.64213 47.2948 3.72754 44.9408 3.72754C42.5868 3.72754 40.6716 5.64213 40.6716 7.9955V16.2999C40.6716 16.7226 41.0143 17.0652 41.4369 17.0652C41.8596 17.0652 42.2022 16.7226 42.2022 16.2999V11.9408H47.6794V23.9858H42.2022V19.8169C42.2022 19.3942 41.8596 19.0516 41.4369 19.0516C41.0143 19.0516 40.6716 19.3942 40.6716 19.8169V36.6157C40.6716 36.7402 40.702 36.8574 40.7548 36.9613C40.7553 36.9623 40.7551 36.9633 40.7556 36.9643L43.8721 43.0566C44.1563 43.6087 44.3807 44.0448 44.9432 44.0448H44.9444C45.5052 44.0441 45.7305 43.604 45.9913 43.0943L49.1261 36.9643C49.1272 36.9621 49.1276 36.9603 49.1285 36.9582C49.1802 36.8551 49.2101 36.7391 49.2101 36.6158V9.8554H50.384C50.8468 9.8554 50.9644 9.93948 50.9644 10.7118V16.395C50.9644 16.8177 51.307 17.1603 51.7297 17.1603C52.1523 17.1603 52.495 16.8177 52.495 16.395V10.7118C52.4949 10.3935 52.4949 9.8605 52.2468 9.3608ZM44.9413 41.7858L42.688 37.381H47.1938L44.9413 41.7858ZM47.6794 35.8504H42.2022V25.5165H47.6794V35.8504ZM47.6794 10.4103H42.2022V7.9956C42.2022 6.48621 43.4308 5.25825 44.9408 5.25825C46.4509 5.25825 47.6794 6.48621 47.6794 7.9956V10.4103Z" fill="#017200"></path></g></svg>
            </span>
            <h3 class="text-2xl font-bold text-[#017200]">Mohon</h3>
          </div>
           </div>
            <ul class="space-y-2 text-lg ">
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Bantuan Am
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Bantuan Pelajaran
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Sewaan Permis/ Tanah
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Sewaan Bazar Wakaf
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Wakaf Tanah
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-8 h-8 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Panduan Pelaksanaan Perakuan Permastautin
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Potongan Zakat Gaji Bulanan
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-8 h-8 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Kebenaran Potongan Gaji Wakaf Tunai
                </NuxtLink>
              </li>
            </ul>
           </div>
        </div>
      </div>

    <!-- Bayar -->
      <div class="relative mx-auto">
        <!-- Third Container (Largest - Bottom) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[335px] h-[560px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(0,84,165,1)_250%,rgba(0,84,165,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-0"></div>

        <!-- Second Container (Medium - Middle) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[340px] h-[550px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(0,84,165,1)_250%,rgba(0,84,165,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-10"></div>

        <!-- Main Container (Normal - Top) -->
      <div class="relative z-20 bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(0,84,165,1)_250%,rgba(0,84,165,1)_100%)] border-[#B6C1DB] border-[1px] rounded-2xl shadow-lg p-8 w-[350px] h-[540px] overflow-hidden">
        
        <!-- Inline SVG background -->
        <div class="absolute top-[-120px] right-[-230px] z-0 w-[450px] h-[450px] opacity-[0.05] pointer-events-none">
        <svg xmlns="http://www.w3.org/2000/svg" width="59" height="50" viewBox="0 0 49 50" fill="none" class="w-full h-full"><g id="Group"><path id="Vector" d="M40.4752 38.2219C40.8273 37.6107 40.9215 36.8553 40.6682 36.1392C40.2062 34.8406 38.757 34.164 37.4374 34.6309C37.4335 34.6323 37.4297 34.6336 37.4258 34.6351L35.0113 35.5352C35.0288 35.2156 34.9876 34.8899 34.877 34.5758C34.6522 33.9435 34.1932 33.439 33.5847 33.1552C32.9772 32.8719 32.2883 32.8418 31.6451 33.0707C31.6416 33.072 31.6381 33.0733 31.6347 33.0745L27.1353 34.7523C27.1461 34.4566 27.1016 34.1589 26.9998 33.8724C26.788 33.2759 26.3559 32.7974 25.7829 32.5251C25.1989 32.2475 24.5364 32.2162 23.909 32.4399L15.6861 35.4868C15.3688 35.3698 15.0752 35.2481 14.7904 35.1294C12.9435 34.3596 11.5703 33.9336 8.05332 35.1075C7.88086 34.1958 7.07969 33.5037 6.11865 33.5037H2.25498C1.16855 33.5037 0.284668 34.3876 0.284668 35.4741V39.2071C0.284668 39.6147 0.615039 39.9452 1.02266 39.9452C1.43027 39.9452 1.76064 39.6147 1.76064 39.2071V35.4741C1.76064 35.2016 1.98242 34.9798 2.25498 34.9798H6.11855C6.38643 34.9798 6.61279 35.2061 6.61279 35.4741V46.7702C6.61279 47.0382 6.38643 47.2645 6.11855 47.2645H2.25498C1.98252 47.2645 1.76064 47.0428 1.76064 46.7702V42.6034C1.76064 42.1957 1.43027 41.8653 1.02266 41.8653C0.615039 41.8653 0.284668 42.1957 0.284668 42.6034V46.7702C0.284668 47.8567 1.16855 48.7406 2.25498 48.7406H6.11855C7.03389 48.7406 7.80303 48.1122 8.02334 47.265C10.1458 47.3303 11.3314 47.5551 13.8513 48.3091L18.2806 49.6335C19.1039 49.8784 20.2022 50 21.3061 50C22.4628 50 23.6257 49.8663 24.4833 49.6006C26.7521 48.8997 30.3631 47.5233 31.7924 46.9421L40.6246 43.3479C41.2766 43.0815 41.7633 42.5428 41.9948 41.831C42.2649 41.0008 42.1453 40.0203 41.6833 39.2736C41.386 38.7908 40.969 38.437 40.4752 38.2219ZM33.6597 37.6146C33.6929 37.6048 33.7257 37.5926 33.7578 37.578L37.935 36.0206C38.4963 35.8249 39.0852 36.0935 39.277 36.6326C39.465 37.1643 39.1852 37.75 38.6531 37.9382C38.6494 37.9396 38.6456 37.941 38.6419 37.9423L28.0126 41.8968C28.0122 41.6668 27.9885 41.4341 27.937 41.2025C27.8329 40.7333 27.6307 40.3138 27.3526 39.966L33.6597 37.6146ZM32.1444 34.46C32.4186 34.3638 32.7084 34.3755 32.9609 34.4932C33.2084 34.6085 33.3949 34.8136 33.4855 35.0683C33.6358 35.4952 33.4822 35.976 33.1206 36.2402L25.7883 38.9738L22.8013 37.9438L32.1444 34.46ZM24.413 33.8273C24.6601 33.7393 24.9215 33.7501 25.1492 33.8584C25.3657 33.9614 25.529 34.1417 25.6088 34.3664C25.6892 34.593 25.6755 34.839 25.5703 35.0591C25.4648 35.2798 25.2812 35.4459 25.0532 35.5268C25.0366 35.5328 25.0208 35.5399 25.0048 35.5468L20.6063 37.1869L17.8815 36.2474L24.413 33.8273ZM40.5911 41.3744C40.5239 41.581 40.3783 41.854 40.0673 41.9811L31.2361 45.5749C29.8277 46.1477 26.2732 47.5029 24.047 48.1906C22.6276 48.6304 20.1297 48.6434 18.7022 48.2191L14.2742 46.8951C11.6403 46.107 10.3324 45.8611 8.08867 45.7905V36.6563C11.6138 35.407 12.6661 35.8435 14.2224 36.4921C14.6001 36.6495 25.5574 40.4557 25.5574 40.4557C25.5652 40.4584 25.5731 40.461 25.5811 40.4634C26.2395 40.6659 26.4401 41.2715 26.4958 41.5225C26.5892 41.9431 26.525 42.365 26.3297 42.7002C26.3278 42.7034 26.3261 42.7067 26.3243 42.7098C26.2542 42.8281 26.168 42.9355 26.066 43.0278C25.5125 43.5282 24.5365 43.5821 23.3171 43.1794L17.0864 41.1238C16.6995 40.9959 16.282 41.2064 16.1543 41.5934C16.0267 41.9805 16.2369 42.3978 16.624 42.5255L22.8545 44.5811C23.5953 44.8257 24.2305 44.921 24.7707 44.921C25.9475 44.921 26.6732 44.4687 27.0561 44.1226C27.204 43.9888 27.3359 43.8405 27.4513 43.6806L38.283 39.6508C38.2932 39.6474 38.3034 39.6448 38.3135 39.641C39.0424 39.363 39.9806 39.3239 40.427 40.0489C40.6641 40.4319 40.7284 40.9522 40.5911 41.3744Z" fill="#0054A5"></path><path id="Vector_2" d="M48.4851 10.9831L43.2006 1.04512C42.9549 0.581546 42.5421 0.241409 42.0384 0.0873079C41.5354 -0.0665983 41.0033 -0.0158171 40.5416 0.230081L37.1391 2.03848C36.2013 2.53819 35.8356 3.69395 36.3015 4.63995C35.9368 4.83653 35.6023 5.01914 35.2944 5.18711C32.5818 6.66748 31.7631 7.11426 28.1001 7.55078C27.6953 7.59903 27.4064 7.96621 27.4546 8.371C27.4993 8.7461 27.8179 9.02178 28.1865 9.02178C28.2157 9.02178 28.2451 9.02002 28.2748 9.01651C32.2203 8.54629 33.2499 7.98438 36.0015 6.48282C36.3047 6.31739 36.6338 6.1378 36.9916 5.94483L40.4981 12.5406C39.0803 13.3789 38.1651 14.2521 37.4282 15.4457C36.1965 17.4441 34.6786 18.2137 33.2108 18.9579C32.5563 19.2897 31.8796 19.6328 31.2491 20.0741L25.2748 24.2624C25.1151 24.3606 24.9598 24.4362 24.8122 24.489C24.7996 24.4927 24.787 24.4966 24.7746 24.5011C24.5379 24.5799 24.3222 24.5986 24.1439 24.5508C23.9029 24.4862 23.6941 24.2907 23.5234 23.97C23.0981 23.171 23.7354 20.8147 24.8947 19.6743L28.6359 15.9887C28.6513 15.9735 28.666 15.9576 28.68 15.9412C29.3218 15.1869 29.2914 14.5762 29.1529 14.1966C28.9211 13.5612 28.25 13.1463 27.1575 12.9631C24.0476 12.4431 22.8431 13.226 22.1017 14.2542C21.4274 13.8599 20.7008 13.5563 19.9332 13.3487C19.5011 13.2314 19.0619 13.1481 18.6193 13.0974L18.6985 12.9505C20.0296 10.4784 22.0363 9.75362 24.8428 9.38526C25.247 9.33223 25.5316 8.96162 25.4785 8.55752C25.4254 8.15332 25.0545 7.86875 24.6507 7.92178C21.9005 8.28272 19.1186 9.05694 17.3992 12.2501L16.9589 13.0659C15.2412 13.1979 13.5643 13.8407 12.1952 14.9015C10.6602 16.0907 9.58126 17.7123 9.07491 19.5905C7.80245 24.3049 10.6026 29.1756 15.3169 30.448C16.0872 30.6558 16.8642 30.7557 17.6308 30.7556C20.9598 30.7555 24.0897 28.8719 25.5933 25.7623C25.7523 25.6897 25.9119 25.6047 26.0718 25.5051C26.083 25.498 26.0941 25.4907 26.105 25.4831L32.0961 21.2831C32.6404 20.9021 33.2417 20.5972 33.8783 20.2744C35.4517 19.4767 37.235 18.5726 38.6845 16.2206C39.2757 15.2632 40.0276 14.5458 41.1924 13.8464L41.6137 14.6388C41.9665 15.301 42.6481 15.679 43.3523 15.6789C43.6633 15.6789 43.9788 15.6051 44.2722 15.4496L47.6704 13.642C48.1339 13.3962 48.474 12.9834 48.6281 12.4797C48.7819 11.9768 48.7312 11.4452 48.4851 10.9831ZM26.9138 14.419C27.4576 14.5103 27.6747 14.6406 27.7465 14.6967C27.7284 14.743 27.6839 14.8303 27.5751 14.9617L25.1957 17.3058C24.6907 16.4732 24.0499 15.7271 23.3045 15.1024C23.7541 14.4856 24.5209 14.0189 26.9138 14.419ZM15.7014 29.0231C11.773 27.9627 9.43956 23.9038 10.5001 19.975C11.3433 16.847 14.1935 14.6029 17.4304 14.518C18.1442 14.5001 18.8557 14.5858 19.5473 14.7735C20.4018 15.0046 21.194 15.3771 21.9016 15.8808C22.8151 16.531 23.5732 17.3898 24.1089 18.3767L23.8593 18.6226C22.416 20.0421 21.3631 23.0533 22.2205 24.6639C22.6822 25.5312 23.3133 25.8564 23.7614 25.9767C23.766 25.9779 23.7708 25.9787 23.7754 25.9799C22.0468 28.5939 18.8072 29.8607 15.7014 29.0231ZM47.2165 12.0482C47.1779 12.1744 47.0935 12.2773 46.9779 12.3387L43.5797 14.1463C43.3406 14.2731 43.043 14.1828 42.9165 13.9456L37.6313 4.00342C37.5066 3.76924 37.599 3.46592 37.8325 3.34151L41.235 1.53321C41.3053 1.4958 41.3823 1.47676 41.4608 1.47676C41.5093 1.47676 41.5584 1.48409 41.6067 1.49883C41.7328 1.53741 41.8358 1.62188 41.897 1.73731L47.1819 11.6761C47.182 11.6763 47.1821 11.6764 47.1822 11.6766C47.2427 11.7904 47.2549 11.9224 47.2165 12.0482Z" fill="#0054A5"></path></g></svg>
        </div>
          
        <div class="relative z-10">
          <div class="relative ">
          <div class="absolute left-[-3px] top-[-12px] w-[50px] h-[50px] bg-[#E6EEFF] rounded-full"></div>
            <div class="flex mb-6 px-3">
            <span class="text-2xl mr-3 relative z-10">
            <svg xmlns="http://www.w3.org/2000/svg" width="49" height="50" viewBox="0 0 49 50" fill="none"><g id="Group"><path id="Vector" d="M40.4752 38.2219C40.8273 37.6107 40.9215 36.8553 40.6682 36.1392C40.2062 34.8406 38.757 34.164 37.4374 34.6309C37.4335 34.6323 37.4297 34.6336 37.4258 34.6351L35.0113 35.5352C35.0288 35.2156 34.9876 34.8899 34.877 34.5758C34.6522 33.9435 34.1932 33.439 33.5847 33.1552C32.9772 32.8719 32.2883 32.8418 31.6451 33.0707C31.6416 33.072 31.6381 33.0733 31.6347 33.0745L27.1353 34.7523C27.1461 34.4566 27.1016 34.1589 26.9998 33.8724C26.788 33.2759 26.3559 32.7974 25.7829 32.5251C25.1989 32.2475 24.5364 32.2162 23.909 32.4399L15.6861 35.4868C15.3688 35.3698 15.0752 35.2481 14.7904 35.1294C12.9435 34.3596 11.5703 33.9336 8.05332 35.1075C7.88086 34.1958 7.07969 33.5037 6.11865 33.5037H2.25498C1.16855 33.5037 0.284668 34.3876 0.284668 35.4741V39.2071C0.284668 39.6147 0.615039 39.9452 1.02266 39.9452C1.43027 39.9452 1.76064 39.6147 1.76064 39.2071V35.4741C1.76064 35.2016 1.98242 34.9798 2.25498 34.9798H6.11855C6.38643 34.9798 6.61279 35.2061 6.61279 35.4741V46.7702C6.61279 47.0382 6.38643 47.2645 6.11855 47.2645H2.25498C1.98252 47.2645 1.76064 47.0428 1.76064 46.7702V42.6034C1.76064 42.1957 1.43027 41.8653 1.02266 41.8653C0.615039 41.8653 0.284668 42.1957 0.284668 42.6034V46.7702C0.284668 47.8567 1.16855 48.7406 2.25498 48.7406H6.11855C7.03389 48.7406 7.80303 48.1122 8.02334 47.265C10.1458 47.3303 11.3314 47.5551 13.8513 48.3091L18.2806 49.6335C19.1039 49.8784 20.2022 50 21.3061 50C22.4628 50 23.6257 49.8663 24.4833 49.6006C26.7521 48.8997 30.3631 47.5233 31.7924 46.9421L40.6246 43.3479C41.2766 43.0815 41.7633 42.5428 41.9948 41.831C42.2649 41.0008 42.1453 40.0203 41.6833 39.2736C41.386 38.7908 40.969 38.437 40.4752 38.2219ZM33.6597 37.6146C33.6929 37.6048 33.7257 37.5926 33.7578 37.578L37.935 36.0206C38.4963 35.8249 39.0852 36.0935 39.277 36.6326C39.465 37.1643 39.1852 37.75 38.6531 37.9382C38.6494 37.9396 38.6456 37.941 38.6419 37.9423L28.0126 41.8968C28.0122 41.6668 27.9885 41.4341 27.937 41.2025C27.8329 40.7333 27.6307 40.3138 27.3526 39.966L33.6597 37.6146ZM32.1444 34.46C32.4186 34.3638 32.7084 34.3755 32.9609 34.4932C33.2084 34.6085 33.3949 34.8136 33.4855 35.0683C33.6358 35.4952 33.4822 35.976 33.1206 36.2402L25.7883 38.9738L22.8013 37.9438L32.1444 34.46ZM24.413 33.8273C24.6601 33.7393 24.9215 33.7501 25.1492 33.8584C25.3657 33.9614 25.529 34.1417 25.6088 34.3664C25.6892 34.593 25.6755 34.839 25.5703 35.0591C25.4648 35.2798 25.2812 35.4459 25.0532 35.5268C25.0366 35.5328 25.0208 35.5399 25.0048 35.5468L20.6063 37.1869L17.8815 36.2474L24.413 33.8273ZM40.5911 41.3744C40.5239 41.581 40.3783 41.854 40.0673 41.9811L31.2361 45.5749C29.8277 46.1477 26.2732 47.5029 24.047 48.1906C22.6276 48.6304 20.1297 48.6434 18.7022 48.2191L14.2742 46.8951C11.6403 46.107 10.3324 45.8611 8.08867 45.7905V36.6563C11.6138 35.407 12.6661 35.8435 14.2224 36.4921C14.6001 36.6495 25.5574 40.4557 25.5574 40.4557C25.5652 40.4584 25.5731 40.461 25.5811 40.4634C26.2395 40.6659 26.4401 41.2715 26.4958 41.5225C26.5892 41.9431 26.525 42.365 26.3297 42.7002C26.3278 42.7034 26.3261 42.7067 26.3243 42.7098C26.2542 42.8281 26.168 42.9355 26.066 43.0278C25.5125 43.5282 24.5365 43.5821 23.3171 43.1794L17.0864 41.1238C16.6995 40.9959 16.282 41.2064 16.1543 41.5934C16.0267 41.9805 16.2369 42.3978 16.624 42.5255L22.8545 44.5811C23.5953 44.8257 24.2305 44.921 24.7707 44.921C25.9475 44.921 26.6732 44.4687 27.0561 44.1226C27.204 43.9888 27.3359 43.8405 27.4513 43.6806L38.283 39.6508C38.2932 39.6474 38.3034 39.6448 38.3135 39.641C39.0424 39.363 39.9806 39.3239 40.427 40.0489C40.6641 40.4319 40.7284 40.9522 40.5911 41.3744Z" fill="#0054A5"></path><path id="Vector_2" d="M48.4851 10.9831L43.2006 1.04512C42.9549 0.581546 42.5421 0.241409 42.0384 0.0873079C41.5354 -0.0665983 41.0033 -0.0158171 40.5416 0.230081L37.1391 2.03848C36.2013 2.53819 35.8356 3.69395 36.3015 4.63995C35.9368 4.83653 35.6023 5.01914 35.2944 5.18711C32.5818 6.66748 31.7631 7.11426 28.1001 7.55078C27.6953 7.59903 27.4064 7.96621 27.4546 8.371C27.4993 8.7461 27.8179 9.02178 28.1865 9.02178C28.2157 9.02178 28.2451 9.02002 28.2748 9.01651C32.2203 8.54629 33.2499 7.98438 36.0015 6.48282C36.3047 6.31739 36.6338 6.1378 36.9916 5.94483L40.4981 12.5406C39.0803 13.3789 38.1651 14.2521 37.4282 15.4457C36.1965 17.4441 34.6786 18.2137 33.2108 18.9579C32.5563 19.2897 31.8796 19.6328 31.2491 20.0741L25.2748 24.2624C25.1151 24.3606 24.9598 24.4362 24.8122 24.489C24.7996 24.4927 24.787 24.4966 24.7746 24.5011C24.5379 24.5799 24.3222 24.5986 24.1439 24.5508C23.9029 24.4862 23.6941 24.2907 23.5234 23.97C23.0981 23.171 23.7354 20.8147 24.8947 19.6743L28.6359 15.9887C28.6513 15.9735 28.666 15.9576 28.68 15.9412C29.3218 15.1869 29.2914 14.5762 29.1529 14.1966C28.9211 13.5612 28.25 13.1463 27.1575 12.9631C24.0476 12.4431 22.8431 13.226 22.1017 14.2542C21.4274 13.8599 20.7008 13.5563 19.9332 13.3487C19.5011 13.2314 19.0619 13.1481 18.6193 13.0974L18.6985 12.9505C20.0296 10.4784 22.0363 9.75362 24.8428 9.38526C25.247 9.33223 25.5316 8.96162 25.4785 8.55752C25.4254 8.15332 25.0545 7.86875 24.6507 7.92178C21.9005 8.28272 19.1186 9.05694 17.3992 12.2501L16.9589 13.0659C15.2412 13.1979 13.5643 13.8407 12.1952 14.9015C10.6602 16.0907 9.58126 17.7123 9.07491 19.5905C7.80245 24.3049 10.6026 29.1756 15.3169 30.448C16.0872 30.6558 16.8642 30.7557 17.6308 30.7556C20.9598 30.7555 24.0897 28.8719 25.5933 25.7623C25.7523 25.6897 25.9119 25.6047 26.0718 25.5051C26.083 25.498 26.0941 25.4907 26.105 25.4831L32.0961 21.2831C32.6404 20.9021 33.2417 20.5972 33.8783 20.2744C35.4517 19.4767 37.235 18.5726 38.6845 16.2206C39.2757 15.2632 40.0276 14.5458 41.1924 13.8464L41.6137 14.6388C41.9665 15.301 42.6481 15.679 43.3523 15.6789C43.6633 15.6789 43.9788 15.6051 44.2722 15.4496L47.6704 13.642C48.1339 13.3962 48.474 12.9834 48.6281 12.4797C48.7819 11.9768 48.7312 11.4452 48.4851 10.9831ZM26.9138 14.419C27.4576 14.5103 27.6747 14.6406 27.7465 14.6967C27.7284 14.743 27.6839 14.8303 27.5751 14.9617L25.1957 17.3058C24.6907 16.4732 24.0499 15.7271 23.3045 15.1024C23.7541 14.4856 24.5209 14.0189 26.9138 14.419ZM15.7014 29.0231C11.773 27.9627 9.43956 23.9038 10.5001 19.975C11.3433 16.847 14.1935 14.6029 17.4304 14.518C18.1442 14.5001 18.8557 14.5858 19.5473 14.7735C20.4018 15.0046 21.194 15.3771 21.9016 15.8808C22.8151 16.531 23.5732 17.3898 24.1089 18.3767L23.8593 18.6226C22.416 20.0421 21.3631 23.0533 22.2205 24.6639C22.6822 25.5312 23.3133 25.8564 23.7614 25.9767C23.766 25.9779 23.7708 25.9787 23.7754 25.9799C22.0468 28.5939 18.8072 29.8607 15.7014 29.0231ZM47.2165 12.0482C47.1779 12.1744 47.0935 12.2773 46.9779 12.3387L43.5797 14.1463C43.3406 14.2731 43.043 14.1828 42.9165 13.9456L37.6313 4.00342C37.5066 3.76924 37.599 3.46592 37.8325 3.34151L41.235 1.53321C41.3053 1.4958 41.3823 1.47676 41.4608 1.47676C41.5093 1.47676 41.5584 1.48409 41.6067 1.49883C41.7328 1.53741 41.8358 1.62188 41.897 1.73731L47.1819 11.6761C47.182 11.6763 47.1821 11.6764 47.1822 11.6766C47.2427 11.7904 47.2549 11.9224 47.2165 12.0482Z" fill="#0054A5"></path></g></svg>
          </span>
            <h3 class="text-2xl font-bold text-[#0054A5]">Bayar</h3>
          </div>
           </div>
            <ul class="space-y-2 text-lg ">
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                   Bayaran Zakat (Online)
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Bayaran Zakat (Transfer)
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Bayaran Wakaf Tunai
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Bayaran Sewaan
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Fidyah
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Wang Tidak Patuh Syarak
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Kafarah
                </NuxtLink>
              </li>
            </ul>
           </div>
        </div>
      </div>
  </div>
</div>


  </div>
</section>

  <!-- Kemudahan (Phone) -->
<section
  class="relative pt-32 pb-16 bg-cover bg-center block md:hidden lg-hidden xl:hidden 2xl:hidden"
  style="background-image: url('https://s3-alpha-sig.figma.com/img/2ed4/26c1/b652a53cf78c98f970d20258c5d34d04?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=pb1HWDBM-VYerYAj0KzvHe5tEooVu2YWpgRdtP1l2KNwogoRvjsW8yobYCm8siI4ZLcu2hgN7zKHqw0KadZOJzsJCqODy~Yu-eQNBxON5IwNARzOijezWpj2GfoTseo7kGak1lLmFnBlSCz8sBp2CcFmzKZHdTc2MN8wtyUvmXtTgt16NSYBSItn3n1W-wr9kwz4~DdI41G~88QQQXOiVVt27RAU1NxMuYPJDJpnyz~liBKY~5-3Qd1qwDedhhBkkXGB7UK0vO2k9J1jKme93D85c-Ula-5aKS-LLeuBPyMuoX~rpmHIoUx9kSkOe5Qpl-8wcJX3-fqp9zKONnN38A');"
>
  <!-- Overlay -->
  <div class="absolute inset-0 bg-[#F6FBFF]/90"></div>

  <div class="relative mx-auto px-4 md:px-16 max-w-screen-xl">
    <span class="block w-[32px] h-[4px] bg-[#0054A5] mb-2 rounded"></span>
    <h2 class="text-4xl font-bold text-[#374151] mb-6">
      Kemudahan Anda Adalah Keutamaan Kami
    </h2>
    <p class="text-gray-600 mb-12 text-base">
      MAIPs komited dalam menyediakan perkhidmatan digital yang memudahkan urusan anda.
    </p>

<div class="relative">
  <div class="grid grid-cols-1 gap-10">
    <!-- Semak -->
      <div class="relative mx-auto">
        <!-- Third Container (Largest - Bottom) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[335px] h-[560px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(255,254,231,1)_50%,rgba(255,200,180,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-0"></div>

        <!-- Second Container (Medium - Middle) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[340px] h-[550px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(255,254,231,1)_50%,rgba(255,200,180,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-10"></div>

        <!-- Main Container (Normal - Top) -->
      <div class="relative z-20 bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(255,254,231,1)_50%,rgba(255,200,180,1)_100%)] border-[#B6C1DB] border-[1px] rounded-2xl shadow-lg p-8 w-[350px] h-[540px] overflow-hidden">


        <!-- Inline SVG background -->
        <div class="absolute top-[-120px] right-[-230px] z-0 w-[500px] h-[500px] opacity-[0.05] pointer-events-none transfrom scale-x-[-1]">
                        <svg xmlns="http://www.w3.org/2000/svg" width="500" height="500" viewBox="0 0 51 50" fill="none"
                        class="w-full h-full"><g id="Group"><path id="Vector" d="M26.1752 14.6679H33.9067C34.5798 14.6679 35.1274 14.1204 35.1274 13.4472V5.68264C35.1274 5.00948 34.5798 4.46191 33.9067 4.46191H26.1752C25.502 4.46191 24.9545 5.00948 24.9545 5.68264V7.51978C24.9545 7.92437 25.2823 8.25221 25.6869 8.25221C26.0915 8.25221 26.4193 7.92437 26.4193 7.51978V5.92678H33.6625V13.2032H26.4193V11.0439C26.4193 10.6393 26.0915 10.3114 25.6869 10.3114C25.2823 10.3114 24.9545 10.6393 24.9545 11.0439V13.4473C24.9545 14.1204 25.502 14.6679 26.1752 14.6679Z" fill="#FF5A1F"></path><path id="Vector_2" d="M12.5342 13.4844H22.5122C22.9168 13.4844 23.2446 13.1566 23.2446 12.752C23.2446 12.3474 22.9168 12.0195 22.5122 12.0195H12.5342C12.1296 12.0195 11.8018 12.3474 11.8018 12.752C11.8018 13.1566 12.1297 13.4844 12.5342 13.4844Z" fill="#FF5A1F"></path><path id="Vector_3" d="M29.2313 18.9434C29.2313 18.5388 28.9035 18.2109 28.4989 18.2109H18.4302C18.0257 18.2109 17.6978 18.5388 17.6978 18.9434C17.6978 19.348 18.0257 19.6758 18.4302 19.6758H28.4989C28.9034 19.6758 29.2313 19.3479 29.2313 18.9434Z" fill="#FF5A1F"></path><path id="Vector_4" d="M12.5342 10.2969H22.5122C22.9168 10.2969 23.2446 9.96906 23.2446 9.56446C23.2446 9.15987 22.9168 8.83203 22.5122 8.83203H12.5342C12.1296 8.83203 11.8018 9.15987 11.8018 9.56446C11.8018 9.96906 12.1297 10.2969 12.5342 10.2969Z" fill="#FF5A1F"></path><path id="Vector_5" d="M12.5342 7.11038H22.5122C22.9168 7.11038 23.2446 6.78254 23.2446 6.37794C23.2446 5.97335 22.9168 5.64551 22.5122 5.64551H12.5342C12.1296 5.64551 11.8018 5.97335 11.8018 6.37794C11.8018 6.78254 12.1297 7.11038 12.5342 7.11038Z" fill="#FF5A1F"></path><path id="Vector_6" d="M12.5342 27.7803H27.5593C27.9639 27.7803 28.2918 27.4525 28.2918 27.0479C28.2918 26.6433 27.9639 26.3154 27.5593 26.3154H12.5342C12.1296 26.3154 11.8018 26.6433 11.8018 27.0479C11.8018 27.4525 12.1297 27.7803 12.5342 27.7803Z" fill="#FF5A1F"></path><path id="Vector_7" d="M12.5342 23.6826H24.417C24.8216 23.6826 25.1494 23.3548 25.1494 22.9502C25.1494 22.5456 24.8216 22.2178 24.417 22.2178H12.5342C12.1296 22.2178 11.8018 22.5456 11.8018 22.9502C11.8018 23.3548 12.1297 23.6826 12.5342 23.6826Z" fill="#FF5A1F"></path><path id="Vector_8" d="M34.4404 22.2178H27.5918C27.1872 22.2178 26.8594 22.5456 26.8594 22.9502C26.8594 23.3548 27.1872 23.6826 27.5918 23.6826H34.4404C34.845 23.6826 35.1728 23.3548 35.1728 22.9502C35.1728 22.5456 34.8449 22.2178 34.4404 22.2178Z" fill="#FF5A1F"></path><path id="Vector_9" d="M50.0627 45.3059C50.0538 45.2971 50.0446 45.2886 50.0354 45.2803L45.5281 41.2698C46.2403 39.9723 46.6467 38.5185 46.7007 37.0032C46.7151 36.5989 46.3991 36.2596 45.9949 36.2451C45.5899 36.2331 45.2513 36.5468 45.2367 36.951C45.1258 41.2655 41.4714 44.8193 37.1482 44.7761C32.6853 44.7761 29.0543 41.133 29.0543 36.6551C28.9867 32.2666 32.7656 28.4719 37.1482 28.5341C40.5623 28.5341 43.6267 30.7006 44.7735 33.9251C44.909 34.3061 45.3282 34.5055 45.7089 34.3698C46.0901 34.2342 46.2891 33.8154 46.1536 33.4343C44.9303 29.9944 41.8578 27.5751 38.3022 27.1401V1.22072C38.3022 0.547567 37.7546 0 37.0814 0H9.84759C9.17444 0 8.62687 0.547567 8.62687 1.22072V3.86989H5.99255C5.3194 3.86989 4.77183 4.41745 4.77183 5.09061V7.73968H2.13741C1.46425 7.73968 0.916687 8.28724 0.916687 8.9604V45.4987C0.916687 46.1718 1.46425 46.7194 2.13741 46.7194H25.4594C26.1325 46.7194 26.6801 46.1718 26.6801 45.4987V42.8495H29.8597C31.6145 44.9228 34.2306 46.2411 37.1483 46.2411C38.7517 46.2411 40.2995 45.8447 41.6768 45.1L46.2183 49.1674C47.2982 50.2372 49.0479 50.2963 50.1314 49.227C51.2157 48.1907 51.1502 46.3308 50.0627 45.3059ZM10.0917 1.46487H36.8373V27.0753C33.7243 27.1768 30.8955 28.7954 29.2049 31.3231H26.2311C25.8265 31.3231 25.4986 31.6509 25.4986 32.0555C25.4986 32.4601 25.8265 32.7879 26.2311 32.7879H28.3997C28.3016 33.011 28.2113 33.2386 28.1296 33.4712C27.7712 34.4923 27.5896 35.5636 27.5896 36.6551C27.5896 36.9449 27.6033 37.2315 27.6284 37.5149H17.4386C18.4439 36.5518 19.0721 35.1958 19.0721 33.6945V32.788H23.0564C23.461 32.788 23.7888 32.4602 23.7888 32.0556C23.7888 31.651 23.461 31.3232 23.0564 31.3232H18.3396C17.935 31.3232 17.6072 31.651 17.6072 32.0556V33.6945C17.6072 35.8011 15.9011 37.5149 13.8042 37.5149H10.0917V1.46487ZM6.2367 41.3846V31.3726C6.2367 30.968 5.90886 30.6401 5.50426 30.6401C5.09967 30.6401 4.77183 30.968 4.77183 31.3726V41.6287C4.77183 42.3019 5.3194 42.8494 5.99255 42.8494H25.2152V45.2544H2.38155V9.20454H4.77183V28.2767C4.77183 28.6813 5.09967 29.0092 5.50426 29.0092C5.90886 29.0092 6.2367 28.6813 6.2367 28.2767V5.33475H8.62697V38.2473C8.62697 38.6519 8.9548 38.9797 9.3594 38.9797H27.8744C28.087 39.832 28.4132 40.6394 28.8366 41.3847H6.2367V41.3846ZM49.1004 48.1864C48.5935 48.6917 47.7338 48.6401 47.21 48.089L42.9504 44.2739C43.6079 43.7701 44.2143 43.1649 44.7186 42.5101L49.0463 46.361C49.5457 46.8419 49.6036 47.7018 49.1004 48.1864Z" fill="#FF5A1F"></path><path id="Vector_10" d="M37.1484 30.3951C33.7686 30.347 30.8537 33.2723 30.9051 36.6554C30.9051 40.1073 33.7058 42.9155 37.1484 42.9155C40.5908 42.9155 43.3915 40.1073 43.3915 36.6554C43.3915 33.2035 40.5908 30.3951 37.1484 30.3951ZM37.1484 41.4506C34.5136 41.4506 32.37 39.2995 32.37 36.6553C32.3299 34.0642 34.561 31.8233 37.1484 31.8599C39.7831 31.8599 41.9267 34.011 41.9267 36.6553C41.9267 39.2995 39.7832 41.4506 37.1484 41.4506Z" fill="#FF5A1F"></path></g></svg>
          
        </div>
          
        <div class="relative z-10">
      <div class="relative ">
      <div class="absolute left-[-3px] top-[-12px] w-[50px] h-[50px] bg-[#FFE4DA] rounded-full"></div>
        <div class="flex mb-6 px-3">
        <span class="text-2xl mr-3 relative z-10">
              <svg xmlns="http://www.w3.org/2000/svg" width="60" height="60" viewBox="0 0 51 50" fill="none"><g id="Group"><path id="Vector" d="M26.1752 14.6679H33.9067C34.5798 14.6679 35.1274 14.1204 35.1274 13.4472V5.68264C35.1274 5.00948 34.5798 4.46191 33.9067 4.46191H26.1752C25.502 4.46191 24.9545 5.00948 24.9545 5.68264V7.51978C24.9545 7.92437 25.2823 8.25221 25.6869 8.25221C26.0915 8.25221 26.4193 7.92437 26.4193 7.51978V5.92678H33.6625V13.2032H26.4193V11.0439C26.4193 10.6393 26.0915 10.3114 25.6869 10.3114C25.2823 10.3114 24.9545 10.6393 24.9545 11.0439V13.4473C24.9545 14.1204 25.502 14.6679 26.1752 14.6679Z" fill="#FF5A1F"></path><path id="Vector_2" d="M12.5342 13.4844H22.5122C22.9168 13.4844 23.2446 13.1566 23.2446 12.752C23.2446 12.3474 22.9168 12.0195 22.5122 12.0195H12.5342C12.1296 12.0195 11.8018 12.3474 11.8018 12.752C11.8018 13.1566 12.1297 13.4844 12.5342 13.4844Z" fill="#FF5A1F"></path><path id="Vector_3" d="M29.2313 18.9434C29.2313 18.5388 28.9035 18.2109 28.4989 18.2109H18.4302C18.0257 18.2109 17.6978 18.5388 17.6978 18.9434C17.6978 19.348 18.0257 19.6758 18.4302 19.6758H28.4989C28.9034 19.6758 29.2313 19.3479 29.2313 18.9434Z" fill="#FF5A1F"></path><path id="Vector_4" d="M12.5342 10.2969H22.5122C22.9168 10.2969 23.2446 9.96906 23.2446 9.56446C23.2446 9.15987 22.9168 8.83203 22.5122 8.83203H12.5342C12.1296 8.83203 11.8018 9.15987 11.8018 9.56446C11.8018 9.96906 12.1297 10.2969 12.5342 10.2969Z" fill="#FF5A1F"></path><path id="Vector_5" d="M12.5342 7.11038H22.5122C22.9168 7.11038 23.2446 6.78254 23.2446 6.37794C23.2446 5.97335 22.9168 5.64551 22.5122 5.64551H12.5342C12.1296 5.64551 11.8018 5.97335 11.8018 6.37794C11.8018 6.78254 12.1297 7.11038 12.5342 7.11038Z" fill="#FF5A1F"></path><path id="Vector_6" d="M12.5342 27.7803H27.5593C27.9639 27.7803 28.2918 27.4525 28.2918 27.0479C28.2918 26.6433 27.9639 26.3154 27.5593 26.3154H12.5342C12.1296 26.3154 11.8018 26.6433 11.8018 27.0479C11.8018 27.4525 12.1297 27.7803 12.5342 27.7803Z" fill="#FF5A1F"></path><path id="Vector_7" d="M12.5342 23.6826H24.417C24.8216 23.6826 25.1494 23.3548 25.1494 22.9502C25.1494 22.5456 24.8216 22.2178 24.417 22.2178H12.5342C12.1296 22.2178 11.8018 22.5456 11.8018 22.9502C11.8018 23.3548 12.1297 23.6826 12.5342 23.6826Z" fill="#FF5A1F"></path><path id="Vector_8" d="M34.4404 22.2178H27.5918C27.1872 22.2178 26.8594 22.5456 26.8594 22.9502C26.8594 23.3548 27.1872 23.6826 27.5918 23.6826H34.4404C34.845 23.6826 35.1728 23.3548 35.1728 22.9502C35.1728 22.5456 34.8449 22.2178 34.4404 22.2178Z" fill="#FF5A1F"></path><path id="Vector_9" d="M50.0627 45.3059C50.0538 45.2971 50.0446 45.2886 50.0354 45.2803L45.5281 41.2698C46.2403 39.9723 46.6467 38.5185 46.7007 37.0032C46.7151 36.5989 46.3991 36.2596 45.9949 36.2451C45.5899 36.2331 45.2513 36.5468 45.2367 36.951C45.1258 41.2655 41.4714 44.8193 37.1482 44.7761C32.6853 44.7761 29.0543 41.133 29.0543 36.6551C28.9867 32.2666 32.7656 28.4719 37.1482 28.5341C40.5623 28.5341 43.6267 30.7006 44.7735 33.9251C44.909 34.3061 45.3282 34.5055 45.7089 34.3698C46.0901 34.2342 46.2891 33.8154 46.1536 33.4343C44.9303 29.9944 41.8578 27.5751 38.3022 27.1401V1.22072C38.3022 0.547567 37.7546 0 37.0814 0H9.84759C9.17444 0 8.62687 0.547567 8.62687 1.22072V3.86989H5.99255C5.3194 3.86989 4.77183 4.41745 4.77183 5.09061V7.73968H2.13741C1.46425 7.73968 0.916687 8.28724 0.916687 8.9604V45.4987C0.916687 46.1718 1.46425 46.7194 2.13741 46.7194H25.4594C26.1325 46.7194 26.6801 46.1718 26.6801 45.4987V42.8495H29.8597C31.6145 44.9228 34.2306 46.2411 37.1483 46.2411C38.7517 46.2411 40.2995 45.8447 41.6768 45.1L46.2183 49.1674C47.2982 50.2372 49.0479 50.2963 50.1314 49.227C51.2157 48.1907 51.1502 46.3308 50.0627 45.3059ZM10.0917 1.46487H36.8373V27.0753C33.7243 27.1768 30.8955 28.7954 29.2049 31.3231H26.2311C25.8265 31.3231 25.4986 31.6509 25.4986 32.0555C25.4986 32.4601 25.8265 32.7879 26.2311 32.7879H28.3997C28.3016 33.011 28.2113 33.2386 28.1296 33.4712C27.7712 34.4923 27.5896 35.5636 27.5896 36.6551C27.5896 36.9449 27.6033 37.2315 27.6284 37.5149H17.4386C18.4439 36.5518 19.0721 35.1958 19.0721 33.6945V32.788H23.0564C23.461 32.788 23.7888 32.4602 23.7888 32.0556C23.7888 31.651 23.461 31.3232 23.0564 31.3232H18.3396C17.935 31.3232 17.6072 31.651 17.6072 32.0556V33.6945C17.6072 35.8011 15.9011 37.5149 13.8042 37.5149H10.0917V1.46487ZM6.2367 41.3846V31.3726C6.2367 30.968 5.90886 30.6401 5.50426 30.6401C5.09967 30.6401 4.77183 30.968 4.77183 31.3726V41.6287C4.77183 42.3019 5.3194 42.8494 5.99255 42.8494H25.2152V45.2544H2.38155V9.20454H4.77183V28.2767C4.77183 28.6813 5.09967 29.0092 5.50426 29.0092C5.90886 29.0092 6.2367 28.6813 6.2367 28.2767V5.33475H8.62697V38.2473C8.62697 38.6519 8.9548 38.9797 9.3594 38.9797H27.8744C28.087 39.832 28.4132 40.6394 28.8366 41.3847H6.2367V41.3846ZM49.1004 48.1864C48.5935 48.6917 47.7338 48.6401 47.21 48.089L42.9504 44.2739C43.6079 43.7701 44.2143 43.1649 44.7186 42.5101L49.0463 46.361C49.5457 46.8419 49.6036 47.7018 49.1004 48.1864Z" fill="#FF5A1F"></path><path id="Vector_10" d="M37.1484 30.3951C33.7686 30.347 30.8537 33.2723 30.9051 36.6554C30.9051 40.1073 33.7058 42.9155 37.1484 42.9155C40.5908 42.9155 43.3915 40.1073 43.3915 36.6554C43.3915 33.2035 40.5908 30.3951 37.1484 30.3951ZM37.1484 41.4506C34.5136 41.4506 32.37 39.2995 32.37 36.6553C32.3299 34.0642 34.561 31.8233 37.1484 31.8599C39.7831 31.8599 41.9267 34.011 41.9267 36.6553C41.9267 39.2995 39.7832 41.4506 37.1484 41.4506Z" fill="#FF5A1F"></path></g></svg>
            </span>
            <h3 class="text-2xl font-bold text-[#FF5A1F]">Semak</h3>
          </div>
           </div>
          <ul class="space-y-2 text-lg text-gray-700">
            <li class="font-bold">Agihan</li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Skim Bantuan Zakat
              </NuxtLink>
            </li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Status Permohonan
              </NuxtLink>
            </li>
            <li class="font-bold pt-2">Kutipan</li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Kalkulator Zakat 
              </NuxtLink>
            </li>
            <li class="flex items-center cursor-pointer">
              <Icon name="ri:arrow-right-s-fill" class="w-5 h-5 text-black mr-1" />
              <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                Penyata Zakat
              </NuxtLink>
            </li>
          </ul>
           </div>
        </div>
      </div>

    <!-- Mohon -->
      <div class="relative mx-auto">
        <!-- Third Container (Largest - Bottom) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[335px] h-[560px] bg-[linear-gradient(135deg,_rgba(255,255,255,1)_0%,rgba(1,114,0,1)_250%,rgba(1,114,0,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-0"></div>

        <!-- Second Container (Medium - Middle) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[340px] h-[550px] bg-[linear-gradient(135deg,_rgba(255,255,255,1)_0%,rgba(1,114,0,1)_250%,rgba(1,114,0,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-10"></div>

        <!-- Main Container (Normal - Top) -->
      <div class="relative z-20 bg-[linear-gradient(135deg,_rgba(255,255,255,1)_0%,rgba(1,114,0,1)_250%,rgba(1,114,0,1)_100%)] border-[#B6C1DB] border-[1px] rounded-2xl shadow-lg p-8 w-[350px] h-[540px] overflow-hidden">
        
        <!-- Inline SVG background -->
        <div class="absolute top-[-120px] right-[-230px] z-0 w-[500px] h-[500px] opacity-[0.05] pointer-events-none transfrom scale-x-[-1]">
              <svg xmlns="http://www.w3.org/2000/svg" width="53" height="50" viewBox="0 0 53 50" fill="none"
              class="w-full h-full"><g id="Group"><path id="Vector" d="M8.34294 7.87046H30.3431C30.7658 7.87046 31.1085 7.5279 31.1085 7.10515C31.1085 6.68239 30.7658 6.33984 30.3431 6.33984H8.34294C7.92029 6.33984 7.57764 6.68239 7.57764 7.10515C7.57764 7.5279 7.92029 7.87046 8.34294 7.87046Z" fill="#017200"></path><path id="Vector_2" d="M12.2099 10.0156C11.7872 10.0156 11.4446 10.3582 11.4446 10.7809C11.4446 11.2037 11.7872 11.5462 12.2099 11.5462H25.9892C26.4118 11.5462 26.7545 11.2037 26.7545 10.7809C26.7545 10.3582 26.4118 10.0156 25.9892 10.0156H12.2099Z" fill="#017200"></path><path id="Vector_3" d="M6.0867 42.4853H17.0595C17.4821 42.4853 17.8248 42.1427 17.8248 41.72C17.8248 41.2972 17.4821 40.9547 17.0595 40.9547H6.52353V33.2651H31.2145V40.9547H20.4308C20.0081 40.9547 19.6655 41.2972 19.6655 41.72C19.6655 42.1427 20.0081 42.4853 20.4308 42.4853H31.6541C32.2557 42.4853 32.7451 41.9947 32.7451 41.3916V32.828C32.7451 32.225 32.2557 31.7344 31.6541 31.7344H6.0867C5.48353 31.7344 4.99292 32.225 4.99292 32.828V41.3916C4.99292 41.9947 5.48363 42.4853 6.0867 42.4853Z" fill="#017200"></path><path id="Vector_4" d="M6.10117 28.6641H31.464C32.064 28.6641 32.5521 28.176 32.5521 27.5761V24.4882C32.5521 23.8883 32.064 23.4004 31.464 23.4004H6.10117C5.49964 23.4004 5.01025 23.8883 5.01025 24.4882V27.5761C5.01025 28.176 5.49964 28.6641 6.10117 28.6641ZM6.54087 24.931H31.0215V27.1335H6.54087V24.931Z" fill="#017200"></path><path id="Vector_5" d="M6.10117 20.5332H17.0595C17.4822 20.5332 17.8248 20.1907 17.8248 19.7679C17.8248 19.3452 17.4822 19.0026 17.0595 19.0026H6.54087V16.7972H31.0215V19.0025H20.5807C20.158 19.0025 19.8154 19.3451 19.8154 19.7678C19.8154 20.1906 20.158 20.5331 20.5807 20.5331H31.464C32.064 20.5331 32.5521 20.0438 32.5521 19.4424V16.3546C32.5521 15.7547 32.064 15.2666 31.464 15.2666H6.10117C5.49964 15.2666 5.01025 15.7547 5.01025 16.3546V19.4424C5.01025 20.0439 5.49964 20.5332 6.10117 20.5332Z" fill="#017200"></path><path id="Vector_6" d="M36.1897 0H1.54837C0.832449 0 0.25 0.582347 0.25 1.29827V48.7018C0.25 49.4177 0.832449 50 1.54837 50H36.1897C36.9072 50 37.4909 49.4177 37.4909 48.7017V1.29827C37.4909 0.582347 36.9072 0 36.1897 0ZM35.9603 48.4694H1.78061V1.53061H35.9603V48.4694Z" fill="#017200"></path><path id="Vector_7" d="M52.2468 9.3608C52.0548 8.97387 51.5572 8.32478 50.3839 8.32478H49.21V7.9955C49.21 5.64213 47.2948 3.72754 44.9408 3.72754C42.5868 3.72754 40.6716 5.64213 40.6716 7.9955V16.2999C40.6716 16.7226 41.0143 17.0652 41.4369 17.0652C41.8596 17.0652 42.2022 16.7226 42.2022 16.2999V11.9408H47.6794V23.9858H42.2022V19.8169C42.2022 19.3942 41.8596 19.0516 41.4369 19.0516C41.0143 19.0516 40.6716 19.3942 40.6716 19.8169V36.6157C40.6716 36.7402 40.702 36.8574 40.7548 36.9613C40.7553 36.9623 40.7551 36.9633 40.7556 36.9643L43.8721 43.0566C44.1563 43.6087 44.3807 44.0448 44.9432 44.0448H44.9444C45.5052 44.0441 45.7305 43.604 45.9913 43.0943L49.1261 36.9643C49.1272 36.9621 49.1276 36.9603 49.1285 36.9582C49.1802 36.8551 49.2101 36.7391 49.2101 36.6158V9.8554H50.384C50.8468 9.8554 50.9644 9.93948 50.9644 10.7118V16.395C50.9644 16.8177 51.307 17.1603 51.7297 17.1603C52.1523 17.1603 52.495 16.8177 52.495 16.395V10.7118C52.4949 10.3935 52.4949 9.8605 52.2468 9.3608ZM44.9413 41.7858L42.688 37.381H47.1938L44.9413 41.7858ZM47.6794 35.8504H42.2022V25.5165H47.6794V35.8504ZM47.6794 10.4103H42.2022V7.9956C42.2022 6.48621 43.4308 5.25825 44.9408 5.25825C46.4509 5.25825 47.6794 6.48621 47.6794 7.9956V10.4103Z" fill="#017200"></path></g></svg>
        </div>
          
        <div class="relative z-10">
          <div class="relative ">
          <div class="absolute left-[-3px] top-[-12px] w-[50px] h-[50px] bg-[#E8FDE8] rounded-full"></div>
            <div class="flex mb-6 px-3">
            <span class="text-2xl mr-3 relative z-10">
          <svg xmlns="http://www.w3.org/2000/svg" width="53" height="50" viewBox="0 0 53 50" fill="none"><g id="Group"><path id="Vector" d="M8.34294 7.87046H30.3431C30.7658 7.87046 31.1085 7.5279 31.1085 7.10515C31.1085 6.68239 30.7658 6.33984 30.3431 6.33984H8.34294C7.92029 6.33984 7.57764 6.68239 7.57764 7.10515C7.57764 7.5279 7.92029 7.87046 8.34294 7.87046Z" fill="#017200"></path><path id="Vector_2" d="M12.2099 10.0156C11.7872 10.0156 11.4446 10.3582 11.4446 10.7809C11.4446 11.2037 11.7872 11.5462 12.2099 11.5462H25.9892C26.4118 11.5462 26.7545 11.2037 26.7545 10.7809C26.7545 10.3582 26.4118 10.0156 25.9892 10.0156H12.2099Z" fill="#017200"></path><path id="Vector_3" d="M6.0867 42.4853H17.0595C17.4821 42.4853 17.8248 42.1427 17.8248 41.72C17.8248 41.2972 17.4821 40.9547 17.0595 40.9547H6.52353V33.2651H31.2145V40.9547H20.4308C20.0081 40.9547 19.6655 41.2972 19.6655 41.72C19.6655 42.1427 20.0081 42.4853 20.4308 42.4853H31.6541C32.2557 42.4853 32.7451 41.9947 32.7451 41.3916V32.828C32.7451 32.225 32.2557 31.7344 31.6541 31.7344H6.0867C5.48353 31.7344 4.99292 32.225 4.99292 32.828V41.3916C4.99292 41.9947 5.48363 42.4853 6.0867 42.4853Z" fill="#017200"></path><path id="Vector_4" d="M6.10117 28.6641H31.464C32.064 28.6641 32.5521 28.176 32.5521 27.5761V24.4882C32.5521 23.8883 32.064 23.4004 31.464 23.4004H6.10117C5.49964 23.4004 5.01025 23.8883 5.01025 24.4882V27.5761C5.01025 28.176 5.49964 28.6641 6.10117 28.6641ZM6.54087 24.931H31.0215V27.1335H6.54087V24.931Z" fill="#017200"></path><path id="Vector_5" d="M6.10117 20.5332H17.0595C17.4822 20.5332 17.8248 20.1907 17.8248 19.7679C17.8248 19.3452 17.4822 19.0026 17.0595 19.0026H6.54087V16.7972H31.0215V19.0025H20.5807C20.158 19.0025 19.8154 19.3451 19.8154 19.7678C19.8154 20.1906 20.158 20.5331 20.5807 20.5331H31.464C32.064 20.5331 32.5521 20.0438 32.5521 19.4424V16.3546C32.5521 15.7547 32.064 15.2666 31.464 15.2666H6.10117C5.49964 15.2666 5.01025 15.7547 5.01025 16.3546V19.4424C5.01025 20.0439 5.49964 20.5332 6.10117 20.5332Z" fill="#017200"></path><path id="Vector_6" d="M36.1897 0H1.54837C0.832449 0 0.25 0.582347 0.25 1.29827V48.7018C0.25 49.4177 0.832449 50 1.54837 50H36.1897C36.9072 50 37.4909 49.4177 37.4909 48.7017V1.29827C37.4909 0.582347 36.9072 0 36.1897 0ZM35.9603 48.4694H1.78061V1.53061H35.9603V48.4694Z" fill="#017200"></path><path id="Vector_7" d="M52.2468 9.3608C52.0548 8.97387 51.5572 8.32478 50.3839 8.32478H49.21V7.9955C49.21 5.64213 47.2948 3.72754 44.9408 3.72754C42.5868 3.72754 40.6716 5.64213 40.6716 7.9955V16.2999C40.6716 16.7226 41.0143 17.0652 41.4369 17.0652C41.8596 17.0652 42.2022 16.7226 42.2022 16.2999V11.9408H47.6794V23.9858H42.2022V19.8169C42.2022 19.3942 41.8596 19.0516 41.4369 19.0516C41.0143 19.0516 40.6716 19.3942 40.6716 19.8169V36.6157C40.6716 36.7402 40.702 36.8574 40.7548 36.9613C40.7553 36.9623 40.7551 36.9633 40.7556 36.9643L43.8721 43.0566C44.1563 43.6087 44.3807 44.0448 44.9432 44.0448H44.9444C45.5052 44.0441 45.7305 43.604 45.9913 43.0943L49.1261 36.9643C49.1272 36.9621 49.1276 36.9603 49.1285 36.9582C49.1802 36.8551 49.2101 36.7391 49.2101 36.6158V9.8554H50.384C50.8468 9.8554 50.9644 9.93948 50.9644 10.7118V16.395C50.9644 16.8177 51.307 17.1603 51.7297 17.1603C52.1523 17.1603 52.495 16.8177 52.495 16.395V10.7118C52.4949 10.3935 52.4949 9.8605 52.2468 9.3608ZM44.9413 41.7858L42.688 37.381H47.1938L44.9413 41.7858ZM47.6794 35.8504H42.2022V25.5165H47.6794V35.8504ZM47.6794 10.4103H42.2022V7.9956C42.2022 6.48621 43.4308 5.25825 44.9408 5.25825C46.4509 5.25825 47.6794 6.48621 47.6794 7.9956V10.4103Z" fill="#017200"></path></g></svg>
            </span>
            <h3 class="text-2xl font-bold text-[#017200]">Mohon</h3>
          </div>
           </div>
            <ul class="space-y-2 text-lg ">
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Bantuan Am
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Bantuan Pelajaran
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Sewaan Permis/ Tanah
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Sewaan Bazar Wakaf
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Wakaf Tanah
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-8 h-8 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Panduan Pelaksanaan Perakuan Permastautin
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Potongan Zakat Gaji Bulanan
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-8 h-8 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Borang Kebenaran Potongan Gaji Wakaf Tunai
                </NuxtLink>
              </li>
            </ul>
           </div>
        </div>
      </div>

    <!-- Bayar -->
      <div class="relative mx-auto">
        <!-- Third Container (Largest - Bottom) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[335px] h-[560px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(0,84,165,1)_250%,rgba(0,84,165,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-0"></div>

        <!-- Second Container (Medium - Middle) -->
        <div class="absolute -top-0 left-1/2 -translate-x-1/2 w-[340px] h-[550px] bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(0,84,165,1)_250%,rgba(0,84,165,1)_100%)] border-[#B6C1DB] border-b-[1px] rounded-2xl shadow-md z-10"></div>

        <!-- Main Container (Normal - Top) -->
      <div class="relative z-20 bg-[linear-gradient(135deg,rgba(255,255,255,1)_0%,rgba(0,84,165,1)_250%,rgba(0,84,165,1)_100%)] border-[#B6C1DB] border-[1px] rounded-2xl shadow-lg p-8 w-[350px] h-[540px] overflow-hidden">
        
        <!-- Inline SVG background -->
        <div class="absolute top-[-120px] right-[-230px] z-0 w-[450px] h-[450px] opacity-[0.05] pointer-events-none">
        <svg xmlns="http://www.w3.org/2000/svg" width="59" height="50" viewBox="0 0 49 50" fill="none" class="w-full h-full"><g id="Group"><path id="Vector" d="M40.4752 38.2219C40.8273 37.6107 40.9215 36.8553 40.6682 36.1392C40.2062 34.8406 38.757 34.164 37.4374 34.6309C37.4335 34.6323 37.4297 34.6336 37.4258 34.6351L35.0113 35.5352C35.0288 35.2156 34.9876 34.8899 34.877 34.5758C34.6522 33.9435 34.1932 33.439 33.5847 33.1552C32.9772 32.8719 32.2883 32.8418 31.6451 33.0707C31.6416 33.072 31.6381 33.0733 31.6347 33.0745L27.1353 34.7523C27.1461 34.4566 27.1016 34.1589 26.9998 33.8724C26.788 33.2759 26.3559 32.7974 25.7829 32.5251C25.1989 32.2475 24.5364 32.2162 23.909 32.4399L15.6861 35.4868C15.3688 35.3698 15.0752 35.2481 14.7904 35.1294C12.9435 34.3596 11.5703 33.9336 8.05332 35.1075C7.88086 34.1958 7.07969 33.5037 6.11865 33.5037H2.25498C1.16855 33.5037 0.284668 34.3876 0.284668 35.4741V39.2071C0.284668 39.6147 0.615039 39.9452 1.02266 39.9452C1.43027 39.9452 1.76064 39.6147 1.76064 39.2071V35.4741C1.76064 35.2016 1.98242 34.9798 2.25498 34.9798H6.11855C6.38643 34.9798 6.61279 35.2061 6.61279 35.4741V46.7702C6.61279 47.0382 6.38643 47.2645 6.11855 47.2645H2.25498C1.98252 47.2645 1.76064 47.0428 1.76064 46.7702V42.6034C1.76064 42.1957 1.43027 41.8653 1.02266 41.8653C0.615039 41.8653 0.284668 42.1957 0.284668 42.6034V46.7702C0.284668 47.8567 1.16855 48.7406 2.25498 48.7406H6.11855C7.03389 48.7406 7.80303 48.1122 8.02334 47.265C10.1458 47.3303 11.3314 47.5551 13.8513 48.3091L18.2806 49.6335C19.1039 49.8784 20.2022 50 21.3061 50C22.4628 50 23.6257 49.8663 24.4833 49.6006C26.7521 48.8997 30.3631 47.5233 31.7924 46.9421L40.6246 43.3479C41.2766 43.0815 41.7633 42.5428 41.9948 41.831C42.2649 41.0008 42.1453 40.0203 41.6833 39.2736C41.386 38.7908 40.969 38.437 40.4752 38.2219ZM33.6597 37.6146C33.6929 37.6048 33.7257 37.5926 33.7578 37.578L37.935 36.0206C38.4963 35.8249 39.0852 36.0935 39.277 36.6326C39.465 37.1643 39.1852 37.75 38.6531 37.9382C38.6494 37.9396 38.6456 37.941 38.6419 37.9423L28.0126 41.8968C28.0122 41.6668 27.9885 41.4341 27.937 41.2025C27.8329 40.7333 27.6307 40.3138 27.3526 39.966L33.6597 37.6146ZM32.1444 34.46C32.4186 34.3638 32.7084 34.3755 32.9609 34.4932C33.2084 34.6085 33.3949 34.8136 33.4855 35.0683C33.6358 35.4952 33.4822 35.976 33.1206 36.2402L25.7883 38.9738L22.8013 37.9438L32.1444 34.46ZM24.413 33.8273C24.6601 33.7393 24.9215 33.7501 25.1492 33.8584C25.3657 33.9614 25.529 34.1417 25.6088 34.3664C25.6892 34.593 25.6755 34.839 25.5703 35.0591C25.4648 35.2798 25.2812 35.4459 25.0532 35.5268C25.0366 35.5328 25.0208 35.5399 25.0048 35.5468L20.6063 37.1869L17.8815 36.2474L24.413 33.8273ZM40.5911 41.3744C40.5239 41.581 40.3783 41.854 40.0673 41.9811L31.2361 45.5749C29.8277 46.1477 26.2732 47.5029 24.047 48.1906C22.6276 48.6304 20.1297 48.6434 18.7022 48.2191L14.2742 46.8951C11.6403 46.107 10.3324 45.8611 8.08867 45.7905V36.6563C11.6138 35.407 12.6661 35.8435 14.2224 36.4921C14.6001 36.6495 25.5574 40.4557 25.5574 40.4557C25.5652 40.4584 25.5731 40.461 25.5811 40.4634C26.2395 40.6659 26.4401 41.2715 26.4958 41.5225C26.5892 41.9431 26.525 42.365 26.3297 42.7002C26.3278 42.7034 26.3261 42.7067 26.3243 42.7098C26.2542 42.8281 26.168 42.9355 26.066 43.0278C25.5125 43.5282 24.5365 43.5821 23.3171 43.1794L17.0864 41.1238C16.6995 40.9959 16.282 41.2064 16.1543 41.5934C16.0267 41.9805 16.2369 42.3978 16.624 42.5255L22.8545 44.5811C23.5953 44.8257 24.2305 44.921 24.7707 44.921C25.9475 44.921 26.6732 44.4687 27.0561 44.1226C27.204 43.9888 27.3359 43.8405 27.4513 43.6806L38.283 39.6508C38.2932 39.6474 38.3034 39.6448 38.3135 39.641C39.0424 39.363 39.9806 39.3239 40.427 40.0489C40.6641 40.4319 40.7284 40.9522 40.5911 41.3744Z" fill="#0054A5"></path><path id="Vector_2" d="M48.4851 10.9831L43.2006 1.04512C42.9549 0.581546 42.5421 0.241409 42.0384 0.0873079C41.5354 -0.0665983 41.0033 -0.0158171 40.5416 0.230081L37.1391 2.03848C36.2013 2.53819 35.8356 3.69395 36.3015 4.63995C35.9368 4.83653 35.6023 5.01914 35.2944 5.18711C32.5818 6.66748 31.7631 7.11426 28.1001 7.55078C27.6953 7.59903 27.4064 7.96621 27.4546 8.371C27.4993 8.7461 27.8179 9.02178 28.1865 9.02178C28.2157 9.02178 28.2451 9.02002 28.2748 9.01651C32.2203 8.54629 33.2499 7.98438 36.0015 6.48282C36.3047 6.31739 36.6338 6.1378 36.9916 5.94483L40.4981 12.5406C39.0803 13.3789 38.1651 14.2521 37.4282 15.4457C36.1965 17.4441 34.6786 18.2137 33.2108 18.9579C32.5563 19.2897 31.8796 19.6328 31.2491 20.0741L25.2748 24.2624C25.1151 24.3606 24.9598 24.4362 24.8122 24.489C24.7996 24.4927 24.787 24.4966 24.7746 24.5011C24.5379 24.5799 24.3222 24.5986 24.1439 24.5508C23.9029 24.4862 23.6941 24.2907 23.5234 23.97C23.0981 23.171 23.7354 20.8147 24.8947 19.6743L28.6359 15.9887C28.6513 15.9735 28.666 15.9576 28.68 15.9412C29.3218 15.1869 29.2914 14.5762 29.1529 14.1966C28.9211 13.5612 28.25 13.1463 27.1575 12.9631C24.0476 12.4431 22.8431 13.226 22.1017 14.2542C21.4274 13.8599 20.7008 13.5563 19.9332 13.3487C19.5011 13.2314 19.0619 13.1481 18.6193 13.0974L18.6985 12.9505C20.0296 10.4784 22.0363 9.75362 24.8428 9.38526C25.247 9.33223 25.5316 8.96162 25.4785 8.55752C25.4254 8.15332 25.0545 7.86875 24.6507 7.92178C21.9005 8.28272 19.1186 9.05694 17.3992 12.2501L16.9589 13.0659C15.2412 13.1979 13.5643 13.8407 12.1952 14.9015C10.6602 16.0907 9.58126 17.7123 9.07491 19.5905C7.80245 24.3049 10.6026 29.1756 15.3169 30.448C16.0872 30.6558 16.8642 30.7557 17.6308 30.7556C20.9598 30.7555 24.0897 28.8719 25.5933 25.7623C25.7523 25.6897 25.9119 25.6047 26.0718 25.5051C26.083 25.498 26.0941 25.4907 26.105 25.4831L32.0961 21.2831C32.6404 20.9021 33.2417 20.5972 33.8783 20.2744C35.4517 19.4767 37.235 18.5726 38.6845 16.2206C39.2757 15.2632 40.0276 14.5458 41.1924 13.8464L41.6137 14.6388C41.9665 15.301 42.6481 15.679 43.3523 15.6789C43.6633 15.6789 43.9788 15.6051 44.2722 15.4496L47.6704 13.642C48.1339 13.3962 48.474 12.9834 48.6281 12.4797C48.7819 11.9768 48.7312 11.4452 48.4851 10.9831ZM26.9138 14.419C27.4576 14.5103 27.6747 14.6406 27.7465 14.6967C27.7284 14.743 27.6839 14.8303 27.5751 14.9617L25.1957 17.3058C24.6907 16.4732 24.0499 15.7271 23.3045 15.1024C23.7541 14.4856 24.5209 14.0189 26.9138 14.419ZM15.7014 29.0231C11.773 27.9627 9.43956 23.9038 10.5001 19.975C11.3433 16.847 14.1935 14.6029 17.4304 14.518C18.1442 14.5001 18.8557 14.5858 19.5473 14.7735C20.4018 15.0046 21.194 15.3771 21.9016 15.8808C22.8151 16.531 23.5732 17.3898 24.1089 18.3767L23.8593 18.6226C22.416 20.0421 21.3631 23.0533 22.2205 24.6639C22.6822 25.5312 23.3133 25.8564 23.7614 25.9767C23.766 25.9779 23.7708 25.9787 23.7754 25.9799C22.0468 28.5939 18.8072 29.8607 15.7014 29.0231ZM47.2165 12.0482C47.1779 12.1744 47.0935 12.2773 46.9779 12.3387L43.5797 14.1463C43.3406 14.2731 43.043 14.1828 42.9165 13.9456L37.6313 4.00342C37.5066 3.76924 37.599 3.46592 37.8325 3.34151L41.235 1.53321C41.3053 1.4958 41.3823 1.47676 41.4608 1.47676C41.5093 1.47676 41.5584 1.48409 41.6067 1.49883C41.7328 1.53741 41.8358 1.62188 41.897 1.73731L47.1819 11.6761C47.182 11.6763 47.1821 11.6764 47.1822 11.6766C47.2427 11.7904 47.2549 11.9224 47.2165 12.0482Z" fill="#0054A5"></path></g></svg>
        </div>
          
        <div class="relative z-10">
          <div class="relative ">
          <div class="absolute left-[-3px] top-[-12px] w-[50px] h-[50px] bg-[#E6EEFF] rounded-full"></div>
            <div class="flex mb-6 px-3">
            <span class="text-2xl mr-3 relative z-10">
            <svg xmlns="http://www.w3.org/2000/svg" width="49" height="50" viewBox="0 0 49 50" fill="none"><g id="Group"><path id="Vector" d="M40.4752 38.2219C40.8273 37.6107 40.9215 36.8553 40.6682 36.1392C40.2062 34.8406 38.757 34.164 37.4374 34.6309C37.4335 34.6323 37.4297 34.6336 37.4258 34.6351L35.0113 35.5352C35.0288 35.2156 34.9876 34.8899 34.877 34.5758C34.6522 33.9435 34.1932 33.439 33.5847 33.1552C32.9772 32.8719 32.2883 32.8418 31.6451 33.0707C31.6416 33.072 31.6381 33.0733 31.6347 33.0745L27.1353 34.7523C27.1461 34.4566 27.1016 34.1589 26.9998 33.8724C26.788 33.2759 26.3559 32.7974 25.7829 32.5251C25.1989 32.2475 24.5364 32.2162 23.909 32.4399L15.6861 35.4868C15.3688 35.3698 15.0752 35.2481 14.7904 35.1294C12.9435 34.3596 11.5703 33.9336 8.05332 35.1075C7.88086 34.1958 7.07969 33.5037 6.11865 33.5037H2.25498C1.16855 33.5037 0.284668 34.3876 0.284668 35.4741V39.2071C0.284668 39.6147 0.615039 39.9452 1.02266 39.9452C1.43027 39.9452 1.76064 39.6147 1.76064 39.2071V35.4741C1.76064 35.2016 1.98242 34.9798 2.25498 34.9798H6.11855C6.38643 34.9798 6.61279 35.2061 6.61279 35.4741V46.7702C6.61279 47.0382 6.38643 47.2645 6.11855 47.2645H2.25498C1.98252 47.2645 1.76064 47.0428 1.76064 46.7702V42.6034C1.76064 42.1957 1.43027 41.8653 1.02266 41.8653C0.615039 41.8653 0.284668 42.1957 0.284668 42.6034V46.7702C0.284668 47.8567 1.16855 48.7406 2.25498 48.7406H6.11855C7.03389 48.7406 7.80303 48.1122 8.02334 47.265C10.1458 47.3303 11.3314 47.5551 13.8513 48.3091L18.2806 49.6335C19.1039 49.8784 20.2022 50 21.3061 50C22.4628 50 23.6257 49.8663 24.4833 49.6006C26.7521 48.8997 30.3631 47.5233 31.7924 46.9421L40.6246 43.3479C41.2766 43.0815 41.7633 42.5428 41.9948 41.831C42.2649 41.0008 42.1453 40.0203 41.6833 39.2736C41.386 38.7908 40.969 38.437 40.4752 38.2219ZM33.6597 37.6146C33.6929 37.6048 33.7257 37.5926 33.7578 37.578L37.935 36.0206C38.4963 35.8249 39.0852 36.0935 39.277 36.6326C39.465 37.1643 39.1852 37.75 38.6531 37.9382C38.6494 37.9396 38.6456 37.941 38.6419 37.9423L28.0126 41.8968C28.0122 41.6668 27.9885 41.4341 27.937 41.2025C27.8329 40.7333 27.6307 40.3138 27.3526 39.966L33.6597 37.6146ZM32.1444 34.46C32.4186 34.3638 32.7084 34.3755 32.9609 34.4932C33.2084 34.6085 33.3949 34.8136 33.4855 35.0683C33.6358 35.4952 33.4822 35.976 33.1206 36.2402L25.7883 38.9738L22.8013 37.9438L32.1444 34.46ZM24.413 33.8273C24.6601 33.7393 24.9215 33.7501 25.1492 33.8584C25.3657 33.9614 25.529 34.1417 25.6088 34.3664C25.6892 34.593 25.6755 34.839 25.5703 35.0591C25.4648 35.2798 25.2812 35.4459 25.0532 35.5268C25.0366 35.5328 25.0208 35.5399 25.0048 35.5468L20.6063 37.1869L17.8815 36.2474L24.413 33.8273ZM40.5911 41.3744C40.5239 41.581 40.3783 41.854 40.0673 41.9811L31.2361 45.5749C29.8277 46.1477 26.2732 47.5029 24.047 48.1906C22.6276 48.6304 20.1297 48.6434 18.7022 48.2191L14.2742 46.8951C11.6403 46.107 10.3324 45.8611 8.08867 45.7905V36.6563C11.6138 35.407 12.6661 35.8435 14.2224 36.4921C14.6001 36.6495 25.5574 40.4557 25.5574 40.4557C25.5652 40.4584 25.5731 40.461 25.5811 40.4634C26.2395 40.6659 26.4401 41.2715 26.4958 41.5225C26.5892 41.9431 26.525 42.365 26.3297 42.7002C26.3278 42.7034 26.3261 42.7067 26.3243 42.7098C26.2542 42.8281 26.168 42.9355 26.066 43.0278C25.5125 43.5282 24.5365 43.5821 23.3171 43.1794L17.0864 41.1238C16.6995 40.9959 16.282 41.2064 16.1543 41.5934C16.0267 41.9805 16.2369 42.3978 16.624 42.5255L22.8545 44.5811C23.5953 44.8257 24.2305 44.921 24.7707 44.921C25.9475 44.921 26.6732 44.4687 27.0561 44.1226C27.204 43.9888 27.3359 43.8405 27.4513 43.6806L38.283 39.6508C38.2932 39.6474 38.3034 39.6448 38.3135 39.641C39.0424 39.363 39.9806 39.3239 40.427 40.0489C40.6641 40.4319 40.7284 40.9522 40.5911 41.3744Z" fill="#0054A5"></path><path id="Vector_2" d="M48.4851 10.9831L43.2006 1.04512C42.9549 0.581546 42.5421 0.241409 42.0384 0.0873079C41.5354 -0.0665983 41.0033 -0.0158171 40.5416 0.230081L37.1391 2.03848C36.2013 2.53819 35.8356 3.69395 36.3015 4.63995C35.9368 4.83653 35.6023 5.01914 35.2944 5.18711C32.5818 6.66748 31.7631 7.11426 28.1001 7.55078C27.6953 7.59903 27.4064 7.96621 27.4546 8.371C27.4993 8.7461 27.8179 9.02178 28.1865 9.02178C28.2157 9.02178 28.2451 9.02002 28.2748 9.01651C32.2203 8.54629 33.2499 7.98438 36.0015 6.48282C36.3047 6.31739 36.6338 6.1378 36.9916 5.94483L40.4981 12.5406C39.0803 13.3789 38.1651 14.2521 37.4282 15.4457C36.1965 17.4441 34.6786 18.2137 33.2108 18.9579C32.5563 19.2897 31.8796 19.6328 31.2491 20.0741L25.2748 24.2624C25.1151 24.3606 24.9598 24.4362 24.8122 24.489C24.7996 24.4927 24.787 24.4966 24.7746 24.5011C24.5379 24.5799 24.3222 24.5986 24.1439 24.5508C23.9029 24.4862 23.6941 24.2907 23.5234 23.97C23.0981 23.171 23.7354 20.8147 24.8947 19.6743L28.6359 15.9887C28.6513 15.9735 28.666 15.9576 28.68 15.9412C29.3218 15.1869 29.2914 14.5762 29.1529 14.1966C28.9211 13.5612 28.25 13.1463 27.1575 12.9631C24.0476 12.4431 22.8431 13.226 22.1017 14.2542C21.4274 13.8599 20.7008 13.5563 19.9332 13.3487C19.5011 13.2314 19.0619 13.1481 18.6193 13.0974L18.6985 12.9505C20.0296 10.4784 22.0363 9.75362 24.8428 9.38526C25.247 9.33223 25.5316 8.96162 25.4785 8.55752C25.4254 8.15332 25.0545 7.86875 24.6507 7.92178C21.9005 8.28272 19.1186 9.05694 17.3992 12.2501L16.9589 13.0659C15.2412 13.1979 13.5643 13.8407 12.1952 14.9015C10.6602 16.0907 9.58126 17.7123 9.07491 19.5905C7.80245 24.3049 10.6026 29.1756 15.3169 30.448C16.0872 30.6558 16.8642 30.7557 17.6308 30.7556C20.9598 30.7555 24.0897 28.8719 25.5933 25.7623C25.7523 25.6897 25.9119 25.6047 26.0718 25.5051C26.083 25.498 26.0941 25.4907 26.105 25.4831L32.0961 21.2831C32.6404 20.9021 33.2417 20.5972 33.8783 20.2744C35.4517 19.4767 37.235 18.5726 38.6845 16.2206C39.2757 15.2632 40.0276 14.5458 41.1924 13.8464L41.6137 14.6388C41.9665 15.301 42.6481 15.679 43.3523 15.6789C43.6633 15.6789 43.9788 15.6051 44.2722 15.4496L47.6704 13.642C48.1339 13.3962 48.474 12.9834 48.6281 12.4797C48.7819 11.9768 48.7312 11.4452 48.4851 10.9831ZM26.9138 14.419C27.4576 14.5103 27.6747 14.6406 27.7465 14.6967C27.7284 14.743 27.6839 14.8303 27.5751 14.9617L25.1957 17.3058C24.6907 16.4732 24.0499 15.7271 23.3045 15.1024C23.7541 14.4856 24.5209 14.0189 26.9138 14.419ZM15.7014 29.0231C11.773 27.9627 9.43956 23.9038 10.5001 19.975C11.3433 16.847 14.1935 14.6029 17.4304 14.518C18.1442 14.5001 18.8557 14.5858 19.5473 14.7735C20.4018 15.0046 21.194 15.3771 21.9016 15.8808C22.8151 16.531 23.5732 17.3898 24.1089 18.3767L23.8593 18.6226C22.416 20.0421 21.3631 23.0533 22.2205 24.6639C22.6822 25.5312 23.3133 25.8564 23.7614 25.9767C23.766 25.9779 23.7708 25.9787 23.7754 25.9799C22.0468 28.5939 18.8072 29.8607 15.7014 29.0231ZM47.2165 12.0482C47.1779 12.1744 47.0935 12.2773 46.9779 12.3387L43.5797 14.1463C43.3406 14.2731 43.043 14.1828 42.9165 13.9456L37.6313 4.00342C37.5066 3.76924 37.599 3.46592 37.8325 3.34151L41.235 1.53321C41.3053 1.4958 41.3823 1.47676 41.4608 1.47676C41.5093 1.47676 41.5584 1.48409 41.6067 1.49883C41.7328 1.53741 41.8358 1.62188 41.897 1.73731L47.1819 11.6761C47.182 11.6763 47.1821 11.6764 47.1822 11.6766C47.2427 11.7904 47.2549 11.9224 47.2165 12.0482Z" fill="#0054A5"></path></g></svg>
          </span>
            <h3 class="text-2xl font-bold text-[#0054A5]">Bayar</h3>
          </div>
           </div>
            <ul class="space-y-2 text-lg ">
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                   Bayaran Zakat (Online)
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Bayaran Zakat (Transfer)
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Bayaran Wakaf Tunai
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Bayaran Sewaan
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Fidyah
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Wang Tidak Patuh Syarak
                </NuxtLink>
              </li>
              <li class="flex items-center cursor-pointer">
                <Icon name="ri:arrow-right-s-fill" class="w-6 h-6 text-black mr-1 transition-transform duration-200 hover:scale-105" />
                <NuxtLink to="" class="transition-transform duration-200 hover:underline hover:scale-105">
                  Kafarah
                </NuxtLink>
              </li>
            </ul>
           </div>
        </div>
      </div>
  </div>
</div>


  </div>
</section>

<!-- Aktiviti -->
<section class="pt-32 pb-16 bg-white">
  <div class="max-w-screen-xl mx-auto px-4 sm:px-8 lg:px-16">
      <span class="block w-8 h-1 bg-[#0054A5] mb-2 rounded-full"></span>
      <h2 class="text-4xl font-bold text-[#374151] mb-8 max-w-2xl">Sertai Aktiviti Menarik</h2>

    <!-- Grid layout -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 mb-16">
      <article
        v-for="(item, index) in aktiviti"
        :key="index"
        class="relative group bg-gray-50 rounded-2xl overflow-hidden shadow-md border border-gray-200 min-h-[440px]"
      >
        <div
          v-if="item.specificDate"
          class="absolute top-0 left-10 bg-[#FDF600] text-[#374151] px-4 py-1 text-center rounded-b-[20px] shadow"
        >
          <p class="text-sm font-bold">{{ item.specificDate.day }}</p>
          <p class="text-xs">{{ item.specificDate.month }}</p>
        </div>

        <div class="aspect-[16/9] overflow-hidden">
          <img
            :src="item.image"
            alt="Imej Aktiviti"
            :class="[
              'w-full h-full object-cover',
              index === 1 ? 'object-[center_-10px]' : 'object-center'
            ]"
          />
        </div>

        <div class="p-7 space-y-3">
          <h3 class="text-xl font-semibold text-gray-800 line-clamp-2">
            {{ item.title }}
          </h3>

          <!-- Info Rows -->
          <div class="space-y-2 text-sm text-gray-600">
            <div class="flex items-center gap-2">
              <Icon name="bi:calendar" class="w-4 h-4 text-[#0054A5]" />
              <span>{{ item.date }}</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="fa-regular:clock" class="w-4 h-4 text-[#0054A5]" />
              <span>{{ item.time }}</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="ri:map-pin-line" class="w-4 h-4 text-[#0054A5]" />
              <span>{{ item.location }}</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="fa-regular:user" class="w-4 h-4 text-[#0054A5]" />
              <span>{{ item.organizer }}</span>
            </div>
            <div class="flex items-center gap-2">
              <Icon name="akar-icons:phone" class="w-4 h-4 text-[#0054A5]" />
              <span>{{ item.phone }}</span>
            </div>
          </div>
        </div>
      </article>
          </div>
      <div class="text-center text-[#0054A5]">
        <NuxtButton
          class="inline-flex items-center space-x-3 px-6 py-3 border-[#0054A5] border-[1px] rounded-[10px] cursor-pointer"
        >
          <p>Lihat Semua</p>
            <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
        </NuxtButton>
      </div>

  </div>
</section>


<!-- Kursus (Desktop - Small And Large)-->
  <section
    class="relative py-16 bg-cover bg-center hidden lg:block xl:block 2xl:block"
    :style="{
      backgroundImage: 'url(\'https://s3-alpha-sig.figma.com/img/2ed4/26c1/b652a53cf78c98f970d20258c5d34d04?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=pb1HWDBM-VYerYAj0KzvHe5tEooVu2YWpgRdtP1l2KNwogoRvjsW8yobYCm8siI4ZLcu2hgN7zKHqw0KadZOJzsJCqODy~Yu-eQNBxON5IwNARzOijezWpj2GfoTseo7kGak1lLmFnBlSCz8sBp2CcFmzKZHdTc2MN8wtyUvmXtTgt16NSYBSItn3n1W-wr9kwz4~DdI41G~88QQQXOiVVt27RAU1NxMuYPJDJpnyz~liBKY~5-3Qd1qwDedhhBkkXGB7UK0vO2k9J1jKme93D85c-Ula-5aKS-LLeuBPyMuoX~rpmHIoUx9kSkOe5Qpl-8wcJX3-fqp9zKONnN38A\')'
    }"
  >
    <!-- Overlay -->
    <div class="absolute inset-0 bg-[#0054A5]/90"></div>

<div class="relative text-white px-8 py-12">
  <div class="grid grid-cols-1 lg:flex gap-10 items-start max-w-6xl mx-auto">

    <!-- Image Section -->
    <div class="relative lg:w-[400px]">
      <NuxtImg
        class="w-full object-cover object-center rounded-lg shadow-lg"
        src="https://www.maips.gov.my/wp-content/uploads/2025/02/Iklan-kursus.png"
        alt="Kerjaya Asnaf"
      />
    </div>

    <!-- Text Content Section -->
    <div class="flex flex-col flex-1">
      <div>
        <div class="border border-1 font-bold rounded-full w-fit border-white text-white bg-transparent px-8 py-2 mb-6">
          <p>Kerjaya</p>
        </div>
        <h2 class="text-sm">Kerjaya Asnaf</h2>
        <h3 class="text-2xl font-bold mb-4">Kursus Kemahiran Anjuran MAIPs</h3>
        <p class="text-sm mb-4">
          Ingin tingkatkan kemahiran diri anda untuk berkerjaya dalam bidang Drone Piloting & <span class="font-bold">Maintenance?</span>
        </p>

        <ul class="mb-6 list-decimal list-inside space-y-3">
          <li>Pensijilan profesional yang diperakui oleh <span class="font-bold">Aerodyne</span></li>
          <li>Yuran pengajian adalah <span class="font-bold">PERCUMA</span> dan elaun sara diri RM400/bulan akan diberi.</li>
          <li>Program ini terbuka kepada <span class="font-bold">Warga Perlis</span> sahaja.</li>
        </ul>

        <p class="mb-5">
          Untuk maklumat lanjut, sila hubungi Pn. Amylia di talian: <span class="font-bold">019-5944621</span>
        </p>
      </div>

      <div>
        <NuxtButton
          class="inline-flex items-center space-x-3 px-6 py-3 bg-[#FDF600] text-[#374151] font-semibold rounded-lg cursor-pointer"
        >
          <span>Mohon Sekarang</span>
          <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
        </NuxtButton>
      </div>

      <div class="pt-20 border-b-2 border-white"></div>

      <div class="flex space-x-3 mt-10">
        <NuxtButton class="flex items-center justify-center h-12 w-12 cursor-pointer">
          <span class="inline-flex items-center justify-center w-10 h-10 rounded-[10px] bg-white border-[1px]">
            <Icon name="mdi:chevron-left" class="w-6 h-6 text-[#0054A5]" />
          </span>
        </NuxtButton>
        <NuxtButton class="flex items-center justify-center h-12 w-12 cursor-pointer">
          <span class="inline-flex items-center justify-center w-10 h-10 rounded-[10px] bg-white border-[1px]">
            <Icon name="mdi:chevron-right" class="w-6 h-6 text-[#0054A5]" />
          </span>
        </NuxtButton>
      </div>
    </div>
  </div>

  <!-- Circle Navigation Indicator -->
  <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 flex space-x-3 z-10">
    <div class="w-3 h-3 rounded-full bg-white"></div>
    <div class="w-3 h-3 rounded-full bg-gray-400"></div>
    <div class="w-3 h-3 rounded-full bg-gray-400"></div>
  </div>
</div>

  </section>

<!-- Kursus (Tablet & Phone)-->
  <section
    class="relative pt-8 pb-16 bg-cover bg-center block md:block  lg:hidden xl:hidden 2xl:hidden"
    :style="{
      backgroundImage: 'url(\'https://s3-alpha-sig.figma.com/img/2ed4/26c1/b652a53cf78c98f970d20258c5d34d04?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=pb1HWDBM-VYerYAj0KzvHe5tEooVu2YWpgRdtP1l2KNwogoRvjsW8yobYCm8siI4ZLcu2hgN7zKHqw0KadZOJzsJCqODy~Yu-eQNBxON5IwNARzOijezWpj2GfoTseo7kGak1lLmFnBlSCz8sBp2CcFmzKZHdTc2MN8wtyUvmXtTgt16NSYBSItn3n1W-wr9kwz4~DdI41G~88QQQXOiVVt27RAU1NxMuYPJDJpnyz~liBKY~5-3Qd1qwDedhhBkkXGB7UK0vO2k9J1jKme93D85c-Ula-5aKS-LLeuBPyMuoX~rpmHIoUx9kSkOe5Qpl-8wcJX3-fqp9zKONnN38A\')'
    }"
  >
    <!-- Overlay -->
    <div class="absolute inset-0 bg-[#0054A5]/90"></div>

<div class="relative text-white px-8 py-20">
  <div class="grid grid-cols-1 lg:flex gap-10 items-start max-w-6xl mx-auto">

    <!-- Image Section -->
    <div class="relative w-full">
      <NuxtImg
        class="w-full object-cover object-center rounded-lg shadow-lg"
        src="https://www.maips.gov.my/wp-content/uploads/2024/12/iklan-1-tablet.png"
        alt="Kerjaya Asnaf"
      />
    </div>

    <!-- Text Content Section -->
    <div class="flex flex-col flex-1">
      <div>
        <div class="border border-1 font-bold rounded-full w-fit border-white text-white bg-transparent px-8 py-2 mb-6">
          <p>Kerjaya</p>
        </div>
        <h2 class="text-sm">Kerjaya Asnaf</h2>
        <h3 class="text-2xl font-bold mb-4">Kursus Kemahiran Anjuran MAIPs</h3>
        <p class="text-sm mb-4">
          Ingin tingkatkan kemahiran diri anda untuk berkerjaya dalam bidang Drone Piloting & <span class="font-bold">Maintenance?</span>
        </p>

        <ul class="mb-6 list-decimal list-inside space-y-3">
          <li>Pensijilan profesional yang diperakui oleh <span class="font-bold">Aerodyne</span></li>
          <li>Yuran pengajian adalah <span class="font-bold">PERCUMA</span> dan elaun sara diri RM400/bulan akan diberi.</li>
          <li>Program ini terbuka kepada <span class="font-bold">Warga Perlis</span> sahaja.</li>
        </ul>

        <p class="mb-5">
          Untuk maklumat lanjut, sila hubungi Pn. Amylia di talian: <span class="font-bold">019-5944621</span>
        </p>
      </div>

      <div>
        <NuxtButton
          class="inline-flex items-center space-x-3 px-6 py-3 bg-[#FDF600] text-[#374151] font-semibold rounded-lg cursor-pointer"
        >
          <span>Mohon Sekarang</span>
          <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
        </NuxtButton>
      </div>
    </div>
  </div>

  <!-- Circle Navigation Indicator -->
  <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 flex space-x-3 z-10">
    <div class="w-3 h-3 rounded-full bg-white"></div>
    <div class="w-3 h-3 rounded-full bg-gray-400"></div>
    <div class="w-3 h-3 rounded-full bg-gray-400"></div>
  </div>
</div>

  </section>

<!-- Liputan (Desktop - Small And Large & Tablet) -->
<section class="py-16 px-8 bg-white mx-auto px-16
hidden md:block lg:block xl:block 2xl:block max-w-screen-xl">
   <span class="block w-[32px] h-[4px] bg-[#0054A5] mb-2 rounded"></span>
   <h2 class="text-4xl font-bold text-[#374151] mb-6">Saksikan Liputan Video Terkini Kami</h2>

   <div class="flex flex-col lg:flex-row gap-4">
      <!-- Main Video Player -->
      <div class="relative w-full lg:w-2/3 h-[500px] rounded-xl overflow-hidden shadow-lg">
         <NuxtImg
            src="https://s3-alpha-sig.figma.com/img/d2a9/93a0/d7b51e8149aa660b1005369812ffa6ea?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=kzrBAs618SyRcyBPHSsQlqQEDfjooC07Q8A9dUkgIH2X62-yH3sPgp2QMgELRA5Qh-PDooQaatst-LsdJayO0hTGUnHWIAgRqTGQtNGLZL2adv1I71wzp1WVzgTpdt3ZjFYqZlZAY4Dl0Ch6FZHvaug7Qfb1z6~CS26jjH7CFO8INyttHZWT-Ze6KhFrpdDZ8Lbu0d5CtMN5WSJU4NxwwhxyCAiZTt5gF57E8p8yrx5sv3O1zxbDVztJLrtZbzVTeLpyRDzfivBYIbunPIHl8yTkahmliBsyHb2je5aPoRmThJAVce6myv4WpiuXEblQaXhe5~ztCaDpGvIxt7908g__"
            alt="Video Thumbnail"
            class="w-full h-[500px] object-cover"
         />
         <!-- Overlay Play Icon -->
         <div class="absolute inset-0 flex items-center justify-center bg-black/30">
            <div class="w-20 h-20 rounded-full bg-[#00395E] flex items-center justify-center">
               <Icon name="ri:play-circle-line" class="w-16 h-16 text-white opacity-90" />
            </div>
         </div>
         <!-- Top-left Caption -->
         <div class="absolute top-0 left-0 w-full bg-gradient-to-b from-black/80 to-transparent p-4">
            <p class="text-white text-3xl font-semibold">
               Berita Wilayah - Perlis: Tuan Rumah Sambutan Hari Ulang Tahun Askar Wataniah ke-66
            </p>
            <p class="text-white text-sm font-light">
               Berita RTM
            </p>
         </div>
      </div>

      <!-- Video List (Right Column) -->
      <div 
         class="w-full lg:w-1/3 max-h-[500px] overflow-y-auto space-y-4 pr-2 p-2 rounded-xl"
         style="
            background-image: 
               linear-gradient(to bottom, #00263F 100%, #0B0D10 100%);
         "
      >
         <div
            v-for="(video, index) in berita"
            :key="index"
            :class="[ 
               'flex items-start gap-3 p-3 rounded-lg cursor-pointer transition',
               video.isChosen 
                  ? 'bg-[#EBFCFA] text-[#0054A5]' 
                  : 'text-white'
            ]"
            :style="!video.isChosen ? ` 
               background-image: 
                  linear-gradient(to bottom, #00263F 100%, #0B0D10 100%);
            ` : ''"
         >
            <NuxtImg 
               :src="video.image" 
               class="w-16 h-16 object-cover rounded-full flex-shrink-0" 
            />
            <div class="flex flex-col justify-center overflow-hidden">
               <h4 class="font-semibold text-sm truncate whitespace-nowrap overflow-hidden w-full">
                  {{ video.title }}
               </h4>
               <p
                  class="text-xs mt-1 truncate w-full"
                  :class="video.isChosen ? 'text-[#0054A5]' : 'text-[#DEE1FF]'"
               >
                  {{ video.description }}
               </p>
            </div>
         </div>
      </div>
   </div>
   <div class="flex justify-center mt-10">
      <NuxtButton
         class="inline-flex items-center space-x-3 px-6 py-3 border-[#0054A5] text-[#0054A5] border-[1px] rounded-[10px] cursor-pointer"
      >
         <p>Lihat Semua</p>
         <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
      </NuxtButton>
   </div>
</section>

<!-- Liputan (Phone) -->
<section class="py-16 px-8 bg-white mx-auto px-16
block md:hidden lg:hidden xl:hidden 2xl:hidden max-w-screen-xl">
   <span class="block w-[32px] h-[4px] bg-[#0054A5] mb-2 rounded"></span>
   <h2 class="text-4xl font-bold text-[#374151] mb-6">Saksikan Liputan Video Terkini Kami</h2>

   <div class="flex flex-col lg:flex-row gap-4">
      <!-- Main Video Player -->
      <div class="relative w-full h-full rounded-xl overflow-hidden shadow-lg">
         <NuxtImg
            src="https://s3-alpha-sig.figma.com/img/d2a9/93a0/d7b51e8149aa660b1005369812ffa6ea?Expires=1745798400&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=kzrBAs618SyRcyBPHSsQlqQEDfjooC07Q8A9dUkgIH2X62-yH3sPgp2QMgELRA5Qh-PDooQaatst-LsdJayO0hTGUnHWIAgRqTGQtNGLZL2adv1I71wzp1WVzgTpdt3ZjFYqZlZAY4Dl0Ch6FZHvaug7Qfb1z6~CS26jjH7CFO8INyttHZWT-Ze6KhFrpdDZ8Lbu0d5CtMN5WSJU4NxwwhxyCAiZTt5gF57E8p8yrx5sv3O1zxbDVztJLrtZbzVTeLpyRDzfivBYIbunPIHl8yTkahmliBsyHb2je5aPoRmThJAVce6myv4WpiuXEblQaXhe5~ztCaDpGvIxt7908g__"
            alt="Video Thumbnail"
            class="w-full h-full object-cover"
         />
         <!-- Overlay Play Icon -->
         <div class="absolute inset-0 flex items-center justify-center bg-black/30">
            <div class="w-16 h-16 rounded-full bg-[#00395E] flex items-center justify-center">
               <Icon name="ri:play-circle-line" class="w-12 h-12 text-white opacity-90" />
            </div>
         </div>
         <!-- Top-left Caption -->
         <div class="absolute top-0 left-0 w-full bg-gradient-to-b from-black/80 to-transparent p-4">
            <p class="text-white text-xs font-semibold">
               Berita Wilayah - Perlis: Tuan Rumah Sambutan Hari Ulang Tahun Askar Wataniah ke-66
            </p>
            <p class="text-white text-xs font-light">
               Berita RTM
            </p>
         </div>
      </div>

      <!-- Video List (Right Column) -->
      <div 
         class="w-full lg:w-1/3 max-h-[500px] overflow-y-auto space-y-4 pr-2 p-2 rounded-xl"
         style="
            background-image: 
               linear-gradient(to bottom, #00263F 100%, #0B0D10 100%);
         "
      >
         <div
            v-for="(video, index) in berita"
            :key="index"
            :class="[ 
               'flex items-start gap-3 p-3 rounded-lg cursor-pointer transition',
               video.isChosen 
                  ? 'bg-[#EBFCFA] text-[#0054A5]' 
                  : 'text-white'
            ]"
            :style="!video.isChosen ? ` 
               background-image: 
                  linear-gradient(to bottom, #00263F 100%, #0B0D10 100%);
            ` : ''"
         >
            <NuxtImg 
               :src="video.image" 
               class="w-16 h-16 object-cover rounded-full flex-shrink-0" 
            />
            <div class="flex flex-col justify-center overflow-hidden">
               <h4 class="font-semibold text-sm truncate whitespace-nowrap overflow-hidden w-full">
                  {{ video.title }}
               </h4>
               <p
                  class="text-xs mt-1 truncate w-full"
                  :class="video.isChosen ? 'text-[#0054A5]' : 'text-[#DEE1FF]'"
               >
                  {{ video.description }}
               </p>
            </div>
         </div>
      </div>
   </div>
   <div class="flex justify-center mt-10">
      <NuxtButton
         class="inline-flex items-center space-x-3 px-6 py-3 border-[#0054A5] text-[#0054A5] border-[1px] rounded-[10px] cursor-pointer"
      >
         <p>Lihat Semua</p>
         <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
      </NuxtButton>
   </div>
</section>


<!-- Bayar (Desktop - Small And Large) -->
<section class="relative bg-[#CCE3F2] overflow-hidden hidden lg:flex items-center justify-center min-h-[200px]">
  <!-- Gradient overlay -->
  <div class="absolute inset-0 bg-gradient-to-t from-white to-[#FFFEFE00] opacity-70 pointer-events-none"></div>

  <!-- Main Content -->
  <div class="relative z-10 flex flex-col lg:flex-row items-center justify-between gap-12 px-6 w-full max-w-7xl text-[#374151]">
    
    <!-- Left: Text -->
    <div class="flex-1 space-y-4 text-center lg:text-left">
      <h1 class="text-2xl lg:text-4xl font-bold">Keselesaan dan Kemudahan di Tangan Anda</h1>
      <p class="text-base lg:text-lg">
        Kami menyediakan pelbagai kaedah bayaran terkini untuk pusat bayaran untuk zakat, wakaf, dan sewa.
      </p>
      <NuxtButton
        class="inline-flex items-center font-bold space-x-3 px-6 py-3 bg-[#FDF600] text-[#374151] border border-gray-300 rounded-[5px] cursor-pointer"
      >
        <p>Jom Bayar Sekarang</p>
        <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
      </NuxtButton>
    </div>

    <!-- Right: Image -->
<div class="flex-1 w-full max-h-[800px] flex justify-center border-none">
  <NuxtImg src="/bayar.png" class="w-full max-h-[800px] object-contain" />
</div>
  </div>
</section>

<!-- Bayar (Tablet & Phone) -->
<section class="relative bg-[#CCE3F2] overflow-hidden block lg:hidden items-center justify-center min-h-[200px] ">
  <!-- Gradient overlay -->
  <div class="absolute inset-0 bg-gradient-to-t from-white to-[#FFFEFE00] opacity-70 pointer-events-none"></div>

  <!-- Main Content -->
  <div class="relative z-10 flex flex-col items-start justify-between gap-3 w-full max-w-7xl text-[#374151]">
    
    <!-- Left: Text -->
    <div class="flex-1 space-y-4 text-left py-12 px-12">
      <h1 class="text-4xl font-bold">Keselesaan dan Kemudahan <br/>di Tangan Anda</h1>
      <p class="text-lg">
        Kami menyediakan pelbagai kaedah bayaran terkini <br/> untuk pusat bayaran untuk zakat, wakaf, dan sewa.
      </p>
      <NuxtButton
        class="inline-flex items-center font-bold space-x-3 px-6 py-3 bg-[#FDF600] text-[#374151] border border-gray-300 rounded-[5px] cursor-pointer"
      >
        <p>Jom Bayar Sekarang</p>
        <Icon name="heroicons:arrow-long-right" class="w-5 h-5" />
      </NuxtButton>
    </div>

    <!-- Right: Image -->
    <div class="flex-1 w-full max-h-[800px] flex justify-center border-none">
      <NuxtImg src="/bayar.png" class="w-full max-h-[800px] object-contain" />
    </div>
  </div>
</section>

<!-- Pautan Pantas -->
<section class="py-16 px-8 bg-white mx-auto px-16 max-w-screen-xl">
   <span class="block w-[32px] h-[4px] bg-[#0054A5] mb-2 rounded"></span>
   <h2 class="text-4xl font-bold text-[#374151] mb-6">Pautan Pantas</h2>

   <!-- MAIPs -->
    <NuxtButton
      @click="toggleLinks1"
      class="flex flex-col items-start gap-2 px-4 py-4 bg-white border-[2px] border-gray-200 text-white rounded-[5px] mb-4 cursor-pointer w-full"
    >
      <!-- Button Header -->
      <div class="flex items-center gap-2">
        <Icon
          :name="showLinks1 ? 'mdi:minus-circle-outline' : 'ri:add-circle-line'"
          class="w-5 h-5 text-[#374151]"
        />
        <h4 class="font-bold text-[#374151]">Pautan MAIPs</h4>
      </div>

      <!-- Transition Wrapper -->
      <transition
        name="fade-expand"
        mode="out-in"
      >
        <div
          v-if="showLinks1"
          class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 xl:grid-cols-9 gap-4 px-2 py-2 mt-3 w-full text-[#374151]"
        >
      <div
        v-for="(item, index) in pautanMAIPs"
        :key="index"
        class="flex flex-col items-center"
      >
        <!-- NuxtLink wrapping the image and title -->
        <NuxtLink
          :to="item.link"
          class="flex flex-col items-center"
        >
          <NuxtImg
            :src="item.image"
            :alt="item.title"
            class="w-20 h-20 object-cover rounded-t-lg"
          />
          <h2 class="font-bold text-center text-sm">{{ item.title }}</h2>
        </NuxtLink>
      </div>

        </div>
      </transition>
    </NuxtButton>

     <!-- MAIN -->
    <NuxtButton
      @click="toggleLinks2"
      class="flex flex-col items-start gap-2 px-4 py-4 bg-white border-[2px] border-gray-200 text-white rounded-[5px] mb-4 cursor-pointer w-full"
    >
      <!-- Button Header -->
      <div class="flex items-center gap-2">
        <Icon
          :name="showLinks2 ? 'mdi:minus-circle-outline' : 'ri:add-circle-line'"
          class="w-5 h-5 text-[#374151]"
        />
        <h4 class="font-bold text-[#374151]">Pautan MAIN</h4>
      </div>

      <!-- Transition Wrapper -->
      <transition
        name="fade-expand"
        mode="out-in"
      >
        <div
          v-if="showLinks2"
          class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 xl:grid-cols-9 gap-4 px-2 py-2 mt-3 w-full text-[#374151]"
        >
      <div
        v-for="(item, index) in pautanMAIN"
        :key="index"
        class="flex flex-col items-center"
      >
        <!-- NuxtLink wrapping the image and title -->
        <NuxtLink
          :to="item.link"
          class="flex flex-col items-center"
        >
          <NuxtImg
            :src="item.image"
            :alt="item.title"
            class="w-20 h-20 object-cover rounded-t-lg"
          />
          <h2 class="font-bold text-center text-sm">{{ item.title }}</h2>
        </NuxtLink>
      </div>

        </div>
      </transition>
    </NuxtButton>

    <!-- Agensi -->
    <NuxtButton
      @click="toggleLinks3"
      class="flex flex-col items-start gap-2 px-4 py-4 bg-white border-[2px] border-gray-200 text-white rounded-[5px] mb-4 cursor-pointer w-full"
    >
      <!-- Button Header -->
      <div class="flex items-center gap-2">
        <Icon
          :name="showLinks3 ? 'mdi:minus-circle-outline' : 'ri:add-circle-line'"
          class="w-5 h-5 text-[#374151]"
        />
        <h4 class="font-bold text-[#374151]">Pautan Agensi Kerajaan</h4>
      </div>

      <!-- Transition Wrapper -->
      <transition
        name="fade-expand"
        mode="out-in"
      >
        <div
          v-if="showLinks3"
          class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 xl:grid-cols-9 gap-4 px-2 py-2 mt-3 w-full text-[#374151]"
        >
      <div
        v-for="(item, index) in pautanAgensi"
        :key="index"
        class="flex flex-col items-center"
      >
        <!-- NuxtLink wrapping the image and title -->
        <NuxtLink
          :to="item.link"
          class="flex flex-col items-center"
        >
          <NuxtImg
            :src="item.image"
            :alt="item.title"
            class="w-20 h-20 object-cover rounded-t-lg"
          />
          <h2 class="font-bold text-center text-sm">{{ item.title }}</h2>
        </NuxtLink>
      </div>

        </div>
      </transition>
    </NuxtButton>

</section>

</template>

<style>
.fade-expand-enter-active,
.fade-expand-leave-active {
  transition: all 0.5s ease;
  overflow: hidden;
}

.fade-expand-enter-from,
.fade-expand-leave-to {
  opacity: 0;
  transform: scaleY(0.95);
  max-height: 0;
}

.fade-expand-enter-to,
.fade-expand-leave-from {
  opacity: 1;
  transform: scaleY(1);
  max-height: 1000px;
}
</style>

