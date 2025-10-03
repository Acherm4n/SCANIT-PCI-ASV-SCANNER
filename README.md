<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PCI ASV SCANNER Infographic</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;900&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 320px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }
    </style>
</head>
<body class="bg-[#003f5c] text-white">

    <div class="container mx-auto p-4 md:p-8">

        <header class="text-center py-12">
            <div class="text-6xl md:text-8xl font-black tracking-tighter text-[#ffa600]">SCANIT!</div>
            <h1 class="text-3xl md:text-5xl font-bold mt-2">PCI ASV SCANNER</h1>
            <p class="text-xl mt-4 text-gray-300">by John Dominick Limpag</p>
            <p class="max-w-3xl mx-auto mt-6 text-lg text-gray-200">
                An automated Nmap wrapper for internal PCI DSS vulnerability assessments, designed to find high-risk misconfigurations before your official audit.
            </p>
        </header>

        <main>
            <section id="introduction" class="my-16">
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8 items-center">
                    <div class="md:col-span-1 text-center">
                        <div class="text-8xl font-extrabold text-[#ff6e54]">77%</div>
                        <p class="text-xl mt-2 text-gray-300">of organizations fail their interim PCI DSS compliance assessments.</p>
                    </div>
                    <div class="md:col-span-2 bg-[#444e86] p-8 rounded-2xl shadow-2xl">
                        <h2 class="text-2xl font-bold text-[#ffa600]">The Challenge of Continuous Compliance</h2>
                        <p class="mt-4 text-gray-200">
                            Maintaining PCI DSS compliance is a continuous effort, not a one-time audit. Internal networks are dynamic, and new vulnerabilities can emerge daily. This tool helps you proactively identify and remediate common issues related to weak encryption, insecure services, and unpatched software, forming a critical part of a robust security posture.
                        </p>
                    </div>
                </div>
            </section>
            
            <section id="process" class="my-16 text-center">
                 <h2 class="text-3xl font-bold mb-8">How It Works: The 3-Step Process</h2>
                 <div class="flex flex-col md:flex-row justify-center items-center gap-4 md:gap-0">
                    <div class="bg-[#955196] p-6 rounded-2xl shadow-xl w-full md:w-1/4">
                        <div class="text-4xl font-bold">1</div>
                        <h3 class="text-xl font-semibold mt-2">User Input</h3>
                        <p class="mt-2 text-gray-200">Provide a target IP or network range to scan.</p>
                    </div>
                    <div class="text-4xl font-bold text-[#dd5182] transform md:rotate-0 rotate-90">→</div>
                     <div class="bg-[#dd5182] p-6 rounded-2xl shadow-xl w-full md:w-1/4">
                        <div class="text-4xl font-bold">2</div>
                        <h3 class="text-xl font-semibold mt-2">Nmap Execution</h3>
                        <p class="mt-2 text-gray-200">The script runs a detailed Nmap scan with PCI-focused NSE scripts.</p>
                    </div>
                     <div class="text-4xl font-bold text-[#ff6e54] transform md:rotate-0 rotate-90">→</div>
                    <div class="bg-[#ff6e54] p-6 rounded-2xl shadow-xl w-full md:w-1/4">
                        <div class="text-4xl font-bold">3</div>
                        <h3 class="text-xl font-semibold mt-2">Report Generation</h3>
                        <p class="mt-2 text-gray-200">Results are saved in multiple formats (.nmap, .xml, .gnmap) for analysis.</p>
                    </div>
                 </div>
            </section>

            <section id="capabilities" class="my-16">
                <h2 class="text-3xl font-bold text-center mb-12">Core Scanning Capabilities</h2>
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    
                    <div class="bg-white/10 p-6 rounded-2xl backdrop-blur-sm shadow-xl">
                        <h3 class="text-xl font-bold text-[#ffa600]">SSL/TLS Configuration Weaknesses (PCI 4.1)</h3>
                        <p class="text-gray-300 mt-2 mb-4">Identifies outdated protocols and weak cipher suites that put cardholder data at risk during transmission.</p>
                        <div class="chart-container">
                            <canvas id="sslChart"></canvas>
                        </div>
                    </div>

                    <div class="bg-white/10 p-6 rounded-2xl backdrop-blur-sm shadow-xl">
                        <h3 class="text-xl font-bold text-[#ffa600]">Insecure HTTP Methods Enabled (PCI 6.5)</h3>
                        <p class="text-gray-300 mt-2 mb-4">Detects risky methods like TRACE, PUT, or DELETE on web servers, which can be leveraged in cross-site tracing attacks.</p>
                        <div class="chart-container">
                             <canvas id="methodsChart"></canvas>
                        </div>
                    </div>

                    <div class="bg-white/10 p-6 rounded-2xl backdrop-blur-sm shadow-xl">
                        <h3 class="text-xl font-bold text-[#ffa600]">Vulnerable Service Versions (PCI 6.1, 6.2)</h3>
                         <p class="text-gray-300 mt-2 mb-4">Highlights services running on outdated software with known vulnerabilities, a primary target for attackers.</p>
                        <div class="chart-container">
                             <canvas id="vulnChart"></canvas>
                        </div>
                    </div>

                    <div class="bg-white/10 p-6 rounded-2xl backdrop-blur-sm shadow-xl">
                        <h3 class="text-xl font-bold text-[#ffa600]">Security Header Adoption Rate</h3>
                        <p class="text-gray-300 mt-2 mb-4">Checks for the presence of crucial HTTP security headers that help protect against common web attacks.</p>
                        <div class="chart-container">
                            <canvas id="headersChart"></canvas>
                        </div>
                    </div>

                </div>
            </section>

            <section id="usage" class="my-16">
                <h2 class="text-3xl font-bold text-center mb-12">Getting Started</h2>
                <div class="bg-[#444e86] p-8 rounded-2xl shadow-2xl max-w-4xl mx-auto">
                    <h3 class="text-2xl font-bold text-[#ffa600]">Installation</h3>
                    <pre class="bg-black/50 text-white p-4 rounded-lg mt-4 overflow-x-auto"><code>git clone https://github.com/YourUsername/pci-asv-scanner
cd pci-asv-scanner
chmod +x pci-asv-scanner.sh</code></pre>

                    <h3 class="text-2xl font-bold mt-8 text-[#ffa600]">Example Usage</h3>
                    <pre class="bg-black/50 text-white p-4 rounded-lg mt-4 overflow-x-auto"><code># Scan top 1000 ports on a single host
sudo ./pci-asv-scanner.sh 192.168.1.5

# Scan specific ports on a network range
sudo ./pci-asv-scanner.sh 192.168.1.0/24 -p80,443,22

# Display help information
./pci-asv-scanner.sh -h</code></pre>
                </div>
            </section>
        </main>

        <footer class="text-center py-8 mt-12 border-t border-white/20">
            <p class="text-gray-400">Disclaimer: This tool is intended for internal, informational purposes and is not a substitute for a certified ASV scan.</p>
            <p class="text-gray-400 mt-2">PCI ASV SCANNER | Created by John Dominick Limpag</p>
        </footer>

    </div>

    <script>
        const tooltipCallback = {
            plugins: {
                tooltip: {
                    callbacks: {
                        title: function(tooltipItems) {
                            const item = tooltipItems[0];
                            let label = item.chart.data.labels[item.dataIndex];
                            if (Array.isArray(label)) {
                              return label.join(' ');
                            } else {
                              return label;
                            }
                        }
                    }
                }
            }
        };

        const chartColors = ['#955196', '#dd5182', '#ff6e54', '#ffa600', '#444e86'];

        function createSslChart() {
            const ctx = document.getElementById('sslChart').getContext('2d');
            new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['Weak Ciphers (TLS 1.0/1.1)', 'Outdated Protocol (SSLv3)', 'Secure Configuration'],
                    datasets: [{
                        label: 'SSL/TLS Scan Findings',
                        data: [25, 15, 60],
                        backgroundColor: chartColors,
                        borderColor: '#003f5c',
                        borderWidth: 4
                    }]
                },
                options: {
                    ...tooltipCallback,
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        ...tooltipCallback.plugins,
                        legend: {
                            position: 'bottom',
                            labels: {
                                color: 'white'
                            }
                        }
                    }
                }
            });
        }
        
        function createMethodsChart() {
            const ctx = document.getElementById('methodsChart').getContext('2d');
            new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: ['TRACE', 'PUT', 'DELETE', 'OPTIONS'],
                    datasets: [{
                        label: 'Insecure Methods Found',
                        data: [68, 22, 15, 85],
                        backgroundColor: chartColors,
                    }]
                },
                options: {
                    ...tooltipCallback,
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                             ticks: { color: 'white' },
                             grid: { color: 'rgba(255, 255, 255, 0.2)'}
                        },
                        x: {
                             ticks: { color: 'white' },
                             grid: { color: 'rgba(255, 255, 255, 0.2)'}
                        }
                    },
                    plugins: {
                        ...tooltipCallback.plugins,
                        legend: {
                           display: false
                        }
                    }
                }
            });
        }

        function createVulnChart() {
            const ctx = document.getElementById('vulnChart').getContext('2d');
            new Chart(ctx, {
                type: 'line',
                data: {
                    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
                    datasets: [{
                        label: 'Critical Vulnerabilities Found',
                        data: [5, 8, 6, 10, 7, 4],
                        fill: true,
                        backgroundColor: 'rgba(255, 110, 84, 0.3)',
                        borderColor: '#ff6e54',
                        tension: 0.3
                    }]
                },
                options: {
                     ...tooltipCallback,
                    responsive: true,
                    maintainAspectRatio: false,
                     scales: {
                        y: {
                             beginAtZero: true,
                             ticks: { color: 'white' },
                             grid: { color: 'rgba(255, 255, 255, 0.2)'}
                        },
                        x: {
                             ticks: { color: 'white' },
                             grid: { color: 'rgba(255, 255, 255, 0.2)'}
                        }
                    },
                    plugins: {
                        ...tooltipCallback.plugins,
                        legend: {
                           position: 'bottom',
                           labels: { color: 'white' }
                        }
                    }
                }
            });
        }

        function createHeadersChart() {
             const ctx = document.getElementById('headersChart').getContext('2d');
            new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: [['Strict-Transport-Security', '(HSTS)'], 'X-Frame-Options', 'X-Content-Type-Options', 'Content-Security-Policy'],
                    datasets: [{
                        label: '% of Scanned Hosts Implementing Header',
                        data: [45, 85, 92, 25],
                        backgroundColor: chartColors.slice().reverse(),
                    }]
                },
                options: {
                     ...tooltipCallback,
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                     scales: {
                        y: {
                             ticks: { color: 'white', font: { size: 14 } },
                             grid: { display: false }
                        },
                        x: {
                             ticks: { color: 'white' },
                             grid: { color: 'rgba(255, 255, 255, 0.2)'}
                        }
                    },
                    plugins: {
                        ...tooltipCallback.plugins,
                        legend: {
                           display: false
                        }
                    }
                }
            });
        }

        document.addEventListener('DOMContentLoaded', () => {
            createSslChart();
            createMethodsChart();
            createVulnChart();
            createHeadersChart();
        });
    </script>
</body>
</html>

