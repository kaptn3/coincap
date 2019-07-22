<template>
  <main>
    <a-table
      :head="head"
      :body="body"
    />
  </main>
</template>

<script>
// @ is an alias to /src
import ATable from '@/components/Table.vue';
import axios from 'axios';

export default {
  name: 'home',
  components: {
    ATable,
  },
  data() {
    return {
      head: [
        'Rank',
        'Name',
        'Price',
        'Market Cap',
        'VWAP (24Hr)',
        'Supply',
        'Volume (24Hr)',
        'Change (24Hr)',
        'Trade',
      ],
      body: [],
    };
  },
  mounted() {
    setInterval(() => {
      axios.get('https://api.coincap.io/v2/assets', {
        crossdomain: true 
      })
        .then((response) => {
          const data = response.data.data.slice(0, 10);
          this.body = data;
        });
    }, 1000);
  },
};
</script>
