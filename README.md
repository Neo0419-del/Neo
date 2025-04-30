<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2025 Election Results</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            background-color: #f5f5f5;
        }
        
        h1 {
            color: #333;
            margin-bottom: 30px;
        }
        
        .chart-container {
            position: relative;
            width: 400px;
            height: 400px;
            margin-bottom: 30px;
        }
        
        #electionPieChart {
            width: 100%;
            height: 100%;
        }
        
        .legend {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
            margin-top: 20px;
        }
        
        .legend-item {
            display: flex;
            align-items: center;
            margin: 5px;
        }
        
        .legend-color {
            width: 20px;
            height: 20px;
            margin-right: 8px;
            border-radius: 3px;
        }
        
        .results-table {
            margin-top: 30px;
            border-collapse: collapse;
            width: 80%;
            max-width: 500px;
            background-color: white;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .results-table th, .results-table td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        
        .results-table th {
            background-color: #4a4a4a;
            color: white;
        }
        
        .results-table tr:hover {
            background-color: #f1f1f1;
        }
    </style>
</head>
<body>
    <h1>2025 Election Results</h1>
    
    <div class="chart-container">
        <canvas id="electionPieChart"></canvas>
    </div>
    
    <div class="legend">
        <div class="legend-item">
            <div class="legend-color" style="background-color: #4285F4;"></div>
            <span>DAD (45%)</span>
        </div>
        <div class="legend-item">
            <div class="legend-color" style="background-color: #EA4335;"></div>
            <span>PPP (5%)</span>
        </div>
        <div class="legend-item">
            <div class="legend-color" style="background-color: #FBBC05;"></div>
            <span>CCCC (27%)</span>
        </div>
        <div class="legend-item">
            <div class="legend-color" style="background-color: #34A853;"></div>
            <span>MCD (23%)</span>
        </div>
    </div>
    
    <table class="results-table">
        <thead>
            <tr>
                <th>Party</th>
                <th>Vote Share</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>DAD</td>
                <td>45%</td>
            </tr>
            <tr>
                <td>CCCC</td>
                <td>27%</td>
            </tr>
            <tr>
                <td>MCD</td>
                <td>23%</td>
            </tr>
            <tr>
                <td>PPP</td>
                <td>5%</td>
            </tr>
        </tbody>
    </table>

    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const ctx = document.getElementById('electionPieChart').getContext('2d');
            
            const electionData = {
                labels: ['DAD', 'PPP', 'CCCC', 'MCD'],
                datasets: [{
                    data: [45, 5, 27, 23],
                    backgroundColor: [
                        '#4285F4', // DAD - Blue
                        '#EA4335', // PPP - Red
                        '#FBBC05', // CCCC - Yellow
                        '#34A853'  // MCD - Green
                    ],
                    borderColor: '#fff',
                    borderWidth: 2
                }]
            };
            
            const config = {
                type: 'pie',
                data: electionData,
                options: {
                    responsive: true,
                    plugins: {
                        legend: {
                            display: false // We're using our custom legend
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return `${context.label}: ${context.raw}%`;
                                }
                            }
                        }
                    },
                    animation: {
                        animateScale: true,
                        animateRotate: true
                    }
                }
            };
            
            new Chart(ctx, config);
        });
    </script>
</body>
</html>
