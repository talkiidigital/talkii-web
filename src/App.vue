<template>
  <div id="app" class="min-h-screen bg-gray-50">
    <!-- Header -->
    <header class="bg-white shadow-sm sticky top-0 z-50">
      <nav class="container-custom py-4">
        <div class="flex items-center justify-between">
          <!-- Logo -->
          <div class="flex items-center space-x-2">
            <img :src="talkiiLogo" alt="Logo Talkii" class="h-7 w-auto" />
            <span class="text-2xl font-bold gradient-text">Talkii</span>
          </div>

          <!-- Desktop Navigation -->
          <div class="hidden md:flex items-center space-x-8">
            <a href="#inicio" class="text-gray-700 hover:text-primary-500 transition-colors">
              {{ t.home }}
            </a>
            <a href="#como-funciona" class="text-gray-700 hover:text-primary-500 transition-colors">
              {{ t.howItWorks }}
            </a>
            <a href="#precos" class="text-gray-700 hover:text-primary-500 transition-colors">
              {{ t.pricing }}
            </a>
            <a href="#sobre" class="text-gray-700 hover:text-primary-500 transition-colors">
              {{ t.about }}
            </a>
            <a href="#contato" class="text-gray-700 hover:text-primary-500 transition-colors">
              {{ t.contact }}
            </a>
          </div>

          <!-- Language Toggle & CTA -->
          <div class="flex items-center space-x-4">
            <button @click="toggleLanguage"
              class="flex items-center space-x-1 px-3 py-2 rounded-lg border border-gray-200 hover:border-primary-300 transition-colors">
              <Globe class="h-4 w-4" />
              <span class="text-sm font-medium">{{ currentLanguage.toUpperCase() }}</span>
            </button>
            <button class="btn-primary hidden md:block">
              {{ t.getStarted }}
            </button>

            <!-- Mobile menu button -->
            <button @click="toggleMobileMenu" class="md:hidden p-2 rounded-lg hover:bg-gray-100">
              <Menu v-if="!mobileMenuOpen" class="h-6 w-6" />
              <X v-else class="h-6 w-6" />
            </button>
          </div>
        </div>

        <!-- Mobile Navigation -->
        <div v-if="mobileMenuOpen" class="md:hidden mt-4 pb-4 border-t border-gray-200">
          <div class="flex flex-col space-y-4 pt-4">
            <a href="#inicio" @click="closeMobileMenu" class="text-gray-700 hover:text-primary-500 transition-colors">
              {{ t.home }}
            </a>
            <a href="#como-funciona" @click="closeMobileMenu"
              class="text-gray-700 hover:text-primary-500 transition-colors">
              {{ t.howItWorks }}
            </a>
            <a href="#precos" @click="closeMobileMenu" class="text-gray-700 hover:text-primary-500 transition-colors">
              {{ t.pricing }}
            </a>
            <a href="#sobre" @click="closeMobileMenu" class="text-gray-700 hover:text-primary-500 transition-colors">
              {{ t.about }}
            </a>
            <a href="#contato" @click="closeMobileMenu" class="text-gray-700 hover:text-primary-500 transition-colors">
              {{ t.contact }}
            </a>
            <button class="btn-primary w-full">
              {{ t.getStarted }}
            </button>
          </div>
        </div>
      </nav>
    </header>

    <!-- Hero Section -->
    <section id="inicio" class="bg-gradient-to-br from-primary-50 to-secondary-50 py-20">
      <div class="container-custom">
        <div class="grid lg:grid-cols-2 gap-12 items-center">
          <div class="animate-fade-in-up">
            <div
              class="inline-flex items-center px-4 py-2 bg-primary-100 rounded-full text-primary-700 text-sm font-medium mb-6">
              {{ t.revolutionize }}
            </div>

            <h1 class="text-4xl md:text-6xl font-bold text-gray-900 mb-6 leading-tight">
              {{ t.heroTitle1 }}
              <span class="gradient-text">{{ t.heroTitle2 }}</span>{{ t.heroTitle3 }}
              <span class="gradient-text">{{ t.heroTitle4 }}</span>
              <span class="gradient-text">{{ t.heroTitle5 }}</span>
            </h1>

            <p class="text-xl text-gray-600 mb-8 leading-relaxed">
              {{ t.heroDescription }}
            </p>

            <div class="flex flex-col sm:flex-row gap-4">
              <!-- <button class="btn-primary">
                {{ t.tryFree }}
              </button> -->
              <button class="btn-primary" @click="scrollToSection('como-funciona')">
                {{ t.seeHowWorks }}
              </button>
            </div>
          </div>

          <div class="relative">
            <img :src="heroImage" :alt="t.heroTitle1" class="w-full h-auto rounded-2xl shadow-2xl" />
          </div>
        </div>
      </div>
    </section>

    <!-- How It Works Section -->
    <section id="como-funciona" class="py-20 bg-white">
      <div class="container-custom">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
            {{ t.howItWorksTitle }}
          </h2>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">
            {{ t.howItWorksSubtitle }}
          </p>
        </div>

        <div class="grid md:grid-cols-3 gap-8 mb-16">
          <div class="text-center card-hover p-6 rounded-xl bg-gradient-to-br from-primary-50 to-primary-100">
            <div class="w-16 h-16 bg-primary-500 rounded-full flex items-center justify-center mx-auto mb-6">
              <Smartphone class="h-8 w-8 text-white" />
            </div>
            <h3 class="text-xl font-bold text-gray-900 mb-4">{{ t.step1Title }}</h3>
            <p class="text-gray-600">{{ t.step1Description }}</p>
          </div>

          <div class="text-center card-hover p-6 rounded-xl bg-gradient-to-br from-secondary-50 to-secondary-100">
            <div class="w-16 h-16 bg-secondary-500 rounded-full flex items-center justify-center mx-auto mb-6">
              <MessageCircle class="h-8 w-8 text-white" />
            </div>
            <h3 class="text-xl font-bold text-gray-900 mb-4">{{ t.step2Title }}</h3>
            <p class="text-gray-600">{{ t.step2Description }}</p>
          </div>

          <div class="text-center card-hover p-6 rounded-xl bg-gradient-to-br from-primary-50 to-secondary-50">
            <div
              class="w-16 h-16 bg-gradient-to-r from-primary-500 to-secondary-500 rounded-full flex items-center justify-center mx-auto mb-6">
              <Heart class="h-8 w-8 text-white" />
            </div>
            <h3 class="text-xl font-bold text-gray-900 mb-4">{{ t.step3Title }}</h3>
            <p class="text-gray-600">{{ t.step3Description }}</p>
          </div>
        </div>

        <div class="text-center">
          <img :src="automationImage" :alt="t.howItWorksTitle" class="w-full max-w-4xl mx-auto rounded-2xl shadow-xl" />
        </div>
      </div>
    </section>

    <!-- Benefits Section -->
    <section class="py-20 bg-gray-50">
      <div class="container-custom">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
            {{ t.benefitsTitle }}
          </h2>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">
            {{ t.benefitsSubtitle }}
          </p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div class="text-center card-hover p-6 bg-white rounded-xl shadow-lg">
            <Clock class="h-12 w-12 text-primary-500 mx-auto mb-4" />
            <h3 class="text-lg font-bold text-gray-900 mb-2">{{ t.saveTime }}</h3>
            <p class="text-gray-600 text-sm">{{ t.saveTimeDesc }}</p>
          </div>

          <div class="text-center card-hover p-6 bg-white rounded-xl shadow-lg">
            <Target class="h-12 w-12 text-secondary-500 mx-auto mb-4" />
            <h3 class="text-lg font-bold text-gray-900 mb-2">{{ t.effectiveMatches }}</h3>
            <p class="text-gray-600 text-sm">{{ t.effectiveMatchesDesc }}</p>
          </div>

          <div class="text-center card-hover p-6 bg-white rounded-xl shadow-lg">
            <MessageCircle class="h-12 w-12 text-primary-500 mx-auto mb-4" />
            <h3 class="text-lg font-bold text-gray-900 mb-2">{{ t.naturalConversations }}</h3>
            <p class="text-gray-600 text-sm">{{ t.naturalConversationsDesc }}</p>
          </div>

          <div class="text-center card-hover p-6 bg-white rounded-xl shadow-lg">
            <TrendingUp class="h-12 w-12 text-secondary-500 mx-auto mb-4" />
            <h3 class="text-lg font-bold text-gray-900 mb-2">{{ t.provenResults }}</h3>
            <p class="text-gray-600 text-sm">{{ t.provenResultsDesc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section class="py-20 bg-white">
      <div class="container-custom">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
            {{ t.testimonialsTitle }}
          </h2>
          <p class="text-xl text-gray-600">{{ t.testimonialsSubtitle }}</p>
        </div>

        <div class="grid md:grid-cols-3 gap-8">
          <div class="card-hover p-8 bg-gradient-to-br from-primary-50 to-primary-100 rounded-xl">
            <div class="flex items-center mb-4">
              <div
                class="w-12 h-12 bg-primary-500 rounded-full flex items-center justify-center text-white font-bold text-lg mr-4">
                M
              </div>
              <div>
                <h4 class="font-bold text-gray-900">{{ t.testimonial1Name }}</h4>
                <div class="flex text-yellow-400">
                  <Star v-for="i in 5" :key="i" class="h-4 w-4 fill-current" />
                </div>
              </div>
            </div>
            <p class="text-gray-700 italic">"{{ t.testimonial1Text }}"</p>
          </div>

          <div class="card-hover p-8 bg-gradient-to-br from-secondary-50 to-secondary-100 rounded-xl">
            <div class="flex items-center mb-4">
              <div
                class="w-12 h-12 bg-secondary-500 rounded-full flex items-center justify-center text-white font-bold text-lg mr-4">
                R
              </div>
              <div>
                <h4 class="font-bold text-gray-900">{{ t.testimonial2Name }}</h4>
                <div class="flex text-yellow-400">
                  <Star v-for="i in 5" :key="i" class="h-4 w-4 fill-current" />
                </div>
              </div>
            </div>
            <p class="text-gray-700 italic">"{{ t.testimonial2Text }}"</p>
          </div>

          <div class="card-hover p-8 bg-gradient-to-br from-primary-50 to-secondary-50 rounded-xl">
            <div class="flex items-center mb-4">
              <div
                class="w-12 h-12 bg-gradient-to-r from-primary-500 to-secondary-500 rounded-full flex items-center justify-center text-white font-bold text-lg mr-4">
                C
              </div>
              <div>
                <h4 class="font-bold text-gray-900">{{ t.testimonial3Name }}</h4>
                <div class="flex text-yellow-400">
                  <Star v-for="i in 5" :key="i" class="h-4 w-4 fill-current" />
                </div>
              </div>
            </div>
            <p class="text-gray-700 italic">"{{ t.testimonial3Text }}"</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Pricing Section (Reimaginada - Plano Único) -->
    <section id="precos" class="relative py-24 bg-gray-50 overflow-hidden">
      <span
        class="pointer-events-none absolute -top-20 -right-16 w-72 h-72 bg-secondary-300/40 blur-3xl rounded-full"></span>
      <span
        class="pointer-events-none absolute -bottom-24 -left-20 w-96 h-96 bg-primary-300/30 blur-3xl rounded-full"></span>
      <div class="container-custom relative">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
            {{ t.pricingTitle }}
          </h2>
          <p class="text-xl text-gray-600">{{ t.pricingSubtitle }}</p>
        </div>

        <div class="max-w-5xl mx-auto">
          <div class="p-[2px] rounded-3xl bg-gradient-to-r from-primary-500 to-secondary-500 shadow-2xl">
            <div class="rounded-3xl bg-white/80 backdrop-blur p-8 md:p-12">
              <div class="md:grid md:grid-cols-2 md:gap-10 items-center">
                <div>
                  <div class="flex items-center gap-3 mb-4">
                    <span
                      class="inline-flex items-center px-3 py-1 rounded-full text-xs font-medium bg-primary-100 text-primary-700">Plano
                      único</span>
                    <span class="text-xs uppercase tracking-wider text-gray-500">Sem fidelidade</span>
                  </div>
                  <h3 class="text-3xl font-extrabold text-gray-900 mb-2">{{ t.premiumPlan }}</h3>
                  <div class="flex items-end gap-2 mb-6">
                    <span class="text-6xl font-extrabold gradient-text">{{ t.premiumPrice }}</span>
                    <span class="text-gray-600 mb-3">/{{ t.month }}</span>
                  </div>
                  <button class="w-full md:w-auto btn-primary px-8">{{ t.getStarted }}</button>
                  <p class="text-sm text-gray-600 mt-3">7 dias grátis. Cancele quando quiser.</p>
                </div>

                <div class="mt-8 md:mt-0">
                  <ul class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <li class="flex items-center">
                      <Check class="h-5 w-5 text-green-500 mr-3" />
                      <span class="text-gray-700">{{ t.premiumFeature1 }}</span>
                    </li>
                    <li class="flex items-center">
                      <Check class="h-5 w-5 text-green-500 mr-3" />
                      <span class="text-gray-700">{{ t.premiumFeature2 }}</span>
                    </li>
                    <li class="flex items-center">
                      <Check class="h-5 w-5 text-green-500 mr-3" />
                      <span class="text-gray-700">{{ t.premiumFeature3 }}</span>
                    </li>
                    <li class="flex items-center">
                      <Check class="h-5 w-5 text-green-500 mr-3" />
                      <span class="text-gray-700">{{ t.premiumFeature4 }}</span>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- FAQ Section -->
    <section class="py-20 bg-white">
      <div class="container-custom">
        <div class="text-center mb-16">
          <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">
            {{ t.faqTitle }}
          </h2>
          <p class="text-xl text-gray-600">{{ t.faqSubtitle }}</p>
        </div>

        <div class="max-w-4xl mx-auto space-y-6">
          <div v-for="(faq, index) in faqs" :key="index"
            class="bg-gray-50 rounded-xl p-6 cursor-pointer hover:bg-gray-100 transition-colors"
            @click="toggleFaq(index)">
            <div class="flex justify-between items-center">
              <h3 class="text-lg font-semibold text-gray-900">{{ faq.question }}</h3>
              <div class="transform transition-transform" :class="{ 'rotate-180': faq.open }">
                <svg class="w-5 h-5 text-gray-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
                </svg>
              </div>
            </div>
            <div v-if="faq.open" class="mt-4 text-gray-600">
              {{ faq.answer }}
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="py-20 bg-gradient-to-r from-primary-500 to-secondary-500">
      <div class="container-custom text-center">
        <h2 class="text-3xl md:text-4xl font-bold text-white mb-4">
          {{ t.ctaTitle }}
        </h2>
        <p class="text-xl text-primary-100 mb-8 max-w-3xl mx-auto">
          {{ t.ctaSubtitle }}
        </p>
        <button
          class="bg-white text-primary-600 font-semibold py-4 px-8 rounded-lg hover:bg-gray-100 transition-colors transform hover:scale-105 shadow-lg text-lg">
          {{ t.ctaButton }}
        </button>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white py-12">
      <div class="container-custom">
        <div class="text-center">
          <div class="flex items-center justify-center space-x-2 mb-4">
            <img :src="talkiiLogo" alt="Logo Talkii" class="h-7 w-auto" />
            <span class="text-2xl font-bold">Talkii</span>
          </div>
          <p class="text-gray-400 mb-6">{{ t.footerText }}</p>
          <div class="flex justify-center space-x-6 text-sm text-gray-400">
            <a href="#" class="hover:text-white transition-colors">{{ t.privacy }}</a>
            <a href="#" class="hover:text-white transition-colors">{{ t.terms }}</a>
            <a href="#" class="hover:text-white transition-colors">{{ t.contact }}</a>
          </div>
          <div class="mt-8 pt-8 border-t border-gray-800 text-center text-gray-400 text-sm">
            © 2025 Talkii. {{ t.allRightsReserved }}
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, watch } from 'vue'
import {
  Heart,
  MessageCircle,
  Smartphone,
  Clock,
  Target,
  TrendingUp,
  Star,
  Check,
  Menu,
  X,
  Globe
} from 'lucide-vue-next'

import heroImage from './assets/hero-image.png'
import automationImage from './assets/automation-illustration.png'
import talkiiLogo from './assets/talkii_logo.png'

type Language = 'pt' | 'en'
const currentLanguage = ref<Language>('pt')
const mobileMenuOpen = ref(false)

const translations = {
  pt: {
    // Header
    home: "Início",
    howItWorks: "Como Funciona",
    pricing: "Preços",
    about: "Sobre",
    contact: "Contato",
    getStarted: "Começar Agora",

    // Hero Section
    revolutionize: "🚀 Revolucione seus encontros",
    heroTitle1: "Não fazemos ",
    heroTitle2: "gol",
    heroTitle3: ", mas damos a ",
    heroTitle4: "assistência ",
    heroTitle5: "perfeita",
    heroDescription: "Comece conversas sem esforço. A Talkii te dá as melhores respostas até o momento certo de você assumir.",
    tryFree: "Experimente Grátis",
    seeHowWorks: "Ver Como Funciona",

    // How It Works
    howItWorksTitle: "Como a Talkii funciona para você",
    howItWorksSubtitle: "Três passos simples para transformar suas conversas em conexões reais",
    step1Title: "1. Comece no WhatsApp",
    step1Description: "Fale direto com a Talkii, sua parceira inteligente no amor, em um chat prático e sempre disponível.",
    step2Title: "2. Tenha respostas certeiras",
    step2Description: "A IA sugere mensagens criativas, quebra-gelos e estratégias para deixar a conversa leve, divertida e envolvente.",
    step3Title: "3. Assuma com confiança",
    step3Description: "Deixe a Talkii conduzir o início e, quando chegar a hora, entre em cena com naturalidade e autenticidade.",

    // Benefits
    benefitsTitle: "Por que escolher a Talkii?",
    benefitsSubtitle: "Transforme sua experiência em aplicativos de relacionamento",
    saveTime: "Economize Tempo",
    saveTimeDesc: "Sem horas perdidas em conversas que não levam a lugar nenhum",
    effectiveMatches: "Matches Efetivos",
    effectiveMatchesDesc: "Foco apenas em pessoas realmente interessadas em se encontrar",
    naturalConversations: "Conversas Naturais",
    naturalConversationsDesc: "IA treinada para conversas autênticas e envolventes",
    provenResults: "Resultados Comprovados",
    provenResultsDesc: "Aumente suas chances de conseguir encontros reais",

    // Testimonials
    testimonialsTitle: "O que nossos usuários dizem",
    testimonialsSubtitle: "Histórias reais de sucesso",
    testimonial1Name: "Marina, 28",
    testimonial1Text: "Em 2 semanas consegui 5 encontros reais! A Talkii realmente funciona. Não perco mais tempo com conversas que não vão dar em nada.",
    testimonial2Name: "Rafael, 32",
    testimonial2Text: "Trabalho muito e não tinha tempo para ficar conversando. A Talkii me ajudou a encontrar alguém especial sem o estresse.",
    testimonial3Name: "Carla, 26",
    testimonial3Text: "Sou tímida para iniciar conversas. A Talkii quebrou o gelo por mim e agora estou namorando há 6 meses!",

    // Pricing
    pricingTitle: "Planos que cabem no seu bolso",
    pricingSubtitle: "Escolha o plano ideal para você",
    basicPlan: "Básico",
    basicPrice: "R$ 29",
    proPlan: "Pro",
    proPrice: "R$ 59",
    premiumPlan: "Premium",
    premiumPrice: "R$ 99",
    month: "mês",
    mostPopular: "Mais Popular",
    basicFeature1: "1 aplicativo conectado",
    basicFeature2: "50 conversas por mês",
    basicFeature3: "Suporte por email",
    proFeature1: "3 aplicativos conectados",
    proFeature2: "Conversas ilimitadas",
    proFeature3: "Relatórios detalhados",
    proFeature4: "Suporte prioritário",
    premiumFeature1: "Todos os aplicativos",
    premiumFeature2: "Coach pessoal",
    premiumFeature3: "Análise avançada",
    premiumFeature4: "Suporte 24/7",

    // FAQ
    faqTitle: "Perguntas Frequentes",
    faqSubtitle: "Tire suas dúvidas sobre a Talkii",
    faq2Question: "A IA realmente conversa de forma natural?",
    faq2Answer: "Sim! Nossa IA é treinada com milhões de conversas reais e se adapta ao seu estilo de comunicação.",
    faq3Question: "Posso cancelar a qualquer momento?",
    faq3Answer: "Claro! Não há fidelidade. Você pode cancelar sua assinatura a qualquer momento pelo painel de controle.",

    // CTA
    ctaTitle: "Pronto para encontrar alguém especial?",
    ctaSubtitle: "Junte-se a milhares de pessoas que já transformaram sua vida amorosa com a Talkii",
    ctaButton: "Começar Minha Jornada",

    // Footer
    footerText: "Converse melhor, conquiste mais",
    privacy: "Privacidade",
    terms: "Termos",
    allRightsReserved: "Todos os direitos reservados."
  },
  en: {
    // Header
    home: "Home",
    howItWorks: "How It Works",
    pricing: "Pricing",
    about: "About",
    contact: "Contact",
    getStarted: "Get Started",

    // Hero Section
    revolutionize: "🚀 Revolutionize your dating",
    heroTitle1: "We don't score ",
    heroTitle2: "goals",
    heroTitle3: ", but we provide the perfect ",
    heroTitle4: "assist",
    heroTitle5: "",
    heroDescription: "Start conversations effortlessly. Talkii gives you the best replies until the right moment to take over.",
    tryFree: "Try Free",
    seeHowWorks: "See How It Works",

    // How It Works
    howItWorksTitle: "How Talkii works for you",
    howItWorksSubtitle: "Three simple steps to turn your chats into real connections",
    step1Title: "1. Start on WhatsApp",
    step1Description: "Chat directly with Talkii, your smart partner in love, always practical and available.",
    step2Title: "2. Get spot-on replies",
    step2Description: "AI suggests creative messages, icebreakers and strategies to keep the conversation light, fun and engaging.",
    step3Title: "3. Take over with confidence",
    step3Description: "Let Talkii guide the start and, when the time is right, step in naturally and authentically.",

    // Benefits
    benefitsTitle: "Why choose Talkii?",
    benefitsSubtitle: "Transform your dating experience",
    saveTime: "Save Time",
    saveTimeDesc: "No more hours wasted on conversations that lead nowhere",
    effectiveMatches: "Effective Matches",
    effectiveMatchesDesc: "Focus only on people really interested in meeting",
    naturalConversations: "Natural Conversations",
    naturalConversationsDesc: "AI trained for authentic and engaging conversations",
    provenResults: "Proven Results",
    provenResultsDesc: "Increase your chances of getting real dates",

    // Testimonials
    testimonialsTitle: "What our users say",
    testimonialsSubtitle: "Real success stories",
    testimonial1Name: "Marina, 28",
    testimonial1Text: "In 2 weeks I got 5 real dates! Talkii really works. I don't waste time anymore with conversations that go nowhere.",
    testimonial2Name: "Rafael, 32",
    testimonial2Text: "I work a lot and didn't have time to keep chatting. Talkii helped me find someone special without the stress.",
    testimonial3Name: "Carla, 26",
    testimonial3Text: "I'm shy about starting conversations. Talkii broke the ice for me and now I've been dating for 6 months!",

    // Pricing
    pricingTitle: "Plans that fit your budget",
    pricingSubtitle: "Choose the ideal plan for you",
    basicPlan: "Basic",
    basicPrice: "$19",
    proPlan: "Pro",
    proPrice: "$39",
    premiumPlan: "Premium",
    premiumPrice: "$69",
    month: "month",
    mostPopular: "Most Popular",
    basicFeature1: "1 connected app",
    basicFeature2: "50 conversations per month",
    basicFeature3: "Email support",
    proFeature1: "3 connected apps",
    proFeature2: "Unlimited conversations",
    proFeature3: "Detailed reports",
    proFeature4: "Priority support",

    // FAQ
    faqTitle: "Frequently Asked Questions",
    faqSubtitle: "Get your questions about Talkii answered",
    faq2Question: "Does the AI really chat naturally?",
    faq2Answer: "Yes! Our AI is trained with millions of real conversations and adapts to your communication style.",
    faq3Question: "Can I cancel at any time?",
    faq3Answer: "Of course! There's no commitment. You can cancel your subscription at any time from the control panel.",

    // CTA
    ctaTitle: "Ready to find someone special?",
    ctaSubtitle: "Join thousands of people who have already transformed their love life with Talkii",
    ctaButton: "Start My Journey",

    // Footer
    footerText: "Chat better, connect more",
    privacy: "Privacy",
    terms: "Terms",
    allRightsReserved: "All rights reserved."
  }
} satisfies Record<Language, Record<string, string>>

type Translation = Record<string, string>
const t = computed<Translation>(() => translations[currentLanguage.value])

type FaqItem = { question: string; answer: string; open: boolean }
const faqs = ref<FaqItem[]>([])

const buildFaqs = (tr: Translation, prev: FaqItem[] = []): FaqItem[] => ([
  { question: tr.faq2Question, answer: tr.faq2Answer, open: prev[0]?.open ?? false },
  { question: tr.faq3Question, answer: tr.faq3Answer, open: prev[1]?.open ?? false },
])

// inicializa e mantém as perguntas sincronizadas com o idioma
faqs.value = buildFaqs(t.value)
watch(t, (tr) => { faqs.value = buildFaqs(tr, faqs.value) })

const toggleLanguage = () => {
  currentLanguage.value = currentLanguage.value === 'pt' ? 'en' : 'pt'
}

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
}

const toggleFaq = (index: number) => {
  faqs.value[index].open = !faqs.value[index].open
}

const scrollToSection = (id: string) => {
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}
</script>
