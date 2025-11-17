<script setup></script>
<template>
  <div
    class="border-t border-gray-200 bg-gray-50 px-4 py-3 sm:px-5"
    role="contentinfo"
    aria-label="Todo list footer"
  >
    <div class="flex flex-col sm:flex-row sm:items-center gap-3 sm:gap-4">
      <!-- Compteur avec aria-live -->
      <p class="text-sm text-gray-600">
        <span
          id="items-left"
          class="font-medium"
          aria-live="polite"
          aria-atomic="true"
          >2</span
        >
        items left
      </p>

      <!-- Filtres -->
      <nav class="flex items-center gap-2" aria-label="Filters">
        <button
          class="px-3 py-1.5 text-sm rounded-full border border-gray-300 hover:border-gray-400 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-blue-500"
          aria-pressed="true"
        >
          All
        </button>
        <button
          class="px-3 py-1.5 text-sm rounded-full border border-gray-300 hover:border-gray-400 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-blue-500"
          aria-pressed="false"
        >
          Active
        </button>
        <button
          class="px-3 py-1.5 text-sm rounded-full border border-gray-300 hover:border-gray-400 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-blue-500"
          aria-pressed="false"
        >
          Completed
        </button>
      </nav>

      <!-- Action secondaire -->
      <div class="sm:ml-auto">
        <button
          class="text-sm text-gray-600 hover:text-gray-800 underline underline-offset-2 decoration-gray-300 hover:decoration-gray-500 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-blue-500 rounded"
        >
          Clear completed
        </button>
      </div>
    </div>
  </div>
</template>
<style scoped></style>
