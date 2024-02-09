<template>
  <div>
    <!-- Encabezado -->
    <div class="bg-red-500 text-white p-4 rounded-t-lg">
      <h1 class="text-xl font-bold">MamuroEmail</h1>
    </div>
    
    <!-- Buscador -->
    <div class="flex justify-center">
      <SearchField />
    </div>
    
  </div>
</template>

<script>
import { provide, reactive } from 'vue';
import SearchField from './SearchField.vue';


export default {
  name: 'EmailDashboard',
  components: {
    SearchField 
  },
  setup() {
    // Crear un estado reactivo para los datos de búsqueda
    const searchResults = reactive({
      emails: []
    });

    // Proporcionar el estado y cualquier método para modificarlo
    provide('searchResults', searchResults);

    return {}; // setup debe retornar siempre un objeto
  }
}
</script>