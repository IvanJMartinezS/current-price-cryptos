<template>
  <table>
    <thead>
      <tr class="bg-gray-100 border-b-2 border-gray-400">
        <th>Icon</th>
        <th>
          <span>Ranking</span>
        </th>
        <th>Name</th>
        <th>Price</th>
        <th>Market Cap</th>
        <th>Chg 24hs</th>
        <td class="hidden sm:block"></td>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="a in assets"
        :key="a.id"
        class="border-b border-gray-200 hover:bg-gray-100 hover:bg-orange-100"
      >
        <td>
          <img
            :src="
              `https://static.coincap.io/assets/icons/${a.symbol.toLowerCase()}@2x.png`
            "
            :alt="a.name"
          />
        </td>
        <td>
          <b>#{{ a.rank }}</b>
        </td>
        <td>{{ a.name }}</td>
        <td>{{ a.priceUsd | dollar }}</td>
        <td>{{ a.marketCapUsd | dollar }}</td>
        <td>{{ a.changePercent24Hr | percent }}</td>
        <td class="hidden sm:block"></td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "Data",
  props: {
    assets: {
      type: Array,
      default: () => []
    }
  }
};
</script>

<style scoped>
.up::before {
  content: "👆";
}
.down::before {
  content: "👇";
}
td {
  padding: 20px 0px;
  font-size: 0.6rem;
  text-align: center;
}
th {
  padding: 5px;
  font-size: 0.6rem;
}
@media (min-width: 640px) {
  td,
  th {
    padding: 20px;
    font-size: 1rem;
  }
  th {
    padding: 12px;
  }
}

img {
  width: 64px;
  height: 64px;
}
</style>