<template>
    <div class="flex-1 bg-green-500 text-white p-4">
      {{ data }}
    </div>
  </template>
  
  <script>
  export default {
    name: 'EmailBody',
    props: {
        data: {
        type: String,
        required: true,
        },
    }
  }
  </script>
  