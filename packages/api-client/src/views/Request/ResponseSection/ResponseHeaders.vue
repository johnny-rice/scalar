<script setup lang="ts">
import DataTable from '@/components/DataTable/DataTable.vue'
import DataTableRow from '@/components/DataTable/DataTableRow.vue'
import DataTableText from '@/components/DataTable/DataTableText.vue'
import ViewLayoutCollapse from '@/components/ViewLayout/ViewLayoutCollapse.vue'

type Header = { name: string; value: string; required: boolean }

defineProps<{
  headers: Header[]
}>()
</script>
<template>
  <ViewLayoutCollapse
    :defaultOpen="false"
    :itemCount="headers.length">
    <template #title>Headers</template>
    <DataTable
      v-if="headers.length"
      :columns="['minmax(auto, min-content)', 'minmax(50%, 1fr)']"
      scroll>
      <DataTableRow
        v-for="(item, idx) in headers"
        :key="idx"
        class="text-c-1">
        <DataTableText
          class="sticky left-0 z-1 bg-b-1 max-w-48"
          :text="item.name" />
        <DataTableText
          class="z-0"
          :text="item.value" />
      </DataTableRow>
    </DataTable>
    <!-- Empty state -->
    <div
      v-else
      class="text-c-3 px-4 text-sm border rounded min-h-12 justify-center flex items-center bg-b-1 mx-1">
      No Headers
    </div>
  </ViewLayoutCollapse>
</template>
