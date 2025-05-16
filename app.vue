<template>
  <div class="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-100 text-gray-800">
    <!-- Header -->
   <header class="py-6 px-4 sm:px-6 lg:px-8 bg-white shadow-sm sticky top-0 z-10">
      <div class="max-w-7xl mx-auto flex justify-between items-center">
        <div class="flex items-center space-x-2">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-indigo-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>
          <h1 class="text-2xl font-bold text-gray-900">Копить или жить?</h1>
        </div>
        <nav class="hidden md:flex space-x-8">
          <a href="#calculator" class="text-gray-600 hover:text-indigo-600 transition">Калькулятор</a>
          <a href="#strategies" class="text-gray-600 hover:text-indigo-600 transition">Стратегии</a>
          <a href="#analysis" class="text-gray-600 hover:text-indigo-600 transition">Анализ</a>
          <a href="#tips" class="text-gray-600 hover:text-indigo-600 transition">Советы</a>
        </nav>
        <button class="md:hidden text-gray-600" @click="mobileMenuOpen = !mobileMenuOpen">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
        </button>
      </div>
      
      <!-- Mobile menu -->
      <div v-if="mobileMenuOpen" class="md:hidden mt-4 space-y-2">
        <a href="#calculator" class="block px-3 py-2 rounded-lg bg-indigo-50 text-indigo-700" @click="mobileMenuOpen = false">Калькулятор</a>
        <a href="#strategies" class="block px-3 py-2 rounded-lg hover:bg-indigo-50" @click="mobileMenuOpen = false">Стратегии</a>
        <a href="#analysis" class="block px-3 py-2 rounded-lg hover:bg-indigo-50" @click="mobileMenuOpen = false">Анализ</a>
        <a href="#tips" class="block px-3 py-2 rounded-lg hover:bg-indigo-50" @click="mobileMenuOpen = false">Советы</a>
      </div>
    </header>

    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
      <!-- Hero section -->
      <section class="text-center py-12 md:py-20 bg-gradient-to-br from-blue-50 to-indigo-50 rounded-xl mx-4 sm:mx-6 lg:mx-8 mb-12">
  <div class="max-w-4xl mx-auto px-4 sm:px-6">
    <h2 class="text-4xl md:text-5xl font-bold text-gray-800 mb-6 leading-tight">
      Найдите идеальный баланс между накоплениями и качеством жизни
    </h2>
    <p class="text-xl text-gray-600 mb-8 max-w-3xl mx-auto leading-relaxed">
      Узнайте, как грамотно распределить ваш доход между сбережениями и текущими расходами, чтобы наслаждаться жизнью сегодня и быть финансово защищенным завтра.
    </p>
    <div class="flex flex-col sm:flex-row justify-center gap-4">
      <button 
        @click="scrollToCalculator"
        class="px-6 py-3 bg-indigo-600 text-white font-medium rounded-lg hover:bg-indigo-700 transition shadow-md hover:shadow-lg transform hover:-translate-y-1 cursor-pointer"
      >
        Попробовать калькулятор
      </button>
      <button 
        @click="showVideoModal = true"
        class="px-6 py-3 border-2 border-indigo-600 text-indigo-600 font-medium rounded-lg hover:bg-indigo-50 transition flex items-center justify-center gap-2 hover:shadow-md cursor-pointer"
      >
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
          <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9.555 7.168A1 1 0 008 8v4a1 1 0 001.555.832l3-2a1 1 0 000-1.664l-3-2z" clip-rule="evenodd" />
        </svg>
        Как это работает
      </button>
    </div>
  </div>
</section>

      <!-- Calculator section -->
      <section id="calculator" class="bg-white rounded-xl shadow-md p-6 md:p-8 mb-12">
        <h2 class="text-2xl font-bold text-gray-900 mb-6">Финансовый калькулятор</h2>
        
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
          <!-- Inputs -->
          <div class="lg:col-span-1 space-y-6">
            <!-- Income -->
            <div>
              <label for="income" class="block text-sm font-medium text-gray-700 mb-1">Ваш ежемесячный доход (₽)</label>
              <input 
                type="number" 
                id="income" 
                v-model.number="income"
                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-indigo-500 focus:border-indigo-500"
                min="0"
                step="1000"
              >
            </div>
            
            <!-- Expenses -->
            <div>
              <label for="expenses" class="block text-sm font-medium text-gray-700 mb-1">Обязательные расходы (₽/мес)</label>
              <input 
                type="number" 
                id="expenses" 
                v-model.number="expenses"
                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-indigo-500 focus:border-indigo-500"
                min="0"
                step="1000"
              >
            </div>
            
            <!-- Savings rate -->
            <div>
              <label for="savingsRate" class="block text-sm font-medium text-gray-700 mb-1">Процент дохода на сбережения</label>
              <div class="flex items-center space-x-4">
                <input 
                  type="range" 
                  id="savingsRate" 
                  v-model.number="savingsRate"
                  class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer"
                  min="0"
                  max="100"
                  step="1"
                >
                <span class="text-gray-700 font-medium w-12">{{ savingsRate }}%</span>
              </div>
            </div>
            
            <!-- Investment return -->
            <div>
              <label for="investmentReturn" class="block text-sm font-medium text-gray-700 mb-1">Доходность инвестиций (% годовых)</label>
              <input 
                type="number" 
                id="investmentReturn" 
                v-model.number="investmentReturn"
                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-indigo-500 focus:border-indigo-500"
                min="0"
                max="30"
                step="0.1"
              >
            </div>
            
            <!-- Years -->
            <div>
              <label for="years" class="block text-sm font-medium text-gray-700 mb-1">Период планирования (лет)</label>
              <input 
                type="number" 
                id="years" 
                v-model.number="years"
                class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-indigo-500 focus:border-indigo-500"
                min="1"
                max="60"
                step="1"
              >
            </div>
            
            <!-- Risk tolerance -->
            <div>
              <label class="block text-sm font-medium text-gray-700 mb-2">Ваша толерантность к риску</label>
              <div class="grid grid-cols-3 gap-2">
                <button 
                  v-for="(risk, index) in riskLevels" 
                  :key="index"
                  @click="riskTolerance = risk.value"
                  :class="{
                    'bg-indigo-100 border-indigo-500 text-indigo-700 cursor-pointer': riskTolerance === risk.value,
                    'bg-white border-gray-300 text-gray-700 hover:bg-gray-50 cusor-pointer': riskTolerance !== risk.value
                  }"
                  class="py-2 px-3 border rounded-lg text-sm font-medium transition cursor-pointer"
                >
                  {{ risk.label }}
                </button>
              </div>
            </div>
          </div>
          
          <!-- Results -->
          <div class="lg:col-span-2">
            <div class="bg-indigo-50 rounded-lg p-6 mb-6">
              <h3 class="text-lg font-semibold text-gray-900 mb-4">Ваш финансовый баланс</h3>
              
              <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
                <div class="bg-white rounded-lg p-4 shadow-sm">
                  <p class="text-sm text-gray-500 mb-1">Доступно на жизнь</p>
                  <p class="text-2xl font-bold text-indigo-600">{{ formatCurrency(disposableIncome) }}</p>
                  <p class="text-xs text-gray-500 mt-1">{{ disposableIncomePercentage }}% от дохода</p>
                </div>
                <div class="bg-white rounded-lg p-4 shadow-sm">
                  <p class="text-sm text-gray-500 mb-1">Накопления</p>
                  <p class="text-2xl font-bold text-indigo-600">{{ formatCurrency(savingsAmount) }}</p>
                  <p class="text-xs text-gray-500 mt-1">{{ savingsRate }}% от дохода</p>
                </div>
                <div class="bg-white rounded-lg p-4 shadow-sm">
                  <p class="text-sm text-gray-500 mb-1">Будущие накопления</p>
                  <p class="text-2xl font-bold text-indigo-600">{{ formatCurrency(futureSavings) }}</p>
                  <p class="text-xs text-gray-500 mt-1">за {{ years }} лет</p>
                </div>
              </div>
              
              <div class="h-4 bg-gray-200 rounded-full overflow-hidden mb-2">
                <div 
                  class="h-full bg-indigo-600 rounded-full transition-all duration-500"
                  :style="{ width: `${savingsRate}%` }"
                ></div>
              </div>
              <div class="flex justify-between text-sm text-gray-600">
                <span>Траты ({{ disposableIncomePercentage }}%)</span>
                <span>Накопления ({{ savingsRate }}%)</span>
              </div>
            </div>
            
            <!-- Charts -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div class="bg-white p-4 rounded-lg shadow-sm border border-gray-100">
                <h4 class="font-medium text-gray-900 mb-3">Рост накоплений</h4>
                <div class="h-64">
                  <canvas ref="savingsChart"></canvas>
                </div>
              </div>
              <div class="bg-white p-4 rounded-lg shadow-sm border border-gray-100">
                <h4 class="font-medium text-gray-900 mb-3">Распределение</h4>
                <div class="h-64">
                  <canvas ref="pieChart"></canvas>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Strategies section -->
      <section id="strategies" class="mb-12">
        <h2 class="text-2xl font-bold text-gray-900 mb-6">Стратегии баланса</h2>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div 
            v-for="(strategy, index) in strategies" 
            :key="index"
            class="bg-white rounded-xl shadow-sm overflow-hidden border border-gray-100 hover:shadow-md transition"
            :class="{ 'ring-2 ring-indigo-500': selectedStrategy === index }"
            @click="selectedStrategy = index"
          >
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="p-3 rounded-lg mr-4" :class="strategyColors[index].bg">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" :class="strategyColors[index].text" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" :d="strategyIcons[index]" />
                  </svg>
                </div>
                <h3 class="text-lg font-semibold text-gray-900">{{ strategy.title }}</h3>
              </div>
              <p class="text-gray-600 mb-4">{{ strategy.description }}</p>
              <ul class="space-y-2 text-sm text-gray-600">
                <li v-for="(point, pointIndex) in strategy.points" :key="pointIndex" class="flex items-start">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mt-0.5 mr-2 flex-shrink-0 text-indigo-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                  </svg>
                  <span>{{ point }}</span>
                </li>
              </ul>
            </div>
            <div class="px-6 py-3 bg-gray-50 border-t border-gray-100 text-sm text-gray-500">
              Рекомендуется для: {{ strategy.recommendedFor }}
            </div>
          </div>
        </div>
        
        <div v-if="selectedStrategy !== null" class="mt-8 bg-indigo-50 rounded-xl p-6">
          <h3 class="text-lg font-semibold text-gray-900 mb-4">Как реализовать стратегию "{{ strategies[selectedStrategy].title }}"</h3>
          <div class="prose prose-indigo max-w-none">
            <p>{{ strategies[selectedStrategy].implementation }}</p>
            <div class="mt-4">
              <h4 class="font-medium text-gray-900 mb-2">Пример расчета для ваших данных:</h4>
              <div class="bg-white rounded-lg p-4 shadow-sm">
                <p class="text-sm text-gray-600 mb-2">При текущем доходе {{ formatCurrency(income) }} и выбранной стратегии:</p>
                <ul class="space-y-2">
                  <li class="flex justify-between">
                    <span>Накопления:</span>
                    <span class="font-medium">{{ formatCurrency(strategySavings(selectedStrategy)) }}</span>
                  </li>
                  <li class="flex justify-between">
                    <span>Доступно на жизнь:</span>
                    <span class="font-medium">{{ formatCurrency(strategySpending(selectedStrategy)) }}</span>
                  </li>
                  <li class="flex justify-between">
                    <span>Будущая сумма через {{ years }} лет:</span>
                    <span class="font-medium">{{ formatCurrency(strategyFutureValue(selectedStrategy)) }}</span>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Analysis section -->
      <section id="analysis" class="bg-white rounded-xl shadow-md p-6 md:p-8 mb-12">
        <h2 class="text-2xl font-bold text-gray-900 mb-6">Анализ вашего выбора</h2>
        
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
          <div>
            <h3 class="text-lg font-semibold text-gray-900 mb-4">Сравнение стратегий</h3>
            <div class="h-80">
              <canvas ref="comparisonChart"></canvas>
            </div>
          </div>
          
          <div>
            <h3 class="text-lg font-semibold text-gray-900 mb-4">Рекомендации</h3>
            <div class="space-y-4">
              <div 
                v-for="(recommendation, index) in filteredRecommendations"
                :key="index"
                class="flex items-start p-4 rounded-lg"
                :class="recommendation.type === 'warning' ? 'bg-amber-50 border border-amber-100' : 'bg-green-50 border border-green-100'"
              >
                <div class="mr-3 mt-0.5 flex-shrink-0">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" :class="recommendation.type === 'warning' ? 'text-amber-500' : 'text-green-500'" viewBox="0 0 20 20" fill="currentColor">
                    <path fill-rule="evenodd" d="M18 10a8 8 0 11-16 0 8 8 0 0116 0zm-7-4a1 1 0 11-2 0 1 1 0 012 0zM9 9a1 1 0 000 2v3a1 1 0 001 1h1a1 1 0 100-2h-1V9z" clip-rule="evenodd" />
                  </svg>
                </div>
                <div>
                  <h4 class="font-medium" :class="recommendation.type === 'warning' ? 'text-amber-800' : 'text-green-800'">
                    {{ recommendation.title }}
                  </h4>
                  <p class="text-sm mt-1" :class="recommendation.type === 'warning' ? 'text-amber-700' : 'text-green-700'">
                    {{ recommendation.message }}
                  </p>
                </div>
              </div>
            </div>
            
            <div class="mt-6 bg-gray-50 rounded-lg p-4 border border-gray-200">
              <h4 class="font-medium text-gray-900 mb-2">Ваш финансовый профиль</h4>
              <div class="space-y-3">
                <div>
                  <div class="flex justify-between text-sm text-gray-600 mb-1">
                    <span>Сбережения</span>
                    <span>{{ savingsProfile }}</span>
                  </div>
                  <div class="w-full bg-gray-200 rounded-full h-2">
                    <div 
                      class="bg-indigo-600 h-2 rounded-full" 
                      :style="{ width: `${Math.min(savingsRate, 100)}%` }"
                    ></div>
                  </div>
                </div>
                <div>
                  <div class="flex justify-between text-sm text-gray-600 mb-1">
                    <span>Риск</span>
                    <span>{{ riskProfile }}</span>
                  </div>
                  <div class="w-full bg-gray-200 rounded-full h-2">
                    <div 
                      class="bg-indigo-600 h-2 rounded-full" 
                      :style="{ width: `${riskTolerance * 25}%` }"
                    ></div>
                  </div>
                </div>
                <div>
                  <div class="flex justify-between text-sm text-gray-600 mb-1">
                    <span>Баланс</span>
                    <span>{{ balanceProfile }}</span>
                  </div>
                  <div class="w-full bg-gray-200 rounded-full h-2">
                    <div 
                      class="bg-indigo-600 h-2 rounded-full" 
                      :style="{ width: `${balanceScore}%` }"
                    ></div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Tips section -->
      <section id="tips" class="mb-12">
        <h2 class="text-2xl font-bold text-gray-900 mb-6">Советы по балансу</h2>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
          <div 
            v-for="(tip, index) in tips"
            :key="index"
            class="bg-white rounded-xl shadow-sm overflow-hidden border border-gray-100 hover:shadow-md transition"
          >
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="p-3 rounded-lg mr-4" :class="tipColors[index].bg">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" :class="tipColors[index].text" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" :d="tipIcons[index]" />
                  </svg>
                </div>
                <h3 class="text-lg font-semibold text-gray-900">{{ tip.title }}</h3>
              </div>
              <p class="text-gray-600">{{ tip.description }}</p>
            </div>
            <div class="px-6 py-3 bg-gray-50 border-t border-gray-100">
              <button 
                @click="showTipDetails(index)"
                class="text-sm font-medium text-indigo-600 hover:text-indigo-500 flex items-center"
              >
                Подробнее
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 ml-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </section>

      <!-- CTA section -->
      <section class="bg-indigo-700 rounded-xl shadow-xl overflow-hidden mb-12">
        <div class="grid grid-cols-1 lg:grid-cols-2">
          <div class="p-8 md:p-12">
            <h2 class="text-2xl font-bold text-white mb-4">Готовы оптимизировать свои финансы?</h2>
            <p class="text-indigo-100 mb-6">
              Подпишитесь на нашу рассылку и получайте персонализированные советы по управлению финансами, эксклюзивные инструменты и специальные предложения.
            </p>
            <form @submit.prevent="subscribe" class="space-y-4">
              <div>
                <label for="email" class="sr-only">Email</label>
                <input 
                  type="email" 
                  id="email" 
                  v-model="email"
                  placeholder="Ваш email"
                  class="w-full px-4 py-3 rounded-lg bg-indigo-800 border border-indigo-600 text-white placeholder-indigo-300 focus:ring-2 focus:ring-white focus:border-white"
                  required
                >
              </div>
              <button 
                type="submit"
                class="w-full px-6 py-3 bg-white text-indigo-700 font-medium rounded-lg hover:bg-gray-100 transition shadow-md cursor-pointer"
              >
                Подписаться
              </button>
            </form>
            <p class="text-xs text-indigo-200 mt-4">
              Мы уважаем вашу конфиденциальность. Отписаться можно в любой момент.
            </p>
          </div>
          <div class="hidden lg:block bg-indigo-600 relative">
            <div class="absolute inset-0 bg-gradient-to-br from-indigo-500 to-indigo-700 opacity-80"></div>
            <img 
              src="https://images.unsplash.com/photo-1554224155-6726b3ff858f?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80" 
              alt="Финансовое планирование"
              class="w-full h-full object-cover"
            >
          </div>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <footer class="bg-gray-900 text-gray-400 py-12 px-4 sm:px-6 lg:px-8">
      <div class="max-w-7xl mx-auto">
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
          <div>
            <div class="flex items-center space-x-2 mb-4">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-indigo-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
              <span class="text-xl font-bold text-white">Копить или жить?</span>
            </div>
            <p class="text-sm mb-4">
              Помогаем найти баланс между сегодняшними радостями и завтрашней финансовой стабильностью.
            </p>
            <div class="flex space-x-4">
              <a href="#" class="text-gray-400 hover:text-white">
                <span class="sr-only">Facebook</span>
                <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                  <path fill-rule="evenodd" d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33v6.988C18.343 21.128 22 16.991 22 12z" clip-rule="evenodd" />
                </svg>
              </a>
              <a href="#" class="text-gray-400 hover:text-white">
                <span class="sr-only">Instagram</span>
                <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                  <path fill-rule="evenodd" d="M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z" clip-rule="evenodd" />
                </svg>
              </a>
              <a href="#" class="text-gray-400 hover:text-white">
                <span class="sr-only">Telegram</span>
                <svg class="h-6 w-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                  <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm4.64 6.8c-.15 1.58-.8 5.42-1.13 7.19-.14.75-.42 1-.68 1.03-.58.05-1.02-.38-1.58-.75-.88-.58-1.38-.94-2.23-1.5-.99-.65-.35-1.01.22-1.59.15-.15 2.71-2.48 2.76-2.69.03-.1.06-.22.02-.31-.05-.1-.17-.14-.36-.05-1.4.92-3.99 2.67-5.22 3.51-.53.36-.85.55-.97.53-.21-.04-.37-.63-.57-1.18-.35-1.02-.67-2.04-.99-3.06-.36-1.19-.72-1.19-1.07-1.19h-.3c-.34 0-.89.13-1.36.66-.47.54-.18 1.67.71 3.29.47.88 1.07 1.82 1.54 2.45.47.63.94 1.33 1.51 1.68.47.29.9.38 1.28.38.17 0 .34 0 .5-.03.55-.11 1.33-.6 1.59-1.18.33-.75 1.18-4.32 1.34-5.47.03-.22.06-.33.03-.44-.03-.11-.11-.16-.25-.16h-1.4c-.15 0-.36.05-.72.38-.36.33-.71.73-1.07 1.14z"/>
                </svg>
              </a>
            </div>
          </div>
          <div>
            <h3 class="text-sm font-semibold text-white uppercase tracking-wider mb-4">Ресурсы</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-white transition">Блог</a></li>
              <li><a href="#" class="hover:text-white transition">Калькуляторы</a></li>
              <li><a href="#" class="hover:text-white transition">Гайды</a></li>
              <li><a href="#" class="hover:text-white transition">Исследования</a></li>
            </ul>
          </div>
          <div>
            <h3 class="text-sm font-semibold text-white uppercase tracking-wider mb-4">Компания</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-white transition">О нас</a></li>
              <li><a href="#" class="hover:text-white transition">Команда</a></li>
              <li><a href="#" class="hover:text-white transition">Карьера</a></li>
              <li><a href="#" class="hover:text-white transition">Контакты</a></li>
            </ul>
          </div>
          <div>
            <h3 class="text-sm font-semibold text-white uppercase tracking-wider mb-4">Правовая информация</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-white transition">Конфиденциальность</a></li>
              <li><a href="#" class="hover:text-white transition">Условия</a></li>
              <li><a href="#" class="hover:text-white transition">Cookie</a></li>
              <li><a href="#" class="hover:text-white transition">Отказ от ответственности</a></li>
            </ul>
          </div>
        </div>
        <div class="mt-8 pt-8 border-t border-gray-800 text-sm text-gray-400 text-center">
          &copy; 2023 Копить или жить? Все права защищены.
        </div>
      </div>
    </footer>

    <!-- Video Modal -->
    <div v-if="showVideoModal" class="fixed inset-0 z-50 overflow-y-auto">
  <div class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
    <div class="fixed inset-0 transition-opacity" aria-hidden="true">
      <div class="absolute inset-0 bg-gray-300 opacity-20" @click="showVideoModal = false"></div>
    </div>
    
    <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>
    
    <div class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-4xl sm:w-full">
      <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
        <div class="sm:flex sm:items-start">
          <div class="mt-3 text-center sm:mt-0 sm:text-left w-full">
            <div class="flex justify-between items-center mb-4">
              <h3 class="text-lg leading-6 font-medium text-gray-900">
                Как работает калькулятор "Копить или жить?"
              </h3>
              <button @click="showVideoModal = false" class="text-gray-400 hover:text-gray-500">
                <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                </svg>
              </button>
            </div>
            <div class="mt-2 aspect-w-16 aspect-h-9 bg-gray-100 rounded-lg overflow-hidden">
              <iframe 
                class="w-full h-96" 
                src="https://www.youtube.com/embed/dQw4w9WgXcQ" 
                title="YouTube video player" 
                frameborder="0" 
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                allowfullscreen
              ></iframe>
            </div>
            <div class="mt-4 text-gray-700">
              <p>Наш калькулятор помогает найти оптимальный баланс между текущими расходами и будущими сбережениями. Вот как это работает:</p>
              <ul class="list-disc pl-5 mt-2 space-y-1">
                <li>Введите ваш ежемесячный доход и обязательные расходы</li>
                <li>Установите желаемый процент сбережений</li>
                <li>Выберите период планирования и ожидаемую доходность инвестиций</li>
                <li>Определите вашу толерантность к риску</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
        <button 
          type="button" 
          @click="showVideoModal = false"
          class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-indigo-600 text-base font-medium text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:ml-3 sm:w-auto sm:text-sm"
        >
          Закрыть
        </button>
      </div>
    </div>
  </div>
</div>

    <!-- Tip Detail Modal -->
    <div v-if="currentTip !== null" class="fixed inset-0 z-50 overflow-y-auto">
      <div class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
        <div class="fixed inset-0 transition-opacity" aria-hidden="true">
          <div class="absolute inset-0 bg-gray-200 opacity-30" @click="currentTip = null"></div>
        </div>
        
        <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>
        
        <div class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-2xl sm:w-full">
          <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
            <div class="sm:flex sm:items-start">
              <div class="mt-3 text-center sm:mt-0 sm:text-left w-full">
                <div class="flex justify-between items-center mb-4">
                  <h3 class="text-lg leading-6 font-medium text-gray-900">
                    {{ tips[currentTip].title }}
                  </h3>
                  <button @click="currentTip = null" class="text-gray-400 hover:text-gray-500">
                    <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                  </button>
                </div>
                <div class="mt-2">
                  <div class="prose prose-indigo max-w-none">
                    <p>{{ tips[currentTip].fullDescription }}</p>
                    <div v-if="tips[currentTip].steps" class="mt-4">
                      <h4 class="font-medium text-gray-900">Как реализовать:</h4>
                      <ol class="list-decimal pl-5 space-y-2">
                        <li v-for="(step, index) in tips[currentTip].steps" :key="index">{{ step }}</li>
                      </ol>
                    </div>
                    <div v-if="tips[currentTip].example" class="mt-4 bg-gray-50 p-4 rounded-lg">
                      <h4 class="font-medium text-gray-900">Пример:</h4>
                      <p>{{ tips[currentTip].example }}</p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
            <button 
              type="button" 
              @click="currentTip = null"
              class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-indigo-600 text-base font-medium text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:ml-3 sm:w-auto sm:text-sm"
            >
              Закрыть
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Subscription Success Toast -->
   <div v-if="showSuccessToast" class="fixed bottom-4 right-4 z-50 min-w-[300px]">
  <div class="bg-green-50 border border-green-200 rounded-lg shadow-lg overflow-hidden w-full">
    <div class="p-4"> 
      <div class="flex items-start">
            <div class="flex-shrink-0">
              <svg class="h-5 w-5 text-green-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
              </svg>
            </div>
            <div class="ml-3 w-0 flex-1 pt-0.5">
              <p class="text-sm font-medium text-green-800 h-auto">Подписка оформлена!</p>
              <p class="mt-1 text-sm text-green-600 h-auto">Спасибо за подписку. Проверьте ваш email для подтверждения.</p>
            </div>
            <div class="ml-4 flex-shrink-0 flex">
              <button @click="showSuccessToast = false" class="bg-white rounded-md inline-flex text-gray-400 hover:text-gray-500 focus:outline-none">
                <span class="sr-only">Закрыть</span>
                <svg class="h-5 w-5" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor">
                  <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd" />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Chart, registerables } from 'chart.js';
Chart.register(...registerables);

export default {
  data() {
    return {
      mobileMenuOpen: false,
      showVideoModal: false,
      showSuccessToast: false,
      currentTip: null,
      email: '',
      
      // Calculator data
      income: 100000,
      expenses: 50000,
      savingsRate: 20,
      investmentReturn: 7,
      years: 10,
      riskTolerance: 2, // 1-4 scale
      
      // Strategies
      selectedStrategy: 1,
      strategies: [
        {
          title: "Агрессивные накопления",
          description: "Максимальные сбережения с минимальными текущими тратами",
          points: [
            "50-70% дохода на сбережения",
            "Минимальные расходы на жизнь",
            "Быстрый рост капитала"
          ],
          recommendedFor: "Молодые специалисты без обязательств",
          implementation: "Эта стратегия подходит для тех, кто готов временно ограничить свои текущие расходы ради быстрого накопления капитала. Основной фокус на инвестировании большей части дохода в инструменты с высокой доходностью. Рекомендуется откладывать 50-70% дохода, живя на оставшиеся 30-50%."
        },
        {
          title: "Сбалансированный подход",
          description: "Оптимальный баланс между текущими расходами и сбережениями",
          points: [
            "20-30% дохода на сбережения",
            "Комфортные расходы на жизнь",
            "Умеренный рост капитала"
          ],
          recommendedFor: "Семьи и люди среднего возраста",
          implementation: "Этот подход позволяет и комфортно жить сегодня, и заботиться о будущем. Рекомендуется откладывать 20-30% дохода, распределяя сбережения между надежными и умеренно рискованными инструментами. Оставшиеся 70-80% дохода идут на текущие нужды и качество жизни."
        },
        {
          title: "Текущее потребление",
          description: "Минимальные сбережения с акцентом на текущее качество жизни",
          points: [
            "5-10% дохода на сбережения",
            "Максимальные расходы на жизнь",
            "Медленный рост капитала"
          ],
          recommendedFor: "Пожилые люди или те, кто ценит текущий комфорт",
          implementation: "Эта стратегия подходит для тех, кто предпочитает жить сегодняшним днем. Рекомендуется откладывать 5-10% дохода на непредвиденные расходы, а остальные средства тратить на текущие нужды. Важно помнить, что такой подход требует дополнительных источников дохода в будущем."
        }
      ],
      
      // Tips
      tips: [
        {
          title: "Правило 50/30/20",
          description: "Классическое правило распределения доходов",
          fullDescription: "Правило 50/30/20 предлагает распределять доход следующим образом: 50% на основные потребности (жилье, еда, транспорт), 30% на желания (развлечения, хобби) и 20% на сбережения. Это простой и эффективный способ поддерживать баланс между текущими расходами и будущими накоплениями.",
          steps: [
            "Рассчитайте ваш ежемесячный доход после налогов",
            "50% направьте на обязательные расходы",
            "30% оставьте на личные желания",
            "20% откладывайте на сбережения"
          ],
          example: "При доходе 100,000₽: 50,000₽ на жилье и еду, 30,000₽ на развлечения, 20,000₽ на сбережения."
        },
        {
          title: "Автоматизация сбережений",
          description: "Настройте автоматические переводы на счета",
          fullDescription: "Автоматизация сбережений помогает дисциплинировать себя и делает процесс накопления безболезненным. Настройте автоматический перевод определенной суммы на сберегательный счет сразу после получения зарплаты. Таким образом, вы не будете тратить эти деньги на текущие нужды.",
          steps: [
            "Откройте отдельный сберегательный счет",
            "Настройте автоматический перевод в день зарплаты",
            "Начните с небольшой суммы (5-10%)",
            "Постепенно увеличивайте процент сбережений"
          ],
          example: "При зарплате 80,000₽ автоматически переводите 8,000₽ (10%) на сберегательный счет."
        },
        {
          title: "Инвестируйте разницу",
          description: "Откладывайте сэкономленные средства",
          fullDescription: "Каждый раз, когда вам удается сэкономить (например, нашли товар дешевле, отказались от ненужной покупки), переводите сэкономленную сумму на инвестиционный счет. Это формирует полезную финансовую привычку и ускоряет рост капитала.",
          steps: [
            "Отслеживайте свои сбережения от оптимизации расходов",
            "Создайте отдельный счет для инвестиций",
            "Регулярно переводите сэкономленные суммы",
            "Инвестируйте в диверсифицированные инструменты"
          ],
          example: "Вместо кофе за 300₽ купили за 150₽ — 150₽ на инвестиции. Сэкономили 2,000₽ на абонементе — инвестируйте эту сумму."
        },
        {
          title: "Правило 24 часов",
          description: "Откладывайте импульсные покупки",
          fullDescription: "Перед совершением незапланированной покупки выжидайте 24 часа. Это время позволяет оценить, действительно ли вам нужна эта вещь, или это импульсивное желание. Сэкономленные таким образом средства можно направить на сбережения.",
          steps: [
            "При желании совершить незапланированную покупку — ждите 24 часа", 
            "Оцените необходимость покупки после паузы",
            "Если покупка действительно нужна — совершите ее",
            "Если нет — переведите эту сумму на сбережения"
          ],
          example: "Хотите купить новую курту за 15,000₽ — подождите день. Если желание не прошло — купите. Если прошло — отложите эти деньги."
        }
      ],
      
      // Risk levels
      riskLevels: [
        { label: 'Низкая', value: 1 },
        { label: 'Умеренная', value: 2 },
        { label: 'Высокая', value: 3 }
      ]
    }
  },
  
  computed: {
    disposableIncome() {
      return Math.max(0, this.income - this.expenses - this.savingsAmount)
    },
    
    disposableIncomePercentage() {
      return Math.round((this.disposableIncome / this.income) * 100)
    },
    
    savingsAmount() {
      return this.income * (this.savingsRate / 100)
    },
    
    futureSavings() {
      const monthlyRate = this.investmentReturn / 100 / 12
      const months = this.years * 12
      let futureValue = 0
      
      for (let i = 0; i < months; i++) {
        futureValue = (futureValue + this.savingsAmount) * (1 + monthlyRate)
      }
      
      return futureValue
    },
    
    strategyColors() {
      return [
        { bg: 'bg-red-100', text: 'text-red-600' },
        { bg: 'bg-indigo-100', text: 'text-indigo-600' },
        { bg: 'bg-green-100', text: 'text-green-600' }
      ]
    },
    
    strategyIcons() {
      return [
        'M13 7h8m0 0v8m0-8l-8 8-4-4-6 6',
        'M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z',
        'M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15'
      ]
    },
    
    tipColors() {
      return [
        { bg: 'bg-blue-100', text: 'text-blue-600' },
        { bg: 'bg-purple-100', text: 'text-purple-600' },
        { bg: 'bg-teal-100', text: 'text-teal-600' },
        { bg: 'bg-amber-100', text: 'text-amber-600' }
      ]
    },
    
    tipIcons() {
      return [
        'M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2',
        'M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z',
        'M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10',
        'M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z'
      ]
    },
    
    savingsProfile() {
      if (this.savingsRate >= 30) return 'Агрессивный'
      if (this.savingsRate >= 15) return 'Умеренный'
      return 'Минимальный'
    },
    
    riskProfile() {
      return this.riskLevels[this.riskTolerance - 1].label
    },
    
    balanceScore() {
      // Calculate balance score between 0-100 based on savings rate and risk tolerance
      const savingsScore = Math.min(this.savingsRate * 2, 100) * 0.6
      const riskScore = (this.riskTolerance / 3) * 100 * 0.4
      return Math.round(savingsScore + riskScore)
    },
    
    balanceProfile() {
      if (this.balanceScore >= 80) return 'Отличный'
      if (this.balanceScore >= 60) return 'Хороший'
      if (this.balanceScore >= 40) return 'Средний'
      return 'Требует улучшений'
    },
    
    filteredRecommendations() {
      const recs = []
      
      // Savings rate recommendations
      if (this.savingsRate < 10) {
        recs.push({
          type: 'warning',
          title: 'Низкий уровень сбережений',
          message: 'Ваш уровень сбережений ниже рекомендуемого минимума (10-15%). Рассмотрите возможность увеличения процента откладываемых средств.'
        })
      } else if (this.savingsRate > 40) {
        recs.push({
          type: 'info',
          title: 'Высокий уровень сбережений',
          message: 'Вы откладываете значительную часть дохода. Убедитесь, что текущее качество жизни вас устраивает.'
        })
      } else {
        recs.push({
          type: 'success',
          title: 'Оптимальный уровень сбережений',
          message: 'Ваш уровень сбережений соответствует рекомендуемым значениям для долгосрочного финансового здоровья.'
        })
      }
      
      // Risk tolerance recommendations
      if (this.riskTolerance === 1 && this.years > 10) {
        recs.push({
          type: 'warning',
          title: 'Консервативные инвестиции',
          message: 'При долгосрочном горизонте планирования можно рассмотреть более доходные инструменты с умеренным риском.'
        })
      } else if (this.riskTolerance === 3 && this.years < 5) {
        recs.push({
          type: 'warning',
          title: 'Высокий риск',
          message: 'При коротком периоде планирования высокорисковые инвестиции могут быть неоправданны.'
        })
      }
      
      // Balance recommendations
      if (this.disposableIncome < this.expenses * 0.3) {
        recs.push({
          type: 'warning',
          title: 'Ограниченный бюджет',
          message: 'Свободных средств после обязательных расходов и сбережений остается мало. Рассмотрите оптимизацию расходов или увеличение дохода.'
        })
      }
      
      return recs
    }
  },
  
  methods: {
    formatCurrency(value) {
      return new Intl.NumberFormat('ru-RU', { style: 'currency', currency: 'RUB', maximumFractionDigits: 0 }).format(value)
    },
    
    scrollToCalculator() {
      const element = document.getElementById('calculator')
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' })
      }
    },
    
    showTipDetails(index) {
      this.currentTip = index
    },
    
    subscribe() {
      // In a real app, you would send this to your backend
      console.log('Subscribed with email:', this.email)
      this.email = ''
      this.showSuccessToast = true
      setTimeout(() => {
        this.showSuccessToast = false
      }, 5000)
    },
    
    strategySavings(index) {
      const rates = [0.6, 0.25, 0.1]
      return this.income * rates[index]
    },
    
    strategySpending(index) {
      return this.income - this.expenses - this.strategySavings(index)
    },
    
    strategyFutureValue(index) {
      const monthlyRate = this.investmentReturn / 100 / 12
      const months = this.years * 12
      let futureValue = 0
      const savings = this.strategySavings(index)
      
      for (let i = 0; i < months; i++) {
        futureValue = (futureValue + savings) * (1 + monthlyRate)
      }
      
      return futureValue
    },
    
    initCharts() {
      
      // Savings growth chart 
      const savingsCtx = this.$refs.savingsChart.getContext('2d');
      this.savingsChart = new Chart(savingsCtx, {
        type: 'line',
        data: {
          labels: Array.from({ length: this.years }, (_, i) => (i + 1).toString()),
          datasets: [{
            label: 'Накопления',
            data: this.calculateSavingsGrowth(),
            borderColor: '#4f46e5',
            backgroundColor: 'rgba(79, 70, 229, 0.1)',
            fill: true,
            tension: 0.4
          }]
        },
        options: {
          responsive: true,
          plugins: {
            legend: {
              display: false
            },
            tooltip: {
              callbacks: {
                label: (context) => {
                  return `${context.dataset.label}: ${this.formatCurrency(context.raw)}`
                }
              }
            }
          },
          scales: {
            y: {
              beginAtZero: true,
              ticks: {
                callback: (value) => this.formatCurrency(value)
              }
            }
          }
        }
      })
      
      // Pie chart
     const pieCtx = this.$refs.pieChart.getContext('2d');
      this.pieChart = new Chart(pieCtx, {
        type: 'doughnut',
        data: {
          labels: ['Обязательные расходы', 'Свободные средства', 'Накопления'],
          datasets: [{
            data: [this.expenses, this.disposableIncome, this.savingsAmount],
            backgroundColor: [
              'rgba(239, 68, 68, 0.7)',
              'rgba(16, 185, 129, 0.7)',
              'rgba(99, 102, 241, 0.7)'
            ],
            borderColor: [
              'rgba(239, 68, 68, 1)',
              'rgba(16, 185, 129, 1)',
              'rgba(99, 102, 241, 1)'
            ],
            borderWidth: 1
          }]
        },
        options: {
          responsive: true,
          plugins: {
            tooltip: {
              callbacks: {
                label: (context) => {
                  const label = context.label || ''
                  const value = context.raw || 0
                  const percentage = Math.round((value / this.income) * 100)
                  return `${label}: ${this.formatCurrency(value)} (${percentage}%)`
                }
              }
            }
          }
        }
      })
      
      // Comparison chart
       const comparisonCtx = this.$refs.comparisonChart.getContext('2d');
      this.comparisonChart = new Chart(comparisonCtx, {
        type: 'bar',
        data: {
          labels: this.strategies.map(s => s.title),
          datasets: [{
            label: 'Будущие накопления',
            data: [
              this.strategyFutureValue(0),
              this.strategyFutureValue(1),
              this.strategyFutureValue(2)
            ],
            backgroundColor: [
              'rgba(239, 68, 68, 0.7)',
              'rgba(99, 102, 241, 0.7)',
              'rgba(16, 185, 129, 0.7)'
            ]
          }]
        },
        options: {
          responsive: true,
          plugins: {
            legend: {
              display: false
            },
            tooltip: {
              callbacks: {
                label: (context) => {
                  return `${this.formatCurrency(context.raw)} через ${this.years} лет`
                }
              }
            }
          },
          scales: {
            y: {
              beginAtZero: true,
              ticks: {
                callback: (value) => this.formatCurrency(value)
              }
            }
          }
        }
      })
    },
    
    calculateSavingsGrowth() {
      const monthlyRate = this.investmentReturn / 100 / 12
      const result = []
      let total = 0
      
      for (let year = 1; year <= this.years; year++) {
        for (let month = 1; month <= 12; month++) {
          total = (total + this.savingsAmount) * (1 + monthlyRate)
        }
        result.push(total)
      }
      
      return result
    },
    
    updateCharts() {
      if (this.savingsChart && this.pieChart && this.comparisonChart) {
        // Update savings chart
        this.savingsChart.data.labels = Array.from({ length: this.years }, (_, i) => (i + 1).toString())
        this.savingsChart.data.datasets[0].data = this.calculateSavingsGrowth()
        
        // Update pie chart
        this.pieChart.data.datasets[0].data = [this.expenses, this.disposableIncome, this.savingsAmount]
        
        // Update comparison chart
        this.comparisonChart.data.datasets[0].data = [
          this.strategyFutureValue(0),
          this.strategyFutureValue(1),
          this.strategyFutureValue(2)
        ]
        
        // Update all charts
        this.savingsChart.update()
        this.pieChart.update()
        this.comparisonChart.update()
      }
    }
  },
  
  mounted() {
    this.initCharts();  
  },
  
  watch: {
    income() {
      this.updateCharts()
    },
    expenses() {
      this.updateCharts()
    },
    savingsRate() {
      this.updateCharts()
    },
    investmentReturn() {
      this.updateCharts()
    },
    years() {
      this.updateCharts()
    }
  }
}
</script>

<style>
/* Custom styles can be added here if needed */
.prose {
  color: #374151;
  max-width: 65ch;
}

.prose p {
  margin-top: 1.25em;
  margin-bottom: 1.25em;
}

.prose ul {
  margin-top: 1.25em;
  margin-bottom: 1.25em;
  padding-left: 1.625em;
  list-style-type: disc;
}

.prose ol {
  margin-top: 1.25em;
  margin-bottom: 1.25em;
  padding-left: 1.625em;
  list-style-type: decimal;
}

.prose li {
  margin-top: 0.5em;
  margin-bottom: 0.5em;
}

.prose-indigo a {
  color: #4f46e5;
  text-decoration: none;
  font-weight: 500;
}

.prose-indigo a:hover {
  text-decoration: underline;
}
</style>