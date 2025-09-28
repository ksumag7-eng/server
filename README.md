<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BookTracker - Ваш персональный книжный трекер</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #4a6fa5;
            --secondary-color: #6e9887;
            --accent-color: #e76f51;
            --light-color: #f8f9fa;
            --dark-color: #343a40;
            --success-color: #28a745;
            --reading-color: #17a2b8;
            --planned-color: #ffc107;
            --dropped-color: #dc3545;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --gradient: linear-gradient(135deg, #4a6fa5 0%, #6e9887 100%);
            --bg-color: #f5f7fa;
            --text-color: #333;
            --card-bg: white;
            --header-bg: linear-gradient(135deg, #4a6fa5 0%, #6e9887 100%);
        }

        /* Темы */
        .theme-white-black {
            --bg-color: #ffffff;
            --text-color: #000000;
            --card-bg: #f8f9fa;
            --header-bg: linear-gradient(135deg, #ffffff 0%, #e9ecef 100%);
            --primary-color: #000000;
            --secondary-color: #495057;
        }

        .theme-white-blue {
            --bg-color: #f0f8ff;
            --text-color: #1a365d;
            --card-bg: #ffffff;
            --header-bg: linear-gradient(135deg, #4a6fa5 0%, #6e9887 100%);
            --primary-color: #2b6cb0;
            --secondary-color: #4299e1;
        }

        .theme-white-pink {
            --bg-color: #fff5f7;
            --text-color: #702459;
            --card-bg: #ffffff;
            --header-bg: linear-gradient(135deg, #ed64a6 0%, #fbb6ce 100%);
            --primary-color: #d53f8c;
            --secondary-color: #f687b3;
        }

        .theme-white-purple {
            --bg-color: #faf5ff;
            --text-color: #44337a;
            --card-bg: #ffffff;
            --header-bg: linear-gradient(135deg, #805ad5 0%, #d6bcfa 100%);
            --primary-color: #6b46c1;
            --secondary-color: #9f7aea;
        }

        .theme-white-gray {
            --bg-color: #f7fafc;
            --text-color: #2d3748;
            --card-bg: #ffffff;
            --header-bg: linear-gradient(135deg, #a0aec0 0%, #e2e8f0 100%);
            --primary-color: #4a5568;
            --secondary-color: #718096;
        }

        .theme-black-green {
            --bg-color: #1a202c;
            --text-color: #c6f6d5;
            --card-bg: #2d3748;
            --header-bg: linear-gradient(135deg, #22543d 0%, #38a169 100%);
            --primary-color: #38a169;
            --secondary-color: #48bb78;
        }

        .theme-black-blue {
            --bg-color: #1a202c;
            --text-color: #bee3f8;
            --card-bg: #2d3748;
            --header-bg: linear-gradient(135deg, #2b6cb0 0%, #3182ce 100%);
            --primary-color: #3182ce;
            --secondary-color: #4299e1;
        }

        .theme-black-pink {
            --bg-color: #1a202c;
            --text-color: #fed7e2;
            --card-bg: #2d3748;
            --header-bg: linear-gradient(135deg, #97266d 0%, #d53f8c 100%);
            --primary-color: #d53f8c;
            --secondary-color: #ed64a6;
        }

        .theme-black-purple {
            --bg-color: #1a202c;
            --text-color: #e9d8fd;
            --card-bg: #2d3748;
            --header-bg: linear-gradient(135deg, #553c9a 0%, #805ad5 100%);
            --primary-color: #805ad5;
            --secondary-color: #9f7aea;
        }

        .theme-black-green-alt {
            --bg-color: #1a202c;
            --text-color: #c6f6d5;
            --card-bg: #2d3748;
            --header-bg: linear-gradient(135deg, #22543d 0%, #38a169 100%);
            --primary-color: #38a169;
            --secondary-color: #48bb78;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: var(--bg-color);
            color: var(--text-color);
            line-height: 1.6;
            min-height: 100vh;
            transition: background 0.3s, color 0.3s;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }
        
        /* Header Styles */
        header {
            background: var(--header-bg);
            color: white;
            padding: 1rem 0;
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 10px;
        }
        
        nav ul {
            display: flex;
            list-style: none;
            gap: 20px;
        }
        
        nav a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            padding: 0.5rem;
            border-radius: 4px;
            transition: background 0.3s;
        }
        
        nav a:hover, nav a.active {
            background: rgba(255, 255, 255, 0.2);
        }
        
        .user-actions {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .btn {
            padding: 0.5rem 1rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s ease;
        }
        
        .btn-primary {
            background-color: var(--secondary-color);
            color: white;
        }
        
        .btn-outline {
            background-color: transparent;
            border: 1px solid white;
            color: white;
        }
        
        .btn:hover {
            opacity: 0.9;
            transform: translateY(-2px);
        }
        
        /* Main content */
        .main-content {
            padding: 2rem 0;
        }
        
        .page {
            display: none;
        }
        
        .page.active {
            display: block;
        }
        
        /* Auth Forms */
        .auth-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .auth-modal.active {
            display: flex;
        }
        
        .auth-container {
            background: var(--card-bg);
            color: var(--text-color);
            padding: 2rem;
            border-radius: 10px;
            box-shadow: var(--shadow);
            width: 100%;
            max-width: 400px;
            position: relative;
        }
        
        .close-modal {
            position: absolute;
            top: 10px;
            right: 10px;
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-color);
        }
        
        .auth-form h2 {
            text-align: center;
            margin-bottom: 1.5rem;
            color: var(--primary-color);
        }
        
        .form-group {
            margin-bottom: 1rem;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
        }
        
        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
            background: var(--card-bg);
            color: var(--text-color);
        }
        
        .form-switch {
            text-align: center;
            margin-top: 1rem;
        }
        
        .form-switch a {
            color: var(--primary-color);
            text-decoration: none;
            cursor: pointer;
        }
        
        /* Home page */
        .hero {
            background: var(--header-bg);
            color: white;
            padding: 3rem;
            border-radius: 10px;
            margin-bottom: 2rem;
            text-align: center;
        }
        
        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }
        
        .hero p {
            font-size: 1.2rem;
            max-width: 600px;
            margin: 0 auto;
        }
        
        .current-time {
            margin-top: 1rem;
            font-size: 1rem;
            opacity: 0.9;
        }
        
        .home-search {
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: var(--shadow);
            margin-bottom: 2rem;
        }
        
        .search-bar {
            display: flex;
        }
        
        .search-bar input {
            flex: 1;
            padding: 0.75rem;
            border: 1px solid #ddd;
            border-radius: 4px 0 0 4px;
            font-size: 1rem;
            background: var(--card-bg);
            color: var(--text-color);
        }
        
        .search-bar button {
            padding: 0 1.5rem;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 0 4px 4px 0;
            cursor: pointer;
        }
        
        .section-title {
            margin: 2rem 0 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 2px solid var(--primary-color);
            color: var(--primary-color);
        }
        
        .books-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 2rem;
        }
        
        .book-card {
            background: var(--card-bg);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: transform 0.3s;
            cursor: pointer;
        }
        
        .book-card:hover {
            transform: translateY(-5px);
        }
        
        .book-cover {
            height: 250px;
            background: #ddd;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: #777;
        }
        
        .book-info {
            padding: 1rem;
        }
        
        .book-title {
            font-weight: bold;
            margin-bottom: 0.5rem;
        }
        
        .book-author {
            color: #666;
            font-style: italic;
            margin-bottom: 0.5rem;
        }
        
        .book-meta {
            display: flex;
            justify-content: space-between;
            color: #777;
            font-size: 0.9rem;
        }
        
        .add-to-library {
            width: 100%;
            margin-top: 0.5rem;
            padding: 0.5rem;
            background: var(--primary-color);
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        
        /* Library page */
        .library-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .search-filters {
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: var(--shadow);
            margin-bottom: 2rem;
        }
        
        .filters {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .filters select {
            padding: 0.5rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            min-width: 150px;
            background: var(--card-bg);
            color: var(--text-color);
        }
        
        .category-tabs {
            display: flex;
            gap: 5px;
            margin-bottom: 1rem;
            overflow-x: auto;
        }
        
        .category-tab {
            padding: 0.5rem 1rem;
            background-color: #e9ecef;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            white-space: nowrap;
        }
        
        .category-tab.active {
            background-color: var(--primary-color);
            color: white;
        }
        
        .book-details {
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: var(--shadow);
            margin-bottom: 2rem;
        }
        
        .book-status {
            font-size: 0.8rem;
            font-weight: 500;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            color: white;
            display: inline-block;
            margin-bottom: 1rem;
        }
        
        .status-read {
            background-color: var(--success-color);
        }
        
        .status-reading {
            background-color: var(--reading-color);
        }
        
        .status-planned {
            background-color: var(--planned-color);
        }
        
        .status-dropped {
            background-color: var(--dropped-color);
        }
        
        .rating {
            display: flex;
            gap: 5px;
            margin: 0.5rem 0;
        }
        
        .rating span {
            cursor: pointer;
            font-size: 1.5rem;
            color: #ddd;
        }
        
        .rating span.active {
            color: gold;
        }
        
        .tag-input {
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
            margin: 0.5rem 0;
            padding: 0.5rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            min-height: 42px;
        }
        
        .tag-item {
            background-color: var(--secondary-color);
            color: white;
            padding: 0.25rem 0.5rem;
            border-radius: 20px;
            font-size: 0.8rem;
            display: flex;
            align-items: center;
        }
        
        .tag-item span {
            margin-left: 5px;
            cursor: pointer;
        }
        
        /* Account page */
        .account-header {
            display: flex;
            align-items: center;
            gap: 20px;
            margin-bottom: 2rem;
        }
        
        .user-avatar {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background: var(--header-bg);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5rem;
            color: white;
        }
        
        .user-info h2 {
            margin-bottom: 0.5rem;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 2rem;
        }
        
        .stat-card {
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: var(--shadow);
            text-align: center;
        }
        
        .stat-value {
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary-color);
            margin: 0.5rem 0;
        }
        
        .stat-label {
            color: #666;
        }
        
        .chart-container {
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: var(--shadow);
            margin-bottom: 2rem;
        }
        
        .chart-placeholder {
            height: 300px;
            background: var(--bg-color);
            display: flex;
            align-items: center;
            justify-content: center;
            color: #666;
            border-radius: 4px;
        }
        
        .library-restricted {
            text-align: center;
            padding: 3rem;
            background: var(--card-bg);
            border-radius: 8px;
            box-shadow: var(--shadow);
        }
        
        /* Theme selector */
        .theme-selector {
            margin-top: 2rem;
        }
        
        .theme-options {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 15px;
            margin-top: 1rem;
        }
        
        .theme-option {
            padding: 1rem;
            border-radius: 8px;
            cursor: pointer;
            text-align: center;
            border: 2px solid transparent;
            transition: all 0.3s;
        }
        
        .theme-option:hover {
            transform: translateY(-3px);
        }
        
        .theme-option.active {
            border-color: var(--primary-color);
        }
        
        .theme-preview {
            width: 100%;
            height: 60px;
            border-radius: 4px;
            margin-bottom: 0.5rem;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 10px;
            }
            
            nav ul {
                gap: 10px;
            }
            
            .hero {
                padding: 2rem 1rem;
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .books-grid {
                grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            }
            
            .filters {
                flex-direction: column;
            }
            
            .filters select {
                width: 100%;
            }
            
            .account-header {
                flex-direction: column;
                text-align: center;
            }
            
            .theme-options {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body class="theme-white-blue">
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <i class="fas fa-book"></i> BookTracker
                </div>
                
                <nav>
                    <ul>
                        <li><a href="#" class="nav-link active" data-page="home">Главная</a></li>
                        <li><a href="#" class="nav-link" data-page="library">Моя библиотека</a></li>
                        <li><a href="#" class="nav-link" data-page="account">Аккаунт</a></li>
                    </ul>
                </nav>
                
                <div class="user-actions">
                    <div id="user-welcome" class="user-welcome" style="display: none;">
                        <span>Привет, <span id="username-display"></span>!</span>
                        <button id="logout-btn" class="btn logout-btn">Выйти</button>
                    </div>
                    <div id="auth-buttons">
                        <button id="login-btn" class="btn btn-outline">Войти</button>
                        <button id="register-btn" class="btn btn-primary">Регистрация</button>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <div class="container">
        <div class="main-content">
            <!-- Главная страница -->
            <div id="home-page" class="page active">
                <div class="hero">
                    <h1>Отслеживайте свои книги</h1>
                    <p>Добавляйте книги, ставьте оценки, пишите рецензии и следите за своим прогрессом чтения</p>
                    <div class="current-time" id="current-time"></div>
                </div>
                
                <div class="home-search">
                    <div class="search-bar">
                        <input type="text" id="home-search-input" placeholder="Поиск книг по названию, автору или жанру...">
                        <button id="home-search-btn"><i class="fas fa-search"></i></button>
                    </div>
                </div>
                
                <h2 class="section-title">Новинки месяца</h2>
                <div class="books-grid" id="new-books">
                    <!-- Книги будут загружены через JavaScript -->
                </div>
                
                <h2 class="section-title">Основано на ваших предпочтениях</h2>
                <div class="books-grid" id="recommended-books">
                    <!-- Книги будут загружены через JavaScript -->
                </div>
            </div>
            
            <!-- Страница библиотеки -->
            <div id="library-page" class="page">
                <div class="library-header">
                    <h2>Моя библиотека</h2>
                    <button id="add-book-btn" class="btn btn-primary">Добавить книгу</button>
                </div>
                
                <div id="library-content">
                    <!-- Контент библиотеки будет загружен через JavaScript -->
                </div>
            </div>
            
            <!-- Страница аккаунта -->
            <div id="account-page" class="page">
                <div id="account-content">
                    <!-- Контент аккаунта будет загружен через JavaScript -->
                </div>
            </div>
        </div>
    </div>

    <!-- Модальное окно авторизации -->
    <div id="auth-modal" class="auth-modal">
        <div class="auth-container">
            <button class="close-modal">&times;</button>
            
            <div id="login-form" class="auth-form">
                <h2>Вход в систему</h2>
                <div class="form-group">
                    <label for="login-email">Email</label>
                    <input type="email" id="login-email" placeholder="Введите ваш email">
                </div>
                <div class="form-group">
                    <label for="login-password">Пароль</label>
                    <input type="password" id="login-password" placeholder="Введите ваш пароль">
                </div>
                <button id="login-submit" class="btn btn-primary" style="width: 100%;">Войти</button>
                <div class="form-switch">
                    Нет аккаунта? <a id="switch-to-register">Зарегистрироваться</a>
                </div>
            </div>
            
            <div id="register-form" class="auth-form" style="display: none;">
                <h2>Регистрация</h2>
                <div class="form-group">
                    <label for="register-name">Имя</label>
                    <input type="text" id="register-name" placeholder="Введите ваше имя">
                </div>
                <div class="form-group">
                    <label for="register-email">Email</label>
                    <input type="email" id="register-email" placeholder="Введите ваш email">
                </div>
                <div class="form-group">
                    <label for="register-password">Пароль</label>
                    <input type="password" id="register-password" placeholder="Придумайте пароль">
                </div>
                <button id="register-submit" class="btn btn-primary" style="width: 100%;">Зарегистрироваться</button>
                <div class="form-switch">
                    Уже есть аккаунт? <a id="switch-to-login">Войти</a>
                </div>
            </div>
        </div>
    </div>

    <!-- Модальное окно добавления книги -->
    <div id="add-book-modal" class="auth-modal">
        <div class="auth-container">
            <button class="close-modal">&times;</button>
            <div class="auth-form">
                <h2>Добавить книгу</h2>
                <div class="form-group">
                    <input type="text" id="book-title" placeholder="Название книги*" required>
                </div>
                
                <div class="form-group">
                    <input type="text" id="book-author" placeholder="Автор*" required>
                </div>
                
                <div class="form-group">
                    <select id="book-genre">
                        <option value="">Выберите жанр</option>
                        <option value="Фантастика">Фантастика</option>
                        <option value="Детектив">Детектив</option>
                        <option value="Роман">Роман</option>
                        <option value="Фэнтези">Фэнтези</option>
                        <option value="Биография">Биография</option>
                        <option value="Исторический">Исторический</option>
                        <option value="Научная литература">Научная литература</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <select id="book-status" required>
                        <option value="">Выберите статус</option>
                        <option value="read">Прочитано</option>
                        <option value="reading">Читаю</option>
                        <option value="planned">В планах</option>
                        <option value="dropped">Брошено</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label>Рейтинг</label>
                    <div class="rating" id="book-rating">
                        <span data-value="1">☆</span>
                        <span data-value="2">☆</span>
                        <span data-value="3">☆</span>
                        <span data-value="4">☆</span>
                        <span data-value="5">☆</span>
                    </div>
                    <input type="hidden" id="rating-value" value="0">
                </div>
                
                <div class="form-group">
                    <label>Теги (через запятую)</label>
                    <input type="text" id="book-tags" placeholder="Например: классика, русская литература">
                </div>
                
                <div class="form-group">
                    <textarea id="book-review" placeholder="Рецензия..."></textarea>
                </div>
                
                <button id="add-book-submit" class="btn btn-primary" style="width: 100%;">Добавить книгу</button>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Элементы DOM
            const authModal = document.getElementById('auth-modal');
            const addBookModal = document.getElementById('add-book-modal');
            const userWelcome = document.getElementById('user-welcome');
            const usernameDisplay = document.getElementById('username-display');
            const authButtons = document.getElementById('auth-buttons');
            const loginBtn = document.getElementById('login-btn');
            const registerBtn = document.getElementById('register-btn');
            const logoutBtn = document.getElementById('logout-btn');
            const switchToRegister = document.getElementById('switch-to-register');
            const switchToLogin = document.getElementById('switch-to-login');
            const loginSubmit = document.getElementById('login-submit');
            const registerSubmit = document.getElementById('register-submit');
            const closeModalButtons = document.querySelectorAll('.close-modal');
            const addBookBtn = document.getElementById('add-book-btn');
            const addBookSubmit = document.getElementById('add-book-submit');
            const navLinks = document.querySelectorAll('.nav-link');
            const pages = document.querySelectorAll('.page');
            const homeSearchInput = document.getElementById('home-search-input');
            const homeSearchBtn = document.getElementById('home-search-btn');
            const currentTimeElement = document.getElementById('current-time');
            
            // Переменные состояния
            let currentUser = null;
            let currentRating = 0;
            let allUsers = JSON.parse(localStorage.getItem('users')) || [];
            let allBooks = JSON.parse(localStorage.getItem('books')) || [];
            let sampleBooks = []; // Примеры книг для главной страницы
            let currentTheme = localStorage.getItem('currentTheme') || 'theme-white-blue';
            
            // Применяем сохраненную тему
            document.body.className = currentTheme;
            
            // Инициализация примера книг
            function initSampleBooks() {
                sampleBooks = [
                    {
                        id: 1001,
                        title: "Мастер и Маргарита",
                        author: "Михаил Булгаков",
                        genre: "Роман",
                        year: 1967,
                        rating: 4.8
                    },
                    {
                        id: 1002,
                        title: "1984",
                        author: "Джордж Оруэлл",
                        genre: "Антиутопия",
                        year: 1949,
                        rating: 4.7
                    },
                    {
                        id: 1003,
                        title: "Преступление и наказание",
                        author: "Федор Достоевский",
                        genre: "Роман",
                        year: 1866,
                        rating: 4.6
                    },
                    {
                        id: 1004,
                        title: "Три товарища",
                        author: "Эрих Мария Ремарк",
                        genre: "Роман",
                        year: 1936,
                        rating: 4.5
                    },
                    {
                        id: 1005,
                        title: "Сто лет одиночества",
                        author: "Габриэль Гарсиа Маркес",
                        genre: "Роман",
                        year: 1967,
                        rating: 4.7
                    },
                    {
                        id: 1006,
                        title: "Унесенные ветром",
                        author: "Маргарет Митчелл",
                        genre: "Роман",
                        year: 1936,
                        rating: 4.4
                    },
                    {
                        id: 1007,
                        title: "Анна Каренина",
                        author: "Лев Толстой",
                        genre: "Роман",
                        year: 1877,
                        rating: 4.7
                    },
                    {
                        id: 1008,
                        title: "Маленький принц",
                        author: "Антуан де Сент-Экзюпери",
                        genre: "Повесть",
                        year: 1943,
                        rating: 4.8
                    }
                ];
            }
            
            // Обновление текущего времени
            function updateCurrentTime() {
                const now = new Date();
                const options = { 
                    weekday: 'long', 
                    year: 'numeric', 
                    month: 'long', 
                    day: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit',
                    second: '2-digit'
                };
                currentTimeElement.textContent = now.toLocaleDateString('ru-RU', options);
            }
            
            // Проверка авторизации при загрузке
            const savedUser = localStorage.getItem('currentUser');
            if (savedUser) {
                currentUser = JSON.parse(savedUser);
                showApp();
            } else {
                showAuthButtons();
            }
            
            // Инициализация примера книг и времени
            initSampleBooks();
            updateCurrentTime();
            setInterval(updateCurrentTime, 1000);
            
            // Навигация по страницам
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    const pageId = this.getAttribute('data-page') + '-page';
                    
                    // Обновляем активную ссылку
                    navLinks.forEach(nav => nav.classList.remove('active'));
                    this.classList.add('active');
                    
                    // Показываем соответствующую страницу
                    pages.forEach(page => page.classList.remove('active'));
                    document.getElementById(pageId).classList.add('active');
                    
                    // Загружаем контент для страницы
                    loadPageContent(pageId);
                });
            });
            
            // Загрузка контента для страницы
            function loadPageContent(pageId) {
                switch(pageId) {
                    case 'home-page':
                        loadHomePage();
                        break;
                    case 'library-page':
                        loadLibraryPage();
                        break;
                    case 'account-page':
                        loadAccountPage();
                        break;
                }
            }
            
            // Загрузка главной страницы
            function loadHomePage() {
                // Отображаем новинки месяца
                const newBooksContainer = document.getElementById('new-books');
                newBooksContainer.innerHTML = '';
                
                sampleBooks.slice(0, 4).forEach(book => {
                    const bookCard = createBookCard(book, true);
                    newBooksContainer.appendChild(bookCard);
                });
                
                // Отображаем рекомендации
                const recommendedContainer = document.getElementById('recommended-books');
                recommendedContainer.innerHTML = '';
                
                sampleBooks.slice(4).forEach(book => {
                    const bookCard = createBookCard(book, true);
                    recommendedContainer.appendChild(bookCard);
                });
            }
            
            // Создание карточки книги
            function createBookCard(book, showAddButton = false) {
                const bookCard = document.createElement('div');
                bookCard.className = 'book-card';
                bookCard.innerHTML = `
                    <div class="book-cover">
                        <i class="fas fa-book"></i>
                    </div>
                    <div class="book-info">
                        <div class="book-title">${book.title}</div>
                        <div class="book-author">${book.author}</div>
                        <div class="book-meta">
                            <span>${book.genre}</span>
                            <span>${book.rating}★</span>
                        </div>
                        ${showAddButton ? `<button class="add-to-library" data-book-id="${book.id}">Добавить в библиотеку</button>` : ''}
                    </div>
                `;
                
                // Добавляем обработчик для кнопки добавления в библиотеку
                if (showAddButton) {
                    const addButton = bookCard.querySelector('.add-to-library');
                    addButton.addEventListener('click', function() {
                        if (!currentUser) {
                            authModal.classList.add('active');
                            return;
                        }
                        
                        // Добавляем книгу в библиотеку пользователя
                        const userBook = {
                            id: Date.now(),
                            userId: currentUser.id,
                            title: book.title,
                            author: book.author,
                            genre: book.genre,
                            status: 'planned',
                            rating: 0,
                            tags: [],
                            review: '',
                            dateAdded: new Date().toISOString()
                        };
                        
                        allBooks.push(userBook);
                        localStorage.setItem('books', JSON.stringify(allBooks));
                        
                        alert(`Книга "${book.title}" добавлена в вашу библиотеку!`);
                    });
                }
                
                return bookCard;
            }
            
            // Загрузка страницы библиотеки
            function loadLibraryPage() {
                const libraryContent = document.getElementById('library-content');
                
                if (!currentUser) {
                    libraryContent.innerHTML = `
                        <div class="library-restricted">
                            <h3>Доступ к библиотеке ограничен</h3>
                            <p>Для доступа к вашей библиотеке необходимо войти в систему</p>
                            <button id="library-login-btn" class="btn btn-primary" style="margin-top: 1rem;">Войти</button>
                        </div>
                    `;
                    
                    document.getElementById('library-login-btn').addEventListener('click', () => {
                        authModal.classList.add('active');
                    });
                    
                    return;
                }
                
                libraryContent.innerHTML = `
                    <div class="search-filters">
                        <div class="search-bar">
                            <input type="text" id="library-search-input" placeholder="Поиск по названию, автору, жанру или тегам...">
                            <button id="library-search-btn"><i class="fas fa-search"></i></button>
                        </div>
                        
                        <div class="filters">
                            <select id="genre-filter">
                                <option value="">Все жанры</option>
                                <option value="Фантастика">Фантастика</option>
                                <option value="Детектив">Детектив</option>
                                <option value="Роман">Роман</option>
                                <option value="Фэнтези">Фэнтези</option>
                                <option value="Биография">Биография</option>
                                <option value="Исторический">Исторический</option>
                                <option value="Научная литература">Научная литература</option>
                            </select>
                            
                            <select id="status-filter">
                                <option value="">Все статусы</option>
                                <option value="read">Прочитано</option>
                                <option value="reading">Читаю</option>
                                <option value="planned">В планах</option>
                                <option value="dropped">Брошено</option>
                            </select>
                            
                            <select id="rating-filter">
                                <option value="0">Любой рейтинг</option>
                                <option value="5">5 звезд</option>
                                <option value="4">4+ звезды</option>
                                <option value="3">3+ звезды</option>
                                <option value="2">2+ звезды</option>
                                <option value="1">1+ звезда</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="category-tabs">
                        <button class="category-tab active" data-category="all">Все книги</button>
                        <button class="category-tab" data-category="read">Прочитано</button>
                        <button class="category-tab" data-category="reading">Читаю сейчас</button>
                        <button class="category-tab" data-category="planned">В планах</button>
                        <button class="category-tab" data-category="dropped">Брошено</button>
                    </div>
                    
                    <div class="books-grid" id="user-books">
                        <!-- Книги пользователя будут загружены здесь -->
                    </div>
                `;
                
                // Инициализация функционала библиотеки
                initLibraryFunctionality();
                renderUserBooks();
            }
            
            // Инициализация функционала библиотеки
            function initLibraryFunctionality() {
                // Поиск в библиотеке
                const librarySearchInput = document.getElementById('library-search-input');
                const librarySearchBtn = document.getElementById('library-search-btn');
                
                librarySearchBtn.addEventListener('click', filterBooks);
                librarySearchInput.addEventListener('input', filterBooks);
                
                // Фильтры
                document.getElementById('genre-filter').addEventListener('change', filterBooks);
                document.getElementById('status-filter').addEventListener('change', filterBooks);
                document.getElementById('rating-filter').addEventListener('change', filterBooks);
                
                // Вкладки категорий
                document.querySelectorAll('.category-tab').forEach(tab => {
                    tab.addEventListener('click', function() {
                        document.querySelectorAll('.category-tab').forEach(t => t.classList.remove('active'));
                        this.classList.add('active');
                        filterBooks();
                    });
                });
            }
            
            // Фильтрация книг в библиотеке
            function filterBooks() {
                const searchTerm = document.getElementById('library-search-input').value.toLowerCase();
                const genre = document.getElementById('genre-filter').value;
                const status = document.getElementById('status-filter').value;
                const rating = parseInt(document.getElementById('rating-filter').value);
                const activeCategory = document.querySelector('.category-tab.active').dataset.category;
                
                const userBooks = allBooks.filter(book => book.userId === currentUser.id);
                
                let filteredBooks = userBooks.filter(book => {
                    const matchesSearch = book.title.toLowerCase().includes(searchTerm) || 
                                         book.author.toLowerCase().includes(searchTerm) || 
                                         book.genre.toLowerCase().includes(searchTerm) ||
                                         book.tags.some(tag => tag.toLowerCase().includes(searchTerm));
                    const matchesGenre = genre === '' || book.genre === genre;
                    const matchesStatus = status === '' || book.status === status;
                    const matchesRating = rating === 0 || book.rating >= rating;
                    const matchesCategory = activeCategory === 'all' || book.status === activeCategory;
                    
                    return matchesSearch && matchesGenre && matchesStatus && matchesRating && matchesCategory;
                });
                
                renderUserBooks(filteredBooks);
            }
            
            // Отрисовка книг пользователя
            function renderUserBooks(booksToRender = null) {
                const userBooks = allBooks.filter(book => book.userId === currentUser.id);
                const booksArray = booksToRender || userBooks;
                const booksContainer = document.getElementById('user-books');
                
                if (booksArray.length === 0) {
                    booksContainer.innerHTML = `
                        <div class="empty-state" style="grid-column: 1 / -1;">
                            <h3>Ваша библиотека пуста</h3>
                            <p>Добавьте первую книгу, нажав на кнопку "Добавить книгу"</p>
                        </div>
                    `;
                    return;
                }
                
                booksContainer.innerHTML = '';
                
                booksArray.forEach(book => {
                    const statusText = {
                        'read': 'Прочитано',
                        'reading': 'Читаю',
                        'planned': 'В планах',
                        'dropped': 'Брошено'
                    };
                    
                    const statusClass = {
                        'read': 'status-read',
                        'reading': 'status-reading',
                        'planned': 'status-planned',
                        'dropped': 'status-dropped'
                    };
                    
                    const bookCard = document.createElement('div');
                    bookCard.className = 'book-card';
                    bookCard.innerHTML = `
                        <div class="book-cover">
                            <i class="fas fa-book"></i>
                        </div>
                        <div class="book-info">
                            <div class="book-title">${book.title}</div>
                            <div class="book-author">${book.author}</div>
                            <div class="book-meta">
                                <span>${book.genre || 'Не указан'}</span>
                                <span>${book.rating > 0 ? '★'.repeat(book.rating) : 'Без оценки'}</span>
                            </div>
                            <div class="book-status ${statusClass[book.status]}">${statusText[book.status]}</div>
                        </div>
                    `;
                    
                    booksContainer.appendChild(bookCard);
                });
            }
            
            // Загрузка страницы аккаунта
            function loadAccountPage() {
                const accountContent = document.getElementById('account-content');
                
                if (!currentUser) {
                    accountContent.innerHTML = `
                        <div class="library-restricted">
                            <h3>Доступ к аккаунту ограничен</h3>
                            <p>Для просмотра статистики необходимо войти в систему</p>
                            <button id="account-login-btn" class="btn btn-primary" style="margin-top: 1rem;">Войти</button>
                        </div>
                    `;
                    
                    document.getElementById('account-login-btn').addEventListener('click', () => {
                        authModal.classList.add('active');
                    });
                    
                    return;
                }
                
                accountContent.innerHTML = `
                    <div class="account-header">
                        <div class="user-avatar">
                            <i class="fas fa-user"></i>
                        </div>
                        <div class="user-info">
                            <h2 id="account-username">${currentUser.name}</h2>
                            <p>Участник с <span id="join-date">${new Date(currentUser.joinDate).toLocaleDateString('ru-RU')}</span></p>
                        </div>
                    </div>
                    
                    <h2 class="section-title">Статистика чтения</h2>
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-label">Всего прочитано</div>
                            <div class="stat-value" id="total-books">0</div>
                            <div class="stat-desc">книг</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-label">За эту неделю</div>
                            <div class="stat-value" id="weekly-books">0</div>
                            <div class="stat-desc">книг</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-label">В этом месяце</div>
                            <div class="stat-value" id="monthly-books">0</div>
                            <div class="stat-desc">книг</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-label">В этом году</div>
                            <div class="stat-value" id="yearly-books">0</div>
                            <div class="stat-desc">книг</div>
                        </div>
                    </div>
                    
                    <div class="chart-container">
                        <h3>Прогресс чтения</h3>
                        <div class="chart-placeholder">
                            График чтения по месяцам
                        </div>
                    </div>
                    
                    <div class="chart-container">
                        <h3>Любимые жанры</h3>
                        <div class="chart-placeholder">
                            Круговая диаграмма жанров
                        </div>
                    </div>
                    
                    <div class="theme-selector">
                        <h2 class="section-title">Выбор темы оформления</h2>
                        <div class="theme-options">
                            <div class="theme-option ${currentTheme === 'theme-white-black' ? 'active' : ''}" data-theme="theme-white-black">
                                <div class="theme-preview" style="background: linear-gradient(135deg, #ffffff 0%, #e9ecef 100%);"></div>
                                <span>Бело-черная</span>
                            </div>
                            <div class="theme-option ${currentTheme === 'theme-white-blue' ? 'active' : ''}" data-theme="theme-white-blue">
                                <div class="theme-preview" style="background: linear-gradient(135deg, #4a6fa5 0%, #6e9887 100%);"></div>
                                <span>Бело-синяя</span>
                            </div>
                            <div class="theme-option ${currentTheme === 'theme-white-pink' ? 'active' : ''}" data-theme="theme-white-pink">
                                <div class="theme-preview" style="background: linear-gradient(135deg, #ed64a6 0%, #fbb6ce 100%);"></div>
                                <span>Бело-розовая</span>
                            </div>
                            <div class="theme-option ${currentTheme === 'theme-white-purple' ? 'active' : ''}" data-theme="theme-white-purple">
                                <div class="theme-preview" style="background: linear-gradient(135deg, #805ad5 0%, #d6bcfa 100%);"></div>
                                <span>Бело-фиолетовая</span>
                            </div>
                            <div class="theme-option ${currentTheme === 'theme-white-gray' ? 'active' : ''}" data-theme="theme-white-gray">
                                <div class="theme-preview" style="background: linear-gradient(135deg, #a0aec0 0%, #e2e8f0 100%);"></div>
                                <span>Бело-серая</span>
                            </div>
                            <div class="theme-option ${currentTheme === 'theme-black-green' ? 'active' : ''}" data-theme="theme-black-green">
                                <div class="theme-preview" style="background: linear-gradient(135deg, #22543d 0%, #38a169 100%);"></div>
                                <span>Черно-зеленая</span>
                            </div>
                            <div class="theme-option ${currentTheme === 'theme-black-blue' ? 'active' : ''}" data-theme="theme-black-blue">
                                <div class="theme-preview" style="background: linear-gradient(135deg, #2b6cb0 0%, #3182ce 100%);"></div>
                                <span>Черно-синяя</span>
                            </div>
                            <div class="theme-option ${currentTheme === 'theme-black-pink' ? 'active' : ''}" data-theme="theme-black-pink">
                                <div class="theme-preview" style="background: linear-gradient(135deg, #97266d 0%, #d53f8c 100%);"></div>
                                <span>Черно-розовая</span>
                            </div>
                            <div class="theme-option ${currentTheme === 'theme-black-purple' ? 'active' : ''}" data-theme="theme-black-purple">
                                <div class="theme-preview" style="background: linear-gradient(135deg, #553c9a 0%, #805ad5 100%);"></div>
                                <span>Черно-фиолетовая</span>
                            </div>
                            <div class="theme-option ${currentTheme === 'theme-black-green-alt' ? 'active' : ''}" data-theme="theme-black-green-alt">
                                <div class="theme-preview" style="background: linear-gradient(135deg, #22543d 0%, #38a169 100%);"></div>
                                <span>Черно-зеленая (альт.)</span>
                            </div>
                        </div>
                    </div>
                `;
                
                // Добавляем обработчики для выбора темы
                document.querySelectorAll('.theme-option').forEach(option => {
                    option.addEventListener('click', function() {
                        const theme = this.getAttribute('data-theme');
                        changeTheme(theme);
                    });
                });
                
                updateAccountStats();
            }
            
            // Смена темы
            function changeTheme(theme) {
                document.body.className = theme;
                currentTheme = theme;
                localStorage.setItem('currentTheme', theme);
                
                // Обновляем активную тему в интерфейсе
                document.querySelectorAll('.theme-option').forEach(option => {
                    option.classList.remove('active');
                    if (option.getAttribute('data-theme') === theme) {
                        option.classList.add('active');
                    }
                });
            }
            
            // Обновление статистики аккаунта
            function updateAccountStats() {
                if (!currentUser) return;
                
                const userBooks = allBooks.filter(book => book.userId === currentUser.id);
                const readBooks = userBooks.filter(book => book.status === 'read');
                
                // Подсчет статистики по периодам
                const now = new Date();
                const weekAgo = new Date(now.getTime() - 7 * 24 * 60 * 60 * 1000);
                const monthAgo = new Date(now.getFullYear(), now.getMonth() - 1, now.getDate());
                const yearAgo = new Date(now.getFullYear() - 1, now.getMonth(), now.getDate());
                
                const weeklyBooks = readBooks.filter(book => {
                    const bookDate = new Date(book.dateAdded);
                    return bookDate >= weekAgo;
                }).length;
                
                const monthlyBooks = readBooks.filter(book => {
                    const bookDate = new Date(book.dateAdded);
                    return bookDate >= monthAgo;
                }).length;
                
                const yearlyBooks = readBooks.filter(book => {
                    const bookDate = new Date(book.dateAdded);
                    return bookDate >= yearAgo;
                }).length;
                
                // Обновляем счетчики
                document.getElementById('total-books').textContent = readBooks.length;
                document.getElementById('weekly-books').textContent = weeklyBooks;
                document.getElementById('monthly-books').textContent = monthlyBooks;
                document.getElementById('yearly-books').textContent = yearlyBooks;
            }
            
            // Поиск на главной странице
            homeSearchBtn.addEventListener('click', performHomeSearch);
            homeSearchInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    performHomeSearch();
                }
            });
            
            function performHomeSearch() {
                const searchTerm = homeSearchInput.value.toLowerCase();
                if (!searchTerm) return;
                
                const searchResults = sampleBooks.filter(book => 
                    book.title.toLowerCase().includes(searchTerm) || 
                    book.author.toLowerCase().includes(searchTerm) ||
                    book.genre.toLowerCase().includes(searchTerm)
                );
                
                // Показываем результаты поиска
                const newBooksContainer = document.getElementById('new-books');
                const recommendedContainer = document.getElementById('recommended-books');
                
                newBooksContainer.innerHTML = '';
                recommendedContainer.innerHTML = '';
                
                if (searchResults.length === 0) {
                    newBooksContainer.innerHTML = '<p>По вашему запросу ничего не найдено</p>';
                    return;
                }
                
                searchResults.forEach(book => {
                    const bookCard = createBookCard(book, true);
                    newBooksContainer.appendChild(bookCard);
                });
                
                document.querySelector('.section-title').textContent = 'Результаты поиска';
                recommendedContainer.style.display = 'none';
            }
            
            // Обработчики аутентификации
            loginBtn.addEventListener('click', () => {
                authModal.classList.add('active');
                document.getElementById('login-form').style.display = 'block';
                document.getElementById('register-form').style.display = 'none';
            });
            
            registerBtn.addEventListener('click', () => {
                authModal.classList.add('active');
                document.getElementById('login-form').style.display = 'none';
                document.getElementById('register-form').style.display = 'block';
            });
            
            switchToRegister.addEventListener('click', () => {
                document.getElementById('login-form').style.display = 'none';
                document.getElementById('register-form').style.display = 'block';
            });
            
            switchToLogin.addEventListener('click', () => {
                document.getElementById('login-form').style.display = 'block';
                document.getElementById('register-form').style.display = 'none';
            });
            
            loginSubmit.addEventListener('click', (e) => {
                e.preventDefault();
                const email = document.getElementById('login-email').value;
                const password = document.getElementById('login-password').value;
                
                if (!email || !password) {
                    alert('Пожалуйста, заполните все поля');
                    return;
                }
                
                const user = allUsers.find(u => u.email === email && u.password === password);
                if (user) {
                    currentUser = user;
                    localStorage.setItem('currentUser', JSON.stringify(user));
                    showApp();
                    authModal.classList.remove('active');
                    
                    // Перезагружаем текущую страницу
                    loadPageContent(document.querySelector('.page.active').id);
                } else {
                    alert('Неверный email или пароль');
                }
            });
            
            registerSubmit.addEventListener('click', (e) => {
                e.preventDefault();
                const name = document.getElementById('register-name').value;
                const email = document.getElementById('register-email').value;
                const password = document.getElementById('register-password').value;
                
                if (!name || !email || !password) {
                    alert('Пожалуйста, заполните все поля');
                    return;
                }
                
                if (allUsers.some(u => u.email === email)) {
                    alert('Пользователь с таким email уже существует');
                    return;
                }
                
                const newUser = {
                    id: Date.now(),
                    name,
                    email,
                    password,
                    joinDate: new Date().toISOString()
                };
                
                allUsers.push(newUser);
                localStorage.setItem('users', JSON.stringify(allUsers));
                
                currentUser = newUser;
                localStorage.setItem('currentUser', JSON.stringify(newUser));
                
                showApp();
                authModal.classList.remove('active');
                
                alert('Регистрация прошла успешно!');
                
                // Перезагружаем текущую страницу
                loadPageContent(document.querySelector('.page.active').id);
            });
            
            logoutBtn.addEventListener('click', () => {
                localStorage.removeItem('currentUser');
                currentUser = null;
                showAuthButtons();
                
                // Перезагружаем текущую страницу
                loadPageContent(document.querySelector('.page.active').id);
            });
            
            // Добавление книги
            addBookBtn.addEventListener('click', () => {
                if (!currentUser) {
                    authModal.classList.add('active');
                    return;
                }
                
                addBookModal.classList.add('active');
            });
            
            addBookSubmit.addEventListener('click', (e) => {
                e.preventDefault();
                
                if (!currentUser) {
                    alert('Пожалуйста, войдите в систему');
                    return;
                }
                
                const title = document.getElementById('book-title').value;
                const author = document.getElementById('book-author').value;
                const genre = document.getElementById('book-genre').value;
                const status = document.getElementById('book-status').value;
                const rating = parseInt(document.getElementById('rating-value').value);
                const tags = document.getElementById('book-tags').value.split(',').map(tag => tag.trim()).filter(tag => tag);
                const review = document.getElementById('book-review').value;
                
                if (!title || !author || !status) {
                    alert('Пожалуйста, заполните обязательные поля');
                    return;
                }
                
                const newBook = {
                    id: Date.now(),
                    userId: currentUser.id,
                    title,
                    author,
                    genre,
                    status,
                    rating,
                    tags,
                    review,
                    dateAdded: new Date().toISOString()
                };
                
                allBooks.push(newBook);
                localStorage.setItem('books', JSON.stringify(allBooks));
                
                // Обновляем библиотеку
                if (document.getElementById('library-page').classList.contains('active')) {
                    renderUserBooks();
                }
                
                addBookModal.classList.remove('active');
                
                // Сброс формы
                document.getElementById('book-title').value = '';
                document.getElementById('book-author').value = '';
                document.getElementById('book-genre').value = '';
                document.getElementById('book-status').value = '';
                document.getElementById('book-tags').value = '';
                document.getElementById('book-review').value = '';
                document.querySelectorAll('#book-rating span').forEach(star => {
                    star.textContent = '☆';
                    star.classList.remove('active');
                });
                document.getElementById('rating-value').value = 0;
            });
            
            // Установка рейтинга
            document.querySelectorAll('#book-rating span').forEach(star => {
                star.addEventListener('click', function() {
                    const value = parseInt(this.getAttribute('data-value'));
                    currentRating = value;
                    document.getElementById('rating-value').value = value;
                    
                    document.querySelectorAll('#book-rating span').forEach((s, i) => {
                        if (i < value) {
                            s.textContent = '★';
                            s.classList.add('active');
                        } else {
                            s.textContent = '☆';
                            s.classList.remove('active');
                        }
                    });
                });
            });
            
            // Закрытие модальных окон
            closeModalButtons.forEach(btn => {
                btn.addEventListener('click', () => {
                    authModal.classList.remove('active');
                    addBookModal.classList.remove('active');
                });
            });
            
            // Вспомогательные функции
            function showApp() {
                authButtons.style.display = 'none';
                userWelcome.style.display = 'flex';
                usernameDisplay.textContent = currentUser.name;
            }
            
            function showAuthButtons() {
                authButtons.style.display = 'flex';
                userWelcome.style.display = 'none';
            }
            
            // Инициализация главной страницы
            loadHomePage();
        });
    </script>
</body>
</html>
