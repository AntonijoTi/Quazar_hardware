<template>
    <div class="q-pa-md">
    <q-table
      title="Devices"
      :rows="rows"
      :columns="columns"
      row-key="name"
      :selected-rows-label="getSelectedString"
      selection="multiple"
      v-model:selected="selected"
    />


  </div>
</template>

<script>
  import { ref } from 'vue'

  const columns = [
    {
      name: 'desc',
      required: true,
      label: 'Device Manufacturers',
      align: 'left',
      field: row => row.name,
      format: val => `${val}`,
      sortable: true
    },
    { name: 'device_types', align: 'center', label: 'Device types', field: 'device_types', sortable: true },
    { name: 'device_models', label: 'Device models', field: 'device_models', sortable: true },
    { name: 'operation_system', label: 'Operation System', field: 'operation_system', sortable: true },
  ]

  const rows = [
    {
      name: 'Dell',
      device_types: 'Notebook',
      device_models: 'Dell 27  ',
      operation_system: 'Linux',
    },
    {
      name: 'HP',
      device_types: 'Notebook',
      device_models: 'HP307  ',
      operation_system: 'Linux',
    },
    {
      name: 'Huawei',
      device_types: 'Notebook',
      device_models: 'D15  ',
      operation_system: 'Linux',
    },
    {
      name: 'MAC',
      device_types: 'Notebook',
      device_models: 'MacAir13 ',
      operation_system: 'Linux',
    },
    
  ]

  export default {
    setup () {
      const selected = ref([])

      return {
        selected,
        columns,
        rows,

        getSelectedString () {
          return selected.value.length === 0 ? '' : `${selected.value.length} record${selected.value.length > 1 ? 's' : ''} selected of ${rows.length}`
        }
      }
    }
  }
  </script>
