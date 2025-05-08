<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Pharmacogenomic Profile</title>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f9fafb;
      color: #333;
      margin: 0;
    }

    header {
      background: #2c3e50;
      color: white;
      padding: 1rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    header h1 {
      font-size: 1.4rem;
    }

    nav a {
      color: white;
      margin-left: 1rem;
      text-decoration: none;
    }

    .container {
      padding: 2rem;
      display: flex;
      flex-direction: column;
      gap: 2rem;
    }

    .row {
      display: flex;
      gap: 2rem;
      flex-wrap: wrap;
      justify-content: space-between;
    }

    .column {
      display: flex;
      flex-direction: column;
      gap: 2rem;
      flex: 0 0 48%;
    }

    .card {
      background: white;
      padding: 1.5rem;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    .card:hover {
      transform: translateY(-3px);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
    }

    .card-full {
      width: 100%;
    }

    canvas {
      width: 100% !important;
      height: auto !important;
    }

    .highlight {
      font-weight: bold;
      color: #2c3e50;
    }

    .patient-name {
      font-size: 1.6rem;
      font-weight: bold;
      color: #2c3e50;
      margin-bottom: 1rem;
    }

    table {
      width: 100%;
      margin-bottom: 1rem;
      border-collapse: collapse;
    }

    td {
      padding: 0.5rem;
      font-weight: bold;
      text-align: center;
    }

    footer {
      text-align: center;
      padding: 1rem;
      background: #ecf0f1;
      font-size: 0.9rem;
      color: #666;
    }

    /* Responsive Enhancements */
    @media (max-width: 768px) {
      .row {
        flex-direction: column;
      }

      .card {
        margin-bottom: 1.5rem;
      }

      header h1 {
        font-size: 1.1rem;
      }

      nav a {
        font-size: 0.9rem;
        margin-left: 0.5rem;
      }
    }

    .container > .row:last-of-type {
      margin-bottom: 2rem;
    }
  </style>
</head>
<body>
  <header>
    <h1>Genomic Profile</h1>
    <nav>
      <a href="#patient">Patient Info</a>
      <a href="#charts">Genomic Data</a>
    </nav>
  </header>

  <div class="container">
    <!-- First Row: Patient Info -->
    <div class="row">
      <div class="card card-full" id="patient">
        <div class="patient-name">Mr. Ginkgo Biloba, 65/M</div>
        <table>
          <tr>
            <td>Height: 172 cm</td>
            <td>Weight: 84 kg</td>
            <td>BMI: 28.4</td>
          </tr>
        </table>
        <p><span class="highlight">Clinical Context:</span> Post-op left temporal meningioma.</p>
        <p>Patient has mild cognitive impairment and type 2 diabetes mellitus. He lives alone, struggles with adherence to treatment, and has a history of alcohol use.</p>
      </div>
    </div>

    <!-- Second Row: Genomic Charts (2 charts per column) -->
    <div class="row">
      <div class="column">
        <div class="card">
          <h2>Genomic Profile Curve</h2>
          <canvas id="genomicChart">Your browser does not support the canvas element.</canvas>
        </div>
        <div class="card">
          <h2>Genomic Markers (Top 12)</h2>
          <canvas id="chart1">Your browser does not support the canvas element.</canvas>
        </div>
      </div>
      <div class="column">
        <div class="card">
          <h2>Medication Categories</h2>
          <canvas id="chart2">Your browser does not support the canvas element.</canvas>
        </div>
        <div class="card">
          <h2>CYP2C19 Metabolizer Status</h2>
          <canvas id="chart3">Your browser does not support the canvas element.</canvas>
        </div>
      </div>
    </div>

    <!-- Third Row: Digital Health Record -->
    <div class="row">
      <div class="card card-full">
        <h2>Digital Health Record</h2>
        <p>This patient’s digital health record includes pharmacogenomic results showing sensitivity to warfarin due to the <strong>VKORC1 variant</strong> and reduced metabolism due to <strong>CYP2C9*3 polymorphism</strong>. These results automatically inform prescription adjustments, such as initiating warfarin at a lower dose and monitoring INR closely. Digital alerts are configured to prevent CYP2C9-metabolized drug overdosing.</p>
      </div>
    </div>
  </div>

  <footer>
    &copy; 2025 NeuroCloud™ | Blockchain Verified RX ID: RX-NEURO-2055-0042-A
  </footer>

  <script>
    new Chart(document.getElementById('genomicChart'), {
      type: 'line',
      data: {
        labels: ["VKORC1", "CYP2C9*3"],
        datasets: [{
          label: "Genomic Sensitivity",
          data: [90, 60],
          borderColor: "#3498db",
          fill: false,
          tension: 0.4
        }]
      },
      options: {
        responsive: true,
        plugins: {
          title: {
            display: true,
            text: 'Genomic Sensitivity Curve'
          }
        },
        scales: {
          y: {
            beginAtZero: true,
            max: 100
          }
        }
      }
    });

    new Chart(document.getElementById('chart1'), {
      type: 'bar',
      data: {
        labels: ["CYP3A5","VKORC1","CYP2C19","G6PD","NAT2","SLCO1B1","CYP2D6","UGT1A1","CYP2B6","TPMT","CYP2C9","CFTR"],
        datasets: [{
          label: "# of Patients with Functional Variants",
          data: [50, 38, 35, 28, 22, 20, 18, 17, 13, 6, 4, 2],
          backgroundColor: '#8e44ad'
        }]
      },
      options: {
        responsive: true,
        plugins: {
          legend: { display: false },
          title: { display: true, text: 'Pharmacogene Distribution' }
        }
      }
    });

    new Chart(document.getElementById('chart2'), {
      type: 'bar',
      data: {
        labels: ["Gastrointestinal","CNS","Respiratory","Cardiovascular","Anti-infective","Endocrine","Renal","Other","Immune","Anti-inflammatory"],
        datasets: [{
          label: "Rx Prescriptions",
          data: [470, 400, 310, 160, 110, 90, 60, 45, 30, 22],
          backgroundColor: '#2ecc71'
        }]
      },
      options: {
        responsive: true,
        plugins: {
          legend: { display: false },
          title: { display: true, text: 'Rx Category Distribution' }
        }
      }
    });

    new Chart(document.getElementById('chart3'), {
      type: 'bar',
      data: {
        labels: ["Normal","Intermediate","Rapid","Ultra rapid","Poor"],
        datasets: [{
          label: "Metabolizer Count",
          data: [15, 12, 10, 7, 6],
          backgroundColor: '#e67e22'
        }]
      },
      options: {
        responsive: true,
        plugins: {
          legend: { display: false },
          title: { display: true, text: 'CYP2C19 Metabolizer Status' }
        }
      }
    });
  </script>
</body>
</html>
