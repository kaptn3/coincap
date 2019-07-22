<template>
  <div>
    <table>
      <thead>
        <tr>
          <th
            v-for="item in head"
            :key="item"
          >
            {{ item }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="tr in body"
          :key="tr.rank"
        >
          <td>{{ tr.rank }}</td>
          <td>{{ tr.name }}</td>
          <td>{{ round(tr.priceUsd) }}</td>
          <td>{{ round(tr.marketCapUsd) }}</td>
          <td>{{ round(tr.vwap24Hr) }}</td>
          <td>{{ round(tr.supply) }}</td>
          <td>{{ round(tr.volumeUsd24Hr) }}</td>
          <td>{{ round(tr.changePercent24Hr) }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    name: 'Table',
    props: {
      head: {
        type: Array,
        requires: true
      },
      body: {
        type: Array,
        requires: true
      }
    },
    methods: {
      round(value) {
        return parseFloat(value).toFixed(2);
      }
    }
  };
</script>
