<template>
    <div class="flex items-center bg-gray-100 p-2 rounded-md">
      <input class="flex-grow p-2 bg-transparent outline-none" 
        v-model="searchTerm"
        type="search" 
        placeholder="Buscar..."
        :disabled="isLoading">
        <button @click="sendSearchRequest" class="p-2" :disabled="isLoading">
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
      searchTerm: '',
      isLoading: false,
      error: null, 
    };
  },
  methods: {
    async sendSearchRequest() {
      if (this.searchTerm.trim() === '') {
        return;
      }
      this.isLoading = true;
      this.error = null;
      try {
        const response = await axios.post('http://localhost:3000/emails/search', 
          {"FieldName":"subject","Value":this.searchTerm} 
        );

        console.log(response.data);
        
        const dataParsed  = response.data.hits.hits.map(hit => ({
          _id: hit._id,
          _source: hit._source
        }));

        this.$emit('data-generated', dataParsed);

      } catch (error) {
        this.error = error.message; 
      } finally {
        this.isLoading = false;
      }
    },

  }
}
</script>