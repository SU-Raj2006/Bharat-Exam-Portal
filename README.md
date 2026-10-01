[index.html](https://github.com/user-attachments/files/32927188/index.html)
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BharatExamPort - Sarkari Exam & Govt Jobs Directory</title>
        <link rel="icon" href="exam fevicon.png" type="fevicon.ico">
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter & Poppins -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Poppins:wght@500;600;700;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        heading: ['Poppins', 'sans-serif'],
                    },
                    colors: {
                        sarkariRed: '#dc2626',
                        sarkariBlue: '#1e40af',
                        sarkariDark: '#0f172a',
                    }
                }
            }
        }
    </script>
    <!-- Link External CSS -->
    <link rel="stylesheet" href="style.css">
</head>
<body class="bg-slate-50 dark:bg-slate-950 text-slate-800 dark:text-slate-100 font-sans min-h-screen flex flex-col justify-between selection:bg-red-500 selection:text-white transition-colors duration-200">

    <div>
        <!-- Top Emergency Notification Bar / Breaking Ticker -->
        <div class="bg-sarkariRed text-white text-xs md:text-sm font-medium py-2 px-4 shadow-inner overflow-hidden flex items-center">
            <div class="bg-white text-sarkariRed font-bold px-2.5 py-0.5 rounded text-xs uppercase tracking-wider mr-3 flex-shrink-0 animate-pulse flex items-center gap-1">
                <i class="fa-solid fa-bullhorn"></i> Breaking News
            </div>
            <div class="overflow-hidden whitespace-nowrap w-full">
                <div class="animate-marquee cursor-pointer" onclick="openTickerModal()">
                    🔥 SSC GD Constable 2026 Online Form Live &nbsp;&nbsp;|&nbsp;&nbsp; 🚂 Railway Group D CBT Exam Date Announced &nbsp;&nbsp;|&nbsp;&nbsp; 🛡️ UP Police Constable Final Answer Key Released &nbsp;&nbsp;|&nbsp;&nbsp; 🎖️ Agniveer Army Navy Airforce Registration Open &nbsp;&nbsp;|&nbsp;&nbsp; 🏛️ UPSC Civil Services IAS Notification 2026 Out
                </div>
            </div>
        </div>

        <!-- Main Header -->
        <header class="bg-gradient-to-r from-sarkariDark via-slate-900 to-sarkariBlue text-white shadow-xl sticky top-0 z-40 border-b border-slate-700">
            <div class="max-w-7xl mx-auto px-4 py-3 flex flex-col md:flex-row items-center justify-between gap-4">
                <!-- Logo & Brand -->
                <div class="flex items-center space-x-3 cursor-pointer" onclick="switchTab('home')">
                    <div class="w-12 h-12 rounded-xl bg-gradient-to-tr from-red-600 to-amber-500 flex items-center justify-center text-white shadow-lg text-2xl font-black font-heading border-2 border-white/20">
                        🏛️
                    </div>
                    <div>
                        <h1 class="text-2xl font-extrabold tracking-tight font-heading flex items-center gap-2">
                            BharatExam<span class="text-red-500">Port</span>
                            <span class="text-xs bg-red-600/80 text-white px-2 py-0.5 rounded-full font-sans font-normal border border-red-400">Sarkari Hub</span>
                        </h1>
                        <p class="text-xs text-slate-300 font-medium">India's Premier Portal for Sarkari Exams, Results, Admit Cards & Jobs</p>
                    </div>
                </div>

                <!-- Global Search Bar -->
                <div class="w-full md:w-80 relative">
                    <input type="text" id="globalSearchInput" oninput="handleGlobalSearch(this.value)" placeholder="Search exams, admit cards, answer keys..." class="w-full bg-slate-800/90 text-white placeholder-slate-400 text-sm rounded-xl pl-10 pr-4 py-2.5 border border-slate-700 focus:outline-none focus:ring-2 focus:ring-red-500 shadow-inner">
                    <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-3.5 text-slate-400 text-sm"></i>
                    <div id="searchSuggestions" class="absolute left-0 right-0 mt-2 bg-white dark:bg-slate-900 text-slate-800 dark:text-slate-100 rounded-xl shadow-2xl z-50 hidden max-h-60 overflow-y-auto border border-slate-200 dark:border-slate-800 divide-y divide-slate-100 dark:divide-slate-800"></div>
                </div>

                <!-- Header Actions -->
                <div class="flex items-center gap-2.5">
                    <button onclick="toggleDarkMode()" title="Toggle Dark/Light Mode" class="bg-slate-800 hover:bg-slate-700 text-amber-400 p-2.5 rounded-xl text-sm transition border border-slate-700 shadow-sm">
                        <i id="darkModeIcon" class="fa-solid fa-moon"></i>
                    </button>
                    <button onclick="openBookmarksModal()" class="bg-slate-800 hover:bg-slate-700 text-slate-200 hover:text-white px-3.5 py-2 rounded-xl text-xs font-semibold flex items-center gap-2 border border-slate-700 transition shadow-sm">
                        <i class="fa-solid fa-bookmark text-amber-400"></i> <span class="hidden sm:inline">Saved</span> (<span id="bookmarkCount">0</span>)
                    </button>
                    <button onclick="openTrackerModalTab()" class="bg-slate-800 hover:bg-slate-700 text-slate-200 hover:text-white px-3.5 py-2 rounded-xl text-xs font-semibold flex items-center gap-2 border border-slate-700 transition shadow-sm">
                        <i class="fa-solid fa-file-invoice text-blue-400"></i> <span class="hidden sm:inline">My Apps</span> (<span id="myAppsCount">0</span>)
                    </button>
                    <button onclick="openWizardModal()" class="bg-gradient-to-r from-red-600 to-rose-600 hover:from-red-500 hover:to-rose-500 text-white px-4 py-2 rounded-xl text-xs font-bold shadow-lg shadow-red-900/30 transition flex items-center gap-2">
                        <i class="fa-solid fa-paper-plane"></i> Quick Apply
                    </button>
                </div>
            </div>

            <!-- Navigation Tabs -->
            <div class="bg-slate-900/95 border-t border-slate-800 backdrop-blur-md">
                <div class="max-w-7xl mx-auto px-4 flex items-center overflow-x-auto py-2.5 gap-2 md:gap-3 no-scrollbar">
                    <button onclick="switchTab('home')" id="nav-home" class="nav-btn px-4 py-2 rounded-lg text-xs md:text-sm font-bold transition whitespace-nowrap bg-red-600 text-white shadow-md flex items-center gap-2">
                        <i class="fa-solid fa-house"></i> Home Dashboard
                    </button>
                    <button onclick="switchTab('latest_jobs')" id="nav-latest_jobs" class="nav-btn px-4 py-2 rounded-lg text-xs md:text-sm font-medium transition whitespace-nowrap text-slate-300 hover:text-white hover:bg-slate-800 flex items-center gap-2">
                        <i class="fa-solid fa-briefcase text-blue-400"></i> Latest Jobs
                    </button>
                    <button onclick="switchTab('admit_card')" id="nav-admit_card" class="nav-btn px-4 py-2 rounded-lg text-xs md:text-sm font-medium transition whitespace-nowrap text-slate-300 hover:text-white hover:bg-slate-800 flex items-center gap-2">
                        <i class="fa-solid fa-id-card text-emerald-400"></i> Admit Cards
                    </button>
                    <button onclick="switchTab('results')" id="nav-results" class="nav-btn px-4 py-2 rounded-lg text-xs md:text-sm font-medium transition whitespace-nowrap text-slate-300 hover:text-white hover:bg-slate-800 flex items-center gap-2">
                        <i class="fa-solid fa-square-poll-vertical text-amber-400"></i> Sarkari Results
                    </button>
                    <button onclick="switchTab('answer_key')" id="nav-answer_key" class="nav-btn px-4 py-2 rounded-lg text-xs md:text-sm font-medium transition whitespace-nowrap text-slate-300 hover:text-white hover:bg-slate-800 flex items-center gap-2">
                        <i class="fa-solid fa-key text-purple-400"></i> Answer Keys
                    </button>
                    <button onclick="switchTab('tracker')" id="nav-tracker" class="nav-btn px-4 py-2 rounded-lg text-xs md:text-sm font-medium transition whitespace-nowrap text-slate-300 hover:text-white hover:bg-slate-800 flex items-center gap-2">
                        <i class="fa-solid fa-clipboard-check text-cyan-400"></i> My Applications
                    </button>
                </div>
            </div>
        </header>
    </div>

    <main class="flex-grow max-w-7xl mx-auto w-full px-4 py-6">

        <!-- Home Dashboard View -->
        <div id="view-home" class="space-y-8">
            
            <!-- Hero Banner -->
            <div class="relative rounded-3xl bg-gradient-to-r from-blue-900 via-indigo-900 to-slate-900 text-white p-6 md:p-10 shadow-2xl overflow-hidden border border-blue-500/30">
                <div class="absolute -right-10 -bottom-10 w-80 h-80 bg-red-600/20 rounded-full blur-3xl pointer-events-none"></div>
                <div class="relative z-10 max-w-2xl space-y-4">
                    <span class="bg-red-600 text-white text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider inline-block">🎯 Major Sarkari Exams 2026 Directory</span>
                    <h2 class="text-3xl md:text-4xl font-black font-heading leading-tight">Prepare & Apply for Top Central & State Government Exams Instantly</h2>
                    <p class="text-slate-300 text-sm md:text-base">Access instant multi-step online application wizards, fee calculators, direct admit card downloads, live answer keys, and merit lists styled like your favorite Sarkari portals.</p>
                    <div class="flex flex-wrap gap-3 pt-2">
                        <button onclick="filterCategory('all')" class="bg-white text-slate-900 px-4 py-2.5 rounded-xl text-xs font-bold hover:bg-slate-100 transition shadow">View All Exams</button>
                        <button onclick="openWizardModalWithExam('SSC GD Constable 2026')" class="bg-red-600 hover:bg-red-500 text-white px-4 py-2.5 rounded-xl text-xs font-bold transition shadow-lg shadow-red-900/50 flex items-center gap-2">
                            <i class="fa-solid fa-bolt"></i> Quick Apply: SSC GD
                        </button>
                    </div>
                </div>
            </div>

            <!-- Categorized Quick Filter Chips -->
            <div class="flex items-center gap-2 overflow-x-auto pb-2 no-scrollbar">
                <span class="text-xs font-bold text-slate-500 uppercase tracking-wider flex-shrink-0 mr-1"><i class="fa-solid fa-filter mr-1"></i> Filter Category:</span>
                <button onclick="filterCategory('all')" class="filter-chip px-4 py-2 rounded-xl text-xs font-semibold bg-sarkariBlue text-white shadow-sm transition flex-shrink-0">All Exams</button>
                <button onclick="filterCategory('upsc')" class="filter-chip px-4 py-2 rounded-xl text-xs font-semibold bg-white dark:bg-slate-900 hover:bg-slate-100 dark:hover:bg-slate-800 text-slate-700 dark:text-slate-200 border border-slate-200 dark:border-slate-800 shadow-sm transition flex-shrink-0">UPSC / Civil Services</button>
                <button onclick="filterCategory('ssc')" class="filter-chip px-4 py-2 rounded-xl text-xs font-semibold bg-white dark:bg-slate-900 hover:bg-slate-100 dark:hover:bg-slate-800 text-slate-700 dark:text-slate-200 border border-slate-200 dark:border-slate-800 shadow-sm transition flex-shrink-0">SSC Exams</button>
                <button onclick="filterCategory('railway')" class="filter-chip px-4 py-2 rounded-xl text-xs font-semibold bg-white dark:bg-slate-900 hover:bg-slate-100 dark:hover:bg-slate-800 text-slate-700 dark:text-slate-200 border border-slate-200 dark:border-slate-800 shadow-sm transition flex-shrink-0">Railways (RRB)</button>
                <button onclick="filterCategory('banking')" class="filter-chip px-4 py-2 rounded-xl text-xs font-semibold bg-white dark:bg-slate-900 hover:bg-slate-100 dark:hover:bg-slate-800 text-slate-700 dark:text-slate-200 border border-slate-200 dark:border-slate-800 shadow-sm transition flex-shrink-0">Banking (IBPS/SBI)</button>
                <button onclick="filterCategory('state_psc')" class="filter-chip px-4 py-2 rounded-xl text-xs font-semibold bg-white dark:bg-slate-900 hover:bg-slate-100 dark:hover:bg-slate-800 text-slate-700 dark:text-slate-200 border border-slate-200 dark:border-slate-800 shadow-sm transition flex-shrink-0">State PSC</button>
                <button onclick="filterCategory('police')" class="filter-chip px-4 py-2 rounded-xl text-xs font-semibold bg-white dark:bg-slate-900 hover:bg-slate-100 dark:hover:bg-slate-800 text-slate-700 dark:text-slate-200 border border-slate-200 dark:border-slate-800 shadow-sm transition flex-shrink-0">Police & SI</button>
                <button onclick="filterCategory('teaching')" class="filter-chip px-4 py-2 rounded-xl text-xs font-semibold bg-white dark:bg-slate-900 hover:bg-slate-100 dark:hover:bg-slate-800 text-slate-700 dark:text-slate-200 border border-slate-200 dark:border-slate-800 shadow-sm transition flex-shrink-0">Teaching (CTET)</button>
            </div>

            <!-- Sarkari Result Style 3-Column Grid -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- Column 1: Latest Jobs -->
                <div class="bg-white dark:bg-slate-900 rounded-2xl shadow-md border border-slate-200 dark:border-slate-800 overflow-hidden flex flex-col">
                    <div class="bg-gradient-to-r from-blue-700 to-indigo-800 text-white p-4 font-heading font-bold text-base flex items-center justify-between">
                        <span><i class="fa-solid fa-briefcase mr-2"></i> Latest Jobs</span>
                        <span class="text-xs bg-blue-900/80 px-2 py-0.5 rounded-full border border-blue-400">Updated Daily</span>
                    </div>
                    <div class="p-3 divide-y divide-slate-100 dark:divide-slate-800 overflow-y-auto max-h-[480px]" id="latestJobsListContainer"></div>
                    <div class="p-3 bg-slate-50 dark:bg-slate-950 border-t border-slate-200 dark:border-slate-800 text-center">
                        <button onclick="switchTab('latest_jobs')" class="text-xs font-bold text-sarkariBlue dark:text-blue-400 hover:underline">View All Latest Jobs &rarr;</button>
                    </div>
                </div>

                <!-- Column 2: Admit Card -->
                <div class="bg-white dark:bg-slate-900 rounded-2xl shadow-md border border-slate-200 dark:border-slate-800 overflow-hidden flex flex-col">
                    <div class="bg-gradient-to-r from-emerald-700 to-teal-800 text-white p-4 font-heading font-bold text-base flex items-center justify-between">
                        <span><i class="fa-solid fa-id-card mr-2"></i> Admit Card Links</span>
                        <span class="text-xs bg-emerald-900/80 px-2 py-0.5 rounded-full border border-emerald-400">Direct Download</span>
                    </div>
                    <div class="p-3 divide-y divide-slate-100 dark:divide-slate-800 overflow-y-auto max-h-[480px]" id="admitCardListContainer"></div>
                    <div class="p-3 bg-slate-50 dark:bg-slate-950 border-t border-slate-200 dark:border-slate-800 text-center">
                        <button onclick="switchTab('admit_card')" class="text-xs font-bold text-emerald-700 dark:text-emerald-400 hover:underline">View All Admit Cards &rarr;</button>
                    </div>
                </div>

                <!-- Column 3: Results & Answer Keys -->
                <div class="bg-white dark:bg-slate-900 rounded-2xl shadow-md border border-slate-200 dark:border-slate-800 overflow-hidden flex flex-col">
                    <div class="bg-gradient-to-r from-amber-600 to-orange-700 text-white p-4 font-heading font-bold text-base flex items-center justify-between">
                        <span><i class="fa-solid fa-square-poll-vertical mr-2"></i> Results & Answer Key</span>
                        <span class="text-xs bg-amber-900/80 px-2 py-0.5 rounded-full border border-amber-400">Merit Lists</span>
                    </div>
                    <div class="p-3 divide-y divide-slate-100 dark:divide-slate-800 overflow-y-auto max-h-[480px]" id="resultsListContainer"></div>
                    <div class="p-3 bg-slate-50 dark:bg-slate-950 border-t border-slate-200 dark:border-slate-800 text-center">
                        <button onclick="switchTab('results')" class="text-xs font-bold text-amber-700 dark:text-amber-400 hover:underline">View All Results &rarr;</button>
                    </div>
                </div>
            </div>

            <!-- Master Table Directory -->
            <div class="bg-white dark:bg-slate-900 rounded-2xl shadow-md border border-slate-200 dark:border-slate-800 overflow-hidden">
                <div class="p-5 border-b border-slate-200 dark:border-slate-800 flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                    <div>
                        <h3 class="text-lg font-bold font-heading text-slate-900 dark:text-white flex items-center gap-2">
                            <i class="fa-solid fa-list-check text-red-600"></i> Featured Competitive & Sarkari Exams Master Directory
                        </h3>
                        <p class="text-xs text-slate-500 dark:text-slate-400">Click on any row or title to open comprehensive exam details modal with syllabus, fee breakdown, and apply links.</p>
                    </div>
                    <div class="flex items-center gap-2">
                        <span class="text-xs font-semibold text-slate-500">Sort By:</span>
                        <select id="examSortSelect" onchange="sortExams(this.value)" class="bg-slate-50 dark:bg-slate-800 text-slate-800 dark:text-slate-200 text-xs rounded-xl px-3 py-2 border border-slate-200 dark:border-slate-700 focus:outline-none focus:ring-2 focus:ring-red-500">
                            <option value="latest">Latest First</option>
                            <option value="deadline">Closing Soon</option>
                            <option value="name">Alphabetical (A-Z)</option>
                        </select>
                    </div>
                </div>
                
                <div class="overflow-x-auto">
                    <table class="w-full text-left border-collapse sarkari-table text-xs md:text-sm">
                        <thead>
                            <tr>
                                <th class="p-3.5 font-bold uppercase tracking-wider">Exam Name / Board</th>
                                <th class="p-3.5 font-bold uppercase tracking-wider">Category</th>
                                <th class="p-3.5 font-bold uppercase tracking-wider">Total Vacancy</th>
                                <th class="p-3.5 font-bold uppercase tracking-wider">Last Date</th>
                                <th class="p-3.5 font-bold uppercase tracking-wider">Status</th>
                                <th class="p-3.5 font-bold uppercase tracking-wider text-center">Actions</th>
                            </tr>
                        </thead>
                        <tbody id="masterExamsTableBody" class="divide-y divide-slate-200 dark:divide-slate-800"></tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- Latest Jobs Tab View -->
        <div id="view-latest_jobs" class="space-y-6 hidden">
            <div class="bg-blue-900 text-white p-6 rounded-2xl shadow-lg flex flex-col md:flex-row justify-between items-center gap-4">
                <div>
                    <h2 class="text-2xl font-bold font-heading">Latest Government Jobs & Sarkari Vacancies</h2>
                    <p class="text-xs text-blue-200">Browse active job notifications across UPSC, SSC, Railways, and Banking.</p>
                </div>
                <div>
                    <input type="text" oninput="filterTabSearch('latest_jobs', this.value)" placeholder="Search job title..." class="bg-blue-950 text-white text-xs px-4 py-2 rounded-xl border border-blue-700 focus:outline-none">
                </div>
            </div>
            <div id="fullJobsContainer" class="grid grid-cols-1 md:grid-cols-2 gap-4"></div>
        </div>

        <!-- Admit Card Tab View -->
        <div id="view-admit_card" class="space-y-6 hidden">
            <div class="bg-emerald-900 text-white p-6 rounded-2xl shadow-lg flex flex-col md:flex-row justify-between items-center gap-4">
                <div>
                    <h2 class="text-2xl font-bold font-heading">Admit Card Download Portal</h2>
                    <p class="text-xs text-emerald-200">Download hall tickets for CBT, PET/PST, and Mains examinations.</p>
                </div>
                <div>
                    <input type="text" oninput="filterTabSearch('admit_card', this.value)" placeholder="Search admit card..." class="bg-emerald-950 text-white text-xs px-4 py-2 rounded-xl border border-emerald-700 focus:outline-none">
                </div>
            </div>
            <div id="fullAdmitCardContainer" class="grid grid-cols-1 md:grid-cols-2 gap-4"></div>
        </div>

        <!-- Sarkari Results Tab View -->
        <div id="view-results" class="space-y-6 hidden">
            <div class="bg-amber-800 text-white p-6 rounded-2xl shadow-lg flex flex-col md:flex-row justify-between items-center gap-4">
                <div>
                    <h2 class="text-2xl font-bold font-heading">Sarkari Results & Merit Lists</h2>
                    <p class="text-xs text-amber-200">Check written exam results, cutoff marks, and final merit lists.</p>
                </div>
                <div>
                    <input type="text" oninput="filterTabSearch('results', this.value)" placeholder="Search result..." class="bg-amber-950 text-white text-xs px-4 py-2 rounded-xl border border-amber-700 focus:outline-none">
                </div>
            </div>
            <div id="fullResultsContainer" class="grid grid-cols-1 md:grid-cols-2 gap-4"></div>
        </div>

        <!-- Answer Key Tab View -->
        <div id="view-answer_key" class="space-y-6 hidden">
            <div class="bg-purple-900 text-white p-6 rounded-2xl shadow-lg flex flex-col md:flex-row justify-between items-center gap-4">
                <div>
                    <h2 class="text-2xl font-bold font-heading">Answer Key Trackers & Objection Links</h2>
                    <p class="text-xs text-purple-200">Download provisional and final answer keys with objection submission links.</p>
                </div>
                <div>
                    <input type="text" oninput="filterTabSearch('answer_key', this.value)" placeholder="Search answer key..." class="bg-purple-950 text-white text-xs px-4 py-2 rounded-xl border border-purple-700 focus:outline-none">
                </div>
            </div>
            <div id="fullAnswerKeyContainer" class="grid grid-cols-1 md:grid-cols-2 gap-4"></div>
        </div>

        <!-- My Applications Tracker View -->
        <div id="view-tracker" class="space-y-6 hidden">
            <div class="bg-slate-900 text-white p-6 rounded-2xl shadow-lg flex flex-col md:flex-row justify-between items-center gap-4 border border-slate-800">
                <div>
                    <h2 class="text-2xl font-bold font-heading">My Applications Tracker</h2>
                    <p class="text-xs text-slate-400">Track all your submitted quick-apply applications saved on this browser.</p>
                </div>
                <button onclick="clearMyApplications()" class="bg-red-600 hover:bg-red-500 text-white px-4 py-2 rounded-xl text-xs font-bold transition shadow">
                    Clear Tracker History
                </button>
            </div>
            <div id="myApplicationsList" class="space-y-4"></div>
        </div>

    </main>

    <footer class="bg-slate-900 text-slate-400 border-t border-slate-800 mt-12 py-10">
        <div class="max-w-7xl mx-auto px-4 grid grid-cols-1 md:grid-cols-4 gap-8 mb-8">
            <div class="space-y-3">
                <div class="flex items-center space-x-2">
                    <div class="w-8 h-8 rounded-lg bg-red-600 flex items-center justify-center text-white text-base font-bold">🏛️</div>
                    <span class="text-white font-bold font-heading text-lg">BharatExamPort</span>
                </div>
                <p class="text-xs text-slate-400">Your trusted gateway for Sarkari Exams, Latest Govt Job Notifications, Admit Cards, and Answer Keys across India.</p>
            </div>
            <div>
                <h4 class="text-white font-bold text-sm mb-3">Top Exam Categories</h4>
                <ul class="space-y-2 text-xs">
                    <li><a href="#" onclick="filterCategory('upsc'); switchTab('home')" class="hover:text-white transition">UPSC Civil Services & CDS</a></li>
                    <li><a href="#" onclick="filterCategory('ssc'); switchTab('home')" class="hover:text-white transition">SSC GD, CGL & CHSL</a></li>
                    <li><a href="#" onclick="filterCategory('railway'); switchTab('home')" class="hover:text-white transition">Railway Group D & NTPC</a></li>
                    <li><a href="#" onclick="filterCategory('banking'); switchTab('home')" class="hover:text-white transition">IBPS & SBI Clerk/PO</a></li>
                </ul>
            </div>
            <div>
                <h4 class="text-white font-bold text-sm mb-3">Quick Features</h4>
                <ul class="space-y-2 text-xs">
                    <li><button onclick="openBookmarksModal()" class="hover:text-white transition text-left">Saved Exams Bookmarks</button></li>
                    <li><button onclick="openWizardModal()" class="hover:text-white transition text-left">Multi-Step Online Application Wizard</button></li>
                    <li><button onclick="switchTab('tracker')" class="hover:text-white transition text-left">Application Receipt Tracker</button></li>
                </ul>
            </div>
            <div>
                <h4 class="text-white font-bold text-sm mb-3">Disclaimer</h4>
                <p class="text-xs text-slate-500 leading-relaxed">BharatExamPort is an educational portal. We are not affiliated with any government recruitment board. Please verify details from official websites.</p>
            </div>
        </div>
        <div class="max-w-7xl mx-auto px-4 border-t border-slate-800 pt-6 flex flex-col sm:flex-row items-center justify-between text-xs text-slate-500">
            <p>&copy; 2026 BharatExamPort. All rights reserved.</p>
            <p class="mt-2 sm:mt-0">Designed for Sarkari Aspirants across India 🇮🇳</p>
        </div>
    </footer>

    <!-- MODAL 1: Comprehensive Exam Details Modal -->
    <div id="examDetailsModal" class="fixed inset-0 bg-slate-950/70 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
        <div class="bg-white dark:bg-slate-900 rounded-3xl max-w-2xl w-full p-6 md:p-8 shadow-2xl relative border border-slate-200 dark:border-slate-800 max-h-[90vh] overflow-y-auto">
            <button onclick="closeModal('examDetailsModal')" class="absolute top-5 right-5 text-slate-400 hover:text-slate-700 dark:hover:text-white text-lg">
                <i class="fa-solid fa-xmark"></i>
            </button>
            <div id="modalDetailsContent"></div>
        </div>
    </div>

    <!-- MODAL 2: Multi-Step Online Application Wizard -->
    <div id="wizardModal" class="fixed inset-0 bg-slate-950/70 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
        <div class="bg-white dark:bg-slate-900 rounded-3xl max-w-xl w-full p-6 md:p-8 shadow-2xl relative border border-slate-200 dark:border-slate-800 max-h-[90vh] overflow-y-auto">
            <button onclick="closeModal('wizardModal')" class="absolute top-5 right-5 text-slate-400 hover:text-slate-700 dark:hover:text-white text-lg">
                <i class="fa-solid fa-xmark"></i>
            </button>
            
            <div class="flex items-center gap-3 mb-6">
                <div class="w-12 h-12 rounded-2xl bg-red-100 dark:bg-red-950 text-red-600 flex items-center justify-center text-xl font-bold">
                    📝
                </div>
                <div>
                    <h3 class="text-lg font-bold font-heading text-slate-900 dark:text-white">Multi-Step Online Application Wizard</h3>
                    <p class="text-xs text-slate-500 dark:text-slate-400" id="wizardStepSub">Step 1 of 3: Basic Candidate Details & Exam Selection</p>
                </div>
            </div>

            <!-- Step Progress Indicators -->
            <div class="flex items-center justify-between mb-6 relative">
                <div class="absolute left-0 right-0 top-1/2 -translate-y-1/2 h-1 bg-slate-200 dark:bg-slate-800 -z-0"></div>
                <div id="wizIndicator1" class="w-8 h-8 rounded-full bg-red-600 text-white font-bold text-xs flex items-center justify-center relative z-10 shadow">1</div>
                <div id="wizIndicator2" class="w-8 h-8 rounded-full bg-slate-200 dark:bg-slate-800 text-slate-500 font-bold text-xs flex items-center justify-center relative z-10">2</div>
                <div id="wizIndicator3" class="w-8 h-8 rounded-full bg-slate-200 dark:bg-slate-800 text-slate-500 font-bold text-xs flex items-center justify-center relative z-10">3</div>
            </div>

            <form id="multiStepForm" onsubmit="handleWizardSubmit(event)">
                <!-- STEP 1 -->
                <div id="wizardStep1" class="space-y-4">
                    <div>
                        <label class="block text-xs font-bold text-slate-700 dark:text-slate-300 mb-1">Select Exam / Post *</label>
                        <select id="wizExamSelect" required class="w-full bg-slate-50 dark:bg-slate-800 text-slate-800 dark:text-slate-100 text-xs rounded-xl p-3 border border-slate-300 dark:border-slate-700 focus:outline-none focus:ring-2 focus:ring-red-500"></select>
                    </div>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-xs font-bold text-slate-700 dark:text-slate-300 mb-1">Full Name (As in 10th Certificate) *</label>
                            <input type="text" id="wizName" required placeholder="e.g. Aman Kumar" class="w-full bg-slate-50 dark:bg-slate-800 text-slate-800 dark:text-slate-100 text-xs rounded-xl p-3 border border-slate-300 dark:border-slate-700 focus:outline-none focus:ring-2 focus:ring-red-500">
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-slate-700 dark:text-slate-300 mb-1">Mobile Number *</label>
                            <input type="tel" id="wizMobile" required placeholder="e.g. 9876543210" pattern="[0-9]{10}" class="w-full bg-slate-50 dark:bg-slate-800 text-slate-800 dark:text-slate-100 text-xs rounded-xl p-3 border border-slate-300 dark:border-slate-700 focus:outline-none focus:ring-2 focus:ring-red-500">
                        </div>
                    </div>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-xs font-bold text-slate-700 dark:text-slate-300 mb-1">Date of Birth *</label>
                            <input type="date" id="wizDob" required class="w-full bg-slate-50 dark:bg-slate-800 text-slate-800 dark:text-slate-100 text-xs rounded-xl p-3 border border-slate-300 dark:border-slate-700 focus:outline-none focus:ring-2 focus:ring-red-500">
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-slate-700 dark:text-slate-300 mb-1">Gender *</label>
                            <select id="wizGender" required class="w-full bg-slate-50 dark:bg-slate-800 text-slate-800 dark:text-slate-100 text-xs rounded-xl p-3 border border-slate-300 dark:border-slate-700 focus:outline-none focus:ring-2 focus:ring-red-500">
                                <option value="Male">Male</option>
                                <option value="Female">Female</option>
                                <option value="Other">Other</option>
                            </select>
                        </div>
                    </div>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-xs font-bold text-slate-700 dark:text-slate-300 mb-1">Category *</label>
                            <select id="wizCategory" required class="w-full bg-slate-50 dark:bg-slate-800 text-slate-800 dark:text-slate-100 text-xs rounded-xl p-3 border border-slate-300 dark:border-slate-700 focus:outline-none focus:ring-2 focus:ring-red-500">
                                <option value="GEN">General (GEN)</option>
                                <option value="OBC">Other Backward Class (OBC)</option>
                                <option value="SC">Scheduled Caste (SC)</option>
                                <option value="ST">Scheduled Tribe (ST)</option>
                                <option value="EWS">Economically Weaker Section (EWS)</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-slate-700 dark:text-slate-300 mb-1">Highest Qualification *</label>
                            <select id="wizQualification" required class="w-full bg-slate-50 dark:bg-slate-800 text-slate-800 dark:text-slate-100 text-xs rounded-xl p-3 border border-slate-300 dark:border-slate-700 focus:outline-none focus:ring-2 focus:ring-red-500">
                                <option value="10th">10th Matriculation</option>
                                <option value="12th">12th Intermediate</option>
                                <option value="Graduate">Graduation Degree</option>
                                <option value="PostGraduate">Post Graduation</option>
                            </select>
                        </div>
                    </div>
                    <div class="pt-4 flex justify-end">
                        <button type="button" onclick="goToWizardStep(2)" class="bg-red-600 hover:bg-red-500 text-white font-bold px-6 py-2.5 rounded-xl text-xs uppercase tracking-wider shadow transition">
                            Next: Fee & Documents &rarr;
                        </button>
                    </div>
                </div>

                <!-- STEP 2 -->
                <div id="wizardStep2" class="space-y-4 hidden">
                    <div class="bg-slate-50 dark:bg-slate-800 p-4 rounded-2xl border border-slate-200 dark:border-slate-700 space-y-2">
                        <h4 class="font-bold text-xs text-slate-900 dark:text-white uppercase tracking-wider"><i class="fa-solid fa-calculator text-red-600 mr-1"></i> Automatic Fee Concession Calculation</h4>
                        <div class="flex justify-between text-xs">
                            <span class="text-slate-500 dark:text-slate-400">Selected Category / Gender:</span>
                            <span id="feeBreakdownSummary" class="font-bold text-slate-900 dark:text-slate-100">GEN / Male</span>
                        </div>
                        <div class="flex justify-between text-xs">
                            <span class="text-slate-500 dark:text-slate-400">Application Fee Payable:</span>
                            <span id="calculatedFeeAmount" class="font-bold text-emerald-600 dark:text-emerald-400 text-sm">₹100</span>
                        </div>
                        <p class="text-[10px] text-slate-400 italic">* Note: SC/ST/Female candidates receive 100% fee concession as per Government norms.</p>
                    </div>

                    <div class="space-y-3">
                        <label class="block text-xs font-bold text-slate-700 dark:text-slate-300">Simulate Document Uploads (Scanned Photo & Signature) *</label>
                        <div class="border-2 border-dashed border-slate-300 dark:border-slate-700 rounded-2xl p-4 text-center cursor-pointer hover:border-red-500 transition">
                            <i class="fa-solid fa-cloud-arrow-up text-2xl text-slate-400 mb-1"></i>
                            <p class="text-xs font-semibold text-slate-700 dark:text-slate-300">Click to upload Passport Photo & Signature</p>
                            <p class="text-[10px] text-slate-400">JPG, PNG format up to 500KB (Simulated)</p>
                            <input type="file" id="wizFileUpload" class="hidden" onchange="simulateFileUpload(this)">
                        </div>
                        <div id="uploadStatusText" class="text-xs font-semibold text-emerald-600 dark:text-emerald-400 hidden text-center">
                            <i class="fa-solid fa-check-circle mr-1"></i> Scanned Photo & Signature Verified Successfully!
                        </div>
                    </div>

                    <div class="pt-4 flex justify-between">
                        <button type="button" onclick="goToWizardStep(1)" class="bg-slate-200 dark:bg-slate-800 hover:bg-slate-300 text-slate-700 dark:text-slate-300 font-bold px-5 py-2.5 rounded-xl text-xs uppercase tracking-wider transition">
                            &larr; Back
                        </button>
                        <button type="button" onclick="goToWizardStep(3)" class="bg-red-600 hover:bg-red-500 text-white font-bold px-6 py-2.5 rounded-xl text-xs uppercase tracking-wider shadow transition">
                            Next: Final Review &rarr;
                        </button>
                    </div>
                </div>

                <!-- STEP 3 -->
                <div id="wizardStep3" class="space-y-4 hidden">
                    <div class="bg-slate-50 dark:bg-slate-800 p-4 rounded-2xl border border-slate-200 dark:border-slate-700 space-y-2 text-xs">
                        <h4 class="font-bold text-slate-900 dark:text-white uppercase tracking-wider mb-2"><i class="fa-solid fa-clipboard-check text-emerald-600 mr-1"></i> Review Application Details</h4>
                        <div class="flex justify-between border-b border-slate-200 dark:border-slate-700 pb-1">
                            <span class="text-slate-500">Applicant Name:</span>
                            <span id="reviewName" class="font-bold text-slate-900 dark:text-slate-100"></span>
                        </div>
                        <div class="flex justify-between border-b border-slate-200 dark:border-slate-700 pb-1">
                            <span class="text-slate-500">Mobile Number:</span>
                            <span id="reviewMobile" class="font-bold text-slate-900 dark:text-slate-100"></span>
                        </div>
                        <div class="flex justify-between border-b border-slate-200 dark:border-slate-700 pb-1">
                            <span class="text-slate-500">Category / Gender:</span>
                            <span id="reviewCategory" class="font-bold text-slate-900 dark:text-slate-100"></span>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-slate-500">Total Payable Fee:</span>
                            <span id="reviewFee" class="font-bold text-emerald-600"></span>
                        </div>
                    </div>

                    <div class="flex items-center gap-2">
                        <input type="checkbox" id="declarationCheck" required class="w-4 h-4 rounded text-red-600 focus:ring-red-500">
                        <label for="declarationCheck" class="text-[11px] text-slate-600 dark:text-slate-400">I hereby declare that all information provided is true and correct to the best of my knowledge.</label>
                    </div>

                    <div class="pt-4 flex justify-between">
                        <button type="button" onclick="goToWizardStep(2)" class="bg-slate-200 dark:bg-slate-800 hover:bg-slate-300 text-slate-700 dark:text-slate-300 font-bold px-5 py-2.5 rounded-xl text-xs uppercase tracking-wider transition">
                            &larr; Back
                        </button>
                        <button type="submit" class="bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-500 hover:to-teal-500 text-white font-bold px-6 py-2.5 rounded-xl text-xs uppercase tracking-wider shadow-lg shadow-emerald-900/30 transition">
                            Submit & Generate Receipt Slip
                        </button>
                    </div>
                </div>
            </form>
        </div>
    </div>

    <!-- MODAL 3: Success Receipt Slip Modal -->
    <div id="receiptModal" class="fixed inset-0 bg-slate-950/70 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
        <div class="bg-white dark:bg-slate-900 rounded-3xl max-w-md w-full p-6 md:p-8 shadow-2xl text-center relative border border-slate-200 dark:border-slate-800">
            <div id="printableSlip">
                <div class="w-16 h-16 bg-emerald-100 dark:bg-emerald-950 text-emerald-600 rounded-full flex items-center justify-center text-3xl mx-auto mb-4 shadow">
                    <i class="fa-solid fa-check"></i>
                </div>
                <h3 class="text-xl font-bold font-heading text-slate-900 dark:text-white mb-1">Application Submitted Successfully!</h3>
                <p class="text-xs text-slate-500 dark:text-slate-400 mb-6">Your quick-apply application has been registered & saved to local tracker.</p>
                
                <div class="bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 rounded-2xl p-4 text-left mb-6 space-y-2">
                    <div class="flex justify-between text-xs">
                        <span class="text-slate-500">Registration ID:</span>
                        <span class="font-bold font-mono text-slate-900 dark:text-slate-100" id="slipRegId">BEP202689432</span>
                    </div>
                    <div class="flex justify-between text-xs">
                        <span class="text-slate-500">Applicant Name:</span>
                        <span class="font-bold text-slate-900 dark:text-slate-100" id="slipName">Aman Kumar</span>
                    </div>
                    <div class="flex justify-between text-xs">
                        <span class="text-slate-500">Exam Applied:</span>
                        <span class="font-bold text-slate-900 dark:text-slate-100" id="slipExam">SSC GD Constable 2026</span>
                    </div>
                    <div class="flex justify-between text-xs">
                        <span class="text-slate-500">Fee Paid:</span>
                        <span class="font-bold text-emerald-600 dark:text-emerald-400" id="slipFee">₹100</span>
                    </div>
                    <div class="flex justify-between text-xs">
                        <span class="text-slate-500">Status:</span>
                        <span class="font-bold text-emerald-600">Successfully Registered</span>
                    </div>
                </div>
            </div>

            <div class="flex gap-3">
                <button onclick="window.print()" class="flex-1 bg-slate-100 dark:bg-slate-800 hover:bg-slate-200 text-slate-800 dark:text-slate-200 font-bold py-2.5 rounded-xl text-xs transition">
                    Print Slip
                </button>
                <button onclick="closeModal('receiptModal')" class="flex-1 bg-red-600 hover:bg-red-500 text-white font-bold py-2.5 rounded-xl text-xs transition">
                    Done
                </button>
            </div>
        </div>
    </div>

    <!-- MODAL 4: Bookmarked Exams Modal -->
    <div id="bookmarksModal" class="fixed inset-0 bg-slate-950/70 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
        <div class="bg-white dark:bg-slate-900 rounded-3xl max-w-lg w-full p-6 md:p-8 shadow-2xl relative border border-slate-200 dark:border-slate-800 max-h-[85vh] overflow-y-auto">
            <button onclick="closeModal('bookmarksModal')" class="absolute top-5 right-5 text-slate-400 hover:text-slate-700 dark:hover:text-white text-lg">
                <i class="fa-solid fa-xmark"></i>
            </button>
            <div class="flex items-center gap-3 mb-4">
                <div class="w-12 h-12 rounded-2xl bg-amber-100 dark:bg-amber-950 text-amber-600 flex items-center justify-center text-xl font-bold">
                    🔖
                </div>
                <div>
                    <h3 class="text-lg font-bold font-heading text-slate-900 dark:text-white">Saved Bookmarked Exams</h3>
                    <p class="text-xs text-slate-500 dark:text-slate-400">Quick access to your saved competitive examinations.</p>
                </div>
            </div>
            <div id="bookmarkedExamsList" class="space-y-3"></div>
        </div>
    </div>

    <!-- Link External JavaScript -->
    <script src="script.js"></script>
</body>
</html>
