<template>
  <div id="app" class="bg-[#1A2E1A] text-[#F0E8D6] font-[Outfit]">

    <!-- ===== NAVBAR ===== -->
    <nav
      :class="[
        'fixed top-0 left-0 right-0 z-50 transition-all duration-500',
        scrolled ? 'glass shadow-lg shadow-black/30 py-3' : 'bg-transparent py-5'
      ]"
    >
      <div class="max-w-7xl mx-auto px-6 flex items-center justify-between">
        <!-- Logo -->
        <!-- Logo -->
        <a href="#home" class="flex flex-col items-start">
          <span class="text-3xl font-black tracking-wider text-[#F0E8D6]" style="font-family: 'Outfit', sans-serif; letter-spacing: 0.15em;">grano</span>
          <span class="text-[9px] tracking-[0.3em] text-[#C9A84C] uppercase font-light -mt-1">Yaourt Glacé · Crêpe & Co.</span>
        </a>

        <!-- Desktop Nav -->
        <div class="hidden md:flex items-center gap-8">
          <a
            v-for="link in navLinks"
            :key="link.id"
            :href="'#' + link.id"
            class="text-sm tracking-widest uppercase text-[#F0E8D6]/70 hover:text-[#C9A84C] transition-all duration-300 hover:tracking-[0.25em] relative group"
          >
            {{ link.label }}
            <span class="absolute -bottom-1 left-0 w-0 h-px bg-[#C9A84C] group-hover:w-full transition-all duration-300"></span>
          </a>
        </div>

        <!-- CTA Button -->
        <a
          href="#contact"
          class="hidden md:flex items-center gap-2 bg-[#C9A84C] text-[#1A2E1A] px-6 py-2.5 rounded-full font-semibold text-sm tracking-wide hover:bg-[#E2C46A] transition-all duration-300 hover:scale-105 hover:shadow-lg hover:shadow-[#C9A84C]/30"
        >
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
          </svg>
          Nous trouver
        </a>

        <!-- Mobile Menu Button -->
        <button @click="mobileMenuOpen = !mobileMenuOpen" class="md:hidden text-[#F0E8D6] p-2">
          <svg v-if="!mobileMenuOpen" class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
          </svg>
          <svg v-else class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
          </svg>
        </button>
      </div>

      <!-- Mobile Menu -->
      <Transition name="slide-down">
        <div v-if="mobileMenuOpen" class="md:hidden glass border-t border-[#C9A84C]/20 mt-2">
          <div class="flex flex-col px-6 py-4 gap-4">
            <a
              v-for="link in navLinks"
              :key="link.id"
              :href="'#' + link.id"
              @click="mobileMenuOpen = false"
              class="text-sm tracking-widest uppercase text-[#F0E8D6]/80 hover:text-[#C9A84C] transition-colors py-2 border-b border-[#C9A84C]/10"
            >
              {{ link.label }}
            </a>
          </div>
        </div>
      </Transition>
    </nav>

    <!-- ===== HERO SECTION ===== -->
    <section id="home" class="relative min-h-screen flex items-center justify-center overflow-hidden">
      <!-- Background image -->
      <div class="absolute inset-0">
        <img src="/hero.jpg" alt="Grano - Yaourt Glacé Crêpe & Co." class="w-full h-full object-cover opacity-40" />
        <div class="absolute inset-0 bg-gradient-to-b from-[#1A2E1A]/60 via-[#1A2E1A]/30 to-[#1A2E1A]"></div>
        <div class="absolute inset-0 bg-gradient-to-r from-[#1A2E1A]/80 via-transparent to-[#1A2E1A]/40"></div>
      </div>

      <!-- Floating decorative orbs -->
      <div class="absolute top-1/4 right-1/4 w-64 h-64 bg-[#C9A84C]/10 rounded-full blur-3xl animate-float"></div>
      <div class="absolute bottom-1/3 left-1/6 w-96 h-96 bg-[#2D4A2D]/50 rounded-full blur-3xl" style="animation: float 6s ease-in-out infinite 2s;"></div>

      <!-- Hero Content -->
      <div class="relative z-10 text-center max-w-5xl mx-auto px-6">
        <!-- Badge -->
        <div class="inline-flex items-center gap-2 glass px-4 py-2 rounded-full mb-8 text-xs tracking-[0.2em] uppercase text-[#C9A84C] animate-fade-in-up">
          <span class="w-2 h-2 bg-[#C9A84C] rounded-full animate-pulse"></span>
          Ouvert jusqu'à minuit · Zarzis, Tunisie
        </div>

        <!-- Main Title -->
        <h1 class="text-8xl md:text-[10rem] font-black leading-none mb-4 animate-fade-in-up" style="animation-delay: 0.1s; font-family: 'Outfit', sans-serif; letter-spacing: -0.02em;">
          <span class="gradient-text">grano</span>
        </h1>

        <!-- Subtitle -->
        <p class="text-lg md:text-xl tracking-[0.4em] uppercase text-[#C9A84C]/80 mb-6 animate-fade-in-up font-light" style="animation-delay: 0.2s;">
          Yaourt Glacé · Crêpe & Co.
        </p>

        <!-- Description -->
        <p class="text-[#F0E8D6]/70 text-lg md:text-xl max-w-2xl mx-auto leading-relaxed mb-10 animate-fade-in-up" style="animation-delay: 0.3s; font-weight: 300;">
          Plongez dans un univers de saveurs uniques. Crêpes gourmandes, yaourts glacés onctueux, bubble cups et milkshakes d'exception.
        </p>

        <!-- CTA Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center animate-fade-in-up" style="animation-delay: 0.4s;">
          <a
            href="#menu"
            class="group bg-[#C9A84C] text-[#1A2E1A] px-10 py-4 rounded-full font-bold text-base tracking-wide hover:bg-[#E2C46A] transition-all duration-300 hover:scale-105 animate-pulse-glow flex items-center justify-center gap-2"
          >
            Découvrir le menu
            <svg class="w-5 h-5 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
            </svg>
          </a>
          <a
            href="#about"
            class="glass-light text-[#F0E8D6] px-10 py-4 rounded-full font-medium text-base tracking-wide hover:bg-[#F0E8D6]/15 transition-all duration-300 border border-[#F0E8D6]/20"
          >
            Notre histoire
          </a>
        </div>

        <!-- Stats -->
        <div class="flex flex-wrap justify-center gap-10 mt-16 animate-fade-in-up" style="animation-delay: 0.5s;">
          <div v-for="stat in stats" :key="stat.label" class="text-center">
            <div class="text-3xl font-bold text-[#C9A84C] mb-1">{{ stat.value }}</div>
            <div class="text-xs tracking-widest uppercase text-[#F0E8D6]/50">{{ stat.label }}</div>
          </div>
        </div>
      </div>

      <!-- Scroll indicator -->
      <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 opacity-50">
        <span class="text-xs tracking-widest uppercase">Scroll</span>
        <div class="w-px h-12 bg-gradient-to-b from-[#C9A84C] to-transparent"></div>
      </div>
    </section>

    <!-- ===== MARQUEE BAND ===== -->
    <div class="py-5 bg-[#C9A84C] overflow-hidden relative">
      <div class="flex animate-marquee whitespace-nowrap">
        <span v-for="i in 20" :key="i" class="text-[#1A2E1A] text-sm font-bold tracking-widest uppercase mx-8 flex items-center gap-3">
          <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/></svg>
          Yaourt Glacé · Crêpe Nutella · Bubble Cup · Milkshake Oreo · Speculoos · Ferrero Rocher · Pistachio
        </span>
      </div>
    </div>

    <!-- ===== ABOUT SECTION ===== -->
    <section id="about" class="py-28 relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-br from-[#2D4A2D]/40 to-transparent"></div>
      <div class="max-w-7xl mx-auto px-6 relative z-10">
        <div class="grid md:grid-cols-2 gap-16 items-center">
          <!-- Image side -->
          <div class="relative">
            <div class="relative rounded-3xl overflow-hidden aspect-[4/5]">
              <img src="/interior.jpg" alt="Intérieur du café Grano" class="w-full h-full object-cover" />
              <div class="absolute inset-0 bg-gradient-to-t from-[#1A2E1A]/60 to-transparent"></div>
            </div>
            <!-- Floating card -->
            <div class="absolute -bottom-6 -right-6 glass rounded-2xl p-5 max-w-[200px] animate-pulse-glow">
              <div class="flex items-center gap-1 mb-2">
                <svg v-for="s in 5" :key="s" class="w-4 h-4 text-[#C9A84C]" fill="currentColor" viewBox="0 0 20 20">
                  <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
                </svg>
              </div>
              <p class="text-[#F0E8D6] text-xs leading-relaxed">"Une ambiance magnifique et des saveurs inoubliables !"</p>
              <p class="text-[#C9A84C] text-xs mt-2 font-semibold">Hadil S.</p>
            </div>
            <!-- Decorative badge -->
            <div class="absolute -top-4 -left-4 w-20 h-20 glass rounded-2xl flex flex-col items-center justify-center rotate-12 hover:rotate-0 transition-transform duration-500">
              <span class="text-2xl font-black text-[#C9A84C]">4.4</span>
              <span class="text-[8px] tracking-wider text-[#F0E8D6]/60 uppercase">Google</span>
            </div>
          </div>

          <!-- Text side -->
          <div class="space-y-7">
            <div class="separator"></div>
            <h2 class="text-5xl md:text-6xl font-black leading-tight">
              L'art des<br/>
              <span class="gradient-text">saveurs</span><br/>
              gourmandes
            </h2>
            <p class="text-[#F0E8D6]/70 text-lg leading-relaxed font-light">
              Situé au cœur de Zarzis, <strong class="text-[#C9A84C] font-semibold">Grano</strong> est bien plus qu'une simple crêperie. C'est un lieu de partage où chaque bouchée raconte une histoire de passion et de générosité.
            </p>
            <p class="text-[#F0E8D6]/70 text-lg leading-relaxed font-light">
              Nous sélectionnons les meilleurs ingrédients pour vous offrir une expérience culinaire unique : yaourts glacés crémeux, crêpes dorées aux garnitures généreuses et milkshakes gourmands.
            </p>

            <!-- Features -->
            <div class="grid grid-cols-2 gap-4 mt-8">
              <div v-for="feature in features" :key="feature.title" class="glass rounded-2xl p-4 hover:border-[#C9A84C]/40 transition-all duration-300 group cursor-default">
                <div class="text-2xl mb-2">{{ feature.icon }}</div>
                <div class="text-sm font-semibold text-[#C9A84C] group-hover:text-[#E2C46A] transition-colors">{{ feature.title }}</div>
                <div class="text-xs text-[#F0E8D6]/50 mt-1">{{ feature.desc }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== MENU SECTION ===== -->
    <section id="menu" class="py-28 relative overflow-hidden">
      <div class="absolute inset-0">
        <div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-[#C9A84C]/40 to-transparent"></div>
        <div class="absolute bottom-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-[#C9A84C]/40 to-transparent"></div>
      </div>

      <div class="max-w-7xl mx-auto px-6">
        <!-- Section Header -->
        <div class="text-center mb-16">
          <div class="separator mx-auto mb-6"></div>
          <h2 class="text-5xl md:text-6xl font-black mb-4">Notre <span class="gradient-text">Menu</span></h2>
          <p class="text-[#F0E8D6]/60 text-lg max-w-xl mx-auto font-light">Des créations uniques pour tous les amoureux de douceurs</p>
        </div>

        <!-- Category Tabs -->
        <div class="flex flex-wrap justify-center gap-3 mb-12">
          <button
            v-for="cat in categories"
            :key="cat.id"
            @click="activeCategory = cat.id"
            :class="[
              'px-6 py-2.5 rounded-full text-sm font-semibold tracking-wide transition-all duration-300',
              activeCategory === cat.id
                ? 'bg-[#C9A84C] text-[#1A2E1A] shadow-lg shadow-[#C9A84C]/30 scale-105'
                : 'glass text-[#F0E8D6]/70 hover:text-[#C9A84C] hover:border-[#C9A84C]/40'
            ]"
          >
            {{ cat.icon }} {{ cat.label }}
          </button>
        </div>

        <!-- Menu Cards -->
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="item in filteredMenu"
            :key="item.name"
            class="menu-card glass rounded-3xl overflow-hidden group cursor-pointer"
          >
            <div class="relative h-52 overflow-hidden">
              <img :src="item.image" :alt="item.name" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700" />
              <div class="absolute inset-0 bg-gradient-to-t from-[#1A2E1A]/80 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
              <div class="absolute top-3 right-3">
                <span class="glass px-3 py-1 rounded-full text-xs font-semibold text-[#C9A84C]">{{ item.tag }}</span>
              </div>
              <div class="absolute bottom-0 left-0 right-0 p-4 transform translate-y-full group-hover:translate-y-0 transition-transform duration-300">
                <p class="text-xs text-[#F0E8D6]/80 leading-relaxed">{{ item.description }}</p>
              </div>
            </div>
            <div class="p-5">
              <div class="flex items-start justify-between">
                <div>
                  <h3 class="font-bold text-lg text-[#F0E8D6] group-hover:text-[#C9A84C] transition-colors">{{ item.name }}</h3>
                  <p class="text-xs text-[#F0E8D6]/50 mt-1 tracking-wide">{{ item.subtitle }}</p>
                </div>
                <div class="text-right">
                  <div class="flex items-center gap-0.5">
                    <svg v-for="s in 5" :key="s" class="w-3 h-3 text-[#C9A84C]" fill="currentColor" viewBox="0 0 20 20">
                      <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
                    </svg>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== SIGNATURE ITEMS ===== -->
    <section class="py-28 bg-[#2D4A2D]/30 relative overflow-hidden">
      <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] bg-[#C9A84C]/5 rounded-full blur-3xl"></div>
      <div class="max-w-7xl mx-auto px-6 relative z-10">
        <div class="text-center mb-16">
          <div class="separator mx-auto mb-6"></div>
          <h2 class="text-5xl md:text-6xl font-black mb-4">Les <span class="gradient-text">Incontournables</span></h2>
          <p class="text-[#F0E8D6]/60 text-lg font-light">Les créations qui font notre renommée</p>
        </div>

        <div class="grid md:grid-cols-3 gap-8">
          <div
            v-for="(signature, idx) in signatures"
            :key="signature.title"
            class="relative group"
            :class="idx === 1 ? 'md:-mt-8' : ''"
          >
            <div class="glass rounded-3xl overflow-hidden hover:border-[#C9A84C]/50 transition-all duration-500 group-hover:shadow-2xl group-hover:shadow-[#C9A84C]/10">
              <div class="relative h-72 overflow-hidden">
                <img :src="signature.image" :alt="signature.title" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700" />
                <div class="absolute inset-0 bg-gradient-to-t from-[#1A2E1A] via-[#1A2E1A]/30 to-transparent"></div>
                <div class="absolute bottom-0 left-0 right-0 p-6">
                  <div class="text-3xl mb-2">{{ signature.emoji }}</div>
                  <h3 class="text-2xl font-black text-[#F0E8D6]">{{ signature.title }}</h3>
                  <p class="text-[#C9A84C] text-sm font-medium mt-1">{{ signature.tagline }}</p>
                </div>
              </div>
              <div class="p-6">
                <p class="text-[#F0E8D6]/60 text-sm leading-relaxed font-light">{{ signature.desc }}</p>
                <div class="flex flex-wrap gap-2 mt-4">
                  <span
                    v-for="flavor in signature.flavors"
                    :key="flavor"
                    class="bg-[#C9A84C]/10 text-[#C9A84C] text-xs px-3 py-1 rounded-full border border-[#C9A84C]/20"
                  >
                    {{ flavor }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== GALLERY SECTION ===== -->
    <section id="gallery" class="py-28 relative overflow-hidden">
      <div class="max-w-7xl mx-auto px-6">
        <div class="text-center mb-16">
          <div class="separator mx-auto mb-6"></div>
          <h2 class="text-5xl md:text-6xl font-black mb-4"><span class="gradient-text">Galerie</span></h2>
          <p class="text-[#F0E8D6]/60 text-lg font-light">Un festin pour les yeux avant d'être pour les papilles</p>
        </div>

        <!-- Masonry-style grid -->
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
          <div
            v-for="(gImg, idx) in gallery"
            :key="idx"
            :class="['relative rounded-2xl overflow-hidden group cursor-pointer', gImg.tall ? 'row-span-2' : '']"
            @mouseenter="hoveredGallery = idx"
            @mouseleave="hoveredGallery = null"
          >
            <img
              :src="gImg.src"
              :alt="gImg.alt"
              class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110"
              :style="gImg.tall ? 'height: 500px' : 'height: 240px'"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-[#1A2E1A]/70 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end p-4">
              <p class="text-white text-sm font-medium">{{ gImg.alt }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== REVIEWS SECTION ===== -->
    <section id="reviews" class="py-28 bg-[#2D4A2D]/30 relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-b from-transparent via-[#C9A84C]/3 to-transparent"></div>
      <div class="max-w-7xl mx-auto px-6 relative z-10">
        <!-- Header -->
        <div class="text-center mb-16">
          <div class="separator mx-auto mb-6"></div>
          <h2 class="text-5xl md:text-6xl font-black mb-4">Ce qu'ils <span class="gradient-text">disent</span></h2>
          <!-- Rating summary -->
          <div class="flex flex-col items-center gap-4 mt-8">
            <div class="text-8xl font-black text-[#C9A84C]">4.4</div>
            <div class="flex gap-1">
              <svg v-for="s in 5" :key="s" class="w-8 h-8 text-[#C9A84C]" fill="currentColor" viewBox="0 0 20 20">
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
              </svg>
            </div>
            <p class="text-[#F0E8D6]/50 text-sm tracking-widest uppercase">73 avis Google</p>
          </div>
        </div>

        <!-- Reviews Cards -->
        <div class="grid md:grid-cols-3 gap-6">
          <div
            v-for="review in reviews"
            :key="review.name"
            class="glass rounded-3xl p-7 hover:border-[#C9A84C]/40 transition-all duration-500 hover:-translate-y-2 hover:shadow-xl hover:shadow-[#C9A84C]/10"
          >
            <div class="flex items-start gap-4 mb-5">
              <div class="w-12 h-12 rounded-full bg-gradient-to-br from-[#C9A84C] to-[#7B5C3A] flex items-center justify-center text-[#1A2E1A] font-black text-lg flex-shrink-0">
                {{ review.name.charAt(0) }}
              </div>
              <div>
                <h4 class="font-bold text-[#F0E8D6]">{{ review.name }}</h4>
                <p class="text-xs text-[#F0E8D6]/40 mt-0.5">{{ review.date }}</p>
                <div class="flex gap-0.5 mt-1">
                  <svg v-for="s in review.rating" :key="s" class="w-3.5 h-3.5 text-[#C9A84C]" fill="currentColor" viewBox="0 0 20 20">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
                  </svg>
                </div>
              </div>
            </div>
            <p class="text-[#F0E8D6]/70 text-sm leading-relaxed font-light italic">"{{ review.text }}"</p>
            <div class="mt-4 flex flex-wrap gap-2">
              <span
                v-for="tag in review.tags"
                :key="tag"
                class="text-xs px-2 py-0.5 bg-[#C9A84C]/10 text-[#C9A84C] rounded-full"
              >
                #{{ tag }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== CONTACT SECTION ===== -->
    <section id="contact" class="py-28 relative overflow-hidden">
      <div class="absolute inset-0">
        <div class="absolute top-0 left-0 right-0 h-px bg-gradient-to-r from-transparent via-[#C9A84C]/40 to-transparent"></div>
      </div>
      <div class="max-w-7xl mx-auto px-6">
        <div class="text-center mb-16">
          <div class="separator mx-auto mb-6"></div>
          <h2 class="text-5xl md:text-6xl font-black mb-4">Nous <span class="gradient-text">Trouver</span></h2>
          <p class="text-[#F0E8D6]/60 text-lg font-light">Venez nous rendre visite à Zarzis</p>
        </div>

        <div class="grid md:grid-cols-2 gap-12 items-start">
          <!-- Info cards -->
          <div class="space-y-5">
            <div
              v-for="info in contactInfo"
              :key="info.label"
              class="glass rounded-2xl p-6 flex items-start gap-5 hover:border-[#C9A84C]/40 transition-all duration-300 group"
            >
              <div class="w-12 h-12 bg-[#C9A84C]/10 rounded-xl flex items-center justify-center text-[#C9A84C] text-xl flex-shrink-0 group-hover:bg-[#C9A84C]/20 transition-colors">
                {{ info.icon }}
              </div>
              <div>
                <h4 class="font-semibold text-[#C9A84C] text-sm tracking-widest uppercase mb-1">{{ info.label }}</h4>
                <p class="text-[#F0E8D6]/80 font-medium" v-html="info.value"></p>
                <p v-if="info.sub" class="text-[#F0E8D6]/50 text-sm mt-1">{{ info.sub }}</p>
              </div>
            </div>

            <!-- CTA Button -->
            <a
              href="https://maps.google.com/?q=Grano+Zarzis+Route+du+port+4170"
              target="_blank"
              rel="noopener"
              class="flex items-center justify-center gap-3 w-full bg-[#C9A84C] text-[#1A2E1A] py-4 rounded-2xl font-bold text-base tracking-wide hover:bg-[#E2C46A] transition-all duration-300 hover:scale-[1.02] hover:shadow-xl hover:shadow-[#C9A84C]/30 mt-2"
            >
              <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/>
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/>
              </svg>
              Ouvrir dans Google Maps
            </a>
          </div>

          <!-- Map embed placeholder + Visual -->
          <div class="glass rounded-3xl overflow-hidden aspect-[4/3] relative">
            <iframe
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3296.8!2d11.1073!3d33.5036!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMzPCsDMwJzEzLjAiTiAxMcKwMDYnMjYuMyJF!5e0!3m2!1sfr!2stn!4v1234567890"
              class="w-full h-full border-0"
              style="filter: invert(90%) hue-rotate(160deg) saturate(0.6) brightness(0.9);"
              loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"
            ></iframe>
            <div class="absolute inset-0 pointer-events-none border border-[#C9A84C]/20 rounded-3xl"></div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== FOOTER ===== -->
    <footer class="bg-[#0F1F0F] py-16 relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-t from-black/30 to-transparent"></div>
      <div class="max-w-7xl mx-auto px-6 relative z-10">
        <div class="grid md:grid-cols-3 gap-12 mb-12">
          <!-- Brand -->
          <div class="space-y-4">
            <div>
              <h3 class="text-4xl font-black tracking-wider text-[#F0E8D6]">grano</h3>
              <p class="text-xs tracking-[0.3em] text-[#C9A84C] uppercase font-light">Yaourt Glacé · Crêpe & Co.</p>
            </div>
            <p class="text-[#F0E8D6]/50 text-sm leading-relaxed font-light">
              Une expérience gourmande unique au cœur de Zarzis, Tunisie.
            </p>
            <!-- Social -->
            <div class="flex gap-3">
              <a href="#" aria-label="Facebook" class="w-10 h-10 glass rounded-xl flex items-center justify-center text-[#F0E8D6]/60 hover:text-[#C9A84C] hover:border-[#C9A84C]/40 transition-all duration-300">
                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>
              </a>
              <a href="#" aria-label="Instagram" class="w-10 h-10 glass rounded-xl flex items-center justify-center text-[#F0E8D6]/60 hover:text-[#C9A84C] hover:border-[#C9A84C]/40 transition-all duration-300">
                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
              </a>
              <a href="tel:+21628406108" aria-label="Phone" class="w-10 h-10 glass rounded-xl flex items-center justify-center text-[#F0E8D6]/60 hover:text-[#C9A84C] hover:border-[#C9A84C]/40 transition-all duration-300">
                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/></svg>
              </a>
            </div>
          </div>

          <!-- Quick links -->
          <div>
            <h4 class="font-bold text-[#C9A84C] tracking-widest uppercase text-sm mb-5">Navigation</h4>
            <div class="space-y-3">
              <a v-for="link in navLinks" :key="link.id" :href="'#' + link.id"
                class="block text-[#F0E8D6]/50 hover:text-[#C9A84C] transition-colors text-sm hover:translate-x-1 transform duration-200">
                {{ link.label }}
              </a>
            </div>
          </div>

          <!-- Hours -->
          <div>
            <h4 class="font-bold text-[#C9A84C] tracking-widest uppercase text-sm mb-5">Horaires</h4>
            <div class="space-y-3">
              <div v-for="h in hours" :key="h.days" class="flex justify-between text-sm">
                <span class="text-[#F0E8D6]/50">{{ h.days }}</span>
                <span class="text-[#F0E8D6]/80 font-medium">{{ h.time }}</span>
              </div>
            </div>
            <div class="mt-5 flex items-center gap-2">
              <div class="w-2 h-2 bg-green-400 rounded-full animate-pulse"></div>
              <span class="text-green-400 text-xs font-semibold">Ouvert maintenant</span>
            </div>
          </div>
        </div>

        <!-- Bottom bar -->
        <div class="border-t border-[#F0E8D6]/10 pt-8 flex flex-col md:flex-row justify-between items-center gap-4">
          <p class="text-[#F0E8D6]/30 text-xs">© 2024 Grano — Yaourt Glacé, Crêpe & Co. Tous droits réservés.</p>
          <p class="text-[#F0E8D6]/30 text-xs">Route du port 4170, Zarzis, Tunisie · ☎ 28 406 108</p>
        </div>
      </div>
    </footer>

    <!-- Scroll to top button -->
    <Transition name="fade">
      <button
        v-if="scrolled && scrollY > 500"
        @click="scrollToTop"
        class="fixed bottom-8 right-8 w-12 h-12 bg-[#C9A84C] text-[#1A2E1A] rounded-full flex items-center justify-center shadow-lg shadow-[#C9A84C]/30 hover:bg-[#E2C46A] hover:scale-110 transition-all duration-300 z-50 animate-pulse-glow"
        aria-label="Retour en haut"
      >
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18"/>
        </svg>
      </button>
    </Transition>

  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue'

// Reactive state
const scrolled = ref(false)
const scrollY = ref(0)
const mobileMenuOpen = ref(false)
const activeCategory = ref('all')
const hoveredGallery = ref<number | null>(null)

// Scroll handler
const handleScroll = () => {
  scrollY.value = window.scrollY
  scrolled.value = window.scrollY > 50
}

const scrollToTop = () => window.scrollTo({ top: 0, behavior: 'smooth' })

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))

// Data
const navLinks = [
  { id: 'home', label: 'Accueil' },
  { id: 'about', label: 'À propos' },
  { id: 'menu', label: 'Menu' },
  { id: 'gallery', label: 'Galerie' },
  { id: 'reviews', label: 'Avis' },
  { id: 'contact', label: 'Contact' },
]

const stats = [
  { value: '4.4★', label: 'Note Google' },
  { value: '73+', label: 'Avis clients' },
  { value: '100%', label: 'Fait maison' },
  { value: '0AM', label: 'Fermeture' },
]

const features = [
  { icon: '🧁', title: 'Fait Maison', desc: 'Préparations fraîches chaque jour' },
  { icon: '🌿', title: 'Qualité Premium', desc: 'Ingrédients soigneusement sélectionnés' },
  { icon: '✨', title: 'Créatif', desc: 'Combinaisons de saveurs originales' },
  { icon: '😊', title: 'Service chaleureux', desc: 'Une équipe passionnée et souriante' },
]

const categories = [
  { id: 'all', icon: '🍽️', label: 'Tout' },
  { id: 'yaourt', icon: '🍦', label: 'Yaourt Glacé' },
  { id: 'crepe', icon: '🥞', label: 'Crêpes' },
  { id: 'milkshake', icon: '🥤', label: 'Milkshakes' },
  { id: 'bubble', icon: '🧋', label: 'Bubble Cup' },
]

const menuItems = [
  { name: 'Yaourt Glacé Pistachio', subtitle: 'La star de l\'été', tag: 'Best-seller', category: 'yaourt', image: '/yogurt.jpg', description: 'Yaourt glacé à la pistache, sauce pistachio, granola croquant et pistaches concassées.' },
  { name: 'Yaourt Glacé Nutella Speculoos', subtitle: 'Le classique gourmand', tag: 'Populaire', category: 'yaourt', image: '/yogurt.jpg', description: 'Yaourt glacé nappé de Nutella et Speculoos crémeux, le duo parfait.' },
  { name: 'Crêpe Kinder Bueno', subtitle: 'Indulgence absolue', tag: 'Signature', category: 'crepe', image: '/crepe.jpg', description: 'Crêpe dorée, Nutella, morceaux de Kinder Bueno, amandes effilées, sauce chocolat blanc.' },
  { name: 'Milkshake Oreo', subtitle: 'Onctueux & intense', tag: 'Favori', category: 'milkshake', image: '/milkshake.jpg', description: 'Milkshake crémeux aux Oreo, chantilly généreuse et sauce chocolat maison.' },
  { name: 'Milkshake Caramel', subtitle: 'Douceur dorée', tag: 'Nouveau', category: 'milkshake', image: '/milkshake.jpg', description: 'Milkshake caramel salé, chantilly, popcorn caramel et filet de caramel.' },
  { name: 'Big Bubble Nutella', subtitle: 'Le grand format', tag: 'Coup de cœur', category: 'bubble', image: '/hero.jpg', description: 'Grande bulle crémeuse au Nutella, chantilly et pépites de chocolat.' },
]

const filteredMenu = computed(() =>
  activeCategory.value === 'all'
    ? menuItems
    : menuItems.filter(i => i.category === activeCategory.value)
)

const signatures = [
  {
    emoji: '🍦',
    title: 'Yaourt Glacé',
    tagline: 'La fraîcheur en tourbillon',
    image: '/yogurt.jpg',
    desc: 'Notre spécialité iconique : un tourbillon de yaourt glacé onctueux garni de vos toppings préférés. Pistachio, Nutella, Speculoos...',
    flavors: ['Pistachio', 'Nutella', 'Speculoos', 'Ferrero Rocher'],
  },
  {
    emoji: '🥞',
    title: 'Crêpes Signatures',
    tagline: 'L\'art de la crêpe gourmande',
    image: '/crepe.jpg',
    desc: 'Des crêpes dorées à la perfection, garnies d\'ingrédients premium pour une explosion de saveurs en bouche.',
    flavors: ['Kinder Bueno', 'Nutella', 'Pistachio', 'Banane'],
  },
  {
    emoji: '🥤',
    title: 'Milkshakes & Bubble',
    tagline: 'Le plaisir en grande taille',
    image: '/milkshake.jpg',
    desc: 'Des milkshakes et bubble cups maison à tomber par terre, avec une chantilly généreuse et des toppings de folie.',
    flavors: ['Oreo', 'Caramel', 'Chocolat', 'Fruits rouges'],
  },
]

const gallery = [
  { src: '/hero.jpg', alt: 'Sélection Grano', tall: true },
  { src: '/yogurt.jpg', alt: 'Yaourt Glacé Pistachio', tall: false },
  { src: '/milkshake.jpg', alt: 'Milkshakes Grano', tall: false },
  { src: '/crepe.jpg', alt: 'Crêpe Kinder Bueno', tall: false },
  { src: '/interior.jpg', alt: 'Ambiance Grano', tall: true },
  { src: '/yogurt.jpg', alt: 'Yaourt Glacé Speculoos', tall: false },
]

const reviews = [
  {
    name: 'Hadil Soltana',
    date: 'Il y a un an · Guide Local',
    rating: 5,
    text: 'J\'ai essayé la crêpe et le yaourt glacé. Vraiment délicieux ! Le personnel était professionnel et sympathique. Je recommande vivement les options Ferrero Rocher et Speculoos. Délicieux !',
    tags: ['yaourt', 'ferrero', 'service'],
  },
  {
    name: 'Fatma SAADALLAH',
    date: 'Il y a un an',
    rating: 5,
    text: 'Délicieux ! Une expérience culinaire exceptionnelle. Les saveurs sont uniques et les portions généreuses. Un vrai coup de cœur pour ce café !',
    tags: ['délicieux', 'généreux'],
  },
  {
    name: 'Baylessène Sassi',
    date: 'Il y a 2 ans',
    rating: 5,
    text: 'J\'avais commandé un Big Bubble au Nutella et Milkshake Oreo, c\'était super bon ! Bravo et merci beaucoup Grano, bon travail et bon courage !',
    tags: ['bubble', 'milkshake', 'nutella'],
  },
]

const contactInfo = [
  {
    icon: '📍',
    label: 'Adresse',
    value: 'Route du port 4170, Zarzis',
    sub: 'Gouvernorat de Médenine, Tunisie',
  },
  {
    icon: '📞',
    label: 'Téléphone',
    value: '<a href="tel:+21628406108" class="hover:text-[#C9A84C] transition-colors">28 406 108</a>',
    sub: null,
  },
  {
    icon: '🕐',
    label: 'Horaires',
    value: 'Ouvert jusqu\'à minuit (00h00)',
    sub: 'Sur place · À emporter',
  },
  {
    icon: '⭐',
    label: 'Note Google',
    value: '4.4 / 5 — 73 avis',
    sub: 'Crêperie · Zarzis',
  },
]

const hours = [
  { days: 'Lundi — Vendredi', time: '10h — 00h' },
  { days: 'Samedi', time: '10h — 00h' },
  { days: 'Dimanche', time: '10h — 00h' },
]
</script>

<style>
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease;
}
.slide-down-enter-from,
.slide-down-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
