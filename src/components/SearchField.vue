<template>
    <div class="flex items-center bg-gray-100 p-2 rounded-md">
        <input class="flex-grow p-2 bg-transparent outline-none" type="search" placeholder="Buscar...">
        <button @click="sendSearchRequest" class="p-2">
            <font-awesome-icon icon="search" />
        </button>
    </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'SearchField',
  data() {
    return {
      searchTerm: '' 
    };
  },
  methods: {
    async sendSearchRequest() {
      if (this.searchTerm.trim() === '') {
        return;
      }
      
      try {
        const response = await axios.post('TU_ENDPOINT', {
          body: this.searchTerm 
        });

        console.log(response.data);
        this.$eventBus.$emit('search-completed', response.data);
      } catch (error) {
        console.error(error);
      }
    }
  }
}
</script>