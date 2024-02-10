<template>
  <div>
    <!-- Encabezado -->
    <div class="bg-red-500 text-white p-4 rounded-t-lg">
      <h1 class="text-xl font-bold">Search Emails</h1>
    </div>
    
    <!-- Buscador -->
    <div class="flex justify-center">
      <SearchField @data-generated="onDataGenerated"/>
    </div>
    <div class="flex">
      <SumaryEmailsMatchTable :data="emailsMatched"/>
      <EmailBody />
    </div>
  </div>
</template>

<script>
import SearchField from './SearchField.vue';
import SumaryEmailsMatchTable from './SumaryEmailsMatchTable.vue';
import EmailBody from './EmailBody.vue';

export default {
  name: 'EmailDashboard',
  data(){
    return {
      emailsMatched:[]
    };
  },
  components: {
    SearchField,
    SumaryEmailsMatchTable,
    EmailBody 
  },
  methods: {
    onDataGenerated(data) {
      this.emailsMatched = data;
    },
  },
}
</script>