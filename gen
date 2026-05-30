
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tickets</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- PWA MANIFEST LINK ADDED HERE -->
    <link rel="manifest" href="manifest.json">
    <!-- Set theme color for Android status bar -->
    <meta name="theme-color" content="#10B981"/> 

    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f4f8;
            transition: all 0.3s ease-in-out;
        }
        
        .collapsible-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            padding: 12px 0;
            border-bottom: 1px solid #f3f4f6;
        }

        /* --- Custom Colors --- */
        .header-green {
            background-color: #10B981; /* Vibrant Header Green */
        }
        .decorative-strip {
            background-color: #2F996B; /* Darker Strip Green */
            position: relative;
            z-index: 30;
            color: white;
            text-align: center;
            padding: 1rem;
        }
        
        /* --- NEW TICKET TEAR LINE GRAPHIC --- */
        /* This creates the perforated line with white triangular cutouts */
        .ticket-tear-graphic {
            height: 10px;
            background: 
                /* Pattern 1: White triangles pointing down from the top edge */
                linear-gradient(135deg, white 50%, transparent 50%) 0 0,
                linear-gradient(45deg, white 50%, transparent 50%) 10px 0;
            
            background-size: 20px 10px;
            background-repeat: repeat-x;
            position: relative;
            z-index: 50;

            /* The perforated line itself (light gray dashed border) */
            border-bottom: 2px dashed #9ca3af; 
            
            /* Positioning: Sits exactly between the white and green blocks */
            top: 2px; /* Push it down slightly to sit on the border */
            margin-bottom: -10px; /* Pull the green strip up to meet it */
        }
    </style>
</head>
<body class="bg-gray-100 flex flex-col min-h-screen">
    
    <!-- My Tickets Page (List View) -->
    <div id="my-tickets-page" class="flex flex-col flex-grow">
        <!-- My Tickets Header -->
        <header class="p-4 bg-white shadow-sm flex items-center justify-between">
            <h1 class="text-xl font-semibold text-gray-800 mx-auto">My tickets</h1>
        </header>

        <div class="p-4">
            <!-- Filter Tabs -->
            <div class="flex bg-gray-200 rounded-full p-1 space-x-1 mb-4">
                <button class="flex-1 py-2 text-sm font-medium text-gray-700 bg-white rounded-full shadow-md">AVAILABLE</button>
                <button class="flex-1 py-2 text-sm font-medium text-gray-500">EXPIRED</button>
            </div>
            
            <div id="ticket-list" class="space-y-4">
                <!-- Sample Active Ticket (Clickable to show detail page) -->
                <div class="bg-white rounded-xl shadow-md p-4 cursor-pointer" onclick="showActiveTicket()">
                    <div class="flex items-center space-x-3 mb-2">
                        <span class="text-green-600 font-bold">●</span>
                        <span class="text-gray-900 font-semibold">ABB.STU. - INT. UNICOCAMPANIA - per NAPOLI</span>
                        <span class="bg-green-500 text-white text-xs font-bold px-2 py-0.5 rounded-full ml-auto">Active</span>
                    </div>
                    <p class="text-gray-700 text-sm">Route: <span class="font-medium">NAPOLI - CASERTA</span></p>
                    <p class="text-gray-500 text-xs">Valid up to: 01/08/2026</p>
                    <p class="text-gray-500 text-xs mt-2">Price: <span class="text-sm font-semibold">0,00 €</span></p>
                </div>
            </div>
        </div>
    </div>

    <!-- Active Ticket Page (Detailed View) -->
    <div id="active-ticket-page" class="hidden flex flex-col flex-grow">
        <!-- Active Ticket Header (Vibrant Green: #10B981) -->
        <header class="p-4 header-green shadow-sm flex items-center justify-between">
            <button onclick="showMyTickets()" class="flex items-center space-x-2 text-white">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
                </svg>
                <span class="hidden sm:inline">Back</span>
            </button>
            <h1 class="text-xl font-semibold text-white mx-auto">Active ticket</h1>
            <!-- Empty div for spacing, balancing the back button -->
            <div class="w-12"></div> 
        </header>
    
        <main class="flex-grow flex flex-col w-full">
            
            <!-- Main Content Area with Ticket Info and QR Code -->
            <div class="p-4 flex flex-col items-center flex-grow w-full">
                
                <!-- Full Ticket Card Container -->
                <div class="w-full max-w-sm bg-white rounded-xl shadow-lg">
                    
                    <!-- Ticket Header Info (ABB.STU. - INT. UNICOCAMPANIA...) -->
                    <div class="p-4 border-b border-gray-200">
                        <span class="text-sm font-semibold text-gray-900 block">ABB.STU. - INT. UNICOCAMPANIA - per NAPOLI</span>
                        <span class="text-xs text-gray-500 block">ABB INTEGRATO STUDENTI REGIONE CAMPANIA TIC-SG-NA6D-00</span>
                    </div>

                    <!-- Collapsible Card Info Section -->
                    <div class="w-full bg-white">
                        <div class="px-4 py-2">
                            <div class="collapsible-header" onclick="toggleCardInfo()">
                                <div class="flex items-center space-x-2">
                                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-gray-500" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="8.5" cy="7" r="4"/><line x1="20" y1="8" x2="20" y2="14"/><line x1="23" y1="11" x2="17" y2="11"/></svg>
                                    <span class="text-sm font-medium text-gray-700">Card info</span>
                                </div>
                                <svg id="card-info-arrow" xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 text-gray-500 transform rotate-0 transition-transform duration-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                                </svg>
                            </div>
                        </div>
                        
                        <!-- Card Info Content (Hidden by default) -->
                        <div id="card-info-content" class="px-4 pb-4 hidden border-b border-gray-200">
                            <div class="flex items-center space-x-4">
                                <!-- User Photo: Replaced placeholder with the uploaded image URL -->
                                <img src=" " alt="User Photo" class="w-16 h-16 rounded-full object-cover border-2 border-green-300 shadow-md">
                                <div>
                                    <p class="text-base font-semibold text-gray-900">Gaurav Kumar</p>
                                    <p class="text-xs text-gray-600">JEF-NW9T242222G</p>
                                    <p class="text-xs text-gray-600 mt-1">Card no. <span class="font-mono text-gray-800">2000695622</span></p>
                                    <p class="text-xs text-gray-600">Expires: <span class="font-mono text-gray-800">31/07/2026</span></p>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Collapsible Control and Validation (QR Code) Section -->
                    <div class="w-full bg-white">
                        <div class="px-4 py-2">
                            <div class="collapsible-header border-none" onclick="toggleQrSection()">
                                <div class="flex items-center space-x-2">
                                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-gray-500" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect><line x1="9" y1="9" x2="9" y2="9"></line><line x1="15" y1="9" x2="15" y2="9"></line><line x1="9" y1="15" x2="9" y2="15"></line><line x1="15" y1="15" x2="15" y2="15"></line></svg>
                                    <span class="text-sm font-medium text-gray-700">Control and validation</span>
                                </div>
                                <svg id="qr-arrow" xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 text-gray-500 transform rotate-180 transition-transform duration-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                                </svg>
                            </div>
                        </div>

                        <!-- QR Code Content (The white tile with the green strip at the bottom) -->
                        <div id="qr-content" class="w-full flex flex-col items-center">
                            
                            <!-- White Area: QR Code + Time/Minutes -->
                            <!-- NOTE: Removed bottom padding (pb-4) to make space for the tear graphic -->
                            <div class="w-full flex flex-col items-center bg-white p-6"> 
                                
                                <!-- QR Code Area (Simple, no extra border/shadow) -->
                                <div id="qrcode" class="p-0 inline-block"></div>
                                
                                <!-- TIME AND REMAINING MINUTES (on white background) -->
                                <div class="flex items-center justify-center mt-6 space-x-6 text-xl font-bold text-gray-800">
                                    <!-- Clock Icon and Current Time -->
                                    <div class="flex items-center space-x-2">
                                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                                            <path stroke-linecap="round" stroke-linejoin="round" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                                        </svg>
                                        <span id="current-time">21:04:04</span>
                                    </div>
                                    <!-- Lock Icon and Remaining Minutes -->
                                    <div class="flex items-center space-x-1">
                                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                                            <path stroke-linecap="round" stroke-linejoin="round" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z" />
                                        </svg>
                                        <span>102</span>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- NEW TICKET TEAR LINE GRAPHIC INSERTED HERE -->
                            <div class="ticket-tear-graphic w-full relative"></div> 
                            
                            <!-- DECORATIVE GREEN STRIP WITH TEXT -->
                            <div class="w-full relative">
                                <div class="decorative-strip">
                                    <p id="ticket-route-text" class="font-bold text-sm z-50 relative">FROM NAPOLI TO CASERTA</p>
                                    <p id="ticket-validity-text" class="text-xs font-light z-50 relative">Valid from 16/09/2025 to 01/08/2026</p>
                                </div>
                            </div>

                        </div>
                    </div>

                    <!-- Detailed Ticket Info Card (Bottom Section of the same white card) -->
                    <div class="w-full mx-auto bg-white p-6 relative z-20 border-t border-gray-200">
                        <!-- The content starts directly with issued on/price/details -->
                        <div class="mt-0 space-y-4">
                            <div class="flex justify-between items-center">
                                <span class="text-gray-500">Issued on:</span>
                                <span id="ticket-issue-text" class="text-gray-800 font-medium">16/09/2025 - 11:08</span>
                            </div>
                            <div class="flex justify-between items-center">
                                <span class="text-gray-500">Price</span>
                                <span class="text-xl font-bold text-green-600">0,00 €</span>
                            </div>
                            <div class="flex justify-between items-center cursor-pointer" onclick="toggleDetails()">
                                <span class="text-gray-500">Details</span>
                                <div class="flex items-center space-x-2">
                                    <span class="text-gray-800 font-medium">Read all</span>
                                    <svg id="details-arrow" xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 text-gray-500 transform rotate-0 transition-transform duration-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                                    </svg>
                                </div>
                            </div>
                        </div>
            
                        <!-- Expandable Details -->
                        <div id="extra-details" class="hidden mt-4 space-y-2 text-sm text-gray-600 border-t border-gray-200 pt-4">
                            <div class="flex justify-between">
                                <span>Ticket code:</span>
                                <span class="font-mono text-gray-900">2000W/2693395</span>
                            </div>
                            <div class="flex justify-between">
                                <span>PNR:</span>
                                <span class="font-mono text-gray-900">XNJFXZDHE9</span>
                            </div>
                        </div>
            
                        <hr class="my-6 border-t border-gray-200" />
            
                        
                 <!-- Action Buttons -->
<div class="flex flex-col space-y-4">
    <!-- Transfer ticket button styled like screenshot -->
    <button class="w-full bg-blue-900 hover:bg-blue-800 text-white font-bold py-3 px-6 rounded-md transition-colors duration-200">
        Transfer ticket
    </button>
</div>

                    </div>
                </div> <!-- End Full Ticket Card Container -->

            </div>
        </main>
    
        <!-- Bottom Navigation Bar -->
        <nav class="bg-white p-4 shadow-top rounded-t-3xl mt-auto border-t border-gray-200">
            <div class="flex justify-around text-center text-sm font-medium text-gray-500">
                <a href="#" class="flex flex-col items-center p-2 rounded-lg hover:bg-gray-200 transition-colors">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                    </svg>
                    <span>Explore</span>
                </a>
                <a href="#" class="flex flex-col items-center p-2 rounded-lg hover:bg-gray-200 transition-colors">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1.429-9.962L5 12V21h9M14.5 15C15.424 15.65 16 16.5 16 18c0 2.21-1.343 4-3 4s-3-1.79-3-4c0-1.5 1.417-2.35 2.5-3zM8 7h12a2 2 0 012 2v10a2 2 0 01-2 2H8a2 2 0 01-2-2V9a2 2 0 012-2z" />
                    </svg>
                    <span>Buy</span>
                </a>
                <a href="#" class="flex flex-col items-center p-2 rounded-lg hover:bg-gray-200 transition-colors text-green-600">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11H5m14 0a2 2 0 012 2v5a2 2 0 01-2 2H5a2 2 0 01-2-2v-5a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0a2 2 0 002-2h6a2 2 0 002 2M7 7h10" />
                    </svg>
                    <span>My tickets</span>
                </a>
                <a href="#" class="flex flex-col items-center p-2 rounded-lg hover:bg-gray-200 transition-colors">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2a8 8 0 01-8-8c0-1.657 1.343-3 3-3s3-1.895 3-3V7a3 3 0 016 0v2c0 1.105-1.343 2-3 2z" />
                    </svg>
                    <span>Vehicles</span>
                </a>
                <a href="#" class="flex flex-col items-center p-2 rounded-lg hover:bg-gray-200 transition-colors">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5.121 17.804A13.936 13.936 0 0112 16c2.5 0 4.847.655 6.879 1.804M15 10a3 3 0 11-6 0 3 3 0 016 0zm6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
                    </svg>
                    <span>Profile</span>
                </a>
            </div>
        </nav>
    </div>

   <script>
    // Base QR Code Data (without timestamp)
    const baseQrData = `STUDRC
TIC
2025-09-16T23:27
2026-07-31T23:59
XNJFXZDHE9
37
2
0
021a340f1cbbb1d03089175ccae61b0e9ff
5de1c4bdab4998f15bdb245`;

    let qrcodeInstance = null;
    let qrUpdateInterval = null;

    // --- Page Navigation Functions ---
    function showMyTickets() {
        document.getElementById('my-tickets-page').classList.remove('hidden');
        document.getElementById('active-ticket-page').classList.add('hidden');
        if (qrUpdateInterval) {
            clearInterval(qrUpdateInterval);
        }
    }

    function showActiveTicket() {
        document.getElementById('my-tickets-page').classList.add('hidden');
        document.getElementById('active-ticket-page').classList.remove('hidden');
        generateQrCode();
        // Refresh QR code every 15 minutes
        qrUpdateInterval = setInterval(generateQrCode, 15 * 60 * 1000);
        openQrSection();
    }

    // --- QR Code & Time Functions ---
    function generateQrCode() {
        const qrcodeElement = document.getElementById("qrcode");
        qrcodeElement.innerHTML = ''; // Clear previous QR

        // Get current local time with timezone offset
        const now = new Date();
        const tzOffsetMin = now.getTimezoneOffset(); // in minutes
        const offsetSign = tzOffsetMin > 0 ? "-" : "+";
        const absOffsetMin = Math.abs(tzOffsetMin);
        const offsetHours = String(Math.floor(absOffsetMin / 60)).padStart(2, "0");
        const offsetMinutes = String(absOffsetMin % 60).padStart(2, "0");
        const offsetStr = `${offsetSign}${offsetHours}:${offsetMinutes}`;

        const isoTimestamp =
            now.getFullYear() +
            "-" + String(now.getMonth() + 1).padStart(2, "0") +
            "-" + String(now.getDate()).padStart(2, "0") +
            "T" + String(now.getHours()).padStart(2, "0") +
            ":" + String(now.getMinutes()).padStart(2, "0") +
            ":" + String(now.getSeconds()).padStart(2, "0") +
            offsetStr;

        // Merge base data with timestamp
        const qrData = `${baseQrData}
${isoTimestamp}`;

        // Generate QR Code
        qrcodeInstance = new QRCode(qrcodeElement, {
            text: qrData,
            width: 180,
            height: 180,
            colorDark: "#000000",
            colorLight: "#ffffff",
            correctLevel: QRCode.CorrectLevel.H
        });

        updateTime();
    }

    function updateTime() {
        const now = new Date();
        const hours = now.getHours().toString().padStart(2, '0');
        const minutes = now.getMinutes().toString().padStart(2, '0');
        const seconds = now.getSeconds().toString().padStart(2, '0');
        document.getElementById('current-time').textContent = `${hours}:${minutes}:${seconds}`;
    }

    // Run updateTime immediately and then every second
    updateTime();
    setInterval(updateTime, 1000);



        // --- Collapsible Handlers ---
        
        // Toggle Card Info
        function toggleCardInfo() {
            const content = document.getElementById('card-info-content');
            const arrow = document.getElementById('card-info-arrow');
            if (content.classList.contains('hidden')) {
                content.classList.remove('hidden');
                arrow.classList.add('rotate-180');
            } else {
                content.classList.add('hidden');
                arrow.classList.remove('rotate-180');
            }
        }
        
        // Toggle QR Code Section (Control and validation)
        function toggleQrSection() {
            const content = document.getElementById('qr-content');
            const arrow = document.getElementById('qr-arrow');
            if (content.classList.contains('hidden')) {
                content.classList.remove('hidden');
                arrow.classList.add('rotate-180');
                generateQrCode(); 
            } else {
                content.classList.add('hidden');
                arrow.classList.remove('rotate-180');
            }
        }

        function openQrSection() {
             const content = document.getElementById('qr-content');
             const arrow = document.getElementById('qr-arrow');
             // Ensure it's not hidden and arrow is pointing up on load
             content.classList.remove('hidden'); 
             arrow.classList.add('rotate-180');
        }

        // Toggle Details (The bottom card)
        function toggleDetails() {
            const details = document.getElementById('extra-details');
            const arrow = document.getElementById('details-arrow');
            if (details.classList.contains('hidden')) {
                details.classList.remove('hidden');
                arrow.classList.add('rotate-180');
            } else {
                details.classList.add('hidden');
                arrow.classList.remove('rotate-180');
            }
        }
    </script>
</body>
</html>




