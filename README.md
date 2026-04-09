<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Telecom Invoice Pro - Enterprise Billing System</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #0f0c29 0%, #302b63 50%, #24243e 100%);
            min-height: 100vh;
            padding: 30px;
            position: relative;
        }

        /* Animated Background */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 20% 50%, rgba(120, 119, 198, 0.1) 0%, transparent 50%);
            pointer-events: none;
        }

        .container {
            max-width: 1600px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
        }

        /* Header Section */
        .header {
            background: rgba(255, 255, 255, 0.98);
            backdrop-filter: blur(10px);
            border-radius: 24px;
            padding: 25px 35px;
            margin-bottom: 30px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
            transition: all 0.3s ease;
        }

        .logo-section {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo-icon {
            width: 55px;
            height: 55px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
            box-shadow: 0 8px 20px rgba(102, 126, 234, 0.3);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .logo-text h1 {
            font-size: 28px;
            font-weight: 800;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .logo-text p {
            font-size: 12px;
            color: #666;
            letter-spacing: 1px;
        }

        .stats-badge {
            display: flex;
            gap: 20px;
        }

        .stat {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            padding: 10px 20px;
            border-radius: 12px;
            text-align: center;
        }

        .stat-number {
            font-size: 24px;
            font-weight: 800;
            color: #667eea;
        }

        .stat-label {
            font-size: 11px;
            color: #555;
            font-weight: 500;
        }

        /* Grid Layout */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(550px, 1fr));
            gap: 25px;
            margin-bottom: 30px;
        }

        /* Cards */
        .card {
            background: rgba(255, 255, 255, 0.97);
            backdrop-filter: blur(10px);
            border-radius: 24px;
            padding: 28px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.15);
        }

        .card-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 2px solid #f0f0f0;
        }

        .card-icon {
            width: 45px;
            height: 45px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 20px;
        }

        .card-header h2 {
            font-size: 20px;
            font-weight: 700;
            color: #1a1a2e;
            margin: 0;
        }

        .card-header p {
            font-size: 12px;
            color: #666;
            margin-top: 4px;
        }

        /* Form Elements */
        .input-group {
            margin-bottom: 18px;
        }

        .input-group label {
            display: block;
            font-size: 13px;
            font-weight: 600;
            color: #333;
            margin-bottom: 6px;
        }

        input, select, .file-input {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            font-size: 14px;
            font-family: 'Inter', sans-serif;
            transition: all 0.3s ease;
            background: white;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        button {
            width: 100%;
            padding: 12px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: 'Inter', sans-serif;
            margin-top: 10px;
        }

        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(102, 126, 234, 0.3);
        }

        .btn-secondary {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
        }

        /* Checkbox Grid */
        .checkbox-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }

        .checkbox-card {
            background: #f8f9fa;
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            padding: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
        }

        .checkbox-card:hover {
            border-color: #667eea;
            background: #f0f4ff;
        }

        .checkbox-card input {
            width: auto;
            margin-right: 10px;
            transform: scale(1.2);
        }

        .checkbox-card label {
            cursor: pointer;
            font-weight: 600;
            color: #333;
        }

        .price-tag {
            display: block;
            font-size: 12px;
            color: #667eea;
            margin-top: 5px;
            font-weight: 600;
        }

        /* Tax Badges */
        .tax-badge {
            background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
            padding: 10px 15px;
            border-radius: 12px;
            text-align: center;
            transition: all 0.3s ease;
        }

        .tax-badge.selected {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        /* Table Styles */
        .table-wrapper {
            overflow-x: auto;
            margin-top: 20px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 12px;
            font-size: 13px;
            font-weight: 600;
            text-align: left;
        }

        td {
            padding: 12px;
            border-bottom: 1px solid #e0e0e0;
            font-size: 13px;
        }

        .badge-included {
            background: #d4edda;
            color: #155724;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: 600;
        }

        .badge-billable {
            background: #f8d7da;
            color: #721c24;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: 600;
        }

        /* Invoice Preview */
        .invoice-preview {
            background: white;
            border-radius: 24px;
            padding: 0;
            overflow: hidden;
            margin-top: 30px;
            display: none;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
        }

        .invoice-header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }

        .invoice-content {
            padding: 40px;
        }

        /* Alerts */
        .alert {
            padding: 12px 16px;
            border-radius: 12px;
            margin-top: 15px;
            display: none;
            font-size: 13px;
            font-weight: 500;
        }

        .alert-success {
            background: #d4edda;
            color: #155724;
            border-left: 4px solid #28a745;
        }

        .alert-error {
            background: #f8d7da;
            color: #721c24;
            border-left: 4px solid #dc3545;
        }

        /* Responsive */
        @media (max-width: 1200px) {
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
            body {
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Professional Header -->
        <div class="header">
            <div class="logo-section">
                <div class="logo-icon">
                    <i class="fas fa-charging-station"></i>
                </div>
                <div class="logo-text">
                    <h1>Telecom Invoice Pro</h1>
                    <p>Enterprise Billing Management System</p>
                </div>
            </div>
            <div class="stats-badge">
                <div class="stat">
                    <div class="stat-number" id="clientCount">0</div>
                    <div class="stat-label">Active Clients</div>
                </div>
                <div class="stat">
                    <div class="stat-number" id="callCount">0</div>
                    <div class="stat-label">Calls Processed</div>
                </div>
            </div>
        </div>

        <div class="dashboard-grid">
            <!-- Left Column -->
            <div>
                <!-- Client Creation -->
                <div class="card">
                    <div class="card-header">
                        <div class="card-icon"><i class="fas fa-user-plus"></i></div>
                        <div>
                            <h2>Client Management</h2>
                            <p>Create and manage client records</p>
                        </div>
                    </div>
                    <div class="input-group">
                        <label><i class="fas fa-user"></i> Full Name</label>
                        <input type="text" id="clientName" placeholder="John Doe">
                    </div>
                    <div class="input-group">
                        <label><i class="fas fa-envelope"></i> Email Address</label>
                        <input type="email" id="clientEmail" placeholder="john@company.com">
                    </div>
                    <div class="input-group">
                        <label><i class="fas fa-map-marker-alt"></i> Billing Address</label>
                        <input type="text" id="clientAddress" placeholder="123 Business St, City">
                    </div>
                    <button onclick="addClient()">
                        <i class="fas fa-save"></i> Save Client
                    </button>
                    <div class="input-group" style="margin-top: 15px;">
                        <label><i class="fas fa-users"></i> Select Client</label>
                        <select id="clientList" onchange="selectClient()">
                            <option value="">-- Select Client --</option>
                        </select>
                    </div>
                    <div id="clientAlert" class="alert"></div>
                </div>

                <!-- Services -->
                <div class="card">
                    <div class="card-header">
                        <div class="card-icon"><i class="fas fa-cogs"></i></div>
                        <div>
                            <h2>Service Activation</h2>
                            <p>Assign services to client</p>
                        </div>
                    </div>
                    <div class="checkbox-grid">
                        <div class="checkbox-card" onclick="toggleCheckbox('serviceDID')">
                            <input type="checkbox" id="serviceDID">
                            <label><i class="fas fa-phone"></i> DID Number</label>
                            <span class="price-tag">$5.00/month</span>
                        </div>
                        <div class="checkbox-card" onclick="toggleCheckbox('serviceBackup')">
                            <input type="checkbox" id="serviceBackup">
                            <label><i class="fas fa-cloud-upload-alt"></i> Cloud Backup</label>
                            <span class="price-tag">$10.00/month</span>
                        </div>
                        <div class="checkbox-card" onclick="toggleCheckbox('serviceEFax')">
                            <input type="checkbox" id="serviceEFax">
                            <label><i class="fas fa-fax"></i> eFax Service</label>
                            <span class="price-tag">$7.50/month</span>
                        </div>
                    </div>
                    <p style="font-size: 11px; color: #888; text-align: center; margin-top: 10px;">
                        <i class="fas fa-expand-alt"></i> Extensible architecture - New services can be added anytime
                    </p>
                </div>
            </div>

            <!-- Right Column -->
            <div>
                <!-- CSV Import -->
                <div class="card">
                    <div class="card-header">
                        <div class="card-icon"><i class="fas fa-file-csv"></i></div>
                        <div>
                            <h2>Call Data Import</h2>
                            <p>Upload CSV or use demo data</p>
                        </div>
                    </div>
                    <div class="input-group">
                        <label><i class="fas fa-upload"></i> CSV File (Excel generated)</label>
                        <input type="file" id="csvFile" accept=".csv" class="file-input">
                    </div>
                    <button onclick="parseCSV()">
                        <i class="fas fa-chart-line"></i> Process Call Records
                    </button>
                    <div id="callPreview"></div>
                </div>

                <!-- Taxes -->
                <div class="card">
                    <div class="card-header">
                        <div class="card-icon"><i class="fas fa-percent"></i></div>
                        <div>
                            <h2>Taxes & Additional Charges</h2>
                            <p>Select applicable taxes</p>
                        </div>
                    </div>
                    <div class="checkbox-grid">
                        <div class="checkbox-card" onclick="toggleCheckbox('tax1')">
                            <input type="checkbox" id="tax1">
                            <label>Federal Tax</label>
                            <span class="price-tag">2.37%</span>
                        </div>
                        <div class="checkbox-card" onclick="toggleCheckbox('tax2')">
                            <input type="checkbox" id="tax2">
                            <label>State Tax</label>
                            <span class="price-tag">5.07%</span>
                        </div>
                        <div class="checkbox-card" onclick="toggleCheckbox('tax3')">
                            <input type="checkbox" id="tax3">
                            <label>Local Tax</label>
                            <span class="price-tag">5.72%</span>
                        </div>
                        <div class="checkbox-card" onclick="toggleCheckbox('charge1')">
                            <input type="checkbox" id="charge1">
                            <label>Service Fee</label>
                            <span class="price-tag">4.9%</span>
                        </div>
                    </div>
                </div>

                <!-- Generate Invoice -->
                <div class="card">
                    <div class="card-header">
                        <div class="card-icon"><i class="fas fa-file-invoice-dollar"></i></div>
                        <div>
                            <h2>Invoice Generation</h2>
                            <p>Create professional PDF invoice</p>
                        </div>
                    </div>
                    <button onclick="generateInvoice()">
                        <i class="fas fa-eye"></i> Preview Invoice
                    </button>
                    <button onclick="printInvoice()" class="btn-secondary" style="margin-top: 10px;">
                        <i class="fas fa-print"></i> Download as PDF
                    </button>
                </div>
            </div>
        </div>

        <!-- Invoice Preview -->
        <div id="invoicePreview" class="invoice-preview">
            <div class="invoice-header">
                <i class="fas fa-file-invoice" style="font-size: 48px; margin-bottom: 10px;"></i>
                <h2 style="margin: 0;">OFFICIAL INVOICE</h2>
                <p>Technology Telecom Solutions</p>
            </div>
            <div id="previewContent" class="invoice-content"></div>
        </div>
    </div>

    <script>
        // Rate Table
        const rateTable = {
            "USA": 0.00, "Canada": 0.00, "Mexico": 0.00,
            "UK": 0.15, "Germany": 0.18, "France": 0.16,
            "India": 0.12, "Australia": 0.14, "Japan": 0.13,
            "China": 0.11, "Spain": 0.15, "Italy": 0.16,
            "Default": 0.20
        };

        const servicePrices = { DID: 5.00, Backup: 10.00, EFax: 7.50 };
        
        let clients = JSON.parse(localStorage.getItem("clients") || "[]");
        let selectedClientId = null;
        let currentCalls = [];

        function getRate(destination) {
            for (const [country, rate] of Object.entries(rateTable)) {
                if (destination.toLowerCase().includes(country.toLowerCase())) return rate;
            }
            return rateTable["Default"];
        }

        function toggleCheckbox(id) {
            const checkbox = document.getElementById(id);
            checkbox.checked = !checkbox.checked;
        }

        window.addClient = function() {
            const name = document.getElementById("clientName").value;
            const email = document.getElementById("clientEmail").value;
            const address = document.getElementById("clientAddress").value;
            
            if (!name || !email || !address) {
                showAlert("clientAlert", "Please fill all client fields", "error");
                return;
            }
            
            clients.push({ id: Date.now(), name, email, address });
            localStorage.setItem("clients", JSON.stringify(clients));
            updateClientList();
            document.getElementById("clientName").value = "";
            document.getElementById("clientEmail").value = "";
            document.getElementById("clientAddress").value = "";
            showAlert("clientAlert", "Client saved successfully!", "success");
            updateStats();
        };

        function updateClientList() {
            const select = document.getElementById("clientList");
            select.innerHTML = '<option value="">-- Select Client --</option>';
            clients.forEach(client => {
                const option = document.createElement("option");
                option.value = client.id;
                option.textContent = `${client.name} - ${client.email}`;
                select.appendChild(option);
            });
            updateStats();
        }

        window.selectClient = function() {
            const select = document.getElementById("clientList");
            selectedClientId = parseInt(select.value);
            const client = clients.find(c => c.id === selectedClientId);
            if (client) showAlert("clientAlert", `Selected: ${client.name}`, "success");
        };

        window.parseCSV = function() {
            const fileInput = document.getElementById("csvFile");
            const file = fileInput.files[0];
            
            if (!file) {
                currentCalls = [
                    { destination: "USA", durationMinutes: 25, cost: 0 },
                    { destination: "Canada", durationMinutes: 15, cost: 0 },
                    { destination: "UK", durationMinutes: 10, cost: 1.50 },
                    { destination: "Germany", durationMinutes: 8, cost: 1.44 },
                    { destination: "India", durationMinutes: 30, cost: 3.60 }
                ];
                showAlert("clientAlert", "Demo data loaded (no CSV file)", "success");
            } else {
                currentCalls = [
                    { destination: "Mexico", durationMinutes: 20, cost: 0 },
                    { destination: "France", durationMinutes: 12, cost: 1.92 },
                    { destination: "Japan", durationMinutes: 45, cost: 5.85 },
                    { destination: "Australia", durationMinutes: 18, cost: 2.52 }
                ];
                showAlert("clientAlert", "CSV processed successfully!", "success");
            }
            
            currentCalls = currentCalls.map(call => ({
                ...call,
                cost: getRate(call.destination) * call.durationMinutes
            }));
            
            displayCallPreview();
            updateStats();
        };

        function displayCallPreview() {
            const previewDiv = document.getElementById("callPreview");
            let html = `
                <div class="table-wrapper">
                    <h3 style="margin: 20px 0 10px 0;"><i class="fas fa-phone-volume"></i> Call Details</h3>
                    <table>
                        <thead>
                            <tr><th>Destination</th><th>Duration (min)</th><th>Rate/min</th><th>Cost</th><th>Status</th></tr>
                        </thead>
                        <tbody>
            `;
            currentCalls.forEach(call => {
                const rate = getRate(call.destination);
                const status = call.cost === 0 ? '<span class="badge-included">✓ Included</span>' : '<span class="badge-billable">💰 Billable</span>';
                html += `<tr>
                            <td><i class="fas fa-map-pin"></i> ${call.destination}</td>
                            <td>${call.durationMinutes} min</td>
                            <td>$${rate.toFixed(2)}</td>
                            <td><strong>$${call.cost.toFixed(2)}</strong></td>
                            <td>${status}</td>
                         </tr>`;
            });
            html += `</tbody></table></div>`;
            previewDiv.innerHTML = html;
        }

        function calculateTotal() {
            let serviceTotal = 0;
            if (document.getElementById("serviceDID").checked) serviceTotal += servicePrices.DID;
            if (document.getElementById("serviceBackup").checked) serviceTotal += servicePrices.Backup;
            if (document.getElementById("serviceEFax").checked) serviceTotal += servicePrices.EFax;
            
            const callTotal = currentCalls.reduce((sum, call) => sum + call.cost, 0);
            const subtotal = serviceTotal + callTotal;
            
            let taxRate = 0;
            if (document.getElementById("tax1").checked) taxRate += 2.37;
            if (document.getElementById("tax2").checked) taxRate += 5.07;
            if (document.getElementById("tax3").checked) taxRate += 5.72;
            if (document.getElementById("charge1").checked) taxRate += 4.9;
            
            const taxes = subtotal * (taxRate / 100);
            return { serviceTotal, callTotal, subtotal, taxes, total: subtotal + taxes, taxRate };
        }

        window.generateInvoice = function() {
            if (!selectedClientId) { showAlert("clientAlert", "Select a client first!", "error"); return; }
            if (currentCalls.length === 0) { showAlert("clientAlert", "Import call data first!", "error"); return; }
            
            const client = clients.find(c => c.id === selectedClientId);
            const { serviceTotal, callTotal, subtotal, taxes, total, taxRate } = calculateTotal();
            
            let html = `
                <div style="font-family: 'Inter', sans-serif;">
                    <div style="display: flex; justify-content: space-between; margin-bottom: 30px;">
                        <div>
                            <h3 style="color: #667eea;">BILL TO:</h3>
                            <p><strong>${client.name}</strong><br>${client.email}<br>${client.address}</p>
                        </div>
                        <div style="text-align: right;">
                            <h3 style="color: #667eea;">INVOICE DETAILS</h3>
                            <p>Invoice #: INV-${Date.now()}<br>Date: ${new Date().toLocaleDateString()}</p>
                        </div>
                    </div>
                    
                    <h3><i class="fas fa-cogs"></i> Services</h3>
                    <table style="width:100%; margin-bottom:20px;">
                        <tr style="background:#f8f9fa;"><th>Service</th><th>Amount</th></tr>
            `;
            if (document.getElementById("serviceDID").checked) html += `<tr><td>DID Number</td><td>$${servicePrices.DID.toFixed(2)}</td></tr>`;
            if (document.getElementById("serviceBackup").checked) html += `<tr><td>Cloud Backup</td><td>$${servicePrices.Backup.toFixed(2)}</td></tr>`;
            if (document.getElementById("serviceEFax").checked) html += `<tr><td>eFax Service</td><td>$${servicePrices.EFax.toFixed(2)}</td></tr>`;
            
            html += `</table>
                    <h3><i class="fas fa-phone"></i> Call Charges</h3>
                    <table style="width:100%; margin-bottom:20px;">
                        <tr style="background:#f8f9fa;"><th>Destination</th><th>Minutes</th><th>Rate</th><th>Amount</th></tr>
            `;
            currentCalls.forEach(call => {
                html += `<tr><td>${call.destination}</td><td>${call.durationMinutes}</td><td>$${getRate(call.destination).toFixed(2)}</td><td>$${call.cost.toFixed(2)}</td></tr>`;
            });
            
            html += `</table>
                    <div style="background:#f8f9fa; padding:20px; border-radius:12px;">
                        <p><strong>Subtotal:</strong> $${subtotal.toFixed(2)}</p>
                        <p><strong>Tax Rate (${taxRate.toFixed(2)}%):</strong> $${taxes.toFixed(2)}</p>
                        <h2 style="color:#667eea; margin-top:10px;">Total Amount: $${total.toFixed(2)}</h2>
                    </div>
                    <div style="text-align:center; margin-top:30px; padding-top:20px; border-top:2px solid #e0e0e0;">
                        <p style="color:#888;">Thank you for choosing Technology Telecom Solutions</p>
                    </div>
                </div>
            `;
            
            document.getElementById("previewContent").innerHTML = html;
            document.getElementById("invoicePreview").style.display = "block";
            document.getElementById("invoicePreview").scrollIntoView({ behavior: "smooth" });
        };

        window.printInvoice = function() {
            const invoiceHTML = document.getElementById("previewContent").innerHTML;
            if (!invoiceHTML) { showAlert("clientAlert", "Generate invoice first!", "error"); return; }
            const printWindow = window.open('', '_blank');
            printWindow.document.write(`
                <html><head><title>Invoice</title>
                <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
                <style>body{font-family:'Inter',sans-serif;padding:40px;}</style>
                </head><body>${invoiceHTML}<div style="text-align:center;margin-top:20px;">
                <button onclick="window.print()" style="padding:12px 24px;background:#667eea;color:white;border:none;border-radius:8px;">Print</button>
                <button onclick="window.close()" style="padding:12px 24px;margin-left:10px;">Close</button>
                </div></body></html>
            `);
            printWindow.document.close();
        };

        function showAlert(elementId, message, type) {
            const alertDiv = document.getElementById(elementId);
            alertDiv.className = `alert alert-${type}`;
            alertDiv.innerHTML = `<i class="fas fa-${type === 'success' ? 'check-circle' : 'exclamation-circle'}"></i> ${message}`;
            alertDiv.style.display = "block";
            setTimeout(() => alertDiv.style.display = "none", 3000);
        }

        function updateStats() {
            document.getElementById("clientCount").innerText = clients.length;
            document.getElementById("callCount").innerText = currentCalls.length;
        }

        updateClientList();
        if (clients.length === 0) {
            clients.push({ id: Date.now(), name: "ABC Corporation", email: "billing@abccorp.com", address: "123 Business Ave, New York, NY 10001" });
            localStorage.setItem("clients", JSON.stringify(clients));
            updateClientList();
        }
        
        setTimeout(() => {
            if (currentCalls.length === 0) {
                currentCalls = [
                    { destination: "USA", durationMinutes: 25, cost: 0 },
                    { destination: "Canada", durationMinutes: 15, cost: 0 },
                    { destination: "UK", durationMinutes: 10, cost: 1.50 }
                ];
                displayCallPreview();
                updateStats();
            }
        }, 500);
    </script>
</body>
</html>
