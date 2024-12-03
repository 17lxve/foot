<script setup lang="ts">
import { computed } from 'vue'
const props = defineProps({
  tableHeaders: { type: Array<string | { name: string; content: Array<string> }>, required: true },
  tableData: {
    type: Array<Array<string>>,
    required: true,
  },
})
const subHeaders = computed(() => {
  return props
    .tableHeaders!.filter((attr) => typeof attr !== 'string')
    .map((element) => element.content)
    .flat()
})
</script>
<template>
  <table class="performance-table">
    <thead>
      <tr>
        <th
          v-for="(attribute, i) in tableHeaders"
          :key="`header-${attribute}${i}`"
          :colspan="typeof attribute == 'string' ? 1 : attribute.content.length"
          :rowspan="typeof attribute == 'string' ? 2 : 1"
        >
          {{ typeof attribute === 'string' ? attribute : attribute.name }}
        </th>
      </tr>
      <tr>
        <th v-for="attribute in subHeaders" :key="`sub${attribute}-`">
          {{ attribute }}
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="element in tableData" :key="`element${element}`">
        <td v-for="attribute in element" :key="`${element}${attribute}`">
          {{ attribute }}
        </td>
      </tr>
    </tbody>
  </table>
</template>
<style scoped>
.performance-table {
  width: 100%;
  border-collapse: collapse;
  font-family: Arial, sans-serif;
  border-radius: 2rem;
  overflow: hidden;
  box-shadow: -2px 2px 10px 1px var(--secondary);
}
.performance-table td {
  border: 1px solid black;
}

.performance-table th,
.performance-table td {
  padding: 8px;
  text-align: center;
}

.performance-table th {
  background-color: var(--tertiary);
  font-weight: bold;
  color: var(--text) !important;
}

.performance-table td:first-child {
  text-align: left;
  font-weight: bold;
  background-color: var(--light) !important;
  color: var(--text);
}

.performance-table tbody tr:last-child td:first-child {
  border-radius: 0 0 0 2rem;
}

.sub-row {
  width: 100%;
  margin: 0;
}

.sub-row th {
  width: auto;
}
</style>
