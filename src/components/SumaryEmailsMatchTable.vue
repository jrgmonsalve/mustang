<template>
  <div class="flex-1 bg-blue-500 text-white p-4">
    <table>
      <thead>
        <tr>
          <th>From</th>
          <th>To</th>
          <th>Subject</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in data" :key="item._id">
          <td>{{ item._source.from }}</td>
          <td>{{ item._source.to }}</td>
          <td>{{ item._source.subject }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
  
<script>
export default {
  name: 'SumaryEmailsMatchTable',
  props: {
    data: {
      type: Array,
      required: true,
    },
  },
}
</script>
  