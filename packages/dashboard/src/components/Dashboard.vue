<template>
  <div id="app">
    <header class="header">
      <h1>Simple Vue Dashboard</h1>
    </header>
    <main class="dashboard">
      <section class="stats">
        <div class="card">
          <h2>Users</h2>
          <p>
            Number of users: <strong>{{ stats.users }}</strong>
          </p>
        </div>
        <div class="card">
          <h2>Sales</h2>
          <p>
            Total sales: <strong>{{ stats.sales }}</strong>
          </p>
        </div>
        <div class="card">
          <h2>Revenue</h2>
          <p>
            Total revenue: <strong>${{ stats.revenue }}</strong>
          </p>
        </div>
      </section>
      <section class="charts">
        <h2>Sales Data</h2>
        <Chart type="bar" :data="chartData" />
      </section>
      <section class="table">
        <h2>Recent Transactions</h2>
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>Customer</th>
              <th>Amount</th>
              <th>Date</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="transaction in transactions" :key="transaction.id">
              <td>{{ transaction.id }}</td>
              <td>{{ transaction.customer }}</td>
              <td>${{ transaction.amount }}</td>
              <td>{{ transaction.date }}</td>
            </tr>
          </tbody>
        </table>
      </section>
    </main>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import Chart from "primevue/chart";
//import "primevue/resources/themes/saga-blue/theme.css";
//import "primevue/resources/primevue.css";

export default defineComponent({
  components: {
    Chart,
  },
  data() {
    return {
      stats: {
        users: 120,
        sales: 45,
        revenue: 3200,
      },
      transactions: [
        { id: 1, customer: "John Doe", amount: 120, date: "2024-11-10" },
        { id: 2, customer: "Jane Smith", amount: 250, date: "2024-11-11" },
        { id: 3, customer: "Sam Wilson", amount: 180, date: "2024-11-12" },
      ],
      chartData: {
        labels: ["January", "February", "March", "April"],
        datasets: [
          {
            label: "Sales",
            data: [100, 200, 300, 400],
            backgroundColor: "#42A5F5",
          },
        ],
      },
    };
  },
});
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background: #f4f4f9;
}

.header {
  background: #2c3e50;
  color: white;
  text-align: center;
  padding: 1em 0;
}

.dashboard {
  padding: 1em;
}

.stats {
  display: flex;
  gap: 1em;
  margin-bottom: 2em;
}

.card {
  background: white;
  padding: 1em;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  flex: 1;
}

.charts,
.table {
  background: white;
  padding: 1em;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

table {
  width: 100%;
  border-collapse: collapse;
}

table th,
table td {
  border: 1px solid #ddd;
  padding: 0.5em;
}

table th {
  background: #f4f4f4;
}
</style>
