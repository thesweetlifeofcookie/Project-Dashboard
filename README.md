<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SaaS Application - Filter & Search</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 10px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 10px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb:hover {
            background: #555;
        }
        .checkbox-container input:checked ~ .checkmark {
            background-color: #3b82f6;
            border-color: #3b82f6;
        }
        .checkbox-container input:checked ~ .checkmark:after {
            display: block;
        }
        .checkbox-container .checkmark:after {
            left: 6px;
            top: 2px;
            width: 5px;
            height: 10px;
            border: solid white;
            border-width: 0 2px 2px 0;
            transform: rotate(45deg);
        }
        .dropdown:hover .dropdown-menu {
            display: block;
        }
        .tag-close:hover {
            background-color: rgba(0,0,0,0.1);
        }
    </style>
</head>
<body class="bg-gray-50 font-sans">
    <div class="container mx-auto px-4 py-8 max-w-7xl">
        <!-- Header -->
        <div class="flex justify-between items-center mb-8">
            <h1 class="text-2xl font-bold text-gray-800">Project Dashboard</h1>
            <div class="flex space-x-4">
                <button class="px-4 py-2 bg-white border border-gray-300 rounded-lg text-gray-700 hover:bg-gray-50 flex items-center">
                    <i class="fas fa-sliders-h mr-2"></i>
                    <span>Filters</span>
                </button>
                <button class="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 flex items-center">
                    <i class="fas fa-plus mr-2"></i>
                    <span>New Project</span>
                </button>
            </div>
        </div>

        <!-- Search and Filter Bar -->
        <div class="bg-white rounded-xl shadow-sm p-4 sm:p-6 mb-6 sm:mb-8">
            <div class="flex flex-col md:flex-row md:items-center md:justify-between gap-4">
                <!-- Search Input -->
                <div class="relative flex-grow w-full md:max-w-2xl">
                    <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                        <i class="fas fa-search text-gray-400"></i>
                    </div>
                    <input type="text" class="block w-full pl-10 pr-3 py-2 border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:border-blue-500" placeholder="Search projects...">
                </div>

                <!-- Filter Chips -->
                <div class="flex flex-wrap gap-2 overflow-x-auto pb-2 -mx-1 px-1">
                    <div class="flex items-center bg-blue-50 text-blue-700 px-3 py-1 rounded-full text-sm">
                        <span>Active</span>
                        <button class="ml-1 text-blue-500 hover:text-blue-700 tag-close rounded-full w-5 h-5 flex items-center justify-center">
                            <i class="fas fa-times text-xs"></i>
                        </button>
                    </div>
                    <div class="flex items-center bg-green-50 text-green-700 px-3 py-1 rounded-full text-sm">
                        <span>High Priority</span>
                        <button class="ml-1 text-green-500 hover:text-green-700 tag-close rounded-full w-5 h-5 flex items-center justify-center">
                            <i class="fas fa-times text-xs"></i>
                        </button>
                    </div>
                    <button class="text-blue-600 hover:text-blue-800 text-sm flex items-center">
                        <span>Clear all</span>
                    </button>
                </div>
            </div>

            <!-- Advanced Filters -->
            <div class="mt-6 pt-6 border-t border-gray-200">
                <div class="grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-6">
                    <!-- Status Filter -->
                    <div class="dropdown relative">
                        <button class="w-full flex justify-between items-center px-4 py-2 bg-gray-50 border border-gray-300 rounded-lg text-gray-700 hover:bg-gray-100">
                            <span>Status</span>
                            <i class="fas fa-chevron-down text-xs"></i>
                        </button>
                        <div class="dropdown-menu absolute hidden z-10 mt-1 w-full bg-white shadow-lg rounded-lg py-2 border border-gray-200 sm:w-auto sm:min-w-[200px]">
                            <div class="px-4 py-2">
                                <div class="checkbox-container flex items-center mb-2">
                                    <input type="checkbox" id="status-active" class="opacity-0 absolute h-5 w-5">
                                    <label for="status-active" class="flex items-center cursor-pointer">
                                        <div class="checkmark border border-gray-300 rounded w-5 h-5 flex flex-shrink-0 justify-center items-center mr-2 focus-within:border-blue-500"></div>
                                        <span class="text-gray-700">Active</span>
                                    </label>
                                </div>
                                <div class="checkbox-container flex items-center mb-2">
                                    <input type="checkbox" id="status-pending" class="opacity-0 absolute h-5 w-5">
                                    <label for="status-pending" class="flex items-center cursor-pointer">
                                        <div class="checkmark border border-gray-300 rounded w-5 h-5 flex flex-shrink-0 justify-center items-center mr-2 focus-within:border-blue-500"></div>
                                        <span class="text-gray-700">Pending</span>
                                    </label>
                                </div>
                                <div class="checkbox-container flex items-center">
                                    <input type="checkbox" id="status-completed" class="opacity-0 absolute h-5 w-5">
                                    <label for="status-completed" class="flex items-center cursor-pointer">
                                        <div class="checkmark border border-gray-300 rounded w-5 h-5 flex flex-shrink-0 justify-center items-center mr-2 focus-within:border-blue-500"></div>
                                        <span class="text-gray-700">Completed</span>
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Priority Filter -->
                    <div class="dropdown relative">
                        <button class="w-full flex justify-between items-center px-4 py-2 bg-gray-50 border border-gray-300 rounded-lg text-gray-700 hover:bg-gray-100">
                            <span>Priority</span>
                            <i class="fas fa-chevron-down text-xs"></i>
                        </button>
                        <div class="dropdown-menu absolute hidden z-10 mt-1 w-full bg-white shadow-lg rounded-lg py-2 border border-gray-200">
                            <div class="px-4 py-2">
                                <div class="checkbox-container flex items-center mb-2">
                                    <input type="checkbox" id="priority-high" class="opacity-0 absolute h-5 w-5">
                                    <label for="priority-high" class="flex items-center cursor-pointer">
                                        <div class="checkmark border border-gray-300 rounded w-5 h-5 flex flex-shrink-0 justify-center items-center mr-2 focus-within:border-blue-500"></div>
                                        <span class="text-gray-700">High</span>
                                    </label>
                                </div>
                                <div class="checkbox-container flex items-center mb-2">
                                    <input type="checkbox" id="priority-medium" class="opacity-0 absolute h-5 w-5">
                                    <label for="priority-medium" class="flex items-center cursor-pointer">
                                        <div class="checkmark border border-gray-300 rounded w-5 h-5 flex flex-shrink-0 justify-center items-center mr-2 focus-within:border-blue-500"></div>
                                        <span class="text-gray-700">Medium</span>
                                    </label>
                                </div>
                                <div class="checkbox-container flex items-center">
                                    <input type="checkbox" id="priority-low" class="opacity-0 absolute h-5 w-5">
                                    <label for="priority-low" class="flex items-center cursor-pointer">
                                        <div class="checkmark border border-gray-300 rounded w-5 h-5 flex flex-shrink-0 justify-center items-center mr-2 focus-within:border-blue-500"></div>
                                        <span class="text-gray-700">Low</span>
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Date Range Filter -->
                    <div class="dropdown relative">
                        <button class="w-full flex justify-between items-center px-4 py-2 bg-gray-50 border border-gray-300 rounded-lg text-gray-700 hover:bg-gray-100">
                            <span>Date Range</span>
                            <i class="fas fa-chevron-down text-xs"></i>
                        </button>
                        <div class="dropdown-menu absolute hidden z-10 mt-1 w-full bg-white shadow-lg rounded-lg py-2 border border-gray-200">
                            <div class="px-4 py-2">
                                <div class="mb-3">
                                    <label class="block text-sm text-gray-500 mb-1">From</label>
                                    <input type="date" class="w-full px-3 py-1 border border-gray-300 rounded">
                                </div>
                                <div>
                                    <label class="block text-sm text-gray-500 mb-1">To</label>
                                    <input type="date" class="w-full px-3 py-1 border border-gray-300 rounded">
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Team Filter -->
                    <div class="dropdown relative">
                        <button class="w-full flex justify-between items-center px-4 py-2 bg-gray-50 border border-gray-300 rounded-lg text-gray-700 hover:bg-gray-100">
                            <span>Team</span>
                            <i class="fas fa-chevron-down text-xs"></i>
                        </button>
                        <div class="dropdown-menu absolute hidden z-10 mt-1 w-full bg-white shadow-lg rounded-lg py-2 border border-gray-200 max-h-60 overflow-y-auto custom-scrollbar">
                            <div class="px-4 py-2">
                                <div class="relative mb-2">
                                    <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                                        <i class="fas fa-search text-gray-400 text-xs"></i>
                                    </div>
                                    <input type="text" class="block w-full pl-8 pr-3 py-1 text-sm border border-gray-300 rounded bg-gray-50" placeholder="Search teams...">
                                </div>
                                <div class="checkbox-container flex items-center mb-2">
                                    <input type="checkbox" id="team-dev" class="opacity-0 absolute h-5 w-5">
                                    <label for="team-dev" class="flex items-center cursor-pointer">
                                        <div class="checkmark border border-gray-300 rounded w-5 h-5 flex flex-shrink-0 justify-center items-center mr-2 focus-within:border-blue-500"></div>
                                        <span class="text-gray-700">Development</span>
                                    </label>
                                </div>
                                <div class="checkbox-container flex items-center mb-2">
                                    <input type="checkbox" id="team-design" class="opacity-0 absolute h-5 w-5">
                                    <label for="team-design" class="flex items-center cursor-pointer">
                                        <div class="checkmark border border-gray-300 rounded w-5 h-5 flex flex-shrink-0 justify-center items-center mr-2 focus-within:border-blue-500"></div>
                                        <span class="text-gray-700">Design</span>
                                    </label>
                                </div>
                                <div class="checkbox-container flex items-center mb-2">
                                    <input type="checkbox" id="team-marketing" class="opacity-0 absolute h-5 w-5">
                                    <label for="team-marketing" class="flex items-center cursor-pointer">
                                        <div class="checkmark border border-gray-300 rounded w-5 h-5 flex flex-shrink-0 justify-center items-center mr-2 focus-within:border-blue-500"></div>
                                        <span class="text-gray-700">Marketing</span>
                                    </label>
                                </div>
                                <div class="checkbox-container flex items-center">
                                    <input type="checkbox" id="team-sales" class="opacity-0 absolute h-5 w-5">
                                    <label for="team-sales" class="flex items-center cursor-pointer">
                                        <div class="checkmark border border-gray-300 rounded w-5 h-5 flex flex-shrink-0 justify-center items-center mr-2 focus-within:border-blue-500"></div>
                                        <span class="text-gray-700">Sales</span>
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Results Section -->
        <div class="bg-white rounded-xl shadow-sm overflow-hidden">
            <!-- Results Header -->
            <div class="px-6 py-4 border-b border-gray-200 flex flex-col md:flex-row md:items-center md:justify-between">
                <div class="mb-2 md:mb-0">
                    <h2 class="text-lg font-semibold text-gray-800">Projects</h2>
                    <p class="text-sm text-gray-500">Showing 24 of 128 results</p>
                </div>
                <div class="flex items-center">
                    <span class="text-sm text-gray-500 mr-2">Sort by:</span>
                    <select class="bg-gray-50 border border-gray-300 text-gray-700 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 px-3 py-1">
                        <option>Recently updated</option>
                        <option>Name (A-Z)</option>
                        <option>Name (Z-A)</option>
                        <option>Due date</option>
                    </select>
                </div>
            </div>

            <!-- Results Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 p-6">
                <!-- Project Card 1 -->
                <div class="border border-gray-200 rounded-lg hover:shadow-md transition-shadow">
                    <div class="p-5">
                        <div class="flex justify-between items-start mb-3">
                            <h3 class="font-medium text-gray-800">Website Redesign</h3>
                            <div class="flex space-x-2">
                                <span class="px-2 py-1 bg-blue-100 text-blue-800 text-xs rounded-full">Active</span>
                                <span class="px-2 py-1 bg-red-100 text-red-800 text-xs rounded-full">High</span>
                            </div>
                        </div>
                        <p class="text-sm text-gray-500 mb-4">Complete redesign of company website with modern UI/UX principles</p>
                        <div class="flex items-center justify-between text-sm">
                            <div class="flex items-center text-gray-500">
                                <i class="far fa-calendar-alt mr-1"></i>
                                <span>Due Jun 15</span>
                            </div>
                            <div class="flex -space-x-2">
                                <img class="w-8 h-8 rounded-full border-2 border-white" src="https://randomuser.me/api/portraits/women/44.jpg" alt="Team member">
                                <img class="w-8 h-8 rounded-full border-2 border-white" src="https://randomuser.me/api/portraits/men/32.jpg" alt="Team member">
                                <div class="w-8 h-8 rounded-full border-2 border-white bg-gray-100 flex items-center justify-center text-xs font-medium">+2</div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Project Card 2 -->
                <div class="border border-gray-200 rounded-lg hover:shadow-md transition-shadow">
                    <div class="p-5">
                        <div class="flex justify-between items-start mb-3">
                            <h3 class="font-medium text-gray-800">Mobile App Development</h3>
                            <div class="flex space-x-2">
                                <span class="px-2 py-1 bg-blue-100 text-blue-800 text-xs rounded-full">Active</span>
                                <span class="px-2 py-1 bg-yellow-100 text-yellow-800 text-xs rounded-full">Medium</span>
                            </div>
                        </div>
                        <p class="text-sm text-gray-500 mb-4">Build cross-platform mobile application for iOS and Android</p>
                        <div class="flex items-center justify-between text-sm">
                            <div class="flex items-center text-gray-500">
                                <i class="far fa-calendar-alt mr-1"></i>
                                <span>Due Jul 1</span>
                            </div>
                            <div class="flex -space-x-2">
                                <img class="w-8 h-8 rounded-full border-2 border-white" src="https://randomuser.me/api/portraits/men/75.jpg" alt="Team member">
                                <img class="w-8 h-8 rounded-full border-2 border-white" src="https://randomuser.me/api/portraits/women/68.jpg" alt="Team member">
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Project Card 3 -->
                <div class="border border-gray-200 rounded-lg hover:shadow-md transition-shadow">
                    <div class="p-5">
                        <div class="flex justify-between items-start mb-3">
                            <h3 class="font-medium text-gray-800">Marketing Campaign</h3>
                            <div class="flex space-x-2">
                                <span class="px-2 py-1 bg-green-100 text-green-800 text-xs rounded-full">Completed</span>
                            </div>
                        </div>
                        <p class="text-sm text-gray-500 mb-4">Q2 marketing campaign for new product launch</p>
                        <div class="flex items-center justify-between text-sm">
                            <div class="flex items-center text-gray-500">
                                <i class="far fa-calendar-alt mr-1"></i>
                                <span>Completed May 30</span>
                            </div>
                            <div class="flex -space-x-2">
                                <img class="w-8 h-8 rounded-full border-2 border-white" src="https://randomuser.me/api/portraits/women/12.jpg" alt="Team member">
                                <img class="w-8 h-8 rounded-full border-2 border-white" src="https://randomuser.me/api/portraits/men/42.jpg" alt="Team member">
                                <img class="w-8 h-8 rounded-full border-2 border-white" src="https://randomuser.me/api/portraits/women/33.jpg" alt="Team member">
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Pagination -->
            <div class="px-6 py-4 border-t border-gray-200 flex items-center justify-between">
                <button class="px-4 py-2 border border-gray-300 rounded-lg text-gray-700 hover:bg-gray-50 disabled:opacity-50" disabled>
                    Previous
                </button>
                <div class="flex space-x-1">
                    <button class="w-10 h-10 flex items-center justify-center rounded-lg bg-blue-600 text-white">1</button>
                    <button class="w-10 h-10 flex items-center justify-center rounded-lg text-gray-700 hover:bg-gray-100">2</button>
                    <button class="w-10 h-10 flex items-center justify-center rounded-lg text-gray-700 hover:bg-gray-100">3</button>
                    <span class="flex items-end px-2">...</span>
                    <button class="w-10 h-10 flex items-center justify-center rounded-lg text-gray-700 hover:bg-gray-100">8</button>
                </div>
                <button class="px-4 py-2 border border-gray-300 rounded-lg text-gray-700 hover:bg-gray-50">
                    Next
                </button>
            </div>
        </div>
    </div>

    <script>
        // Toggle dropdown menus
        document.querySelectorAll('.dropdown button').forEach(button => {
            button.addEventListener('click', (e) => {
                e.stopPropagation();
                const dropdown = button.parentElement;
                const menu = dropdown.querySelector('.dropdown-menu');
                
                // Close all other dropdowns first
                document.querySelectorAll('.dropdown-menu').forEach(m => {
                    if (m !== menu) m.classList.add('hidden');
                });
                
                menu.classList.toggle('hidden');
                
                // On mobile, position dropdown below button
                if (window.innerWidth < 640) {
                    const rect = button.getBoundingClientRect();
                    menu.style.position = 'fixed';
                    menu.style.top = `${rect.bottom + window.scrollY}px`;
                    menu.style.left = '16px';
                    menu.style.right = '16px';
                    menu.style.width = 'auto';
                } else {
                    menu.style.position = '';
                    menu.style.top = '';
                    menu.style.left = '';
                    menu.style.right = '';
                }
            });
        });

        // Close dropdowns when clicking outside
        document.addEventListener('click', () => {
            document.querySelectorAll('.dropdown-menu').forEach(menu => {
                menu.classList.add('hidden');
            });
        });

        // Prevent dropdown from closing when clicking inside
        document.querySelectorAll('.dropdown-menu').forEach(menu => {
            menu.addEventListener('click', (e) => {
                e.stopPropagation();
            });
        });

        // Handle checkbox styling
        document.querySelectorAll('.checkbox-container input').forEach(checkbox => {
            checkbox.addEventListener('change', function() {
                const checkmark = this.nextElementSibling.querySelector('.checkmark');
                if (this.checked) {
                    checkmark.classList.add('bg-blue-600', 'border-blue-600');
                } else {
                    checkmark.classList.remove('bg-blue-600', 'border-blue-600');
                }
            });
        });

        // Remove filter tags
        document.querySelectorAll('.tag-close').forEach(button => {
            button.addEventListener('click', function(e) {
                e.stopPropagation();
                this.parentElement.remove();
            });
        });
    </script>
</body>
</html> 
