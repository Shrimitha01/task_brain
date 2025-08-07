# salesData.js 

const salesData = [
  { month: 'January', sales: 12000 },
  { month: 'February', sales: 15000 },
  { month: 'March', sales: 8000 },
  { month: 'April', sales: 17000 },
  { month: 'May', sales: 20000 },
  { month: 'June', sales: 22000 },
  { month: 'July', sales: 18000 },
  { month: 'August', sales: 24000 },
  { month: 'September', sales: 21000 },
  { month: 'October', sales: 23000 },
  { month: 'November', sales: 25000 },
  { month: 'December', sales: 30000 },
];

export default salesData;


#SalesChart.js
import React from 'react';
import { Bar } from 'react-chartjs-2';
import { Chart as ChartJS, BarElement, CategoryScale, LinearScale, Tooltip, Legend } from 'chart.js';
import salesData from '../data/salesData';

ChartJS.register(BarElement, CategoryScale, LinearScale, Tooltip, Legend);

const SalesChart = () => {
  const data = {
    labels: salesData.map(item => item.month),
    datasets: [
      {
        label: 'Monthly Sales (₹)',
        data: salesData.map(item => item.sales),
        backgroundColor: 'rgba(75, 192, 192, 0.6)',
        borderColor: 'black',
        borderWidth: 1,
      },
    ],
  };

  const options = {
    responsive: true,
    scales: {
      y: {
        beginAtZero: true,
      },
    },
  };

  return (
    <div style={{ width: '80%', margin: 'auto' }}>
      <h2>Sales Data Analysis - 2025</h2>
      <Bar data={data} options={options} />
    </div>
  );
};

export default SalesChart;


#App.js

import React from 'react';
import './App.css';
import SalesChart from './components/SalesChart';

function App() {
  return (
    <div className="App">
      <SalesChart />
    </div>
  );
}

export default App;


