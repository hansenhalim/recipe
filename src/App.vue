<template>
  <div class="p-6">
    <div class="py-36 text-center">
      <div class="text-4xl">Recipe Calculator</div>
      <div class="mt-2 font-mono text-slate-400 dark:text-neutral-500">v1.0.0</div>
    </div>

    <div class="grid grid-cols-1 gap-6 divide-y dark:divide-neutral-800">
      <div>
        <div class="rounded-xl bg-emerald-200 py-6 dark:bg-emerald-800">
          <div class="grid h-6 grid-cols-3 divide-x divide-emerald-300 dark:divide-emerald-700">
            <RecipeViewer name="T" :value="RECIPE_0" />
            <RecipeViewer name="G" :value="RECIPE_1" />
            <RecipeViewer name="KT" :value="RECIPE_2" />
          </div>
        </div>

        <div class="mt-2 rounded-xl bg-emerald-200 py-6 dark:bg-emerald-800">
          <div class="grid h-6 grid-cols-3 divide-x divide-emerald-300 dark:divide-emerald-700">
            <RecipeViewer name="KL" :value="RECIPE_3" />
            <RecipeViewer name="TLR" :value="RECIPE_4" />
            <RecipeViewer name="MIGOR" :value="RECIPE_5" />
          </div>
        </div>

        <div class="mt-4 grid grid-cols-2 gap-2">
          <ProductCounter
            name="Pistel"
            :count="PRODUCT_0"
            @add-click="PRODUCT_0++"
            @sub-click="PRODUCT_0--"
          />
          <ProductCounter
            name="Keriting"
            :count="PRODUCT_1"
            @add-click="PRODUCT_1++"
            @sub-click="PRODUCT_1--"
          />
          <ProductCounter
            name="Lenjer Besar"
            :count="PRODUCT_2"
            @add-click="PRODUCT_2++"
            @sub-click="PRODUCT_2--"
          />
          <ProductCounter
            name="Tekwan"
            :count="PRODUCT_3"
            @add-click="PRODUCT_3++"
            @sub-click="PRODUCT_3--"
          />
          <ProductCounter
            name="Kulit"
            :count="PRODUCT_4"
            @add-click="PRODUCT_4++"
            @sub-click="PRODUCT_4--"
          />
          <ProductCounter
            name="Model"
            :count="PRODUCT_5"
            @add-click="PRODUCT_5++"
            @sub-click="PRODUCT_5--"
          />
          <ProductCounter
            name="Telur Kecil"
            :count="PRODUCT_6"
            @add-click="PRODUCT_6++"
            @sub-click="PRODUCT_6--"
          />
          <ProductCounter
            name="Lenjer Kecil"
            :count="PRODUCT_7"
            @add-click="PRODUCT_7++"
            @sub-click="PRODUCT_7--"
          />
          <ProductCounter
            name="Adaan"
            :count="PRODUCT_8"
            @add-click="PRODUCT_8++"
            @sub-click="PRODUCT_8--"
          />
          <ProductCounter
            name="Kapal Selam"
            :count="PRODUCT_9"
            @add-click="PRODUCT_9++"
            @sub-click="PRODUCT_9--"
          />
        </div>
      </div>

      <div class="flex items-center justify-between pt-6">
        <div class="text-slate-600 dark:text-neutral-400">Choose Theme</div>
        <div
          class="dark:highlight-white/5 relative flex items-center rounded-lg p-1.5 px-3 font-medium text-slate-700 shadow-sm ring-1 ring-slate-900/10 dark:bg-slate-600 dark:text-slate-200 dark:ring-0"
        >
          <SunIcon
            :class="{ hidden: theme !== 'light' }"
            class="mr-2 h-5 w-5 text-gray-500 dark:text-gray-300"
          />
          <MoonIcon
            :class="{ hidden: theme !== 'dark' }"
            class="mr-2 h-5 w-5 text-gray-500 dark:text-gray-300"
          />
          <ComputerDesktopIcon
            :class="{ hidden: theme !== 'auto' }"
            class="mr-2 h-5 w-5 text-gray-500 dark:text-gray-300"
          />
          <span>{{ themes[theme] }}</span>
          <svg class="ml-2 h-6 w-6 text-slate-400" fill="none">
            <path
              d="m15 11-3 3-3-3"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            ></path>
          </svg>

          <select v-model="theme" class="absolute inset-0 h-full w-full appearance-none opacity-0">
            <option value="light">Light</option>
            <option value="dark">Dark</option>
            <option value="auto">System</option>
          </select>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue'
import ProductCounter from '@/components/ProductCounter.vue'
import RecipeViewer from '@/components/RecipeViewer.vue'
import { ComputerDesktopIcon, MoonIcon, SunIcon } from '@heroicons/vue/24/solid'

if (
  localStorage.theme === 'dark' ||
  (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)
) {
  document.documentElement.classList.add('dark')
} else {
  document.documentElement.classList.remove('dark')
}

const themes = {
  light: 'Light',
  dark: 'Dark',
  auto: 'System'
}

const theme = ref('auto')

const PRODUCT_0 = ref(0)
const PRODUCT_1 = ref(0)
const PRODUCT_2 = ref(0)
const PRODUCT_3 = ref(0)
const PRODUCT_4 = ref(0)
const PRODUCT_5 = ref(0)
const PRODUCT_6 = ref(0)
const PRODUCT_7 = ref(0)
const PRODUCT_8 = ref(0)
const PRODUCT_9 = ref(0)

const RECIPE_0 = computed(
  () =>
    0.25 * PRODUCT_0.value +
    1.5 * PRODUCT_1.value +
    3 * PRODUCT_2.value +
    1 * PRODUCT_3.value +
    3 * PRODUCT_5.value +
    3 * PRODUCT_6.value +
    3 * PRODUCT_7.value +
    1.5 * PRODUCT_8.value +
    3.75 * PRODUCT_9.value
)

const RECIPE_1 = computed(
  () =>
    0.25 * PRODUCT_0.value +
    1 * PRODUCT_2.value +
    1 * PRODUCT_5.value +
    1 * PRODUCT_6.value +
    1 * PRODUCT_7.value +
    0.25 * PRODUCT_9.value
)

const RECIPE_2 = computed(
  () =>
    0.5 * PRODUCT_0.value +
    1 * PRODUCT_1.value +
    1 * PRODUCT_2.value +
    1 * PRODUCT_6.value +
    1 * PRODUCT_7.value +
    1 * PRODUCT_8.value +
    1 * PRODUCT_9.value
)

const RECIPE_3 = computed(() => 1 * PRODUCT_4.value)

const RECIPE_4 = computed(
  () =>
    4 * PRODUCT_4.value +
    15 * PRODUCT_5.value +
    45 * PRODUCT_6.value +
    5 * PRODUCT_8.value +
    55 * PRODUCT_9.value
)

const RECIPE_5 = computed(() => 2.5 * PRODUCT_5.value)

// PRODUCT_0: PISTEL
// PRODUCT_1: KERITING
// PRODUCT_2: LB
// PRODUCT_3: TEKWAN (TKW)
// PRODUCT_4: KL
// PRODUCT_5: MODEL (MDL)
// PRODUCT_6: TK 1:3
// PRODUCT_7: LK 1:3
// PRODUCT_8: ADAAN 2 (Ø)
// PRODUCT_9: KAPAL SELEM (TB)

// RECIPE_0: T
// RECIPE_1: G
// RECIPE_2: KT
// RECIPE_3: KL
// RECIPE_4: TLR
// RECIPE_5: MIGOR
</script>
