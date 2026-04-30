[index.html](https://github.com/user-attachments/files/27232948/index.html)
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <script>
    // التأكد هل المستخدم مسجل دخول ولا لأ
    if (localStorage.getItem("isLoggedIn") !== "true") {
        // لو مش مسجل، ابعته فوراً لصفحة تسجيل الدخول
        window.location.href = "login.html";
    }
</script>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profzon</title>
    <style>
        /* تعريف الألوان الخاصة بـ Profzon */
        :root {
            --dark-bg: #0d1117;
            --card-bg: #161b22;
            --tech-blue: #36a9b6;
            --tech-green: #00ff88;
            --text-white: #ffffff;
            --text-gray: #8b949e;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--dark-bg);
            color: var(--text-white);
            margin: 0;
            padding: 0;
        }

        /* الهيدر (Header) */
        header {
            background: linear-gradient(90deg, #000, #161b22);
            padding: 20px 10%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--tech-blue);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo-area {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo-text {
            font-size: 28px;
            font-weight: bold;
            letter-spacing: 1px;
        }

        .logo-text span {
            color: var(--tech-green);
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 25px;
            margin: 0;
        }

        nav a {
            text-decoration: none;
            color: var(--text-white);
            font-weight: 500;
            transition: 0.3s;
        }

        nav a:hover {
            color: var(--tech-green);
        }

        /* قسم الواجهة (Hero Section) */
        .hero {
            padding: 80px 10%;
            text-align: center;
            background: radial-gradient(circle at center, #161b22 0%, #0d1117 100%);
        }

        .hero h1 {
            font-size: 45px;
            margin-bottom: 10px;
        }

        .hero p {
            color: var(--text-gray);
            font-size: 18px;
            max-width: 600px;
            margin: 0 auto 30px;
        }

        .btn-main {
            background-color: var(--tech-green);
            color: #000;
            padding: 12px 30px;
            border: none;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }

        .btn-main:hover {
            box-shadow: 0 0 20px var(--tech-green);
        }

        /* شبكة المقالات (Articles Grid) */
        .container {
            padding: 50px 10%;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 10px;
            overflow: hidden;
            border: 1px solid #30363d;
            transition: 0.3s;
        }

        .card:hover {
            transform: translateY(-10px);
            border-color: var(--tech-blue);
        }

        .card-img {
            width: 100%;
            height: 200px;
            background-color: #30363d; /* مكان الصورة */
            display: flex;
            align-items: center;
            justify-content: center;
            font-style: italic;
            color: var(--text-gray);
        }

        .card-content {
            padding: 20px;
        }

        .card-tag {
            color: var(--tech-blue);
            font-size: 12px;
            font-weight: bold;
            text-transform: uppercase;
        }

        .card-title {
            margin: 10px 0;
            font-size: 20px;
        }

        .card-desc {
            color: var(--text-gray);
            font-size: 14px;
            line-height: 1.6;
        }

        /* التذييل (Footer) */
        footer {
            text-align: center;
            padding: 40px;
            background-color: #000;
            border-top: 1px solid #30363d;
            margin-top: 50px;
        }
        .search-container {
    display: flex;
    align-items: center;
    background: rgba(255, 255, 255, 0.05); /* خلفية شفافة جداً */
    border: 1px solid rgba(0, 255, 136, 0.2); /* إطار أخضر خفيف جداً */
    border-radius: 50px; /* زوايا دائرية تماماً */
    padding: 5px 15px;
    transition: all 0.3s ease;
    backdrop-filter: blur(5px); /* تأثير تغبيش الخلفية */
}

.search-container:focus-within {
    border-color: #00ff88; /* ينور بالأخضر عند الضغط عليه */
    box-shadow: 0 0 15px rgba(0, 255, 136, 0.3); /* توهج (Glow) */
    background: rgba(255, 255, 255, 0.1);
}

.search-container input {
    background: transparent;
    border: none;
    color: white;
    padding: 10px;
    outline: none;
    font-size: 14px;
    width: 250px; /* عرض مناسب */
}

.search-btn {
    background: #00ff88;
    border: none;
    border-radius: 50%;
    width: 35px;
    height: 35px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: 0.3s;
}

.search-btn i {
    color: #0b0e14; /* لون الأيقونة أسود عشان تظهر فوق الأخضر */
    font-size: 14px;
}

.search-btn:hover {
    transform: scale(1.1); /* تكبير بسيط عند الوقوف عليه */
    box-shadow: 0 0 10px #00ff88;
}
/* 1. تعريف حركة الأنيميشن */
@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(30px); /* بيبدأ من تحت بـ 30 بكسل */
    }
    to {
        opacity: 1;
        transform: translateY(0); /* بيوصل لمكانه الطبيعي */
    }
}

/* 2. تطبيق الحركة على العناصر */
.hero h1, .hero p, .btn-main, .logo-wrapper, .card {
    animation: fadeInUp 1.5s ease-out forwards;
    opacity: 0; /* عشان يفضل مخفي لحد ما الأنيميشن يبدأ */
}

/* 3. إضافة تأخير (Delay) عشان العناصر تظهر ورا بعض بالترتيب */
.hero h1 { animation-delay: 0.2s; }
.hero p  { animation-delay: 0.6s; }
.btn-main { animation-delay: 1s; }
/* عنوان القسم */
.section-title {
    text-align: center;
    color: #fff;
    margin: 50px 0 30px;
    font-size: 2rem;
    text-shadow: 0 0 10px rgba(0, 212, 255, 0.5);
}

/* شبكة المقالات */
.posts-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 25px;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

/* كارت المقال */
.post-card {
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 15px;
    overflow: hidden;
    transition: 0.3s;
}

.post-card:hover {
    transform: translateY(-5px);
    border-color: #00d4ff;
    background: rgba(255, 255, 255, 0.05);
}

/* صورة المقال */
.post-image {
    height: 200px;
    background-size: cover;
    background-position: center;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

/* محتوى الكارت */
.post-content {
    padding: 20px;
}

.category-tag {
    color: #00d4ff;
    font-size: 0.8rem;
    text-transform: uppercase;
    font-weight: bold;
}

.post-content h3 {
    margin: 10px 0;
    color: #fff;
    font-size: 1.3rem;
}

.post-content p {
    color: #ccc;
    font-size: 0.9rem;
    line-height: 1.6;
}

.read-more {
    display: inline-block;
    margin-top: 15px;
    color: #00d4ff;
    text-decoration: none;
    font-weight: bold;
}
/* تنسيق شريط التنقل الأساسي */
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem 2rem;
    background-color: transparent; /* ليكون فوق الخلفية السوداء */
    position: relative;
    z-index: 1000;
}

/* جعل الثلاث شرطات ظاهرة دائماً */
.menu-toggle {
    display: block; /* أصبحت ظاهرة دائماً */
    cursor: pointer;
    z-index: 1100;
}

.bar {
    display: block;
    width: 30px;
    height: 3px;
    margin: 6px auto;
    background-color: #00ff88; /* اللون الأخضر النيون */
    transition: 0.4s;
}

/* تنسيق القائمة المخفية (التي ستظهر عند الضغط) */
.nav-links {
    position: fixed;
    top: 0;
    right: -100%; /* مخفية تماماً جهة اليمين */
    width: 300px; /* عرض القائمة الجانبية */
    height: 100vh;
    background-color: rgba(11, 14, 20, 0.95); /* لون داكن شفاف قليلاً */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    list-style: none;
    transition: 0.5s ease; /* سرعة الانزلاق */
    z-index: 1050;
}

/* عندما تصبح القائمة نشطة */
.nav-links.active {
    right: 0;
}

.nav-links li {
    margin: 20px 0;
}

.nav-links li a {
    color: white;
    text-decoration: none;
    font-size: 1.5rem;
    transition: 0.3s;
}

.nav-links li a:hover {
    color: #00ff88;
}

/* حركة اختيارية: تحويل الشرطات لعلامة X عند الفتح */
.is-active .bar:nth-child(2) { opacity: 0; }
.is-active .bar:nth-child(1) { transform: translateY(9px) rotate(45deg); }
.is-active .bar:nth-child(3) { transform: translateY(-9px) rotate(-45deg); }
.navbar {
    display: flex;
    align-items: center;
    justify-content: space-between; /* ده هيخلي البحث يمين والشرطات شمال */
    padding: 10px 20px;
    direction: rtl; /* عشان الترتيب يبدأ من اليمين */
}

.search-container {
    flex-grow: 1; /* اختياري: لو عايز البحث ياخد مساحة أكبر */
    max-width: 400px; /* حدد عرض شريط البحث عشان مياكلش الصفحة */
}

.menu-toggle {
    cursor: pointer;
    margin-right: 20px; /* مسافة بسيطة بينه وبين البحث */
}

/* تأكد أن القائمة المخفية واخده position: fixed أو absolute عشان متبوظش التصميم لما تفتح */
.nav-links {
    display: none; /* أو التنسيق اللي عملناه قبل كده للقائمة الجانبية */
}
.nav-links.active {
    right: 0 !important;
    display: flex !important;
    visibility: visible !important;
    opacity: 1 !important;
}
input::placeholder {
    color: rgba(255, 255, 255, 0.5);
    font-style: italic;
}
.search-box {
    position: relative;
    height: 45px;
    width: 45px; /* العرض في البداية صغير (شكل دائرة) */
    transition: all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    display: flex;
    align-items: center;
}

/* عندما نضع الماوس أو نضغط على الصندوق يتمدد العرض */
.search-box:hover, .search-box:focus-within {
    width: 300px;
}

.search-input {
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.1);
    border: 1px solid rgba(0, 255, 136, 0.3);
    border-radius: 50px;
    padding: 0 15px;
    color: white;
    outline: none;
    opacity: 0; /* مخفي في البداية */
    transition: all 0.5s;
}

.search-box:hover .search-input, .search-box:focus-within .search-input {
    opacity: 1; /* يظهر عند التمدد */
}

.search-button {
    position: absolute;
    right: 0;
    width: 45px;
    height: 45px;
    background: #00ff88;
    border-radius: 50%;
    border: none;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: all 0.5s;
}

.search-box:hover .search-button, .search-box:focus-within .search-button {
    background: #00ff88;
    box-shadow: 0 0 10px #00ff88;
}
.search-input {
    direction: rtl;
    padding-right: 60px !important; /* مساحة كافية عشان العدسة واخدة مكان على اليمين */
    padding-left: 15px;
}
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
</head>
<body>

   <header>
    <div style="display: flex; align-items: center; gap: 0px;">
        <img src="logo.png" alt="Logo" style="width: 150px; height: auto;">
        <h1 style="color: rgb(41, 146, 178); margin: 0;">ZON</h1>
        <h1 style="color: rgb(97, 225, 136); margin: 0;">PROF</h1>
    </div>

    <nav class="navbar">
        <div class="search-box">
    <input type="text" class="search-input" placeholder="ابحث عن تكنولوجيا المستقبل...">
    <button class="search-button">
        <i class="fas fa-search"></i>
    </button>
</div>

        <div class="menu-toggle" id="mobile-menu">
            <span class="bar"></span>
            <span class="bar"></span>
            <span class="bar"></span>
        </div>

        <ul class="nav-links">
            <li><a href="explore.html">مسارات تكنولوجيا</a></li>
            <li><a href="contact us.html">اتصل بنا</a></li>
            <li><a href="#" onclick="logout()">تسجيل الخروج</a>

<script>
function logout() {
    // مسح البيانات المخزنة في المتصفح
    localStorage.clear(); 
    sessionStorage.clear();
    // التوجه لصفحة البداية أو تسجيل الدخول
    window.location.href = "login.html"; 
}
</script></li>
            
            
        </ul>
    </nav>
</header>
<script>
    // التأكد هل المستخدم مسجل دخول ولا لأ
    if (localStorage.getItem("isLoggedIn") !== "true") {
        // لو مش مسجل، ابعته فوراً لصفحة تسجيل الدخول
        window.location.href = "login.html";
    }
</script>
    <section class="hero">
    <h1>مرحباً بك في منطقة الاحتراف</h1>
    <p>بوابتك لاستكشاف أحدث التقنيات بلمسة خبير. نحن لا ننقل الخبر، بل نحلله.</p>
    
    <a href="explore.html" style="text-decoration: none;">
        <button class="btn-main">استكشف</button>
    </a>
</section>
<section class="latest-posts">
    <h2 class="section-title">آخر التحليلات التقنية</h2>
    
    <div class="posts-grid">
        <div class="post-card">
            <div class="post-image" style="background-image: url('pict.jpg');"></div>
            <div class="post-content">
                <span class="category-tag">ذكاء اصطناعي</span>
                <h3>كيف سيغير GPT-5 مفهوم البرمجة؟</h3>
                <p>تحليل عميق للقدرات المتوقعة للنموذج القادم وتأثيره على سوق العمل...</p>
               
            <a href="asi.html" href="#" class="read-more">اقرأ المزيد ←</a>
            </div>
        </div>

        <div class="post-card">
            <div class="post-image" style="background-image: url('images.jpg');"></div>
            <div class="post-content">
                <span class="category-tag">أمن سيبراني</span>
                <h3>أخطر ثغرات عام 2026 وكيف تتجنبها</h3>
                <p>دليلك الشامل لحماية بياناتك من هجمات الفدية المتطورة باستخدام AI...</p>
                <a href="#" class="read-more">اقرأ المزيد ←</a>
            </div>
        </div>

        <div class="post-card">
            <div class="post-image" style="background-image: url('\xr.jpg');"></div>
            <div class="post-content">
                <span class="category-tag">الواقع الممتد</span>
                <h3>مراجعة نظارة Apple Vision Pro 2</h3>
                <p>هل استطاعت أبل حل مشاكل الوزن والبطارية في الجيل الثاني؟</p>
                <a href="#" class="read-more">اقرأ المزيد ←</a>
            </div>
        </div>
    </div>
</section>


    <footer>
        <p>&copy; 2026 جميع الحقوق محفوظة لمدونة <strong>Profzon</strong></p>
    </footer>
    <script>
    const menu = document.getElementById('mobile-menu'); // استعمل دي أضمن
    const menuLinks = document.querySelector('.nav-links');

    menu.addEventListener('click', function() {
        menuLinks.classList.toggle('active');
        menu.classList.toggle('is-active');
    });
</script>
</body>
</html>
