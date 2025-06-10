---
layout:     post
title:      "how to install library with conda when no sudo and work on jupyter notebook"
date:       2025-06-09 12:00:00
author:     "yang"
header-img: "img/post-bg-miui6.jpg"
tags:
    - conda
    - library
    - sudo
---

> 这篇文章主要讨论没有权限，通过生成环境在如何添加到jupyter


<div>
    <blockquote>
    
      
# 1设置myparm环境ParmEd
conda create -n myparm python=3.10
# 2激活myparm环境
conda activate myparm
# 3在myparm环境中安装ipykernel为了可以在jupyternotebook中实现选中myparm环境
pip install ipykernel
# 或者
conda install ipykernel
# 3在myparm环境中安装ParmEd实现引用ParmEd
python setup.py install
    <br>
    
</div>


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Intelligent Machines</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-purple: #7b1fa2;
            --secondary-purple: #9c27b0;
            --accent-blue: #2962ff;
            --dark-text: #333;
            --medium-text: #555;
            --light-text: #777;
            --white: #ffffff;
            --light-bg: #f9f9f9;
            --border-color: rgba(123, 31, 162, 0.1);
            --card-shadow: 0 8px 30px rgba(123, 31, 162, 0.1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: var(--white);
            font-family: 'Montserrat', sans-serif;
            color: var(--dark-text);
            line-height: 1.6;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }
        
        .main-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 20;
        }
        
        /* 粒子背景 */
        .particle-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
        }
        
        .particle {
            position: absolute;
            width: 2px;
            height: 2px;
            background: var(--primary-purple);
            border-radius: 50%;
            box-shadow: 0 0 3px var(--primary-purple);
            animation: float 15s infinite linear;
            opacity: 0.4;
        }
        
        .particle.blue {
            background: var(--accent-blue);
            box-shadow: 0 0 3px var(--accent-blue);
        }
        
        .cursor-follower {
            position: fixed;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(123, 31, 162, 0.2) 0%, transparent 70%);
            box-shadow: 0 0 15px rgba(123, 31, 162, 0.1);
            pointer-events: none;
            transform: translate(-50%, -50%);
            z-index: 50;
            transition: transform 0.1s ease, width 0.2s ease, height 0.2s ease;
        }
        
        .ripple {
            position: absolute;
            border-radius: 50%;
            background: rgba(123, 31, 162, 0.1);
            box-shadow: 0 0 15px rgba(123, 31, 162, 0.1);
            animation: rippleEffect 1.2s forwards;
            pointer-events: none;
            transform: translate(-50%, -50%);
            z-index: 5;
        }
        
        /* 头部导航 */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 25px 0;
            position: relative;
            z-index: 30;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary-purple);
            display: flex;
            align-items: center;
        }
        
        .logo-icon {
            width: 36px;
            height: 36px;
            background: var(--primary-purple);
            border-radius: 50%;
            margin-right: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .logo-icon i {
            color: white;
            font-size: 18px;
        }
        
        .nav-links {
            display: flex;
            gap: 35px;
        }
        
        .nav-links a {
            color: var(--medium-text);
            text-decoration: none;
            font-weight: 500;
            font-size: 1rem;
            transition: color 0.3s ease;
            position: relative;
        }
        
        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary-purple);
            transition: width 0.3s ease;
        }
        
        .nav-links a:hover {
            color: var(--primary-purple);
        }
        
        .nav-links a:hover::after {
            width: 100%;
        }
        
        /* 英雄区域 */
        .hero {
            min-height: 85vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
            padding: 20px;
            text-align: center;
            max-width: 800px;
            margin: 0 auto;
            z-index: 20;
        }
        
        .main-title {
            font-size: clamp(3rem, 9vw, 5.5rem);
            font-weight: 700;
            margin-bottom: 1rem;
            letter-spacing: -1px;
            color: var(--dark-text);
            position: relative;
            transition: all 0.4s ease;
        }
        
        .main-title:hover {
            transform: scale(1.02);
            text-shadow: 0 0 15px rgba(123, 31, 162, 0.1);
            cursor: default;
        }
        
        .subtitle {
            font-size: clamp(1.1rem, 2.3vw, 1.5rem);
            font-weight: 400;
            text-transform: uppercase;
            letter-spacing: 3px;
            color: var(--medium-text);
            margin-bottom: 1.5rem;
            transition: all 0.4s ease;
            position: relative;
        }
        
        .subtitle:hover {
            color: var(--primary-purple);
            letter-spacing: 4px;
        }
        
        .description {
            font-size: clamp(1rem, 1.5vw, 1.2rem);
            line-height: 1.8;
            color: var(--medium-text);
            margin-bottom: 2rem;
            max-width: 700px;
            transition: all 0.3s ease;
            padding: 15px;
            border-radius: 8px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .divider {
            width: 80px;
            height: 2px;
            background: linear-gradient(to right, transparent, var(--primary-purple), transparent);
            margin: 1rem auto;
        }
        
        .location-year {
            font-size: clamp(0.9rem, 1.5vw, 1.1rem);
            color: var(--light-text);
            margin-top: 1.5rem;
            letter-spacing: 1px;
            font-weight: 400;
        }
        
        .button-container {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin-top: 35px;
        }
        
        .interactive-btn {
            width: clamp(55px, 6vw, 65px);
            height: clamp(55px, 6vw, 65px);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            background: var(--white);
            border: 1px solid rgba(123, 31, 162, 0.2);
            color: var(--primary-purple);
            font-size: clamp(1.2rem, 2vw, 1.6rem);
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            box-shadow: var(--card-shadow);
        }
        
        .interactive-btn:hover {
            transform: translateY(-5px);
            background: var(--white);
            box-shadow: 0 10px 25px rgba(123, 31, 162, 0.15);
            border-color: rgba(123, 31, 162, 0.4);
        }
        
        /* 服务部分 */
        .content-section {
            padding: 100px 0;
        }
        
        .section-title {
            font-size: clamp(2rem, 4vw, 2.8rem);
            text-align: center;
            margin-bottom: 15px;
            color: var(--dark-text);
            position: relative;
        }
        
        .section-subtitle {
            font-size: clamp(0.9rem, 1.5vw, 1.1rem);
            color: var(--light-text);
            text-align: center;
            max-width: 600px;
            margin: 0 auto 40px;
            font-weight: 400;
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 50px;
        }
        
        .feature-card {
            background: var(--white);
            border-radius: 15px;
            padding: 35px 30px;
            transition: all 0.4s ease;
            border: 1px solid var(--border-color);
            box-shadow: var(--card-shadow);
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 35px rgba(123, 31, 162, 0.1);
            border: 1px solid rgba(123, 31, 162, 0.2);
        }
        
        .feature-card h3 {
            font-size: 1.4rem;
            margin: 20px 0 15px;
            color: var(--primary-purple);
        }
        
        .feature-card p {
            color: var(--medium-text);
            line-height: 1.6;
            font-size: 1rem;
        }
        
        .feature-icon {
            width: 65px;
            height: 65px;
            background: rgba(123, 31, 162, 0.05);
            border-radius: 50%;
            font-size: 1.8rem;
            color: var(--primary-purple);
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }
        
        .feature-card:hover .feature-icon {
            transform: scale(1.1);
            background: rgba(123, 31, 162, 0.1);
        }
        
        .research-section {
            background: var(--light-bg);
            padding: 80px 0;
            border-radius: 25px;
            margin-bottom: 80px;
            position: relative;
            overflow: hidden;
        }
        
        .timeline-container {
            max-width: 700px;
            margin: 0 auto;
            position: relative;
            padding: 30px 0;
        }
        
        .timeline-container::before {
            content: '';
            position: absolute;
            left: 50%;
            top: 0;
            height: 100%;
            width: 2px;
            background: rgba(123, 31, 162, 0.1);
            transform: translateX(-50%);
        }
        
        .timeline-item {
            position: relative;
            margin-bottom: 50px;
        }
        
        .timeline-content {
            padding: 20px;
            background: var(--white);
            border-radius: 15px;
            border: 1px solid var(--border-color);
            width: calc(50% - 40px);
            position: relative;
            box-shadow: var(--card-shadow);
        }
        
        .timeline-item:nth-child(odd) .timeline-content {
            margin-left: auto;
            margin-right: 0;
        }
        
        .timeline-year {
            position: absolute;
            top: 15px;
            background: var(--primary-purple);
            color: white;
            padding: 8px 20px;
            border-radius: 30px;
            font-weight: 600;
            z-index: 1;
        }
        
        .timeline-item:nth-child(odd) .timeline-year {
            left: calc(50% - 30px);
            transform: translateX(-100%);
        }
        
        .timeline-item:nth-child(even) .timeline-year {
            right: calc(50% - 30px);
            transform: translateX(100%);
        }
        
        .contact-section {
            position: relative;
            padding: 80px 0;
        }
        
        .contact-card {
            background: var(--white);
            max-width: 700px;
            margin: 0 auto;
            padding: 50px;
            border-radius: 25px;
            box-shadow: var(--card-shadow);
            border: 1px solid var(--border-color);
            position: relative;
            overflow: hidden;
        }
        
        .contact-info {
            display: flex;
            gap: 20px;
            margin: 30px 0;
            flex-wrap: wrap;
        }
        
        .info-item {
            flex: 1;
            min-width: 200px;
            padding: 20px;
            border-radius: 15px;
            background: rgba(123, 31, 162, 0.05);
            border: 1px solid var(--border-color);
            transition: all 0.3s ease;
        }
        
        .info-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(123, 31, 162, 0.1);
        }
        
        .info-item i {
            font-size: 1.8rem;
            color: var(--primary-purple);
            margin-bottom: 15px;
        }
        
        .info-item h4 {
            margin-bottom: 10px;
            color: var(--dark-text);
        }
        
        .footer {
            text-align: center;
            padding: 40px 0;
            color: var(--light-text);
            font-size: 0.9rem;
            border-top: 1px solid rgba(123, 31, 162, 0.05);
            margin-top: 20px;
            position: relative;
        }
        
        /* 动画关键帧 */
        @keyframes rippleEffect {
            0% {
                width: 5px;
                height: 5px;
                opacity: 0.6;
            }
            100% {
                width: 200px;
                height: 200px;
                opacity: 0;
            }
        }
        
        @keyframes float {
            0%, 100% {
                transform: translate(0, 0);
            }
            25% {
                transform: translate(3px, 3px);
            }
            50% {
                transform: translate(5px, -5px);
            }
            75% {
                transform: translate(-3px, 3px);
            }
        }
        
        /* 响应式调整 */
        @media (max-width: 768px) {
            .header {
                flex-direction: column;
                gap: 20px;
                text-align: center;
            }
            
            .logo {
                justify-content: center;
            }
            
            .nav-links {
                gap: 15px;
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .hero {
                min-height: 70vh;
            }
            
            .timeline-container::before {
                left: 30px;
            }
            
            .timeline-content {
                width: calc(100% - 80px);
                margin-left: 80px;
            }
            
            .timeline-year {
                left: 0 !important;
                transform: none !important;
                right: auto;
            }
        }
        
        @media (max-width: 480px) {
            .main-title {
                font-size: 2.8rem;
            }
            
            .subtitle {
                font-size: 1.2rem;
                letter-spacing: 2px;
            }
            
            .features-grid {
                grid-template-columns: 1fr;
            }
            
            .info-item {
                min-width: 100%;
            }
            
            .contact-card {
                padding: 25px;
            }
        }
    </style>
</head>
<body>
    <!-- 粒子背景 -->
    <div class="particle-bg" id="particleBg"></div>
    
    <!-- 光标跟随元素 -->
    <div class="cursor-follower" id="cursorFollower"></div>
    
    <div class="main-container">
        <!-- 头部导航 -->
        <header class="header">
            <div class="logo">
                <div class="logo-icon">
                    <i class="fas fa-microchip"></i>
                </div>
                <span>INTELLIMACHINE</span>
            </div>
            <nav class="nav-links">
                <a href="#home">Home</a>
                <a href="#services">Services</a>
                <a href="#research">Research</a>
                <a href="#timeline">Timeline</a>
                <a href="#contact">Contact</a>
            </nav>
        </header>
        
        <!-- 主交互区域 -->
        <section id="home" class="hero">
            <h1 class="main-title">Intelligent Machines</h1>
            <h2 class="subtitle">Automation and AI Research Company</h2>
            
            <div class="divider"></div>
            
            <p class="description">
                We build Automation Systems and Autonomous Digital Twins. 
                Working on AGI research to create the next generation of intelligent systems.
            </p>
            
            <p class="location-year">New York City • 2024</p>
            
            <div class="button-container">
                <div class="interactive-btn">
                    <i class="fas fa-play"></i>
                </div>
                <div class="interactive-btn">
                    <i class="fas fa-code"></i>
                </div>
            </div>
        </section>
        
        <!-- 服务部分 -->
        <section id="services" class="content-section">
            <h2 class="section-title">Our Services</h2>
            <p class="section-subtitle">Innovative solutions for the future of automation and artificial intelligence</p>
            
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-robot"></i>
                    </div>
                    <h3>Industrial Automation</h3>
                    <p>Creating intelligent systems that optimize manufacturing processes, reduce costs, and improve efficiency through advanced robotics and AI algorithms.</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-brain"></i>
                    </div>
                    <h3>AI Solutions</h3>
                    <p>Developing tailored artificial intelligence applications for data analysis, predictive maintenance, and intelligent decision-making across industries.</p>
                </div>
                
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-cube"></i>
                    </div>
                    <h3>Digital Twins</h3>
                    <p>Building virtual replicas of physical systems that simulate, predict, and optimize performance throughout the asset lifecycle.</p>
                </div>
            </div>
        </section>
        
        <!-- 研究部分 -->
        <section id="research" class="research-section">
            <div class="main-container">
                <h2 class="section-title">Our Research</h2>
                <p class="section-subtitle">Pioneering work in artificial general intelligence and autonomous systems</p>
                
                <div class="features-grid">
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-atom"></i>
                        </div>
                        <h3>AGI Research</h3>
                        <p>Pioneering work in Artificial General Intelligence with focus on learning algorithms, cognitive architectures, and ethical frameworks.</p>
                    </div>
                    
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-network-wired"></i>
                        </div>
                        <h3>Neural Systems</h3>
                        <p>Advanced neural network development for complex problem solving, pattern recognition, and adaptive learning systems.</p>
                    </div>
                    
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-users-cog"></i>
                        </div>
                        <h3>Human-Machine Synergy</h3>
                        <p>Exploring seamless integration of human intelligence and artificial systems for amplified capabilities and intuitive interactions.</p>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- 时间线部分 -->
        <section id="timeline" class="content-section">
            <h2 class="section-title">Company Timeline</h2>
            <p class="section-subtitle">Key milestones in our development journey</p>
            
            <div class="timeline-container">
                <div class="timeline-item">
                    <div class="timeline-content">
                        <h3>Foundation Year</h3>
                        <p>Founded in New York with a mission to create innovative automation solutions and advance AGI research.</p>
                    </div>
                    <div class="timeline-year">2020</div>
                </div>
                
                <div class="timeline-item">
                    <div class="timeline-content">
                        <h3>Industrial Automation Launch</h3>
                        <p>Successfully launched our first industrial automation system for manufacturing clients, reducing costs by 30%.</p>
                    </div>
                    <div class="timeline-year">2021</div>
                </div>
                
                <div class="timeline-item">
                    <div class="timeline-content">
                        <h3>Digital Twins Platform</h3>
                        <p>Developed our proprietary Digital Twins platform for complex system simulation and optimization.</p>
                    </div>
                    <div class="timeline-year">2022</div>
                </div>
                
                <div class="timeline-item">
                    <div class="timeline-content">
                        <h3>AGI Research Center</h3>
                        <p>Opened our dedicated AGI Research Center in New York with 25 researchers working on foundational models.</p>
                    </div>
                    <div class="timeline-year">2023</div>
                </div>
            </div>
        </section>
        
        <!-- 联系方式 -->
        <section id="contact" class="contact-section">
            <div class="contact-card">
                <h2 class="section-title">Contact Us</h2>
                <p class="section-subtitle">Reach out to our team of experts to discuss how we can collaborate</p>
                
                <div class="contact-info">
                    <div class="info-item">
                        <i class="fas fa-map-marker-alt"></i>
                        <h4>Location</h4>
                        <p>Innovation District, New York City</p>
                    </div>
                    
                    <div class="info-item">
                        <i class="fas fa-envelope"></i>
                        <h4>Email</h4>
                        <p>contact@intellimachine.com</p>
                    </div>
                    
                    <div class="info-item">
                        <i class="fas fa-phone"></i>
                        <h4>Phone</h4>
                        <p>+1 (212) 555-7890</p>
                    </div>
                </div>
                
                <div class="button-container">
                    <div class="interactive-btn" style="border-radius: 50px; width: auto; padding: 0 30px;">
                        <i class="fas fa-paper-plane" style="margin-right: 10px;"></i> Send Message
                    </div>
                </div>
            </div>
        </section>
        
        <!-- 页脚 -->
        <footer class="footer">
            <p>&copy; 2024 Intelligent Machines. All rights reserved.</p>
            <p>New York City • Boston • San Francisco</p>
        </footer>
    </div>
    
    <script>
        // 创建粒子效果（为白色背景优化）
        function createParticles() {
            const container = document.getElementById('particleBg');
            const particleCount = 100;
            const colors = ['purple', 'blue'];
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.classList.add('particle');
                
                // 随机大小和位置
                const size = Math.random() * 2 + 1;
                const posX = Math.random() * 100;
                const posY = Math.random() * 100;
                
                particle.style.width = `${size}px`;
                particle.style.height = `${size}px`;
                particle.style.left = `${posX}%`;
                particle.style.top = `${posY}%`;
                
                // 随机动画延迟
                particle.style.animationDelay = `${Math.random() * 15}s`;
                
                // 随机选择颜色
                if (Math.random() > 0.7) {
                    particle.classList.add(colors[Math.floor(Math.random() * colors.length)]);
                }
                
                container.appendChild(particle);
            }
        }
        
        // 添加涟漪效果（优化）
        function createRipple(e) {
            // 限制涟漪频率
            if (Math.random() > 0.8) {
                const ripple = document.createElement('div');
                ripple.classList.add('ripple');
                ripple.style.left = `${e.clientX}px`;
                ripple.style.top = `${e.pageY}px`;
                document.body.appendChild(ripple);
                
                // 自动移除涟漪元素
                setTimeout(() => {
                    ripple.remove();
                }, 1200);
            }
        }
        
        // 优化光标跟随效果
        let mouseX = window.innerWidth / 2;
        let mouseY = window.innerHeight / 2;
        
        document.addEventListener('mousemove', e => {
            mouseX = e.clientX;
            mouseY = e.clientY;
            createRipple(e);
        });
        
        // 初始化光标跟随器
        let followerX = mouseX;
        let followerY = mouseY;
        const cursorFollower = document.getElementById('cursorFollower');
        
        function updateCursorFollower() {
            const dx = mouseX - followerX;
            const dy = mouseY - followerY;
            
            // 缓动效果
            followerX += dx * 0.15;
            followerY += dy * 0.15;
            
            cursorFollower.style.left = `${followerX}px`;
            cursorFollower.style.top = `${followerY}px`;
            
            requestAnimationFrame(updateCursorFollower);
        }
        
        // 当鼠标在可交互元素上时改变跟随器效果
        const interactiveElements = document.querySelectorAll('a, .main-title, .subtitle, .description, .interactive-btn, .feature-card, .info-item');
        
        interactiveElements.forEach(el => {
            el.addEventListener('mouseenter', () => {
                cursorFollower.style.width = '40px';
                cursorFollower.style.height = '40px';
                cursorFollower.style.background = 'radial-gradient(circle, rgba(123, 31, 162, 0.3) 0%, transparent 70%)';
                cursorFollower.style.boxShadow = '0 0 20px rgba(123, 31, 162, 0.3)';
            });
            
            el.addEventListener('mouseleave', () => {
                cursorFollower.style.width = '30px';
                cursorFollower.style.height = '30px';
                cursorFollower.style.background = 'radial-gradient(circle, rgba(123, 31, 162, 0.2) 0%, transparent 70%)';
                cursorFollower.style.boxShadow = '0 0 15px rgba(123, 31, 162, 0.1)';
            });
        });
        
        // 平滑滚动导航
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    window.scrollTo({
                        top: target.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });
        
        // 卡片悬停效果增强
        const cards = document.querySelectorAll('.feature-card, .info-item');
        cards.forEach(card => {
            card.addEventListener('mousemove', (e) => {
                const cardRect = card.getBoundingClientRect();
                const x = e.clientX - cardRect.left;
                const y = e.clientY - cardRect.top;
                
                const centerX = cardRect.width / 2;
                const centerY = cardRect.height / 2;
                
                const angleY = (x - centerX) / 25;
                const angleX = (centerY - y) / 25;
                
                card.style.transform = `perspective(1000px) rotateX(${angleX}deg) rotateY(${angleY}deg) scale(1.03)`;
            });
            
            card.addEventListener('mouseleave', () => {
                card.style.transform = '';
            });
        });
        
        // 页面加载时初始化效果
        window.addEventListener('DOMContentLoaded', () => {
            createParticles();
            updateCursorFollower();
        });
    </script>
</body>
</html>
