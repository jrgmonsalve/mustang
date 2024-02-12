<template>
  <div class="flex-1 bg-blue-500 text-white p-4">
    <table class="table-auto w-full text-left border-collapse border border-gray-200">
      <caption>
        Emails Matched
      </caption>
      <thead>
        <tr>
          <th>From</th>
          <th>To</th>
          <th>Subject</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in data" :key="item._id" :class="index % 2 === 0 ? 'bg-blue-400' : 'bg-blue-500'">
          <td>{{ item._source.from }}</td>
          <td>{{ item._source.to }}</td>
          <td>{{ item._source.subject }}</td>
          <td class="text-center">
            <button @click="viewEmailBody(item._id)">
              ver..
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

  
<script>
import axios from 'axios';
export default {
  name: 'SumaryEmailsMatchTable',
  props: {
    data: {
      type: Array,
      required: true,
    },
  },
  methods: {
    async viewEmailBody(id) {
      try {
        const response = await axios.get(`http://localhost:3000/emails/${id}`);
        this.$emit('bodyEmail', response.data._source.body);
      } catch (error) {
        console.error('Error fetching details:', error);
      }
    },
  },
}
</script>
  