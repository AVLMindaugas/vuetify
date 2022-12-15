<template>
  <v-app>
    <v-app-bar>
      <v-tabs v-model="tab">
        <v-tab value="page1">Page #1</v-tab>
        <v-tab value="page2">Page #2</v-tab>
        <v-tab value="page3">Page #3</v-tab>
      </v-tabs>
    </v-app-bar>
    <v-main class="pa-10 mt-10 bg-grey-lighten-3">
      <div class="text-h4 mb-3">Page #1</div>
      <v-card>
        <div class="d-flex flex-wrap align-content-start">
          <v-select
            v-for="i in 8" :key="i"
            :label="`Select #${i}`"
            :items="options"
            class="ma-2 pa-2"
          ></v-select>
        </div>
        <v-table>
          <thead>
            <tr>
              <th v-for="i in 8" :key="i">
                {{ `Column #${i}`}}
              </th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="(item, index) in rows"
              :key="index"
            >
              <td v-for="(col, cIdx) in item">
                <template v-if="cIdx === 3">
                  <v-chip v-for="i in 5">Chip</v-chip>
                </template>
                <template v-else>{{ col }}</template>
              </td>
            </tr>
          </tbody>
        </v-table>
      </v-card>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const tab = ref('one')
const options = [
  'Option #1',
  'Option #1',
  'Option #1',
  'Option #1',
  'Option #1',
];
const rows = ref<string[]>([]);

for (let i = 1; i <= 100; i++) {
  const rowData: string[] = [];
  for (let c = 1; c <= 8; c++) {
    rowData.push(`Col: #${c} Row: #${i}`);
  }
  rows.value.push(rowData);
}
</script>
