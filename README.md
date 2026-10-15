# Wearable2```html
<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Wearables — Custom Women's Boutique & Tailor Diary</title>
  
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts: Inter & Playfair Display -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Playfair+Display:ital,wght@0,600;0,700;0,800;1,600&display=swap" rel="stylesheet">
  <!-- Font Awesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'sans-serif'],
            serif: ['Playfair Display', 'serif'],
          },
          colors: {
            brand: {
              50: '#fff1f2',
              100: '#ffe4e6',
              200: '#fecdd3',
              500: '#f43f5e',
              600: '#e11d48',
              700: '#be123c',
              800: '#9f1239',
              900: '#881337',
            },
            gold: {
              400: '#fbbf24',
              500: '#f59e0b',
              600: '#d97706',
            }
          }
        }
      }
    }
  </script>

  <style>
    /* Smooth transitions and scroll behavior */
    html { scroll-behavior: smooth; }
    .bg-grid {
      background-size: 24px 24px;
      background-image: linear-gradient(to right, rgba(225, 29, 72, 0.05) 1px, transparent 1px),
                        linear-gradient(to bottom, rgba(225, 29, 72, 0.05) 1px, transparent 1px);
    }
    .custom-scroll::-webkit-scrollbar {
      width: 6px;
      height: 6px;
    }
    .custom-scroll::-webkit-scrollbar-thumb {
      background: #f43f5e;
      border-radius: 9999px;
    }
    @keyframes pulse-gentle {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.05); }
    }
    .urgent-badge-pulse {
      animation: pulse-gentle 2s infinite ease-in-out;
    }
  </style>
</head>

<body class="bg-stone-50 text-stone-800 font-sans antialiased min-h-screen flex flex-col selection:bg-brand-500 selection:text-white">

  <!-- ================= TOP NOTIFICATION BAR ================= -->
  <div class="bg-gradient-to-r from-brand-700 via-rose-600 to-amber-600 text-white text-xs py-2 px-4 text-center font-medium shadow-xs">
    <div class="max-w-7xl mx-auto flex items-center justify-between gap-2 flex-wrap">
      <div class="flex items-center gap-2">
        <span class="inline-block px-2 py-0.5 rounded-full bg-white/20 text-[10px] font-bold tracking-wider uppercase">✨ Wearables Boutique Indore</span>
        <span class="hidden sm:inline">Custom Fitting &bull; Advance Material &bull; ⚡ Urgent Silai (Sirf Indore Me)</span>
      </div>
      <!-- Customer Care Helpline (Aapka No) -->
      <div class="flex items-center gap-3 text-xs">
        <a href="tel:7725081052" class="hover:underline flex items-center gap-1 font-bold bg-white/10 px-2.5 py-0.5 rounded-full">
          <i class="fa-solid fa-headset text-amber-300"></i>
          <span>Helpdesk: 7725081052</span>
        </a>
      </div>
    </div>
  </div>

  <!-- ================= NAVBAR ================= -->
  <header class="sticky top-0 z-40 bg-white/95 backdrop-blur-md border-b border-rose-100 shadow-xs">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-18 flex items-center justify-between">
      
      <!-- Brand Logo -->
      <div class="flex items-center gap-3 cursor-pointer" onclick="switchView('customer')">
        <div class="w-11 h-11 rounded-2xl bg-gradient-to-tr from-brand-600 to-amber-500 flex items-center justify-center text-white text-xl shadow-md shadow-brand-500/30">
          <i class="fa-solid fa-scissors"></i>
        </div>
        <div>
          <span class="font-serif font-black text-2xl tracking-tight text-stone-900 flex items-center gap-1.5">
            Wearables <span class="text-xs px-2 py-0.5 rounded-md bg-rose-100 text-brand-700 font-sans font-bold uppercase tracking-wider">Boutique</span>
          </span>
          <p class="text-[11px] text-stone-500 font-medium">Custom Tailoring &bull; Silai & Designing</p>
        </div>
      </div>

      <!-- Navigation & Action Buttons -->
      <div class="flex items-center gap-2 sm:gap-3">
        <!-- Customer View Tab -->
        <button id="navCustomerBtn" onclick="switchView('customer')" class="px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold transition flex items-center gap-1.5 bg-brand-50 text-brand-700 border border-brand-200">
          <i class="fa-solid fa-gem"></i>
          <span>Catalog & Order</span>
        </button>

        <!-- Order Track Button -->
        <button onclick="openTrackModal()" class="px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold transition flex items-center gap-1.5 bg-amber-50 text-amber-800 border border-amber-200 hover:bg-amber-100">
          <i class="fa-solid fa-truck-fast text-amber-600"></i>
          <span class="hidden sm:inline">Track Order</span>
          <span class="sm:hidden">Track</span>
        </button>

        <!-- Protected Tailor Diary Button -->
        <button onclick="tryOpenAdminDiary()" class="px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold transition flex items-center gap-1.5 bg-stone-900 text-white hover:bg-stone-800 shadow-sm shadow-stone-900/20">
          <i class="fa-solid fa-lock text-rose-400"></i>
          <span class="hidden sm:inline">Mummy's Diary</span>
          <span class="sm:hidden">Diary</span>
        </button>
      </div>
    </div>
  </header>

  <!-- ================= MAIN CONTAINER ================= -->
  <main class="flex-1">

    <!-- ========================================================================= -->
    <!-- VIEW 1: CUSTOMER VIEW (SHOWCASE, BOOKING & PRICING)                      -->
    <!-- ========================================================================= -->
    <div id="customerSection" class="transition-opacity duration-300">
      
      <!-- HERO BANNER -->
      <section class="relative bg-gradient-to-b from-rose-50 via-white to-stone-50 pt-10 pb-16 px-4 sm:px-6 lg:px-8 border-b border-rose-100 overflow-hidden bg-grid">
        <div class="max-w-5xl mx-auto text-center relative z-10">
          
          <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-rose-100/80 text-brand-800 text-xs font-bold mb-4 border border-rose-200">
            <span class="w-2 h-2 rounded-full bg-brand-600 animate-ping"></span>
            <span>Aapke Pasand Ka Kapda &bull; Aapke Naap Ki Perfect Fitting</span>
          </div>

          <h1 class="text-3xl sm:text-5xl lg:text-6xl font-serif font-black text-stone-900 leading-tight mb-4">
            Custom Wearables Crafted by <span class="text-transparent bg-clip-text bg-gradient-to-r from-brand-600 via-rose-600 to-amber-600">Master Hands</span>
          </h1>

          <p class="text-sm sm:text-base text-stone-600 max-w-2xl mx-auto leading-relaxed mb-8">
            Chahe aap apna kapda le aayein ya humare dwara market se matching astar aur fabric mangwayein — har silai me milegi boutique finish aur aaramdayak fitting.
          </p>

          <div class="flex flex-col sm:flex-row items-center justify-center gap-3">
            <a href="#orderFormAnchor" class="w-full sm:w-auto px-7 py-3.5 bg-gradient-to-r from-brand-600 to-rose-600 hover:from-brand-700 hover:to-rose-700 text-white rounded-2xl font-bold text-sm shadow-lg shadow-brand-500/30 flex items-center justify-center gap-2 transition active:scale-95">
              <i class="fa-solid fa-pen-nib"></i>
              <span>Custom Order Book Karein</span>
            </a>
            <!-- Customer Care Quick Chat (Aapka No) -->
            <a href="https://wa.me/917725081052?text=Namaste!%20Mujhe%20Wearables%20Boutique%20ke%20bare%20me%20jaankari%20chahiye." target="_blank" class="w-full sm:w-auto px-6 py-3.5 bg-white border border-rose-200 text-stone-700 hover:bg-rose-50 rounded-2xl font-bold text-sm transition flex items-center justify-center gap-2 shadow-xs">
              <i class="fa-brands fa-whatsapp text-emerald-600"></i>
              <span>Customer Care Se Baat Karein</span>
            </a>
          </div>

          <!-- Feature Badges -->
          <div class="grid grid-cols-2 md:grid-cols-4 gap-3 sm:gap-4 mt-12 max-w-4xl mx-auto text-left">
            <div class="bg-white p-3.5 sm:p-4 rounded-2xl border border-rose-100 shadow-xs flex items-center gap-3">
              <div class="w-10 h-10 rounded-xl bg-rose-100 text-brand-600 flex items-center justify-center text-lg shrink-0">
                <i class="fa-solid fa-ruler-combined"></i>
              </div>
              <div>
                <h4 class="font-bold text-xs text-stone-900">Custom Naap</h4>
                <p class="text-[11px] text-stone-500">Perfect body contour fit</p>
              </div>
            </div>

            <div class="bg-white p-3.5 sm:p-4 rounded-2xl border border-rose-100 shadow-xs flex items-center gap-3">
              <div class="w-10 h-10 rounded-xl bg-amber-100 text-amber-700 flex items-center justify-center text-lg shrink-0">
                <i class="fa-solid fa-bag-shopping"></i>
              </div>
              <div>
                <h4 class="font-bold text-xs text-stone-900">Advance Material</h4>
                <p class="text-[11px] text-stone-500">Kapda hum khareedte hain</p>
              </div>
            </div>

            <div class="bg-white p-3.5 sm:p-4 rounded-2xl border border-rose-100 shadow-xs flex items-center gap-3">
              <div class="w-10 h-10 rounded-xl bg-emerald-100 text-emerald-600 flex items-center justify-center text-lg shrink-0">
                <i class="fa-solid fa-hand-holding-dollar"></i>
              </div>
              <div>
                <h4 class="font-bold text-xs text-stone-900">Silai On Delivery</h4>
                <p class="text-[11px] text-stone-500">Kapda pasand aane par payment</p>
              </div>
            </div>

            <div class="bg-white p-3.5 sm:p-4 rounded-2xl border border-rose-100 shadow-xs flex items-center gap-3">
              <div class="w-10 h-10 rounded-xl bg-red-100 text-red-600 flex items-center justify-center text-lg shrink-0">
                <i class="fa-solid fa-bolt"></i>
              </div>
              <div>
                <h4 class="font-bold text-xs text-stone-900">Urgent Silai (Indore)</h4>
                <p class="text-[11px] text-stone-500">24-48 ghante me (Sirf Indore)</p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- POPULAR SILAI CATEGORIES -->
      <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-14">
        <div class="flex flex-col md:flex-row md:items-end justify-between mb-8 gap-4">
          <div>
            <span class="text-xs font-bold text-brand-600 uppercase tracking-widest">Silai & Boutique Rate List</span>
            <h2 class="text-2xl sm:text-3xl font-serif font-black text-stone-900 mt-1">Humare Best-Selling Designs</h2>
            <p class="text-xs sm:text-sm text-stone-500">Silai ke rates andazatan hain, design ke mutabik thoda badal sakte hain.</p>
          </div>
          <div class="flex items-center gap-2">
            <span class="inline-flex items-center gap-1.5 px-3 py-1.5 rounded-xl bg-amber-100 text-amber-900 text-xs font-bold">
              <i class="fa-solid fa-bolt text-amber-600"></i> ⚡ Urgent Option: Sirf Indore Me (+₹150 to ₹200)
            </span>
          </div>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
          
          <!-- Item 1: Blouse -->
          <div class="bg-white rounded-3xl p-5 border border-rose-100 shadow-xs hover:shadow-lg transition flex flex-col justify-between group">
            <div>
              <div class="w-full h-44 rounded-2xl bg-gradient-to-tr from-rose-500 to-pink-400 text-white flex flex-col items-center justify-center p-4 relative overflow-hidden mb-4">
                <div class="absolute -top-6 -right-6 w-24 h-24 rounded-full bg-white/10 blur-xs"></div>
                <i class="fa-solid fa-shirt text-5xl mb-2 drop-shadow-md"></i>
                <span class="text-xs font-bold uppercase tracking-wider bg-white/20 px-3 py-1 rounded-full backdrop-blur-xs">Princess & Padded</span>
              </div>
              <h3 class="font-serif font-bold text-lg text-stone-900">Designer Blouse</h3>
              <p class="text-xs text-stone-500 mt-1 leading-relaxed">Padded, Princess Cut, Deep Back Neck, Latkan aur Dori fitting ke sath.</p>
            </div>
            <div class="mt-4 pt-4 border-t border-rose-100 flex items-center justify-between">
              <div>
                <span class="text-[10px] uppercase font-bold text-stone-400 block">Starting Silai</span>
                <span class="text-lg font-black text-brand-700">₹350 - ₹650</span>
              </div>
              <button onclick="prefillGarment('Designer Blouse')" class="px-3.5 py-1.5 rounded-xl bg-rose-50 text-brand-700 hover:bg-brand-600 hover:text-white font-bold text-xs transition">
                Order Karein
              </button>
            </div>
          </div>

          <!-- Item 2: Salwar Suit -->
          <div class="bg-white rounded-3xl p-5 border border-rose-100 shadow-xs hover:shadow-lg transition flex flex-col justify-between group">
            <div>
              <div class="w-full h-44 rounded-2xl bg-gradient-to-tr from-emerald-500 to-teal-400 text-white flex flex-col items-center justify-center p-4 relative overflow-hidden mb-4">
                <div class="absolute -top-6 -right-6 w-24 h-24 rounded-full bg-white/10 blur-xs"></div>
                <i class="fa-solid fa-vest text-5xl mb-2 drop-shadow-md"></i>
                <span class="text-xs font-bold uppercase tracking-wider bg-white/20 px-3 py-1 rounded-full backdrop-blur-xs">Kurti / Pant Set</span>
              </div>
              <h3 class="font-serif font-bold text-lg text-stone-900">Suit & Plazo / Pant</h3>
              <p class="text-xs text-stone-500 mt-1 leading-relaxed">Straight Kurti, Afgani Salwar, Pocket Pant aur Astar ke sath silai.</p>
            </div>
            <div class="mt-4 pt-4 border-t border-rose-100 flex items-center justify-between">
              <div>
                <span class="text-[10px] uppercase font-bold text-stone-400 block">Starting Silai</span>
                <span class="text-lg font-black text-emerald-700">₹400 - ₹700</span>
              </div>
              <button onclick="prefillGarment('Suit & Plazo/Pant')" class="px-3.5 py-1.5 rounded-xl bg-emerald-50 text-emerald-700 hover:bg-emerald-600 hover:text-white font-bold text-xs transition">
                Order Karein
              </button>
            </div>
          </div>

          <!-- Item 3: Anarkali / Gown -->
          <div class="bg-white rounded-3xl p-5 border border-rose-100 shadow-xs hover:shadow-lg transition flex flex-col justify-between group">
            <div>
              <div class="w-full h-44 rounded-2xl bg-gradient-to-tr from-purple-600 to-indigo-500 text-white flex flex-col items-center justify-center p-4 relative overflow-hidden mb-4">
                <div class="absolute -top-6 -right-6 w-24 h-24 rounded-full bg-white/10 blur-xs"></div>
                <i class="fa-solid fa-wand-magic-sparkles text-5xl mb-2 drop-shadow-md"></i>
                <span class="text-xs font-bold uppercase tracking-wider bg-white/20 px-3 py-1 rounded-full backdrop-blur-xs">Flare & Kaliyan</span>
              </div>
              <h3 class="font-serif font-bold text-lg text-stone-900">Anarkali & Long Gown</h3>
              <p class="text-xs text-stone-500 mt-1 leading-relaxed">High Ghera, Cancan astar, umbrella cut aur festive party wear.</p>
            </div>
            <div class="mt-4 pt-4 border-t border-rose-100 flex items-center justify-between">
              <div>
                <span class="text-[10px] uppercase font-bold text-stone-400 block">Starting Silai</span>
                <span class="text-lg font-black text-purple-700">₹800 - ₹1500</span>
              </div>
              <button onclick="prefillGarment('Anarkali / Gown')" class="px-3.5 py-1.5 rounded-xl bg-purple-50 text-purple-700 hover:bg-purple-600 hover:text-white font-bold text-xs transition">
                Order Karein
              </button>
            </div>
          </div>

          <!-- Item 4: Lehenga Choli -->
          <div class="bg-white rounded-3xl p-5 border border-rose-100 shadow-xs hover:shadow-lg transition flex flex-col justify-between group">
            <div>
              <div class="w-full h-44 rounded-2xl bg-gradient-to-tr from-amber-500 to-rose-500 text-white flex flex-col items-center justify-center p-4 relative overflow-hidden mb-4">
                <div class="absolute -top-6 -right-6 w-24 h-24 rounded-full bg-white/10 blur-xs"></div>
                <i class="fa-solid fa-crown text-5xl mb-2 drop-shadow-md"></i>
                <span class="text-xs font-bold uppercase tracking-wider bg-white/20 px-3 py-1 rounded-full backdrop-blur-xs">Bridal & Party</span>
              </div>
              <h3 class="font-serif font-bold text-lg text-stone-900">Lehenga Choli</h3>
              <p class="text-xs text-stone-500 mt-1 leading-relaxed">Full can-can net, heavy latkan, designer blouse and dupatta border work.</p>
            </div>
            <div class="mt-4 pt-4 border-t border-rose-100 flex items-center justify-between">
              <div>
                <span class="text-[10px] uppercase font-bold text-stone-400 block">Starting Silai</span>
                <span class="text-lg font-black text-amber-700">₹1200 - ₹2500</span>
              </div>
              <button onclick="prefillGarment('Lehenga Choli')" class="px-3.5 py-1.5 rounded-xl bg-amber-50 text-amber-700 hover:bg-amber-600 hover:text-white font-bold text-xs transition">
                Order Karein
              </button>
            </div>
          </div>

        </div>
      </section>

      <!-- CUSTOM ORDER FORM -->
      <section id="orderFormAnchor" class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 py-10 mb-16">
        <div class="bg-white rounded-3xl p-6 sm:p-10 border-2 border-rose-200 shadow-xl relative overflow-hidden">
          
          <div class="flex items-center gap-3 mb-6">
            <div class="w-12 h-12 rounded-2xl bg-brand-100 text-brand-600 flex items-center justify-center text-xl">
              <i class="fa-solid fa-clipboard-check"></i>
            </div>
            <div>
              <h2 class="text-xl sm:text-2xl font-serif font-bold text-stone-900">Custom Order Booking Form</h2>
              <p class="text-xs text-stone-500">Order submit karte hi aapko aapka Token Number milega.</p>
            </div>
          </div>

          <form id="publicBookingForm" onsubmit="handleCustomerBooking(event)" class="space-y-6">
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div>
                <label class="block text-xs font-bold text-stone-700 uppercase mb-1">Aapka Naam *</label>
                <input type="text" id="custName" required placeholder="e.g. Priya Sharma" class="w-full p-3 text-sm rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden">
              </div>
              <div>
                <label class="block text-xs font-bold text-stone-700 uppercase mb-1">WhatsApp Mobile Number *</label>
                <input type="tel" id="custPhone" required placeholder="e.g. 9876543210" class="w-full p-3 text-sm rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden">
              </div>
            </div>

            <!-- CITY & LOCATION -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div>
                <label class="block text-xs font-bold text-stone-700 uppercase mb-1">Aapka Shehar (City) *</label>
                <select id="custCity" onchange="checkIndoreEligibility()" class="w-full p-3 text-sm rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden bg-white">
                  <option value="Indore" selected>Indore (इंदौर)</option>
                  <option value="Other">Other City (इंदौर से बाहर)</option>
                </select>
              </div>
              <div>
                <label class="block text-xs font-bold text-stone-700 uppercase mb-1">Indore Area / Colony (Agar Indore se hain)</label>
                <input type="text" id="custArea" placeholder="e.g. Vijay Nagar, Palasia, Rajwada..." class="w-full p-3 text-sm rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden">
              </div>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div>
                <label class="block text-xs font-bold text-stone-700 uppercase mb-1">Garment Ka Type *</label>
                <select id="custGarment" required class="w-full p-3 text-sm rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden bg-white">
                  <option value="">Select Garment</option>
                  <option value="Designer Blouse">Designer Blouse</option>
                  <option value="Suit & Plazo/Pant">Suit & Plazo / Pant</option>
                  <option value="Anarkali / Gown">Anarkali / Gown</option>
                  <option value="Lehenga Choli">Lehenga Choli</option>
                  <option value="Only Kurti / Top">Only Kurti / Top</option>
                  <option value="Other Custom">Kuch Alag (Custom)</option>
                </select>
              </div>
              <div>
                <label class="block text-xs font-bold text-stone-700 uppercase mb-1">Kapda / Material Ka Plan *</label>
                <select id="custFabricMode" required class="w-full p-3 text-sm rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden bg-white">
                  <option value="Customer Layega">Main khud kapda laungi (My own fabric)</option>
                  <option value="Mummy Kharidengi (Advance)">Mummy market se le aayengi (Advance Payment)</option>
            <!-- EMERGENCY / URGENT CHECKBOX (INDORE EXCLUSIVE) -->
            <div class="p-4 rounded-2xl bg-amber-50 border-2 border-amber-200/80 flex items-start gap-3 relative overflow-hidden">
              <input type="checkbox" id="custIsUrgent" onchange="validateUrgentCity(this)" class="mt-1 w-4 h-4 text-brand-600 rounded-sm focus:ring-brand-500">
              <div>
                <label for="custIsUrgent" class="font-bold text-xs sm:text-sm text-stone-900 cursor-pointer flex items-center gap-1.5 flex-wrap">
                  <i class="fa-solid fa-bolt text-amber-600"></i>
                  <span>Emergency / Urgent Silai (24 se 48 Ghante)</span>
                  <span class="text-[10px] bg-red-600 text-white px-2 py-0.5 rounded-full uppercase font-bold tracking-wider">Sirf Indore Me</span>
                </label>
                <p class="text-[11px] text-stone-600 mt-1">
                  ⚡ <strong>Note:</strong> Urgent delivery (+₹150 to ₹200) ki suvidha <strong>sirf aur sirf Indore shehar ke andar</strong> uplabdh hai. Indore se bahar ke orders normal timeline me hi ready honge.
                </p>
                <div id="urgentCityNotice" class="hidden text-[11px] text-red-600 font-bold mt-1.5">
                  ⚠️ Maaf kijiye, Urgent silai sirf Indore ke liye uplabdh hai. Kripya Normal order select karein ya Customer Care se baat karein.
                </div>
              </div>
            </div>

            <div>
              <label class="block text-xs font-bold text-stone-700 uppercase mb-1">Design ki detail ya koi khaas pasand?</label>
              <textarea id="custNotes" rows="3" placeholder="Jaise: V-neck gala, aage hook, asteen par lace lagani hai ya koi specific design..." class="w-full p-3 text-sm rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden"></textarea>
            </div>

            <!-- PAYMENT INFORMATION BOX (MUMMY'S NUMBER) -->
            <div class="p-5 rounded-2xl bg-gradient-to-br from-emerald-50 to-teal-50 border-2 border-emerald-200 text-left">
              <div class="flex items-center justify-between mb-3">
                <span class="text-xs font-black uppercase text-emerald-900 flex items-center gap-2">
                  <i class="fa-solid fa-qrcode text-emerald-600 text-base"></i>
                  <span>Advance Payment Info (Mummy / Tailor Master)</span>
                </span>
                <span class="text-[10px] bg-emerald-200 text-emerald-900 px-2 py-0.5 rounded-md font-bold uppercase">PhonePe / GPay / Paytm</span>
              </div>
              <p class="text-xs text-stone-600 mb-3 leading-relaxed">
                Fabric shopping ya advance payment ke liye aap seedha Mummy ke number par online pay kar sakte hain:
              </p>
              <div class="flex flex-col sm:flex-row items-center justify-between p-3 bg-white rounded-xl border border-emerald-200 gap-3">
                <div>
                  <span class="text-[10px] text-stone-400 font-bold uppercase block">Payment / UPI Number</span>
                  <div class="text-lg font-black text-stone-900 font-mono tracking-wider flex items-center gap-2">
                    <span>6265741833</span>
                    <button type="button" onclick="copyPaymentNumber()" class="text-xs px-2 py-1 rounded-md bg-stone-100 hover:bg-emerald-100 text-stone-700 transition">
                      <i class="fa-regular fa-copy"></i> Copy
                    </button>
                  </div>
                  <span class="text-[10px] text-emerald-700 font-semibold">Boutique Incharge: Mummy</span>
                </div>
                <a href="upi://pay?pa=6265741833@upi&pn=Wearables%20Tailor" class="px-4 py-2 bg-emerald-600 hover:bg-emerald-700 text-white rounded-xl text-xs font-bold transition flex items-center gap-1.5 shadow-xs">
                  <i class="fa-solid fa-arrow-up-right-from-square"></i>
                  <span>UPI App Se Pay Karein</span>
                </a>
              </div>
            </div>

            <button type="submit" class="w-full py-4 bg-gradient-to-r from-brand-600 via-rose-600 to-amber-600 hover:from-brand-700 hover:to-rose-700 text-white font-bold rounded-2xl text-sm shadow-lg shadow-brand-500/25 flex items-center justify-center gap-2 transition active:scale-95">
              <i class="fa-solid fa-paper-plane"></i>
              <span>Order Submit Karein & Token Prapt Karein</span>
            </button>
          </form>
        </div>
      </section>

    </div>

    <!-- ========================================================================= -->
    <!-- VIEW 2: MUMMY'S PROTECTED DIARY & CASH REGISTER                          -->
    <!-- ========================================================================= -->
    <div id="adminSection" class="hidden max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
      
      <!-- ADMIN HEADER & CONTROLS -->
      <div class="flex flex-col sm:flex-row sm:items-center justify-between pb-6 border-b border-rose-200 gap-4 mb-6">
        <div>
          <div class="flex items-center gap-2">
            <span class="w-2.5 h-2.5 rounded-full bg-emerald-500 animate-pulse"></span>
            <span class="text-xs font-bold uppercase tracking-wider text-emerald-700">Authenticated: Mummy's Tailor Diary</span>
          </div>
          <h2 class="text-2xl sm:text-3xl font-serif font-black text-stone-900 mt-0.5">
            Customer Naap & Hisaab Register
          </h2>
          <p class="text-xs text-stone-500">Advance kharcha, silai labor aur delivery status ka pura hisaab.</p>
        </div>

        <div class="flex items-center gap-2 flex-wrap">
          <button onclick="openChangePinModal()" class="px-3.5 py-2.5 bg-white hover:bg-stone-50 text-stone-700 border border-stone-200 rounded-xl text-xs font-bold transition flex items-center gap-1.5 shadow-xs">
            <i class="fa-solid fa-key text-amber-500"></i>
            <span>Change Passcode</span>
          </button>
          
          <button onclick="lockDiaryNow()" class="px-3.5 py-2.5 bg-rose-50 hover:bg-rose-100 text-rose-700 border border-rose-200 rounded-xl text-xs font-bold transition flex items-center gap-1.5 shadow-xs">
            <i class="fa-solid fa-lock"></i>
            <span>Lock Diary</span>
          </button>
          
          <button onclick="openNewOrderModal()" class="px-4 py-2.5 bg-brand-600 hover:bg-brand-700 text-white rounded-xl text-xs font-bold transition flex items-center gap-1.5 shadow-md shadow-brand-500/25">
            <i class="fa-solid fa-plus"></i>
            <span>Naya Order Darj Karein</span>
          </button>
        </div>
      </div>

      <!-- SUMMARY KPI METRICS -->
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-8">
        <div class="bg-white p-4 rounded-2xl border border-rose-100 shadow-xs">
          <span class="text-[11px] font-bold text-stone-500 uppercase">Total Orders</span>
          <div id="statTotalOrders" class="text-2xl font-black text-stone-900 mt-1">0</div>
        </div>
        <div class="bg-white p-4 rounded-2xl border border-amber-100 shadow-xs">
          <span class="text-[11px] font-bold text-amber-700 uppercase">⚡ Urgent Orders</span>
          <div id="statUrgentOrders" class="text-2xl font-black text-amber-600 mt-1">0</div>
        </div>
        <div class="bg-white p-4 rounded-2xl border border-emerald-100 shadow-xs">
          <span class="text-[11px] font-bold text-emerald-700 uppercase">Advance Mila</span>
          <div id="statTotalAdvance" class="text-2xl font-black text-emerald-600 mt-1">₹0</div>
        </div>
        <div class="bg-white p-4 rounded-2xl border border-rose-100 shadow-xs">
          <span class="text-[11px] font-bold text-brand-700 uppercase">Baki Silai (Due)</span>
          <div id="statTotalBalance" class="text-2xl font-black text-brand-600 mt-1">₹0</div>
        </div>
      </div>

      <!-- FILTER & SEARCH -->
      <div class="flex flex-col sm:flex-row gap-3 items-center justify-between mb-6">
        <div class="relative w-full sm:w-80">
          <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-3.5 text-stone-400 text-xs"></i>
          <input type="text" id="adminSearchInput" oninput="renderOrdersTable()" placeholder="Token, Naam ya Phone dhoondhein..." class="w-full pl-9 pr-3 py-2.5 text-xs rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden bg-white">
        </div>
        <div class="flex items-center gap-2 w-full sm:w-auto overflow-x-auto pb-1">
          <button onclick="setFilter('all')" id="filterAll" class="px-3 py-1.5 rounded-lg text-xs font-bold bg-brand-600 text-white shrink-0">Sabhi</button>
          <button onclick="setFilter('in_progress')" id="filterProgress" class="px-3 py-1.5 rounded-lg text-xs font-bold bg-stone-100 text-stone-600 shrink-0">Silai Chalu</button>
          <button onclick="setFilter('ready')" id="filterReady" class="px-3 py-1.5 rounded-lg text-xs font-bold bg-stone-100 text-stone-600 shrink-0">Ready / Trial</button>
          <button onclick="setFilter('delivered')" id="filterDelivered" class="px-3 py-1.5 rounded-lg text-xs font-bold bg-stone-100 text-stone-600 shrink-0">Delivered</button>
        </div>
      </div>

      <!-- ORDERS LIST CONTAINER -->
      <div id="ordersCardsContainer" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
        <!-- Rendered via JavaScript -->
      </div>

    </div>

  </main>

  <!-- ========================================================================= -->
  <!-- MODAL 1: TOKEN CONFIRMATION MODAL                                         -->
  <!-- ========================================================================= -->
  <div id="tokenModal" class="fixed inset-0 z-50 bg-stone-900/80 backdrop-blur-xs hidden items-center justify-center p-4">
    <div class="bg-white rounded-3xl max-w-md w-full p-6 sm:p-7 border-2 border-rose-200 shadow-2xl relative text-center">
      
      <div class="w-14 h-14 mx-auto rounded-2xl bg-emerald-100 text-emerald-600 flex items-center justify-center text-2xl mb-4">
        <i class="fa-solid fa-circle-check"></i>
      </div>

      <span class="text-xs font-bold uppercase tracking-widest text-brand-600">Order Successfully Created</span>
      <h3 class="font-serif font-black text-2xl text-stone-900 mt-1">Aapka Order Token</h3>

      <div class="my-4 p-4 rounded-2xl bg-rose-50 border border-rose-200">
        <span class="text-xs text-stone-500 uppercase font-bold">Token Number</span>
        <div id="confirmedTokenId" class="text-3xl font-black text-brand-700 tracking-wider font-mono">WB-101</div>
        <p class="text-[11px] text-stone-600 mt-1">Is token number ko save kar lein ya screenshot le lein.</p>
      </div>

      <div class="space-y-2 mb-5 text-left text-xs text-stone-600 bg-stone-50 p-3 rounded-xl border border-stone-200">
        <div><strong>Customer:</strong> <span id="confirmedCustomerName">Priya</span></div>
        <div><strong>Garment:</strong> <span id="confirmedGarment">Designer Blouse</span></div>
        <div><strong>Status:</strong> <span class="text-amber-700 font-bold">Order Confirmed &bull; Fabric Verification</span></div>
      </div>

      <div class="flex flex-col gap-2">
        <button id="sendTokenWhatsAppBtn" class="w-full py-3 bg-emerald-600 hover:bg-emerald-700 text-white rounded-xl font-bold text-xs flex items-center justify-center gap-2">
          <i class="fa-brands fa-whatsapp text-base"></i>
          <span>Mummy Ko WhatsApp Par Bhejein (6265741833)</span>
        </button>
        <button onclick="closeTokenModal()" class="w-full py-2.5 bg-stone-100 hover:bg-stone-200 text-stone-700 rounded-xl font-bold text-xs">
          Thik Hai, Band Karein
        </button>
      </div>
    </div>
  </div>

  <!-- ========================================================================= -->
  <!-- MODAL 2: TRACK ORDER MODAL                                                -->
  <!-- ========================================================================= -->
  <div id="trackModal" class="fixed inset-0 z-50 bg-stone-900/80 backdrop-blur-xs hidden items-center justify-center p-4">
    <div class="bg-white rounded-3xl max-w-lg w-full p-6 sm:p-7 border border-rose-200 shadow-2xl relative">
      <button onclick="closeTrackModal()" class="absolute top-4 right-4 text-stone-400 hover:text-stone-700">
        <i class="fa-solid fa-xmark text-lg"></i>
      </button>

      <div class="flex items-center gap-2.5 mb-4">
        <div class="w-10 h-10 rounded-xl bg-amber-100 text-amber-700 flex items-center justify-center text-lg">
          <i class="fa-solid fa-magnifying-glass"></i>
        </div>
        <div>
          <h3 class="font-serif font-bold text-lg text-stone-900">Track Order Status</h3>
          <p class="text-xs text-stone-500">Apna Token No (e.g. WB-101) ya Mobile No daalein.</p>
        </div>
      </div>

      <div class="flex gap-2 mb-5">
        <input type="text" id="trackSearchInput" placeholder="WB-101 ya 9876543210..." class="flex-1 p-3 text-xs sm:text-sm rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden">
        <button onclick="searchOrderStatus()" class="px-5 py-3 bg-brand-600 hover:bg-brand-700 text-white rounded-xl text-xs font-bold shrink-0">
          Dhoondhein
        </button>
      </div>

      <!-- Track Result Area -->
      <div id="trackResultArea" class="hidden">
        <!-- Rendered via JS -->
      </div>
    </div>
  </div>

  <!-- ========================================================================= -->
  <!-- MODAL 3: PROTECTED DIARY PIN LOCK MODAL                                   -->
  <!-- ========================================================================= -->
  <div id="pinModal" class="fixed inset-0 z-50 bg-stone-900/80 backdrop-blur-md hidden items-center justify-center p-4">
    <div class="bg-white rounded-3xl max-w-sm w-full p-6 sm:p-7 border-2 border-rose-200 shadow-2xl relative text-center">
      <button onclick="closePinModal()" class="absolute top-4 right-4 w-8 h-8 rounded-full bg-stone-100 text-stone-500 hover:text-stone-800 flex items-center justify-center">
        <i class="fa-solid fa-xmark"></i>
      </button>

      <div class="w-14 h-14 mx-auto rounded-2xl bg-gradient-to-tr from-brand-600 to-amber-500 text-white flex items-center justify-center text-2xl shadow-lg shadow-brand-500/30 mb-4">
        <i class="fa-solid fa-lock"></i>
      </div>

      <h3 class="font-serif font-bold text-xl text-stone-900">Protected Tailor Diary</h3>
      <p class="text-xs text-stone-600 mt-1 mb-5">
        Yeh hisaab sirf <strong>Mummy</strong> aur <strong>Aapke</strong> liye hai. Kripya PIN darj karein.
      </p>

      <!-- Mode Selector -->
      <div class="flex items-center justify-center gap-2 mb-4 bg-rose-50 p-1 rounded-xl border border-rose-100">
        <button id="authTabMummy" type="button" onclick="setAuthMode('mummy')" class="flex-1 py-1.5 px-3 rounded-lg text-xs font-bold bg-white text-brand-700 shadow-xs transition">
          <i class="fa-solid fa-user-nurse mr-1"></i> Mummy PIN
        </button>
        <button id="authTabAdmin" type="button" onclick="setAuthMode('admin')" class="flex-1 py-1.5 px-3 rounded-lg text-xs font-bold text-stone-600 hover:text-brand-700 transition">
          <i class="fa-solid fa-shield-halved mr-1"></i> Master Key
        </button>
      </div>

      <!-- PIN Input Display -->
      <div class="relative mb-4">
        <input id="secretPinInput" type="password" maxlength="10" placeholder="••••" readonly class="w-full text-center tracking-[0.4em] font-mono text-2xl py-3 px-4 rounded-xl border-2 border-rose-200 focus:border-brand-600 focus:outline-hidden bg-stone-50 text-stone-900">
        <button type="button" onclick="clearPinInput()" class="absolute right-3 top-3 text-stone-400 hover:text-stone-600">
          <i class="fa-solid fa-delete-left text-lg"></i>
        </button>
      </div>

      <!-- Quick Numeric Keypad for Screen Tap -->
      <div id="quickKeypad" class="grid grid-cols-3 gap-2 mb-4">
        <button type="button" onclick="appendPin('1')" class="py-2.5 rounded-xl bg-stone-100 hover:bg-rose-100 text-stone-800 font-bold text-lg active:scale-95 transition">1</button>
        <button type="button" onclick="appendPin('2')" class="py-2.5 rounded-xl bg-stone-100 hover:bg-rose-100 text-stone-800 font-bold text-lg active:scale-95 transition">2</button>
        <button type="button" onclick="appendPin('3')" class="py-2.5 rounded-xl bg-stone-100 hover:bg-rose-100 text-stone-800 font-bold text-lg active:scale-95 transition">3</button>
        <button type="button" onclick="appendPin('4')" class="py-2.5 rounded-xl bg-stone-100 hover:bg-rose-100 text-stone-800 font-bold text-lg active:scale-95 transition">4</button>
        <button type="button" onclick="appendPin('5')" class="py-2.5 rounded-xl bg-stone-100 hover:bg-rose-100 text-stone-800 font-bold text-lg active:scale-95 transition">5</button>
        <button type="button" onclick="appendPin('6')" class="py-2.5 rounded-xl bg-stone-100 hover:bg-rose-100 text-stone-800 font-bold text-lg active:scale-95 transition">6</button>
        <button type="button" onclick="appendPin('7')" class="py-2.5 rounded-xl bg-stone-100 hover:bg-rose-100 text-stone-800 font-bold text-lg active:scale-95 transition">7</button>
        <button type="button" onclick="appendPin('8')" class="py-2.5 rounded-xl bg-stone-100 hover:bg-rose-100 text-stone-800 font-bold text-lg active:scale-95 transition">8</button>
        <button type="button" onclick="appendPin('9')" class="py-2.5 rounded-xl bg-stone-100 hover:bg-rose-100 text-stone-800 font-bold text-lg active:scale-95 transition">9</button>
        <button type="button" onclick="clearPinInput()" class="py-2.5 rounded-xl bg-stone-200 hover:bg-stone-300 text-stone-700 font-bold text-xs uppercase active:scale-95 transition">Clear</button>
        <button type="button" onclick="appendPin('0')" class="py-2.5 rounded-xl bg-stone-100 hover:bg-rose-100 text-stone-800 font-bold text-lg active:scale-95 transition">0</button>
        <button type="button" onclick="submitPinUnlock()" class="py-2.5 rounded-xl bg-brand-600 hover:bg-brand-700 text-white font-bold text-sm active:scale-95 transition">OK</button>
      </div>

      <div id="pinErrorMsg" class="text-xs text-rose-600 font-bold mb-3 hidden">
        <i class="fa-solid fa-triangle-exclamation mr-1"></i> Galat Passcode! Kripya sahi PIN daalein.
      </div>

      <div class="text-[11px] text-stone-500 bg-stone-50 p-2.5 rounded-xl border border-stone-200 leading-tight">
        <span>🔑 <strong>Mummy PIN:</strong> <code>1234</code></span> &bull; 
        <span>🛡️ <strong>Master Key:</strong> <code>admin99</code></span>
      </div>
    </div>
  </div>

  <!-- ========================================================================= -->
  <!-- MODAL 4: CHANGE PIN MODAL                                                 -->
  <!-- ========================================================================= -->
  <div id="changePinModal" class="fixed inset-0 z-50 bg-stone-900/75 backdrop-blur-xs hidden items-center justify-center p-4">
    <div class="bg-white rounded-3xl max-w-sm w-full p-6 border border-stone-200 shadow-2xl relative">
      <button onclick="closeChangePinModal()" class="absolute top-4 right-4 text-stone-400 hover:text-stone-700">
        <i class="fa-solid fa-xmark text-lg"></i>
      </button>

      <h3 class="font-serif font-bold text-lg text-stone-900 mb-1">Passcode Badlein</h3>
      <p class="text-xs text-stone-500 mb-4">Mummy ka 4-digit PIN ya apna Master password update karein.</p>

      <form id="changePinForm" onsubmit="saveNewPasscodes(event)" class="space-y-3">
        <div>
          <label class="block text-[11px] font-bold text-stone-700 uppercase mb-1">Mummy's New PIN (4 Digits)</label>
          <input type="password" id="newMummyPinInput" maxlength="4" placeholder="e.g. 5678" required class="w-full text-sm p-3 rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden">
        </div>
        <div>
          <label class="block text-[11px] font-bold text-stone-700 uppercase mb-1">Aapka New Master Passcode</label>
          <input type="text" id="newMasterKeyInput" placeholder="e.g. mysecret77" required class="w-full text-sm p-3 rounded-xl border border-stone-200 focus:border-brand-500 focus:outline-hidden">
        </div>
        <button type="submit" class="w-full py-3 bg-brand-600 hover:bg-brand-700 text-white rounded-xl font-bold text-xs uppercase tracking-wider transition">
          Naya Passcode Save Karein
        </button>
      </form>
    </div>
  </div>

  <!-- ========================================================================= -->
  <!-- MODAL 5: NEW ORDER / MEASUREMENTS MODAL (MUMMY'S REGISTER)                -->
  <!-- ========================================================================= -->
  <div id="orderEntryModal" class="fixed inset-0 z-50 bg-stone-900/80 backdrop-blur-xs hidden items-center justify-center p-4">
    <div class="bg-white rounded-3xl max-w-2xl w-full p-6 sm:p-7 border border-rose-200 shadow-2xl relative max-h-[90vh] overflow-y-auto custom-scroll">
      <button onclick="closeOrderModal()" class="absolute top-4 right-4 text-stone-400 hover:text-stone-700">
        <i class="fa-solid fa-xmark text-lg"></i>
      </button>

      <div class="flex items-center gap-2.5 mb-5">
        <div class="w-10 h-10 rounded-xl bg-brand-100 text-brand-600 flex items-center justify-center text-lg">
          <i class="fa-solid fa-ruler"></i>
        </div>
        <div>
          <h3 id="orderModalTitle" class="font-serif font-bold text-lg text-stone-900">Naya Tailor Order & Naap</h3>
          <p class="text-xs text-stone-500">Grahak ka naap aur advance hisaab bharein.</p>
        </div>
      </div>

      <form id="orderForm" onsubmit="saveTailorOrder(event)" class="space-y-4">
        <input type="hidden" id="editOrderId" value="">

        <!-- Basic details -->
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
          <div>
            <label class="block text-[11px] font-bold text-stone-700 uppercase mb-1">Customer Ka Naam *</label>
            <input type="text" id="ordCustomerName" required placeholder="Naam" class="w-full p-2.5 text-xs rounded-xl border border-stone-200 focus:border-brand-500">
          </div>
          <div>
            <label class="block text-[11px] font-bold text-stone-700 uppercase mb-1">WhatsApp Number *</label>
            <input type="tel" id="ordCustomerPhone" required placeholder="Mobile No" class="w-full p-2.5 text-xs rounded-xl border border-stone-200 focus:border-brand-500">
          </div>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-3 gap-3">
          <div>
            <label class="block text-[11px] font-bold text-stone-700 uppercase mb-1">Garment *</label>
            <select id="ordGarment" required class="w-full p-2.5 text-xs rounded-xl border border-stone-200 bg-white">
              <option value="Designer Blouse">Designer Blouse</option>
              <option value="Suit & Plazo/Pant">Suit & Plazo / Pant</option>
              <option value="Anarkali / Gown">Anarkali / Gown</option>
              <option value="Lehenga Choli">Lehenga Choli</option>
              <option value="Only Kurti / Top">Only Kurti / Top</option>
              <option value="Other">Other</option>
            </select>
          </div>
          <div>
            <label class="block text-[11px] font-bold text-stone-700 uppercase mb-1">Delivery / Trial Date</label>
            <input type="date" id="ordDeliveryDate" class="w-full p-2.5 text-xs rounded-xl border border-stone-200">
          </div>
          <div>
            <label class="block text-[11px] font-bold text-stone-700 uppercase mb-1">Current Status</label>
            <select id="ordStatus" class="w-full p-2.5 text-xs rounded-xl border border-stone-200 bg-white">
              <option value="Order Received">Order Received</option>
              <option value="Fabric Bought">Fabric Bought (कपड़ा आ गया)</option>
              <option value="In Stitching">In Stitching (सिलाई चालू)</option>
              <option value="Ready for Trial">Ready for Trial (तैयार)</option>
              <option value="Delivered">Delivered (दिया गया)</option>
            </select>
          </div>
        </div>

        <!-- URGENT FLAG IN DIARY -->
        <div class="p-3 rounded-xl bg-amber-50 border border-amber-200 flex items-center justify-between">
          <div class="flex items-center gap-2">
            <input type="checkbox" id="ordIsUrgent" onchange="calculateDiaryBalance()" class="w-4 h-4 text-brand-600 rounded-sm">
            <label for="ordIsUrgent" class="text-xs font-bold text-amber-900 cursor-pointer">
              ⚡ Emergency / Urgent Order
            </label>
          </div>
          <div class="flex items-center gap-1">
            <span class="text-xs text-amber-800 font-bold">Urgent Charge: ₹</span>
            <input type="number" id="ordUrgentCharge" value="0" min="0" oninput="calculateDiaryBalance()" class="w-20 p-1.5 text-xs rounded-lg border border-amber-300 text-center font-bold">
          </div>
        </div>

        <!-- NAAP SECTION (MEASUREMENTS IN INCHES) -->
        <div class="bg-rose-50/60 p-4 rounded-2xl border border-rose-100">
          <div class="flex items-center justify-between mb-3">
            <span class="text-xs font-bold text-brand-800 uppercase flex items-center gap-1.5">
              <i class="fa-solid fa-tape"></i>
              <span>Customer Ka Naap (Inches Me)</span>
            </span>
            <span class="text-[10px] text-stone-500">Mummy ke machine table ke hisaab se</span>
          </div>

          <div class="grid grid-cols-2 sm:grid-cols-4 gap-2.5">
            <div>
              <label class="text-[10px] font-bold text-stone-600 block">Lambi (Length)</label>
              <input type="text" id="naapLength" placeholder="e.g. 14 / 38" class="w-full p-2 text-xs rounded-lg border border-stone-200 bg-white">
            </div>
            <div>
              <label class="text-[10px] font-bold text-stone-600 block">Seena (Chest)</label>
              <input type="text" id="naapChest" placeholder="e.g. 36" class="w-full p-2 text-xs rounded-lg border border-stone-200 bg-white">
            </div>
            <div>
              <label class="text-[10px] font-bold text-stone-600 block">Kamar (Waist)</label>
              <input type="text" id="naapWaist" placeholder="e.g. 30" class="w-full p-2 text-xs rounded-lg border border-stone-200 bg-white">
            </div>
            <div>
              <label class="text-[10px] font-bold text-stone-600 block">Teera (Shoulder)</label>
              <input type="text" id="naapShoulder" placeholder="e.g. 13.5" class="w-full p-2 text-xs rounded-lg border border-stone-200 bg-white">
            </div>
            <div>
              <label class="text-[10px] font-bold text-stone-600 block">Asteen (Sleeve)</label>
              <input type="text" id="naapSleeve" placeholder="e.g. 10 / 5" class="w-full p-2 text-xs rounded-lg border border-stone-200 bg-white">
            </div>
            <div>
              <label class="text-[10px] font-bold text-stone-600 block">Gala (Front/Back)</label>
              <input type="text" id="naapNeck" placeholder="e.g. 6.5 / 8" class="w-full p-2 text-xs rounded-lg border border-stone-200 bg-white">
            </div>
            <div>
              <label class="text-[10px] font-bold text-stone-600 block">Hips</label>
              <input type="text" id="naapHip" placeholder="e.g. 38" class="w-full p-2 text-xs rounded-lg border border-stone-200 bg-white">
            </div>
            <div>
              <label class="text-[10px] font-bold text-stone-600 block">Pant / Salwar</label>
              <input type="text" id="naapBottom" placeholder="e.g. 36" class="w-full p-2 text-xs rounded-lg border border-stone-200 bg-white">
            </div>
          </div>
        </div>

        <!-- HISAAB KITAB (FINANCIALS) -->
        <div class="bg-amber-50/60 p-4 rounded-2xl border border-amber-100">
          <span class="text-xs font-bold text-amber-900 uppercase block mb-3">
            <i class="fa-solid fa-calculator mr-1"></i> Hisaab-Kitab (Advance & Balance Silai)
          </span>

          <div class="grid grid-cols-2 sm:grid-cols-4 gap-2.5">
            <div>
              <label class="text-[10px] font-bold text-stone-600 block">Silai Labor (₹)</label>
              <input type="number" id="finSilai" value="0" min="0" oninput="calculateDiaryBalance()" class="w-full p-2 text-xs rounded-lg border border-stone-200 bg-white font-bold">
            </div>
            <div>
              <label class="text-[10px] font-bold text-stone-600 block">Shopping/Kapda (₹)</label>
              <input type="number" id="finFabric" value="0" min="0" oninput="calculateDiaryBalance()" class="w-full p-2 text-xs rounded-lg border border-stone-200 bg-white">
            </div>
            <div>
              <label class="text-[10px] font-bold text-emerald-700 block">Advance Mila (₹)</label>
              <input type="number" id="finAdvance" value="0" min="0" oninput="calculateDiaryBalance()" class="w-full p-2 text-xs rounded-lg border border-emerald-300 bg-emerald-50 text-emerald-800 font-bold">
            </div>
            <div>
              <label class="text-[10px] font-bold text-brand-700 block">Bacha Paisa (Due)</label>
              <div id="finBalanceDisplay" class="p-2 text-xs rounded-lg bg-rose-100 border border-rose-300 text-brand-800 font-black text-center">
                ₹0
              </div>
            </div>
          </div>
        </div>

        <div>
          <label class="block text-[11px] font-bold text-stone-700 uppercase mb-1">Special Notes / Latkan / Astar</label>
          <textarea id="ordNotes" rows="2" placeholder="e.g. Maroon matching lace lagani hai, piping golden hogi..." class="w-full p-2.5 text-xs rounded-xl border border-stone-200"></textarea>
        </div>
  <!-- FLOATING CUSTOMER CARE BUTTON (AAPKA NUMBER 7725081052) -->
  <div class="fixed bottom-6 left-6 z-40 flex flex-col gap-2">
    <a href="https://wa.me/917725081052?text=Namaste!%20Wearables%20customer%20care%20se%20help%20chahiye." target="_blank" class="w-12 h-12 rounded-full bg-emerald-600 hover:bg-emerald-700 text-white flex items-center justify-center text-2xl shadow-xl hover:scale-105 transition active:scale-95 group relative" title="Customer Care WhatsApp">
      <i class="fa-brands fa-whatsapp"></i>
      <span class="absolute left-14 bg-stone-900 text-white text-[11px] font-bold px-2.5 py-1 rounded-lg opacity-0 group-hover:opacity-100 transition whitespace-nowrap shadow-md pointer-events-none">Customer Care: 7725081052</span>
    </a>
  </div>

  <!-- TOAST NOTIFICATION -->
  <div id="toastNotification" class="fixed bottom-6 right-6 z-50 bg-stone-900 text-white text-xs px-4 py-3 rounded-2xl shadow-xl flex items-center gap-2 transform translate-y-20 opacity-0 transition-all duration-300">
    <i class="fa-solid fa-circle-check text-emerald-400"></i>
    <span id="toastMsg">Changes saved!</span>
  </div>

  <!-- ================= JAVASCRIPT LOGIC ================= -->
  <script>
    // Storage Key
    const STORAGE_KEY = 'wearables_orders_db';
    let currentAuthMode = 'mummy';
    let activeFilter = 'all';

    // Seed Initial Mock Orders if empty
    function initializeOrders() {
      const stored = localStorage.getItem(STORAGE_KEY);
      if (!stored) {
        const initialOrders = [
          {
            id: 'WB-101',
            customerName: 'Pooja Verma',
            phone: '9826011223',
            garment: 'Designer Blouse',
            fabricMode: 'Mummy Kharidengi (Advance)',
            deliveryDate: '2026-10-20',
            status: 'In Stitching',
            isUrgent: true,
            urgentCharge: 150,
            silaiCost: 450,
            fabricCost: 350,
            advancePaid: 400,
            notes: 'Princess cut, potli buttons pichhe, golden piping',
            naap: { length: '14.5', chest: '36', waist: '30', shoulder: '14', sleeve: '10', neck: '6.5/7.5', hip: '', bottom: '' }
          },
          {
            id: 'WB-102',
            customerName: 'Sunita Jain',
            phone: '9876543210',
            garment: 'Suit & Plazo/Pant',
            fabricMode: 'Customer Layega',
            deliveryDate: '2026-10-25',
            status: 'Order Received',
            isUrgent: false,
            urgentCharge: 0,
            silaiCost: 550,
            fabricCost: 0,
            advancePaid: 200,
            notes: 'Afgani salwar, boat neck gala',
            naap: { length: '40', chest: '38', waist: '34', shoulder: '14.5', sleeve: '16', neck: '5.5/6', hip: '41', bottom: '37' }
          }
        ];
        localStorage.setItem(STORAGE_KEY, JSON.stringify(initialOrders));
      }
    }

    function getOrders() {
      return JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
    }

    function saveOrders(orders) {
      localStorage.setItem(STORAGE_KEY, JSON.stringify(orders));
      renderOrdersTable();
    }

    function generateNextToken() {
      const orders = getOrders();
      let maxNum = 100;
      orders.forEach(o => {
        if (o.id && o.id.startsWith('WB-')) {
          const num = parseInt(o.id.replace('WB-', ''));
          if (!isNaN(num) && num > maxNum) maxNum = num;
        }
      });
      return `WB-${maxNum + 1}`;
    }

    // Switch Views
    function switchView(view) {
      const custSec = document.getElementById('customerSection');
      const admSec = document.getElementById('adminSection');
      const custBtn = document.getElementById('navCustomerBtn');

      if (view === 'customer') {
        custSec.classList.remove('hidden');
        admSec.classList.add('hidden');
        custBtn.className = "px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold transition flex items-center gap-1.5 bg-brand-50 text-brand-700 border border-brand-200";
      } else {
        custSec.classList.add('hidden');
        admSec.classList.remove('hidden');
        custBtn.className = "px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold transition flex items-center gap-1.5 bg-white text-stone-600 hover:bg-stone-50 border border-stone-200";
        renderOrdersTable();
      }
    }

    // PIN / AUTH LOGIC
    function getStoredAuthKeys() {
      const storedMummy = localStorage.getItem('wearables_mummy_pin') || '1234';
      const storedAdmin = localStorage.getItem('wearables_master_key') || 'admin99';
      return { mummyPin: storedMummy, adminKey: storedAdmin };
    }

    function setAuthMode(mode) {
      currentAuthMode = mode;
      const mummyBtn = document.getElementById('authTabMummy');
      const adminBtn = document.getElementById('authTabAdmin');
      const input = document.getElementById('secretPinInput');
      const keypad = document.getElementById('quickKeypad');

      if (mode === 'mummy') {
        mummyBtn.className = "flex-1 py-1.5 px-3 rounded-lg text-xs font-bold bg-white text-brand-700 shadow-xs transition";
        adminBtn.className = "flex-1 py-1.5 px-3 rounded-lg text-xs font-bold text-stone-600 hover:text-brand-700 transition";
        input.placeholder = "••••";
        input.readOnly = true;
        keypad.classList.remove('hidden');
      } else {
        adminBtn.className = "flex-1 py-1.5 px-3 rounded-lg text-xs font-bold bg-white text-brand-700 shadow-xs transition";
        mummyBtn.className = "flex-1 py-1.5 px-3 rounded-lg text-xs font-bold text-stone-600 hover:text-brand-700 transition";
        input.placeholder = "Master Key";
        input.readOnly = false;
        keypad.classList.add('hidden');
        input.focus();
      }
      input.value = "";
      document.getElementById('pinErrorMsg').classList.add('hidden');
    }

    function appendPin(n) {
      const input = document.getElementById('secretPinInput');
      if (input.value.length < 8) input.value += n;
      document.getElementById('pinErrorMsg').classList.add('hidden');
      if (currentAuthMode === 'mummy' && input.value.length === 4) {
        submitPinUnlock();
      }
    }

    function clearPinInput() {
      document.getElementById('secretPinInput').value = "";
      document.getElementById('pinErrorMsg').classList.add('hidden');
    }

    function tryOpenAdminDiary() {
      const isAuth = sessionStorage.getItem('wearables_authenticated') === 'true';
      if (isAuth) {
        switchView('admin');
      } else {
        const modal = document.getElementById('pinModal');
        modal.classList.remove('hidden');
        modal.classList.add('flex');
        clearPinInput();
        setAuthMode('mummy');
      }
    }

    function closePinModal() {
      const modal = document.getElementById('pinModal');
      modal.classList.add('hidden');
      modal.classList.remove('flex');
      clearPinInput();
    }

    function submitPinUnlock() {
      const val = document.getElementById('secretPinInput').value.trim();
      const { mummyPin, adminKey } = getStoredAuthKeys();
      const err = document.getElementById('pinErrorMsg');

      if (val === mummyPin || val === adminKey) {
        sessionStorage.setItem('wearables_authenticated', 'true');
        closePinModal();
        switchView('admin');
        showToast("🔓 Diary Unlocked! Namaste.");
      } else {
        err.classList.remove('hidden');
        document.getElementById('secretPinInput').value = "";
      }
    }

    function lockDiaryNow() {
      sessionStorage.removeItem('wearables_authenticated');
      switchView('customer');
      showToast("🔒 Diary Lock Kar Di Gayi!");
    }

    function openChangePinModal() {
      const { mummyPin, adminKey } = getStoredAuthKeys();
      document.getElementById('newMummyPinInput').value = mummyPin;
      document.getElementById('newMasterKeyInput').value = adminKey;
      const modal = document.getElementById('changePinModal');
      modal.classList.remove('hidden');
      modal.classList.add('flex');
    }

    function closeChangePinModal() {
      const modal = document.getElementById('changePinModal');
      modal.classList.add('hidden');
      modal.classList.remove('flex');
    }

    function saveNewPasscodes(e) {
      e.preventDefault();
      const m = document.getElementById('newMummyPinInput').value.trim();
      const a = document.getElementById('newMasterKeyInput').value.trim();
      if (!m || !a) return;
      localStorage.setItem('wearables_mummy_pin', m);
      localStorage.setItem('wearables_master_key', a);
      closeChangePinModal();
      showToast("✅ Naya Passcode Set Ho Gaya!");
    }

    // CUSTOMER BOOKING FORM
    function prefillGarment(name) {
      document.getElementById('custGarment').value = name;
      document.getElementById('orderFormAnchor').scrollIntoView({ behavior: 'smooth' });
    }

    function checkIndoreEligibility() {
      const city = document.getElementById('custCity').value;
      const urgentBox = document.getElementById('custIsUrgent');
      const notice = document.getElementById('urgentCityNotice');

      if (city !== 'Indore' && urgentBox.checked) {
        urgentBox.checked = false;
        notice.classList.remove('hidden');
        showToast("⚠️ Urgent Silai sirf Indore me uplabdh hai!");
      } else {
        notice.classList.add('hidden');
      }
    }

    function validateUrgentCity(el) {
      const city = document.getElementById('custCity').value;
      const notice = document.getElementById('urgentCityNotice');
      if (el.checked && city !== 'Indore') {
        el.checked = false;
        notice.classList.remove('hidden');
        showToast("⚠️ Maaf kijiye, Urgent order sirf Indore ke liye hai!");
      } else {
        notice.classList.add('hidden');
      }
    }

    function handleCustomerBooking(e) {
      e.preventDefault();
      const token = generateNextToken();
      const name = document.getElementById('custName').value.trim();
      const phone = document.getElementById('custPhone').value.trim();
      const city = document.getElementById('custCity').value;
      const area = document.getElementById('custArea').value.trim();
      const garment = document.getElementById('custGarment').value;
      const fabricMode = document.getElementById('custFabricMode').value;
      const isUrgent = document.getElementById('custIsUrgent').checked;
      const notes = document.getElementById('custNotes').value.trim();

      if (isUrgent && city !== 'Indore') {
        showToast("⚠️ Urgent order sirf Indore ke liye available hai!");
        return;
      }

      const locationDetails = city === 'Indore' ? (area ? `Indore (${area})` : 'Indore') : 'Outside Indore';

      const newOrder = {
        id: token,
        customerName: name,
        phone: phone,
        city: city,
        area: area,
        garment: garment,
        fabricMode: fabricMode,
        deliveryDate: '',
        status: 'Order Received',
        isUrgent: isUrgent,
        urgentCharge: isUrgent ? 150 : 0,
        silaiCost: 0,
        fabricCost: 0,
        advancePaid: 0,
        notes: notes ? `${notes} [📍 ${locationDetails}]` : `[📍 ${locationDetails}]`,
        naap: { length: '', chest: '', waist: '', shoulder: '', sleeve: '', neck: '', hip: '', bottom: '' }
      };

      const orders = getOrders();
      orders.unshift(newOrder);
      saveOrders(orders);

      // Show Token Modal
      document.getElementById('confirmedTokenId').innerText = token;
      document.getElementById('confirmedCustomerName').innerText = `${name} (${locationDetails})`;
      document.getElementById('confirmedGarment').innerText = garment + (isUrgent ? ' ⚡ (Urgent - Indore Special)' : '');

      // Direct WhatsApp to Mummy's Number (6265741833)
      const msg = encodeURIComponent(`Namaste Mummy ji! Naya Wearables Order Aaya Hai:%0A🎟️ Token No: ${token}%0A👤 Customer: ${name} (${phone})%0A📍 Location: ${locationDetails}%0A✂️ Garment: ${garment}%0A⚡ Urgent: ${isUrgent ? 'HAAN (Sirf Indore 24-48 Ghante)' : 'Normal'}%0A🛍️ Material Plan: ${fabricMode}%0A📝 Notes: ${notes || 'None'}`);
      document.getElementById('sendTokenWhatsAppBtn').onclick = () => {
        window.open(`https://wa.me/916265741833?text=${msg}`, '_blank');
      };

      const tModal = document.getElementById('tokenModal');
      tModal.classList.remove('hidden');
      tModal.classList.add('flex');

      document.getElementById('publicBookingForm').reset();
      document.getElementById('custCity').value = "Indore";
    }

    function copyPaymentNumber() {
      const tempInput = document.createElement("input");
      tempInput.value = "6265741833";
      document.body.appendChild(tempInput);
      tempInput.select();
      document.execCommand("copy");
      document.body.removeChild(tempInput);
      showToast("📋 Mummy ka Payment No. (6265741833) copy ho gaya!");
    }

    function closeTokenModal() {
      const tModal = document.getElementById('tokenModal');
      tModal.classList.add('hidden');
      tModal.classList.remove('flex');
    }

    // ORDER TRACKING LOGIC
    function openTrackModal() {
      const modal = document.getElementById('trackModal');
      modal.classList.remove('hidden');
      modal.classList.add('flex');
    }

    function closeTrackModal() {
      const modal = document.getElementById('trackModal');
      modal.classList.add('hidden');
      modal.classList.remove('flex');
      document.getElementById('trackResultArea').classList.add('hidden');
    }

    function searchOrderStatus() {
      const query = document.getElementById('trackSearchInput').value.trim().toLowerCase();
      const res = document.getElementById('trackResultArea');
      if (!query) return;

      const orders = getOrders();
      const match = orders.find(o => 
        (o.id && o.id.toLowerCase() === query) || 
        (o.phone && o.phone.includes(query))
      );

      res.classList.remove('hidden');
      if (!match) {
        res.innerHTML = `
          <div class="p-4 rounded-2xl bg-rose-50 text-brand-700 text-xs font-bold text-center border border-rose-200">
            Koi order nahi mila. Token Number (jaise WB-101) ya sahi Phone number daalein.
          </div>
        `;
        return;
      }

      const totalBill = (match.silaiCost || 0) + (match.fabricCost || 0) + (match.urgentCharge || 0);
      const balance = Math.max(0, totalBill - (match.advancePaid || 0));

      res.innerHTML = `
        <div class="p-5 rounded-2xl bg-stone-50 border border-stone-200 text-xs space-y-3">
          <div class="flex items-center justify-between border-b border-stone-200 pb-2">
            <div>
              <span class="text-[10px] font-bold text-stone-400 uppercase">Token ID</span>
              <div class="text-base font-black text-brand-700 font-mono">${match.id}</div>
            </div>
            <span class="px-2.5 py-1 rounded-full text-[11px] font-bold ${match.status === 'Ready for Trial' ? 'bg-purple-100 text-purple-800' : 'bg-amber-100 text-amber-800'}">
              ${match.status}
            </span>
          </div>

          <div class="grid grid-cols-2 gap-2">
            <div><strong>Grahak:</strong> ${match.customerName}</div>
            <div><strong>Garment:</strong> ${match.garment}</div>
            <div><strong>Delivery Date:</strong> ${match.deliveryDate || 'Tay ki ja rahi hai'}</div>
            <div><strong>Priority:</strong> ${match.isUrgent ? '⚡ Urgent Delivery' : 'Normal'}</div>
          </div>

          <div class="p-3 bg-white rounded-xl border border-stone-200 flex justify-between items-center">
            <div>
              <span class="text-[10px] text-stone-400 uppercase font-bold block">Silai & Fabric Total</span>
              <span class="text-sm font-bold text-stone-800">₹${totalBill}</span>
            </div>
            <div class="text-right">
              <span class="text-[10px] text-brand-600 uppercase font-bold block">Delivery Par Bacha Paisa</span>
              <span class="text-sm font-black text-brand-700">₹${balance}</span>
            </div>
          </div>
        </div>
      `;
    }

    // DIARY LOGIC (CALCULATIONS & ORDERS)
    function calculateDiaryBalance() {
      const silai = parseFloat(document.getElementById('finSilai').value) || 0;
      const fabric = parseFloat(document.getElementById('finFabric').value) || 0;
      const advance = parseFloat(document.getElementById('finAdvance').value) || 0;
      const isUrgent = document.getElementById('ordIsUrgent').checked;
      const urgentCharge = isUrgent ? (parseFloat(document.getElementById('ordUrgentCharge').value) || 0) : 0;

      const total = silai + fabric + urgentCharge;
      const bal = Math.max(0, total - advance);
      document.getElementById('finBalanceDisplay').innerText = `₹${bal}`;
    }

    function openNewOrderModal() {
      document.getElementById('orderForm').reset();
      document.getElementById('editOrderId').value = "";
      document.getElementById('orderModalTitle').innerText = "Naya Tailor Order & Naap";
      calculateDiaryBalance();
      const modal = document.getElementById('orderEntryModal');
      modal.classList.remove('hidden');
      modal.classList.add('flex');
    }

    function closeOrderModal() {
      const modal = document.getElementById('orderEntryModal');
      modal.classList.add('hidden');
      modal.classList.remove('flex');
    }

    function saveTailorOrder(e) {
      e.preventDefault();
      const editId = document.getElementById('editOrderId').value;
      const token = editId ? editId : generateNextToken();
      const isUrgent = document.getElementById('ordIsUrgent').checked;

      const orderObj = {
        id: token,
        customerName: document.getElementById('ordCustomerName').value.trim(),
        phone: document.getElementById('ordCustomerPhone').value.trim(),
        garment: document.getElementById('ordGarment').value,
        deliveryDate: document.getElementById('ordDeliveryDate').value,
        status: document.getElementById('ordStatus').value,
        isUrgent: isUrgent,
        urgentCharge: isUrgent ? (parseFloat(document.getElementById('ordUrgentCharge').value) || 0) : 0,
        silaiCost: parseFloat(document.getElementById('finSilai').value) || 0,
        fabricCost: parseFloat(document.getElementById('finFabric').value) || 0,
        advancePaid: parseFloat(document.getElementById('finAdvance').value) || 0,
        notes: document.getElementById('ordNotes').value.trim(),
        naap: {
          length: document.getElementById('naapLength').value.trim(),
          chest: document.getElementById('naapChest').value.trim(),
          waist: document.getElementById('naapWaist').value.trim(),
          shoulder: document.getElementById('naapShoulder').value.trim(),
          sleeve: document.getElementById('naapSleeve').value.trim(),
          neck: document.getElementById('naapNeck').value.trim(),
          hip: document.getElementById('naapHip').value.trim(),
          bottom: document.getElementById('naapBottom').value.trim(),
        }
      };

      const orders = getOrders();
      if (editId) {
        const idx = orders.findIndex(o => o.id === editId);
        if (idx !== -1) orders[idx] = orderObj;
      } else {
        orders.unshift(orderObj);
      }

      saveOrders(orders);
      closeOrderModal();
      showToast("✅ Order Mummy Ki Diary Me Save Ho Gaya!");
    }

    function editOrder(id) {
      const orders = getOrders();
      const order = orders.find(o => o.id === id);
      if (!order) return;

      document.getElementById('editOrderId').value = order.id;
      document.getElementById('orderModalTitle').innerText = `Edit Order: ${order.id}`;
      document.getElementById('ordCustomerName').value = order.customerName || '';
      document.getElementById('ordCustomerPhone').value = order.phone || '';
      document.getElementById('ordGarment').value = order.garment || 'Designer Blouse';
      document.getElementById('ordDeliveryDate').value = order.deliveryDate || '';
      document.getElementById('ordStatus').value = order.status || 'Order Received';
      
      document.getElementById('ordIsUrgent').checked = !!order.isUrgent;
      document.getElementById('ordUrgentCharge').value = order.urgentCharge || 0;
      document.getElementById('finSilai').value = order.silaiCost || 0;
      document.getElementById('finFabric').value = order.fabricCost || 0;
      document.getElementById('finAdvance').value = order.advancePaid || 0;
      document.getElementById('ordNotes').value = order.notes || '';

      const n = order.naap || {};
      document.getElementById('naapLength').value = n.length || '';
      document.getElementById('naapChest').value = n.chest || '';
      document.getElementById('naapWaist').value = n.waist || '';
      document.getElementById('naapShoulder').value = n.shoulder || '';
      document.getElementById('naapSleeve').value = n.sleeve || '';
      document.getElementById('naapNeck').value = n.neck || '';
      document.getElementById('naapHip').value = n.hip || '';
      document.getElementById('naapBottom').value = n.bottom || '';

      calculateDiaryBalance();

      const modal = document.getElementById('orderEntryModal');
      modal.classList.remove('hidden');
      modal.classList.add('flex');
    }

    function deleteOrder(id) {
      if (confirm(`Kya aap Token ${id} ko diary se hatana chahte hain?`)) {
        let orders = getOrders();
        orders = orders.filter(o => o.id !== id);
        saveOrders(orders);
        showToast("🗑️ Order Hata Diya Gaya");
      }
    }

    function setFilter(flt) {
      activeFilter = flt;
      document.getElementById('filterAll').className = flt === 'all' ? "px-3 py-1.5 rounded-lg text-xs font-bold bg-brand-600 text-white shrink-0" : "px-3 py-1.5 rounded-lg text-xs font-bold bg-stone-100 text-stone-600 shrink-0";
      document.getElementById('filterProgress').className = flt === 'in_progress' ? "px-3 py-1.5 rounded-lg text-xs font-bold bg-brand-600 text-white shrink-0" : "px-3 py-1.5 rounded-lg text-xs font-bold bg-stone-100 text-stone-600 shrink-0";
      document.getElementById('filterReady').className = flt === 'ready' ? "px-3 py-1.5 rounded-lg text-xs font-bold bg-brand-600 text-white shrink-0" : "px-3 py-1.5 rounded-lg text-xs font-bold bg-stone-100 text-stone-600 shrink-0";
      document.getElementById('filterDelivered').className = flt === 'delivered' ? "px-3 py-1.5 rounded-lg text-xs font-bold bg-brand-600 text-white shrink-0" : "px-3 py-1.5 rounded-lg text-xs font-bold bg-stone-100 text-stone-600 shrink-0";
      renderOrdersTable();
    }

    function sendWhatsAppBill(id) {
      const orders = getOrders();
      const order = orders.find(o => o.id === id);
      if (!order) return;

      const total = (order.silaiCost || 0) + (order.fabricCost || 0) + (order.urgentCharge || 0);
      const balance = Math.max(0, total - (order.advancePaid || 0));

      const msg = encodeURIComponent(
        `👗 *WEARABLES BOUTIQUE BILL SLIP*\n` +
        `--------------------------------\n` +
        `🎟️ *Token No:* ${order.id}\n` +
        `👤 *Customer:* ${order.customerName}\n` +
        `✂️ *Garment:* ${order.garment} ${order.isUrgent ? '⚡(Urgent)' : ''}\n` +
        `📅 *Delivery Date:* ${order.deliveryDate || 'Jaldi Batayenge'}\n` +
        `--------------------------------\n` +
        `💰 *Silai Labor:* ₹${order.silaiCost || 0}\n` +
        `🛍️ *Fabric / Material:* ₹${order.fabricCost || 0}\n` +
        (order.isUrgent ? `⚡ *Urgent Fee:* ₹${order.urgentCharge || 0}\n` : '') +
        `💵 *Advance Recd:* ₹${order.advancePaid || 0}\n` +
        `--------------------------------\n` +
        `👉 *Baki Silai (Due on Delivery):* ₹${balance}\n\n` +
        `Aap apna kapda trial karke check kar sakti hain. Dhanyawaad!`
      );

      window.open(`https://wa.me/91${order.phone}?text=${msg}`, '_blank');
    }

    function renderOrdersTable() {
      const orders = getOrders();
      const query = (document.getElementById('adminSearchInput').value || '').toLowerCase();
      const container = document.getElementById('ordersCardsContainer');

      // Update KPI
      let totalAdvance = 0;
      let totalBalance = 0;
      let urgentCount = 0;

      orders.forEach(o => {
        const tot = (o.silaiCost || 0) + (o.fabricCost || 0) + (o.urgentCharge || 0);
        totalAdvance += (o.advancePaid || 0);
        totalBalance += Math.max(0, tot - (o.advancePaid || 0));
        if (o.isUrgent) urgentCount++;
      });

      document.getElementById('statTotalOrders').innerText = orders.length;
      document.getElementById('statUrgentOrders').innerText = urgentCount;
      document.getElementById('statTotalAdvance').innerText = `₹${totalAdvance}`;
      document.getElementById('statTotalBalance').innerText = `₹${totalBalance}`;

      // Filtered List
      const filtered = orders.filter(o => {
        const matchesQuery = (o.customerName && o.customerName.toLowerCase().includes(query)) ||
                             (o.id && o.id.toLowerCase().includes(query)) ||
                             (o.phone && o.phone.includes(query));
        if (!matchesQuery) return false;

        if (activeFilter === 'in_progress') return o.status === 'In Stitching' || o.status === 'Fabric Bought';
        if (activeFilter === 'ready') return o.status === 'Ready for Trial';
        if (activeFilter === 'delivered') return o.status === 'Delivered';
        return true;
      });

      if (filtered.length === 0) {
        container.innerHTML = `
          <div class="col-span-full py-12 text-center text-stone-400 bg-white rounded-3xl border border-dashed border-stone-200">
            <i class="fa-solid fa-clipboard-list text-3xl mb-2"></i>
            <p class="text-xs">Koi order nahi mila.</p>
          </div>
        `;
        return;
      }

      container.innerHTML = filtered.map(o => {
        const total = (o.silaiCost || 0) + (o.fabricCost || 0) + (o.urgentCharge || 0);
        const bal = Math.max(0, total - (o.advancePaid || 0));
        const naap = o.naap || {};

        return `
          <div class="bg-white rounded-3xl p-5 border ${o.isUrgent ? 'border-amber-300 ring-2 ring-amber-100' : 'border-rose-100'} shadow-xs flex flex-col justify-between">
            <div>
              <div class="flex items-start justify-between gap-2 mb-3">
                <div class="flex items-center gap-2">
                  <span class="font-mono text-xs font-black px-2.5 py-1 rounded-lg bg-stone-900 text-white">${o.id}</span>
                  ${o.isUrgent ? '<span class="urgent-badge-pulse text-[10px] font-black uppercase px-2 py-0.5 rounded-md bg-amber-500 text-white flex items-center gap-1"><i class="fa-solid fa-bolt"></i> Urgent</span>' : ''}
                </div>
                <span class="text-[11px] font-bold px-2.5 py-1 rounded-full ${o.status === 'Ready for Trial' ? 'bg-purple-100 text-purple-800' : o.status === 'Delivered' ? 'bg-emerald-100 text-emerald-800' : 'bg-rose-100 text-brand-800'}">
                  ${o.status}
                </span>
              </div>

              <h4 class="font-bold text-base text-stone-900">${o.customerName}</h4>
              <p class="text-xs text-stone-500 flex items-center gap-1 mt-0.5">
                <i class="fa-solid fa-phone text-[10px]"></i> ${o.phone} &bull; <strong>${o.garment}</strong>
              </p>

              <!-- Naap Quick View Grid -->
              <div class="my-3 p-2.5 bg-rose-50/50 rounded-xl border border-rose-100 text-[11px] grid grid-cols-4 gap-1 text-center font-mono">
                <div><span class="text-[9px] text-stone-400 block font-sans">L:</span>${naap.length || '-'}</div>
                <div><span class="text-[9px] text-stone-400 block font-sans">C:</span>${naap.chest || '-'}</div>
                <div><span class="text-[9px] text-stone-400 block font-sans">W:</span>${naap.waist || '-'}</div>
                <div><span class="text-[9px] text-stone-400 block font-sans">Slv:</span>${naap.sleeve || '-'}</div>
              </div>

              <!-- Notes -->
              ${o.notes ? `<p class="text-[11px] text-stone-600 bg-amber-50/60 p-2 rounded-lg border border-amber-100 mb-3"><i class="fa-solid fa-note-sticky text-amber-500 mr-1"></i>${o.notes}</p>` : ''}
            </div>

            <div class="pt-3 border-t border-stone-100">
              <div class="flex items-center justify-between text-xs mb-3">
                <div>
                  <span class="text-[10px] text-stone-400 uppercase font-bold block">Advance Mila</span>
                  <span class="font-bold text-emerald-600">₹${o.advancePaid || 0}</span>
                </div>
                <div class="text-right">
                  <span class="text-[10px] text-brand-600 uppercase font-bold block">Silai Baki</span>
                  <span class="font-black text-brand-700 text-sm">₹${bal}</span>
                </div>
              </div>

              <!-- Actions -->
              <div class="flex items-center gap-1.5">
                <button onclick="sendWhatsAppBill('${o.id}')" class="flex-1 py-2 bg-emerald-50 hover:bg-emerald-100 text-emerald-700 rounded-xl text-xs font-bold transition flex items-center justify-center gap-1">
                  <i class="fa-brands fa-whatsapp"></i> Bill Bhejo
                </button>
                <button onclick="editOrder('${o.id}')" class="px-3 py-2 bg-stone-100 hover:bg-stone-200 text-stone-700 rounded-xl text-xs font-bold transition">
                  <i class="fa-solid fa-pen"></i>
                </button>
                <button onclick="deleteOrder('${o.id}')" class="px-3 py-2 bg-rose-50 hover:bg-rose-100 text-rose-600 rounded-xl text-xs font-bold transition">
                  <i class="fa-solid fa-trash"></i>
                </button>
              </div>
            </div>
          </div>
        `;
      }).join('');
    }

    function showToast(msg) {
      const toast = document.getElementById('toastNotification');
      document.getElementById('toastMsg').innerText = msg;
      toast.classList.remove('translate-y-20', 'opacity-0');
      setTimeout(() => {
        toast.classList.add('translate-y-20', 'opacity-0');
      }, 2500);
    }

    // Initialize on load
    window.addEventListener('DOMContentLoaded', () => {
      initializeOrders();
    });
  </script>
</body>
</html>
```