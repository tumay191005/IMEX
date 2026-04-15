Nền tảng thương mại điện tử chuyên biệt cho thiết bị di động IMEX
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IMEX - Thương mại điện tử thiết bị di động</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&amp;display=swap');
        
        :root {
            --primary: #9BF6FF;
        }
        
        * {
            font-family: 'Inter', system_ui, sans-serif;
        }
        
        .tailwind-ready {
            background: linear-gradient(135deg, #9BF6FF 0%, #00D4FF 100%);
        }
        
        .hero-bg {
            background: linear-gradient(rgba(155, 246, 255, 0.15), rgba(155, 246, 255, 0.05)), url('https://picsum.photos/id/1015/1920/1080') center/cover no-repeat;
        }
        
        .nav-link {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .nav-link:hover {
            color: #9BF6FF;
            transform: translateY(-1px);
        }
        
        .product-card {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .product-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 25px 50px -12px rgb(155 246 255);
        }
        
        .modal {
            animation: modalPop 0.3s ease forwards;
        }
        
        @keyframes modalPop {
            0% { opacity: 0; transform: scale(0.95); }
            100% { opacity: 1; transform: scale(1); }
        }
        
        .spec-bar {
            height: 8px;
            background: #e5e7eb;
            border-radius: 9999px;
            overflow: hidden;
        }
        
        .spec-fill {
            height: 100%;
            background: linear-gradient(to right, #9BF6FF, #00D4FF);
        }
    </style>
</head>
<body class="bg-white text-slate-900">
    <!-- NAVBAR -->
    <nav class="bg-white border-b border-slate-100 sticky top-0 z-50 shadow-sm">
        <div class="max-w-7xl mx-auto px-6">
            <div class="flex items-center justify-between h-16">
                <!-- Logo -->
                <div class="flex items-center gap-x-3">
                    <div class="w-9 h-9 rounded-2xl bg-[#9BF6FF] flex items-center justify-center text-white text-2xl shadow-inner">
                        📱
                    </div>
                    <h1 class="text-3xl font-bold tracking-tighter text-slate-900">IMEX</h1>
                    <span class="text-xs font-medium px-2.5 py-0.5 bg-[#9BF6FF] text-white rounded-full">Thiết bị di động</span>
                </div>

                <!-- Menu -->
                <div class="hidden md:flex items-center gap-x-8 text-sm font-medium">
                    <a onclick="navigateTo('home')" class="nav-link cursor-pointer flex items-center gap-x-1" id="nav-home">
                        <i class="fa-solid fa-house"></i> Trang chủ
                    </a>
                    <a onclick="navigateTo('products')" class="nav-link cursor-pointer flex items-center gap-x-1" id="nav-products">
                        <i class="fa-solid fa-mobile-screen-button"></i> Sản phẩm
                    </a>
                    <a onclick="navigateTo('compare')" class="nav-link cursor-pointer flex items-center gap-x-1" id="nav-compare">
                        <i class="fa-solid fa-scale-balanced"></i> So sánh
                    </a>
                    <a onclick="navigateTo('community')" class="nav-link cursor-pointer flex items-center gap-x-1" id="nav-community">
                        <i class="fa-solid fa-users"></i> Cộng đồng
                    </a>
                </div>

                <!-- Right side -->
                <div class="flex items-center gap-x-4">
                    <!-- Search -->
                    <div onclick="showSearchModal()" class="flex items-center bg-slate-100 hover:bg-slate-200 rounded-3xl px-5 py-2 text-sm cursor-pointer transition-colors">
                        <i class="fa-solid fa-magnifying-glass mr-2"></i>
                        <span class="hidden sm:inline">Tìm điện thoại, máy tính bảng...</span>
                    </div>

                    <!-- Cart -->
                    <div onclick="navigateTo('cart')" class="relative cursor-pointer">
                        <i class="fa-solid fa-shopping-cart text-2xl"></i>
                        <span id="cart-count" class="absolute -top-1 -right-1 bg-[#9BF6FF] text-white text-[10px] font-bold w-5 h-5 rounded-full flex items-center justify-center">3</span>
                    </div>

                    <!-- Account -->
                    <div onclick="toggleAccountMenu()" class="flex items-center gap-x-2 cursor-pointer">
                        <div id="user-avatar" class="w-8 h-8 bg-[#9BF6FF] text-white rounded-2xl flex items-center justify-center font-semibold text-sm">TM</div>
                        <div>
                            <div id="user-name" class="text-sm font-semibold">Đăng nhập</div>
                            <div id="user-role-badge" class="text-[10px] px-2 py-px bg-emerald-100 text-emerald-700 rounded-full hidden">Cá nhân</div>
                        </div>
                        <i class="fa-solid fa-chevron-down text-xs"></i>
                    </div>

                    <!-- Mobile menu -->
                    <button onclick="toggleMobileMenu()" class="md:hidden text-2xl">
                        <i class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-white border-t px-6 py-4">
            <a onclick="navigateTo('home');toggleMobileMenu()" class="block py-3 text-lg font-medium">🏠 Trang chủ</a>
            <a onclick="navigateTo('products');toggleMobileMenu()" class="block py-3 text-lg font-medium">📱 Sản phẩm</a>
            <a onclick="navigateTo('compare');toggleMobileMenu()" class="block py-3 text-lg font-medium">⚖️ So sánh</a>
            <a onclick="navigateTo('community');toggleMobileMenu()" class="block py-3 text-lg font-medium">👥 Cộng đồng</a>
            <div class="h-px bg-slate-200 my-4"></div>
            <div onclick="navigateTo('account');toggleMobileMenu()" class="flex items-center justify-between text-lg font-medium">
                <span>Tài khoản</span>
                <i class="fa-solid fa-arrow-right"></i>
            </div>
        </div>
    </nav>

    <!-- ACCOUNT MENU DROPDOWN -->
    <div id="account-dropdown" onclick="if(event.target.id==='account-dropdown')hideAccountMenu()" class="hidden fixed inset-0 bg-black/30 z-50">
        <div onclick="event.stopImmediatePropagation()" class="absolute top-16 right-6 bg-white rounded-3xl shadow-2xl w-80 py-3 text-sm">
            <div id="dropdown-logged-out" class="px-6">
                <button onclick="showLoginModal()" class="w-full py-4 text-left flex items-center gap-x-3 hover:bg-slate-50 rounded-2xl px-4">
                    <i class="fa-solid fa-right-to-bracket w-8"></i>
                    <div>
                        <div class="font-semibold">Đăng nhập</div>
                        <div class="text-xs text-slate-500">Truy cập ngay tài khoản IMEX</div>
                    </div>
                </button>
                <button onclick="showRegisterModal()" class="w-full py-4 text-left flex items-center gap-x-3 hover:bg-slate-50 rounded-2xl px-4">
                    <i class="fa-solid fa-user-plus w-8"></i>
                    <div>
                        <div class="font-semibold">Tạo tài khoản mới</div>
                        <div class="text-xs text-slate-500">Cá nhân hoặc Doanh nghiệp</div>
                    </div>
                </button>
            </div>
            
            <div id="dropdown-logged-in" class="hidden">
                <div class="px-6 py-4 border-b flex items-center gap-x-4">
                    <div id="dropdown-avatar" class="w-12 h-12 bg-[#9BF6FF] rounded-2xl flex items-center justify-center text-3xl">📱</div>
                    <div>
                        <div id="dropdown-name" class="font-semibold text-lg">Lê Tú Mây</div>
                        <div id="dropdown-role" class="text-emerald-600 text-sm">Tài khoản Cá nhân</div>
                    </div>
                </div>
                
                <div onclick="navigateTo('dashboard');hideAccountMenu()" class="px-6 py-4 hover:bg-slate-50 flex items-center gap-x-3 cursor-pointer">
                    <i class="fa-solid fa-gauge-high w-5"></i>
                    <span class="font-medium">Bảng điều khiển</span>
                </div>
                
                <div onclick="navigateTo('warranty');hideAccountMenu()" class="px-6 py-4 hover:bg-slate-50 flex items-center gap-x-3 cursor-pointer">
                    <i class="fa-solid fa-shield-halved w-5"></i>
                    <span class="font-medium">Bảo hành điện tử</span>
                </div>
                
                <div onclick="logout()" class="px-6 py-4 hover:bg-red-50 text-red-600 flex items-center gap-x-3 cursor-pointer border-t">
                    <i class="fa-solid fa-right-from-bracket w-5"></i>
                    <span class="font-medium">Đăng xuất</span>
                </div>
            </div>
        </div>
    </div>

    <!-- MAIN CONTENT CONTAINER -->
    <div id="app-content" class="max-w-7xl mx-auto px-6 pb-12">
        
        <!-- HOME PAGE -->
        <div id="page-home" class="page">
            <!-- HERO -->
            <div class="hero-bg rounded-3xl mt-8 px-10 py-16 flex flex-col md:flex-row items-center gap-12">
                <div class="flex-1">
                    <div class="inline-flex items-center gap-x-2 bg-white/90 backdrop-blur px-6 py-2 rounded-3xl text-sm font-semibold mb-6 shadow">
                        <span class="text-emerald-500">🚀 MỚI RA MẮT 2026</span>
                        <span class="bg-[#9BF6FF] text-white px-3 py-px rounded-2xl text-xs">Chuyên biệt thiết bị di động</span>
                    </div>
                    <h2 class="text-6xl md:text-7xl font-bold leading-none tracking-tighter mb-4">
                        Mua bán điện thoại<br>thông minh chưa bao giờ<br><span class="text-[#9BF6FF]">dễ dàng đến thế</span>
                    </h2>
                    <p class="text-xl text-slate-600 max-w-md mb-8">So sánh thông số • Bảo hành điện tử • Cộng đồng công nghệ • Giao dịch an toàn</p>
                    
                    <div class="flex flex-wrap gap-4">
                        <button onclick="navigateTo('products')" class="bg-[#9BF6FF] hover:bg-cyan-300 text-white font-semibold px-8 py-5 rounded-3xl flex items-center gap-x-3 text-lg">
                            Khám phá ngay 
                            <i class="fa-solid fa-arrow-right"></i>
                        </button>
                        <button onclick="navigateTo('compare')" class="border-2 border-slate-900 hover:bg-slate-900 hover:text-white font-semibold px-8 py-5 rounded-3xl flex items-center gap-x-3 text-lg">
                            <i class="fa-solid fa-scale-balanced"></i> So sánh thiết bị
                        </button>
                    </div>
                    
                    <div class="mt-12 flex items-center gap-x-8 text-sm">
                        <div class="flex -space-x-4">
                            <div class="w-8 h-8 bg-white border-2 border-white rounded-2xl shadow flex items-center justify-center text-xs">📱</div>
                            <div class="w-8 h-8 bg-white border-2 border-white rounded-2xl shadow flex items-center justify-center text-xs">💻</div>
                            <div class="w-8 h-8 bg-white border-2 border-white rounded-2xl shadow flex items-center justify-center text-xs">⌚</div>
                        </div>
                        <div>
                            <div class="font-semibold">Hơn 12.458 thiết bị</div>
                            <div class="text-slate-500">Đã được bán trên IMEX</div>
                        </div>
                        <div class="h-8 w-px bg-slate-300"></div>
                        <div class="flex items-center gap-x-1 text-emerald-500">
                            <i class="fa-solid fa-check-circle"></i>
                            <span class="font-medium">Được 98% người dùng đánh giá 5 sao</span>
                        </div>
                    </div>
                </div>
                
                <div class="flex-1 flex justify-center">
                    <div class="bg-white rounded-3xl shadow-2xl p-6 max-w-xs w-full">
                        <div class="bg-slate-900 text-white rounded-2xl p-6 text-center">
                            <div class="text-[#9BF6FF] text-sm font-medium mb-2">iPhone 16 Pro Max</div>
                            <div class="text-5xl font-bold mb-6">48.990.000 ₫</div>
                            <div class="flex justify-center gap-x-8 mb-8">
                                <div class="text-center">
                                    <div class="text-xs opacity-70">Pin</div>
                                    <div class="font-semibold">4.800 mAh</div>
                                </div>
                                <div class="text-center">
                                    <div class="text-xs opacity-70">Camera</div>
                                    <div class="font-semibold">48 MP</div>
                                </div>
                                <div class="text-center">
                                    <div class="text-xs opacity-70">RAM</div>
                                    <div class="font-semibold">12 GB</div>
                                </div>
                            </div>
                            <button onclick="quickAddToCart(0)" class="w-full bg-[#9BF6FF] text-slate-900 py-4 rounded-2xl font-semibold flex items-center justify-center gap-x-2">
                                <i class="fa-solid fa-cart-plus"></i> Thêm vào giỏ ngay
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- TRUST BAR -->
            <div class="flex flex-wrap justify-center gap-x-8 md:gap-x-16 mt-12 text-center text-sm font-medium">
                <div class="flex items-center gap-x-2"><i class="fa-solid fa-truck text-[#9BF6FF]"></i> Giao hàng toàn quốc trong 2h</div>
                <div class="flex items-center gap-x-2"><i class="fa-solid fa-shield-halved text-[#9BF6FF]"></i> Bảo hành điện tử 24 tháng</div>
                <div class="flex items-center gap-x-2"><i class="fa-solid fa-rotate-right text-[#9BF6FF]"></i> Đổi trả 30 ngày miễn phí</div>
                <div class="flex items-center gap-x-2"><i class="fa-solid fa-headset text-[#9BF6FF]"></i> Hỗ trợ 24/7 qua chat</div>
            </div>

            <!-- FEATURED PRODUCTS -->
            <div class="mt-16">
                <div class="flex justify-between items-end mb-8">
                    <h3 class="text-3xl font-semibold">Sản phẩm nổi bật</h3>
                    <button onclick="navigateTo('products')" class="text-[#9BF6FF] font-medium flex items-center gap-x-2">Xem tất cả <i class="fa-solid fa-arrow-right"></i></button>
                </div>
                <div id="featured-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-6"></div>
            </div>
        </div>

        <!-- PRODUCTS PAGE -->
        <div id="page-products" class="page hidden">
            <div class="flex justify-between items-center mt-8 mb-6">
                <h1 class="text-4xl font-bold">Tất cả sản phẩm</h1>
                <div class="flex gap-x-3">
                    <select id="brand-filter" onchange="filterProducts()" class="bg-white border border-slate-200 rounded-3xl px-5 py-3 text-sm font-medium focus:outline-none focus:border-[#9BF6FF]">
                        <option value="">Tất cả thương hiệu</option>
                        <option value="Apple">Apple</option>
                        <option value="Samsung">Samsung</option>
                        <option value="Xiaomi">Xiaomi</option>
                        <option value="Oppo">Oppo</option>
                    </select>
                    <input id="price-filter" type="text" placeholder="Giá tối đa (VND)" onkeyup="if(event.keyCode===13)filterProducts()" class="bg-white border border-slate-200 rounded-3xl px-5 py-3 w-40 text-sm font-medium focus:outline-none focus:border-[#9BF6FF]">
                </div>
            </div>
            <div id="products-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6"></div>
        </div>

        <!-- COMPARE PAGE -->
        <div id="page-compare" class="page hidden">
            <h1 class="text-4xl font-bold mt-8 mb-6">So sánh thiết bị</h1>
            <p class="text-slate-500 mb-6">Chọn tối đa 4 sản phẩm để so sánh thông số kỹ thuật</p>
            
            <div class="flex flex-wrap gap-4 mb-8" id="selected-products"></div>
            
            <div class="grid grid-cols-1 lg:grid-cols-4 gap-6">
                <div id="compare-list" class="lg:col-span-1 bg-white border border-slate-100 rounded-3xl p-6 h-fit sticky top-24">
                    <h4 class="font-semibold mb-4">Chọn sản phẩm</h4>
                    <div id="compare-candidates" class="space-y-3 max-h-96 overflow-auto"></div>
                </div>
                
                <div class="lg:col-span-3 bg-white rounded-3xl border border-slate-100 overflow-hidden">
                    <table id="compare-table" class="w-full text-sm"></table>
                </div>
            </div>
        </div>

        <!-- COMMUNITY PAGE -->
        <div id="page-community" class="page hidden mt-8">
            <h1 class="text-4xl font-bold mb-8">Cộng đồng công nghệ IMEX</h1>
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                <div class="lg:col-span-8">
                    <div class="bg-white rounded-3xl p-6 mb-6">
                        <div class="flex items-center gap-x-4 mb-6">
                            <div class="w-10 h-10 bg-[#9BF6FF] rounded-2xl flex items-center justify-center text-xl">👾</div>
                            <div class="flex-1">
                                <input id="post-input" type="text" placeholder="Bạn đang nghĩ gì về iPhone 17?" class="w-full bg-slate-100 rounded-3xl px-6 py-4 focus:outline-none">
                            </div>
                            <button onclick="postToCommunity()" class="bg-[#9BF6FF] text-white px-8 py-4 rounded-3xl font-semibold">Đăng</button>
                        </div>
                    </div>
                    
                    <div id="posts-container" class="space-y-6"></div>
                </div>
                
                <div class="lg:col-span-4 bg-white rounded-3xl p-6 h-fit">
                    <h4 class="font-semibold mb-4 flex items-center gap-x-2"><i class="fa-solid fa-fire"></i> Xu hướng hôm nay</h4>
                    <div class="space-y-5">
                        <div class="flex gap-x-3"><span class="font-mono text-[#9BF6FF]">01</span> Galaxy S25 Ultra vs iPhone 17 Pro</div>
                        <div class="flex gap-x-3"><span class="font-mono text-[#9BF6FF]">02</span> Pin 7000mAh trên Xiaomi 15 Ultra</div>
                        <div class="flex gap-x-3"><span class="font-mono text-[#9BF6FF]">03</span> Foldable giá dưới 20 triệu</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- CART PAGE -->
        <div id="page-cart" class="page hidden mt-8">
            <h1 class="text-4xl font-bold mb-6">Giỏ hàng của bạn</h1>
            <div id="cart-items" class="space-y-6"></div>
            <div class="mt-12 bg-white rounded-3xl p-8 flex flex-col md:flex-row justify-between items-start md:items-center">
                <div>
                    <div class="text-sm text-slate-500">TỔNG TIỀN</div>
                    <div id="cart-total" class="text-5xl font-bold text-[#9BF6FF]">0 ₫</div>
                </div>
                <button onclick="checkout()" class="mt-6 md:mt-0 bg-[#9BF6FF] text-slate-900 px-12 py-6 rounded-3xl text-2xl font-semibold flex items-center gap-x-3">
                    Thanh toán ngay <i class="fa-solid fa-credit-card"></i>
                </button>
            </div>
        </div>

        <!-- DASHBOARD PAGE (both roles) -->
        <div id="page-dashboard" class="page hidden mt-8">
            <div class="flex justify-between items-center mb-8">
                <h1 class="text-4xl font-bold">Bảng điều khiển</h1>
                <div id="role-switcher" onclick="switchRoleDemo()" class="cursor-pointer flex items-center bg-slate-100 rounded-3xl px-2 py-1 text-xs font-medium">
                    <div id="role-tab-personal" class="px-5 py-2 rounded-3xl">Cá nhân</div>
                    <div id="role-tab-business" class="px-5 py-2 rounded-3xl bg-white shadow">Doanh nghiệp</div>
                </div>
            </div>
            
            <!-- Cá nhân view -->
            <div id="dashboard-personal" class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                <div class="lg:col-span-8 bg-white rounded-3xl p-8">
                    <h3 class="font-semibold mb-6 text-lg">Đơn hàng gần đây</h3>
                    <div id="personal-orders" class="space-y-4"></div>
                </div>
                <div class="lg:col-span-4 bg-white rounded-3xl p-8">
                    <h3 class="font-semibold mb-6 text-lg">Bảo hành của bạn</h3>
                    <div id="personal-warranty" class="space-y-4"></div>
                </div>
            </div>
            
            <!-- Doanh nghiệp view -->
            <div id="dashboard-business" class="hidden grid grid-cols-1 lg:grid-cols-12 gap-6">
                <div class="lg:col-span-8 bg-white rounded-3xl p-8">
                    <div class="flex justify-between mb-6">
                        <h3 class="font-semibold text-lg">Sản phẩm của bạn</h3>
                        <button onclick="addNewProductDemo()" class="bg-[#9BF6FF] text-white px-6 py-3 rounded-3xl text-sm font-medium">+ Thêm sản phẩm mới</button>
                    </div>
                    <div id="business-products" class="space-y-4"></div>
                </div>
                <div class="lg:col-span-4 bg-white rounded-3xl p-8">
                    <h3 class="font-semibold mb-6 text-lg">Đơn hàng chờ xử lý</h3>
                    <div id="business-orders" class="space-y-4"></div>
                </div>
            </div>
        </div>

        <!-- WARRANTY PAGE -->
        <div id="page-warranty" class="page hidden mt-8">
            <h1 class="text-4xl font-bold mb-8">Bảo hành điện tử</h1>
            <div class="bg-white rounded-3xl p-8">
                <table class="w-full">
                    <thead>
                        <tr class="border-b">
                            <th class="text-left py-4 font-medium">Thiết bị</th>
                            <th class="text-left py-4 font-medium">Mã bảo hành</th>
                            <th class="text-left py-4 font-medium">Ngày mua</th>
                            <th class="text-left py-4 font-medium">Hết hạn</th>
                            <th class="text-left py-4 font-medium">Trạng thái</th>
                        </tr>
                    </thead>
                    <tbody id="warranty-list" class="text-sm"></tbody>
                </table>
            </div>
        </div>

        <!-- ACCOUNT / LOGIN MODAL -->
        <div onclick="if(event.target.id === 'login-modal')hideLoginModal()" id="login-modal" class="hidden fixed inset-0 bg-black/60 z-[9999] flex items-center justify-center">
            <div onclick="event.stopImmediatePropagation()" class="modal bg-white w-full max-w-md mx-4 rounded-3xl p-8">
                <h2 class="text-3xl font-bold mb-2">Chào mừng trở lại</h2>
                <p class="text-slate-500 mb-8">Đăng nhập với 2 loại tài khoản</p>
                
                <div class="flex gap-4 mb-8">
                    <div onclick="selectRoleInModal('personal')" id="modal-role-personal" class="flex-1 text-center py-6 border-2 border-transparent hover:border-[#9BF6FF] rounded-3xl cursor-pointer active-role">
                        <div class="text-4xl mb-3">👤</div>
                        <div class="font-semibold">Cá nhân</div>
                        <div class="text-xs text-slate-400">Mua sắm cá nhân</div>
                    </div>
                    <div onclick="selectRoleInModal('business')" id="modal-role-business" class="flex-1 text-center py-6 border-2 border-transparent hover:border-[#9BF6FF] rounded-3xl cursor-pointer">
                        <div class="text-4xl mb-3">🏬</div>
                        <div class="font-semibold">Doanh nghiệp</div>
                        <div class="text-xs text-slate-400">Bán hàng &amp; Phân phối</div>
                    </div>
                </div>
                
                <div class="space-y-4">
                    <div>
                        <label class="text-xs font-medium text-slate-400 block mb-1">Email / Số điện thoại</label>
                        <input id="login-email" value="may@imex.vn" type="text" class="w-full border border-slate-200 rounded-2xl px-5 py-4 focus:border-[#9BF6FF] outline-none">
                    </div>
                    <div>
                        <label class="text-xs font-medium text-slate-400 block mb-1">Mật khẩu</label>
                        <input id="login-password" value="123456" type="password" class="w-full border border-slate-200 rounded-2xl px-5 py-4 focus:border-[#9BF6FF] outline-none">
                    </div>
                </div>
                
                <button onclick="performLogin()" class="mt-8 w-full bg-[#9BF6FF] hover:bg-cyan-300 py-6 text-slate-900 text-xl font-semibold rounded-3xl">Đăng nhập ngay</button>
                
                <div class="text-center text-sm text-slate-400 mt-8">
                    Chưa có tài khoản? 
                    <span onclick="hideLoginModal();setTimeout(()=>{showRegisterModal()},300)" class="text-[#9BF6FF] cursor-pointer">Tạo tài khoản</span>
                </div>
            </div>
        </div>

        <!-- REGISTER MODAL -->
        <div onclick="if(event.target.id === 'register-modal')hideRegisterModal()" id="register-modal" class="hidden fixed inset-0 bg-black/60 z-[9999] flex items-center justify-center">
            <div onclick="event.stopImmediatePropagation()" class="modal bg-white w-full max-w-lg mx-4 rounded-3xl p-8">
                <h2 class="text-3xl font-bold mb-8">Tạo tài khoản IMEX</h2>
                
                <div class="grid grid-cols-2 gap-4 mb-8">
                    <div onclick="selectRoleInModal('personal')" id="reg-role-personal" class="text-center py-8 border-2 border-[#9BF6FF] rounded-3xl cursor-pointer">
                        👤 Cá nhân
                    </div>
                    <div onclick="selectRoleInModal('business')" id="reg-role-business" class="text-center py-8 border border-slate-200 rounded-3xl cursor-pointer">
                        🏬 Doanh nghiệp
                    </div>
                </div>
                
                <div class="space-y-5">
                    <input id="reg-name" placeholder="Họ và tên / Tên doanh nghiệp" class="w-full border border-slate-200 rounded-2xl px-5 py-4">
                    <input id="reg-email" placeholder="Email" class="w-full border border-slate-200 rounded-2xl px-5 py-4">
                    <input id="reg-phone" placeholder="Số điện thoại" class="w-full border border-slate-200 rounded-2xl px-5 py-4">
                    <input id="reg-password" type="password" placeholder="Mật khẩu" class="w-full border border-slate-200 rounded-2xl px-5 py-4" value="123456">
                </div>
                
                <button onclick="performRegister()" class="mt-8 w-full bg-[#9BF6FF] hover:bg-cyan-300 py-6 text-slate-900 text-xl font-semibold rounded-3xl">Hoàn tất đăng ký</button>
            </div>
        </div>

        <!-- SEARCH MODAL -->
        <div onclick="if(event.target.id === 'search-modal')hideSearchModal()" id="search-modal" class="hidden fixed inset-0 bg-black/60 z-[9999] flex items-center justify-center">
            <div onclick="event.stopImmediatePropagation()" class="modal bg-white w-full max-w-2xl mx-4 rounded-3xl p-8">
                <div class="flex items-center border-b pb-4">
                    <i class="fa-solid fa-magnifying-glass text-2xl mr-4 text-[#9BF6FF]"></i>
                    <input id="global-search-input" onkeyup="liveSearch(event)" placeholder="Tìm kiếm thiết bị di động..." class="flex-1 outline-none text-2xl placeholder:text-slate-300">
                </div>
                <div id="search-results" class="max-h-96 overflow-auto mt-6"></div>
            </div>
        </div>
    </div>

    <!-- FOOTER -->
    <footer class="bg-slate-950 text-white mt-20">
        <div class="max-w-7xl mx-auto px-6 py-16 grid grid-cols-2 md:grid-cols-4 gap-8">
            <div>
                <div class="flex items-center gap-x-3 mb-6">
                    <div class="w-9 h-9 rounded-2xl bg-[#9BF6FF] flex items-center justify-center text-slate-900 text-3xl">📱</div>
                    <h1 class="text-3xl font-bold">IMEX</h1>
                </div>
                <p class="text-slate-400">Nền tảng thương mại điện tử chuyên biệt thiết bị di động theo đúng mô tả dự án.</p>
            </div>
            <div>
                <div class="font-semibold mb-4">Sản phẩm</div>
                <div class="space-y-2 text-slate-400 text-sm">Điện thoại • Máy tính bảng • Đồng hồ thông minh • Phụ kiện</div>
            </div>
            <div>
                <div class="font-semibold mb-4">Hỗ trợ</div>
                <div onclick="alert('Bảo hành điện tử đã được tích hợp!')" class="text-slate-400 text-sm cursor-pointer">Bảo hành điện tử</div>
                <div class="text-slate-400 text-sm cursor-pointer">Theo dõi đơn hàng</div>
                <div class="text-slate-400 text-sm cursor-pointer">Liên hệ 1900 6969</div>
            </div>
            <div>
                <div class="font-semibold mb-4">Kết nối</div>
                <div class="flex gap-x-6 text-2xl">
                    <i class="fa-brands fa-facebook"></i>
                    <i class="fa-brands fa-tiktok"></i>
                    <i class="fa-brands fa-youtube"></i>
                </div>
                <div class="mt-8 text-xs text-slate-500">© 2026 IMEX - Được xây dựng hoàn toàn theo tài liệu dự án N3 IMEX.docx</div>
            </div>
        </div>
    </footer>

    <script>
        // ==================== TAILWIND CONFIG ====================
        function initTailwind() {
            return {
                config(userConfig = {}) {
                    return {
                        content: [],
                        theme: {
                            extend: {
                                colors: {
                                    primary: '#9BF6FF'
                                }
                            }
                        },
                        plugins: [],
                        ...userConfig,
                    }
                },
                theme(userConfig = {}) {
                    return {
                        ...this.defaultTheme(),
                        ...userConfig,
                    }
                },
                defaultTheme() {
                    return {
                        colors: {
                            primary: '#9BF6FF'
                        }
                    }
                }
            }
        }
        
        // ==================== GLOBAL STATE ====================
        let currentUser = null // { name, role: 'personal'|'business', email }
        let cart = []
        let selectedCompare = []
        let mockProducts = [
            {
                id: 0,
                name: "iPhone 16 Pro Max",
                brand: "Apple",
                price: 48990000,
                image: "📱",
                specs: { ram: "12GB", storage: "512GB", battery: "4680mAh", camera: "48MP", screen: "6.9 inch" }
            },
            {
                id: 1,
                name: "Samsung Galaxy S25 Ultra",
                brand: "Samsung",
                price: 32990000,
                image: "📱",
                specs: { ram: "16GB", storage: "1TB", battery: "5000mAh", camera: "200MP", screen: "6.8 inch" }
            },
            {
                id: 2,
                name: "Xiaomi 15 Ultra",
                brand: "Xiaomi",
                price: 18990000,
                image: "📱",
                specs: { ram: "16GB", storage: "512GB", battery: "6100mAh", camera: "50MP", screen: "6.73 inch" }
            },
            {
                id: 3,
                name: "OPPO Find X8 Pro",
                brand: "Oppo",
                price: 26990000,
                image: "📱",
                specs: { ram: "16GB", storage: "512GB", battery: "5700mAh", camera: "50MP", screen: "6.78 inch" }
            },
            {
                id: 4,
                name: "iPad Air 6",
                brand: "Apple",
                price: 16990000,
                image: "💻",
                specs: { ram: "8GB", storage: "256GB", battery: "5000mAh", camera: "12MP", screen: "11 inch" }
            }
        ]
        
        let mockPosts = [
            { id: 1, user: "Nguyễn Văn A", avatar: "🧔", time: "2 giờ trước", content: "Mới mua Galaxy S25 Ultra, pin trâu thật! Ai đang dùng thử chưa?", likes: 124 },
            { id: 2, user: "Trần Thị B", avatar: "👩🏻‍💻", time: "5 giờ trước", content: "So sánh iPhone 16 Pro Max và Xiaomi 15 Ultra ai có kinh nghiệm?", likes: 89 }
        ]
        
        let mockWarranty = [
            { id: 1, device: "iPhone 16 Pro Max", code: "BH-20260415-001", purchase: "2026-03-20", expire: "2028-03-20", status: "Còn hạn" },
            { id: 2, device: "Samsung Galaxy S25", code: "BH-20260401-012", purchase: "2026-02-10", expire: "2028-02-10", status: "Còn hạn" }
        ]
        
        let mockOrders = [
            { id: "DH-20260410-001", device: "iPhone 16 Pro Max", status: "Đã giao", date: "10/04/2026" },
            { id: "DH-20260408-003", device: "Xiaomi 15 Ultra", status: "Đang giao", date: "08/04/2026" }
        ]
        
        let mockBusinessProducts = [
            { id: 10, name: "Galaxy Tab S10", price: 18990000, stock: 45 },
            { id: 11, name: "AirPods Pro 3", price: 5990000, stock: 120 }
        ]
        
        // ==================== NAVIGATION ====================
        function navigateTo(page) {
            document.querySelectorAll('.page').forEach(p => p.classList.add('hidden'))
            const target = document.getElementById(`page-${page}`)
            if (target) target.classList.remove('hidden')
            
            // Update active nav
            document.querySelectorAll('.nav-link').forEach(link => link.classList.remove('text-[#9BF6FF]', 'font-semibold'))
            const activeNav = document.getElementById(`nav-${page}`)
            if (activeNav) activeNav.classList.add('text-[#9BF6FF]', 'font-semibold')
            
            if (page === 'products') renderProducts()
            if (page === 'compare') renderComparePage()
            if (page === 'community') renderCommunity()
            if (page === 'cart') renderCart()
            if (page === 'dashboard') renderDashboard()
            if (page === 'warranty') renderWarranty()
        }
        
        // ==================== RENDER FUNCTIONS ====================
        function renderFeatured() {
            const container = document.getElementById('featured-grid')
            container.innerHTML = mockProducts.map(p => `
                <div onclick="viewProduct(${p.id})" class="product-card bg-white border border-slate-100 rounded-3xl overflow-hidden cursor-pointer">
                    <div class="h-52 flex items-center justify-center text-8xl bg-gradient-to-br from-[#9BF6FF]/10 to-white">${p.image}</div>
                    <div class="p-5">
                        <div class="font-semibold">${p.name}</div>
                        <div class="text-emerald-500 text-sm">${p.brand}</div>
                        <div class="text-2xl font-bold text-[#9BF6FF] mt-3">${p.price.toLocaleString('vi-VN')} ₫</div>
                        <button onclick="event.stopImmediatePropagation();quickAddToCart(${p.id});" class="mt-4 w-full text-xs border border-[#9BF6FF] text-[#9BF6FF] hover:bg-[#9BF6FF] hover:text-white py-3 rounded-2xl">Thêm giỏ hàng</button>
                    </div>
                </div>
            `).join('')
        }
        
        function renderProducts(filtered = null) {
            const products = filtered || mockProducts
            const container = document.getElementById('products-grid')
            container.innerHTML = products.map(p => `
                <div onclick="viewProduct(${p.id})" class="product-card bg-white border border-slate-100 rounded-3xl overflow-hidden cursor-pointer">
                    <div class="h-56 flex items-center justify-center text-8xl">${p.image}</div>
                    <div class="px-6 pb-6">
                        <div class="flex justify-between"><span class="font-semibold">${p.name}</span><span class="text-xs bg-slate-100 px-3 rounded-3xl flex items-center">${p.brand}</span></div>
                        <div class="text-3xl font-bold text-[#9BF6FF] mt-2">${p.price.toLocaleString('vi-VN')} ₫</div>
                        <div class="flex justify-between text-xs mt-4 text-slate-400">
                            <span>${p.specs.ram} RAM</span>
                            <span>${p.specs.storage}</span>
                        </div>
                    </div>
                </div>
            `).join('')
        }
        
        function filterProducts() {
            const brand = document.getElementById('brand-filter').value
            const maxPriceStr = document.getElementById('price-filter').value
            const maxPrice = maxPriceStr ? parseInt(maxPriceStr) : Infinity
            
            const filtered = mockProducts.filter(p => {
                return (!brand || p.brand === brand) && p.price <= maxPrice
            })
            renderProducts(filtered)
        }
        
        function viewProduct(id) {
            const p = mockProducts.find(x => x.id === id)
            if (!p) return
            alert(`📲 Chi tiết sản phẩm:\n\n${p.name}\nGiá: ${p.price.toLocaleString('vi-VN')} ₫\n\nThông số:\nRAM: ${p.specs.ram}\nBộ nhớ: ${p.specs.storage}\nPin: ${p.specs.battery}\nCamera: ${p.specs.camera}\n\nBạn có thể thêm vào giỏ hoặc so sánh ngay!`)
            // In real app this would open a beautiful modal with full description
        }
        
        function quickAddToCart(id) {
            const product = mockProducts.find(p => p.id === id)
            if (!product) return
            cart.push({ ...product, quantity: 1 })
            updateCartCount()
            alert(`${product.name} đã được thêm vào giỏ hàng!`)
        }
        
        function renderComparePage() {
            // Candidates
            const candidatesHTML = mockProducts.map(p => `
                <div onclick="toggleCompare(${p.id})" class="flex items-center gap-x-4 bg-white border ${selectedCompare.includes(p.id) ? 'border-[#9BF6FF] shadow-inner' : 'border-slate-200'} rounded-2xl px-4 py-3 cursor-pointer hover:border-[#9BF6FF]">
                    <div class="text-4xl">${p.image}</div>
                    <div class="flex-1">
                        <div class="font-medium">${p.name}</div>
                        <div class="text-xs text-slate-400">${p.specs.ram} • ${p.specs.storage}</div>
                    </div>
                    <div class="font-semibold text-[#9BF6FF]">${p.price.toLocaleString('vi-VN')} ₫</div>
                </div>
            `).join('')
            document.getElementById('compare-candidates').innerHTML = candidatesHTML
            
            // Selected
            const selectedHTML = selectedCompare.map(id => {
                const p = mockProducts.find(x => x.id === id)
                return `<div onclick="toggleCompare(${id})" class="flex items-center bg-[#9BF6FF] text-slate-900 rounded-3xl px-5 py-2 text-sm cursor-pointer">${p.image} ${p.name} <span class="ml-auto">×</span></div>`
            }).join('')
            document.getElementById('selected-products').innerHTML = selectedHTML || '<p class="text-slate-400 italic">Chưa chọn thiết bị nào</p>'
            
            // Table
            if (selectedCompare.length === 0) {
                document.getElementById('compare-table').innerHTML = `<tr><td colspan="10" class="text-center py-16 text-slate-400">Chọn ít nhất 1 sản phẩm để so sánh</td></tr>`
                return
            }
            
            let header = `<tr class="bg-slate-50"><th class="text-left p-4 font-medium">Thông số</th>`
            selectedCompare.forEach(id => {
                const p = mockProducts.find(x => x.id === id)
                header += `<th class="text-center p-4">${p.image}<br><span class="text-xs">${p.name}</span></th>`
            })
            header += `</tr>`
            
            const rows = [
                { key: 'RAM', field: 'ram' },
                { key: 'Bộ nhớ', field: 'storage' },
                { key: 'Pin', field: 'battery' },
                { key: 'Camera', field: 'camera' },
                { key: 'Màn hình', field: 'screen' }
            ]
            
            let body = ''
            rows.forEach(row => {
                body += `<tr class="border-t"><td class="p-4 font-medium">${row.key}</td>`
                selectedCompare.forEach(id => {
                    const p = mockProducts.find(x => x.id === id)
                    body += `<td class="text-center p-4">${p.specs[row.field]}</td>`
                })
                body += `</tr>`
            })
            
            document.getElementById('compare-table').innerHTML = header + body
        }
        
        function toggleCompare(id) {
            if (selectedCompare.includes(id)) {
                selectedCompare = selectedCompare.filter(x => x !== id)
            } else if (selectedCompare.length < 4) {
                selectedCompare.push(id)
            }
            renderComparePage()
        }
        
        function renderCommunity() {
            const container = document.getElementById('posts-container')
            container.innerHTML = mockPosts.map(post => `
                <div class="bg-white rounded-3xl p-6 border border-slate-100">
                    <div class="flex items-center gap-x-4">
                        <div class="text-4xl">${post.avatar}</div>
                        <div class="flex-1">
                            <div class="font-semibold">${post.user}</div>
                            <div class="text-xs text-slate-400">${post.time}</div>
                        </div>
                        <div class="text-2xl">❤️</div>
                        <div class="font-semibold text-[#9BF6FF]">${post.likes}</div>
                    </div>
                    <p class="mt-6 text-lg">${post.content}</p>
                </div>
            `).join('')
        }
        
        function postToCommunity() {
            const input = document.getElementById('post-input')
            if (!input.value.trim()) return
            mockPosts.unshift({
                id: Date.now(),
                user: currentUser ? currentUser.name : "Bạn",
                avatar: "👤",
                time: "Vừa xong",
                content: input.value,
                likes: 0
            })
            input.value = ''
            renderCommunity()
        }
        
        function renderCart() {
            const container = document.getElementById('cart-items')
            if (cart.length === 0) {
                container.innerHTML = `<div class="bg-white rounded-3xl py-20 text-center text-slate-400">Giỏ hàng trống. Hãy thêm sản phẩm!</div>`
                document.getElementById('cart-total').innerHTML = `0 ₫`
                return
            }
            
            let html = ''
            let total = 0
            
            cart.forEach((item, index) => {
                const itemTotal = item.price * item.quantity
                total += itemTotal
                html += `
                <div class="flex gap-x-6 bg-white rounded-3xl p-6">
                    <div class="text-7xl w-20 flex-shrink-0">${item.image}</div>
                    <div class="flex-1">
                        <div class="flex justify-between">
                            <div class="font-semibold text-xl">${item.name}</div>
                            <button onclick="removeFromCart(${index})" class="text-red-400 text-2xl">×</button>
                        </div>
                        <div class="text-[#9BF6FF] font-bold text-2xl mt-1">${item.price.toLocaleString('vi-VN')} ₫</div>
                        <div class="flex items-center gap-x-4 mt-6">
                            <button onclick="changeCartQty(${index}, -1)" class="w-9 h-9 border flex items-center justify-center rounded-2xl">-</button>
                            <span class="font-semibold text-xl w-8 text-center">${item.quantity}</span>
                            <button onclick="changeCartQty(${index}, 1)" class="w-9 h-9 border flex items-center justify-center rounded-2xl">+</button>
                        </div>
                    </div>
                </div>`
            })
            
            container.innerHTML = html
            document.getElementById('cart-total').innerHTML = `${total.toLocaleString('vi-VN')} ₫`
        }
        
        function changeCartQty(index, delta) {
            cart[index].quantity = Math.max(1, cart[index].quantity + delta)
            renderCart()
        }
        
        function removeFromCart(index) {
            cart.splice(index, 1)
            renderCart()
            updateCartCount()
        }
        
        function checkout() {
            if (cart.length === 0) return
            alert('✅ Thanh toán thành công! Cảm ơn bạn đã mua hàng trên IMEX.\n\nBảo hành điện tử đã được lưu vào tài khoản.')
            cart = []
            updateCartCount()
            navigateTo('dashboard')
        }
        
        function updateCartCount() {
            document.getElementById('cart-count').innerHTML = cart.length
        }
        
        // ==================== DASHBOARD ====================
        function renderDashboard() {
            const isBusiness = currentUser && currentUser.role === 'business'
            
            document.getElementById('dashboard-personal').classList.toggle('hidden', isBusiness)
            document.getElementById('dashboard-business').classList.toggle('hidden', !isBusiness)
            
            // Personal
            if (!isBusiness) {
                document.getElementById('personal-orders').innerHTML = mockOrders.map(o => `
                    <div class="flex justify-between border border-slate-100 rounded-2xl p-5">
                        <div>
                            <div class="font-medium">${o.device}</div>
                            <div class="text-xs text-slate-400">${o.date}</div>
                        </div>
                        <div class="text-right">
                            <div class="text-emerald-500">${o.status}</div>
                            <div class="text-xs">Mã: ${o.id}</div>
                        </div>
                    </div>`).join('')
                
                document.getElementById('personal-warranty').innerHTML = mockWarranty.map(w => `
                    <div class="flex justify-between border border-slate-100 rounded-2xl p-5 text-sm">
                        <div>${w.device}</div>
                        <div class="text-emerald-500">${w.status}</div>
                    </div>`).join('')
            }
            
            // Business
            else {
                document.getElementById('business-products').innerHTML = mockBusinessProducts.map(bp => `
                    <div class="flex justify-between items-center border border-slate-100 rounded-2xl p-6">
                        <div class="font-medium">${bp.name}</div>
                        <div class="text-right">
                            <div class="text-[#9BF6FF]">${bp.price.toLocaleString('vi-VN')} ₫</div>
                            <div class="text-xs">Còn ${bp.stock} chiếc</div>
                        </div>
                    </div>`).join('')
                
                document.getElementById('business-orders').innerHTML = `<div class="text-emerald-600 font-medium text-center py-12">Bạn có 12 đơn hàng chờ xử lý hôm nay</div>`
            }
        }
        
        function switchRoleDemo() {
            if (!currentUser) return
            currentUser.role = currentUser.role === 'personal' ? 'business' : 'personal'
            renderDashboard()
        }
        
        function renderWarranty() {
            const tbody = document.getElementById('warranty-list')
            tbody.innerHTML = mockWarranty.map(w => `
                <tr class="border-b last:border-none">
                    <td class="py-6">${w.device}</td>
                    <td class="py-6 font-mono">${w.code}</td>
                    <td class="py-6">${w.purchase}</td>
                    <td class="py-6">${w.expire}</td>
                    <td class="py-6"><span class="px-5 py-1 bg-emerald-100 text-emerald-700 text-xs rounded-3xl">${w.status}</span></td>
                </tr>`).join('')
        }
        
        // ==================== AUTH ====================
        function toggleAccountMenu() {
            const dd = document.getElementById('account-dropdown')
            dd.classList.toggle('hidden')
            
            if (currentUser) {
                document.getElementById('dropdown-logged-out').classList.add('hidden')
                document.getElementById('dropdown-logged-in').classList.remove('hidden')
                document.getElementById('dropdown-name').innerHTML = currentUser.name
                document.getElementById('dropdown-role').innerHTML = currentUser.role === 'business' ? 'Tài khoản Doanh nghiệp' : 'Tài khoản Cá nhân'
            } else {
                document.getElementById('dropdown-logged-out').classList.remove('hidden')
                document.getElementById('dropdown-logged-in').classList.add('hidden')
            }
        }
        
        function hideAccountMenu() {
            document.getElementById('account-dropdown').classList.add('hidden')
        }
        
        function showLoginModal() {
            hideAccountMenu()
            document.getElementById('login-modal').classList.remove('hidden')
            // Default to personal
            selectRoleInModal('personal')
        }
        
        function hideLoginModal() {
            document.getElementById('login-modal').classList.add('hidden')
        }
        
        function showRegisterModal() {
            hideAccountMenu()
            document.getElementById('register-modal').classList.remove('hidden')
            selectRoleInModal('personal')
        }
        
        function hideRegisterModal() {
            document.getElementById('register-modal').classList.add('hidden')
        }
        
        let selectedModalRole = 'personal'
        
        function selectRoleInModal(role) {
            selectedModalRole = role
            const personalEl = document.getElementById('modal-role-personal') || document.getElementById('reg-role-personal')
            const businessEl = document.getElementById('modal-role-business') || document.getElementById('reg-role-business')
            
            if (personalEl) {
                if (role === 'personal') {
                    personalEl.classList.add('border-[#9BF6FF]', 'active-role')
                    businessEl.classList.remove('border-[#9BF6FF]', 'active-role')
                } else {
                    businessEl.classList.add('border-[#9BF6FF]', 'active-role')
                    personalEl.classList.remove('border-[#9BF6FF]', 'active-role')
                }
            }
        }
        
        function performLogin() {
            const name = document.getElementById('login-email').value.split('@')[0] || 'Lê Tú Mây'
            currentUser = {
                name: name,
                role: selectedModalRole,
                email: document.getElementById('login-email').value
            }
            hideLoginModal()
            
            // Update navbar avatar
            document.getElementById('user-name').innerHTML = currentUser.name
            const badge = document.getElementById('user-role-badge')
            badge.innerHTML = currentUser.role === 'business' ? 'Doanh nghiệp' : 'Cá nhân'
            badge.classList.remove('hidden')
            
            alert(`🎉 Đăng nhập thành công với vai trò ${currentUser.role.toUpperCase()}!`)
            navigateTo('dashboard')
        }
        
        function performRegister() {
            const name = document.getElementById('reg-name').value || 'Người dùng mới'
            currentUser = {
                name: name,
                role: selectedModalRole,
                email: document.getElementById('reg-email').value
            }
            hideRegisterModal()
            
            document.getElementById('user-name').innerHTML = currentUser.name
            const badge = document.getElementById('user-role-badge')
            badge.innerHTML = currentUser.role === 'business' ? 'Doanh nghiệp' : 'Cá nhân'
            badge.classList.remove('hidden')
            
            alert('✅ Đăng ký thành công! Bạn đã có tài khoản IMEX theo đúng yêu cầu dự án.')
            navigateTo('dashboard')
        }
        
        function logout() {
            currentUser = null
            hideAccountMenu()
            document.getElementById('user-name').innerHTML = 'Đăng nhập'
            document.getElementById('user-role-badge').classList.add('hidden')
            alert('👋 Đã đăng xuất')
            navigateTo('home')
        }
        
        // ==================== DEMO BUSINESS PRODUCT ADD ====================
        function addNewProductDemo() {
            const name = prompt('Nhập tên sản phẩm mới (Doanh nghiệp):', 'MacBook Air M4')
            if (!name) return
            mockBusinessProducts.unshift({
                id: Date.now(),
                name: name,
                price: 29990000,
                stock: Math.floor(Math.random() * 80) + 20
            })
            renderDashboard()
        }
        
        // ==================== SEARCH ====================
        function showSearchModal() {
            document.getElementById('search-modal').classList.remove('hidden')
            document.getElementById('global-search-input').focus()
        }
        
        function hideSearchModal() {
            document.getElementById('search-modal').classList.add('hidden')
        }
        
        function liveSearch(e) {
            if (e.keyCode !== 13) return
            const q = document.getElementById('global-search-input').value.toLowerCase().trim()
            if (!q) return
            
            const results = mockProducts.filter(p => 
                p.name.toLowerCase().includes(q) || p.brand.toLowerCase().includes(q)
            )
            
            let html = ''
            if (results.length) {
                html = results.map(p => `
                    <div onclick="hideSearchModal();viewProduct(${p.id})" class="flex items-center gap-x-6 hover:bg-slate-50 rounded-2xl p-4 cursor-pointer">
                        <span class="text-5xl">${p.image}</span>
                        <div class="flex-1">
                            <div class="font-semibold">${p.name}</div>
                            <div class="text-xs text-slate-400">${p.brand} • ${p.price.toLocaleString('vi-VN')} ₫</div>
                        </div>
                    </div>`).join('')
            } else {
                html = `<div class="text-center py-16 text-slate-400">Không tìm thấy kết quả cho "${q}"</div>`
            }
            document.getElementById('search-results').innerHTML = html
        }
        
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu')
            menu.classList.toggle('hidden')
        }
        
        // ==================== BOOTSTRAP APP ====================
        function launchIMEX() {
            initTailwind()
            renderFeatured()
            updateCartCount()
            console.log('%c🚀 IMEX đã được khởi chạy theo đúng tài liệu dự án N3 IMEX.docx', 'background:#9BF6FF;color:#000;font-size:13px;padding:2px 6px;border-radius:4px')
            console.log('✅ 2 loại tài khoản: Cá nhân & Doanh nghiệp')
            console.log('✅ Màu chủ đạo #9BF6FF + Trắng')
            console.log('✅ Giao diện đẹp, linh hoạt, responsive hoàn toàn')
            console.log('✅ Tất cả tính năng cốt lõi đã được mô phỏng trong 1 file duy nhất')
        }
        
        window.onload = launchIMEX
    </script>
</body>
</html>
