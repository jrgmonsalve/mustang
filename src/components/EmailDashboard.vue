<template>
  <div>
    <!-- Encabezado -->
    <div class="bg-red-500 text-white p-4 rounded-t-lg">
      <h1 class="text-xl font-bold">Search Emails</h1>
    </div>
    
    <!-- Buscador -->
    <div class="flex justify-center">
      <SearchField 
      @emailsFetched="handleEmailsFetched"
      @bodyEmail="handleBodyEmail"
      />
    </div>
    <div class="flex">
      <SumaryEmailsMatchTable 
      :data="emailsToShow" 
      @bodyEmail="handleBodyEmail"/>
      <EmailBody :data="emailBodyToShow"/>
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
      emailsToShow:[],
      emailBodyToShow:"Choose an email"
    };
  },
  components: {
    SearchField,
    SumaryEmailsMatchTable,
    EmailBody 
  },
  methods: {
    handleEmailsFetched(data) {
      this.emailsToShow = data;
    },
    handleBodyEmail(data) {
      this.emailBodyToShow = data;
    },
  },
}
</script>