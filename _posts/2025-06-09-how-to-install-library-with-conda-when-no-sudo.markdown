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
    <title>Intelligent Machines - Interactive Page</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: #000;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
        }
        
        .interactive-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
        
        .interactive-canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }
        
        .content {
            text-align: center;
            max-width: 800px;
            padding: 20px;
            z-index: 10;
        }
        
        .main-title {
            font-size: 5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            letter-spacing: -1px;
            text-transform: uppercase;
            position: relative;
            transition: all 0.4s ease;
        }
        
        .main-title:hover {
            transform: scale(1.05);
            text-shadow: 0 0 15px rgba(138, 43, 226, 0.7), 0 0 30px rgba(75, 0, 130, 0.5);
            cursor: default;
        }
        
        .subtitle {
            font-size: 1.6rem;
            font-weight: 300;
            text-transform: uppercase;
            letter-spacing: 4px;
            color: #aaa;
            margin-bottom: 3rem;
            transition: all 0.4s ease;
            position: relative;
        }
        
        .subtitle:hover {
            color: #fff;
            letter-spacing: 5px;
        }
        
        .description {
            font-size: 1.2rem;
            line-height: 1.8;
            color: #bbb;
            margin-bottom: 3rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            transition: all 0.3s ease;
            padding: 15px;
            border-radius: 8px;
        }
        
        .description:hover {
            background: rgba(75, 0, 130, 0.1);
            box-shadow: 0 0 20px rgba(75, 0, 130, 0.3);
            transform: translateY(-3px);
        }
        
        .location-year {
            font-size: 1.1rem;
            color: #888;
            margin-bottom: 2rem;
            letter-spacing: 1px;
        }
        
        .button-container {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 40px;
        }
        
        .interactive-btn {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            background: rgba(138, 43, 226, 0.1);
            border: 1px solid rgba(138, 43, 226, 0.4);
            color: #8a2be2;
            font-size: 1.5rem;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .interactive-btn:hover {
            transform: scale(1.15);
            background: rgba(138, 43, 226, 0.2);
            box-shadow: 0 0 15px rgba(138, 43, 226, 0.6), 
                        0 0 30px rgba(75, 0, 130, 0.3);
            color: #fff;
        }
        
        .interactive-btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 300%;
            height: 300%;
            background: radial-gradient(circle, rgba(138,43,226,0.4) 0%, transparent 70%);
            transform: translate(-50%, -50%) scale(0);
            transition: transform 0.5s ease;
            border-radius: 50%;
            z-index: -1;
        }
        
        .interactive-btn:hover::before {
            transform: translate(-50%, -50%) scale(1);
        }
        
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 5;
        }
        
        .particle {
            position: absolute;
            width: 2px;
            height: 2px;
            background: rgba(138, 43, 226, 0.7);
            border-radius: 50%;
            box-shadow: 0 0 5px #8a2be2, 0 0 10px #8a2be2;
            animation: glow 2s infinite alternate;
        }
        
        .particle:nth-child(2n) {
            background: rgba(75, 0, 130, 0.7);
            box-shadow: 0 0 5px #4b0082, 0 0 10px #4b0082;
            animation-delay: 1s;
        }
        
        .cursor-follower {
            position: fixed;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(138, 43, 226, 0.6) 0%, transparent 70%);
            box-shadow: 0 0 30px 10px rgba(138, 43, 226, 0.4);
            pointer-events: none;
            transform: translate(-50%, -50%);
            z-index: 100;
            transition: transform 0.1s ease, width 0.3s ease, height 0.3s ease;
        }
        
        @keyframes glow {
            0% { opacity: 0.3; transform: scale(0.9); }
            100% { opacity: 1; transform: scale(1.1); }
        }
        
        .ripple {
            position: absolute;
            border-radius: 50%;
            background: rgba(138, 43, 226, 0.4);
            box-shadow: 0 0 30px 10px rgba(138, 43, 226, 0.2);
            animation: rippleEffect 1.5s forwards;
            pointer-events: none;
            transform: translate(-50%, -50%);
        }
        
        @keyframes rippleEffect {
            0% {
                width: 10px;
                height: 10px;
                opacity: 0.7;
            }
            100% {
                width: 600px;
                height: 600px;
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <div class="interactive-background">
        <canvas class="interactive-canvas"></canvas>
        <div class="particles" id="particles"></div>
    </div>
    
    <div class="cursor-follower" id="cursorFollower"></div>
    
    <div class="content">
        <h1 class="main-title">Intelligent Machines</h1>
        <h2 class="subtitle">Automation and AI Research Company</h2>
        <p class="description">We build Automation Systems and Autonomous Digital Twins. Working on AGI research.</p>
        <p class="location-year">New York City 2024</p>
        
        <div class="button-container">
            <div class="interactive-btn">
                <i class="fas fa-play"></i>
            </div>
            <div class="interactive-btn">
                <i class="fas fa-code"></i>
            </div>
        </div>
    </div>
    
    <script>
        // 创建动态背景
        const canvas = document.querySelector('.interactive-canvas');
        const ctx = canvas.getContext('2d');
        
        // 设置canvas大小为窗口大小
        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        
        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);
        
        // 绘制渐变背景
        function drawBackground() {
            const gradient = ctx.createRadialGradient(
                canvas.width * 0.7, canvas.height * 0.3, 0,
                canvas.width * 0.7, canvas.height * 0.3, canvas.width * 1.5
            );
            
            gradient.addColorStop(0, 'rgba(75, 0, 130, 0.2)');
            gradient.addColorStop(0.6, 'rgba(75, 0, 130, 0.08)');
            gradient.addColorStop(1, 'rgba(0, 0, 0, 0)');
            
            ctx.fillStyle = gradient;
            ctx.fillRect(0, 0, canvas.width, canvas.height);
        }
        
        // 创建流动光点
        class GlowParticle {
            constructor() {
                this.reset();
            }
            
            reset() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 3 + 1;
                this.speedX = Math.random() * 0.5 - 0.25;
                this.speedY = Math.random() * 0.5 - 0.25;
                this.hue = Math.random() > 0.5 ? 268 : 259; // 紫色或蓝色调
                this.brightness = Math.random() * 40 + 20; // 20-60%
                this.alpha = Math.random() * 0.4 + 0.1; // 0.1-0.5
            }
            
            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                
                // 如果粒子移出画布，重置
                if (this.x < 0 || this.x > canvas.width || 
                    this.y < 0 || this.y > canvas.height) {
                    this.reset();
                }
            }
            
            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = `hsla(${this.hue}, 80%, ${this.brightness}%, ${this.alpha})`;
                ctx.fill();
            }
        }
        
        // 初始化粒子
        const particles = [];
        const particleCount = 150;
        
        for (let i = 0; i < particleCount; i++) {
            particles.push(new GlowParticle());
        }
        
        // 动画循环
        function animate() {
            // 清除画布（使用半透明覆盖创造拖尾效果）
            ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            
            // 绘制背景
            drawBackground();
            
            // 更新和绘制粒子
            particles.forEach(particle => {
                particle.update();
                particle.draw();
            });
            
            requestAnimationFrame(animate);
        }
        
        animate();
        
        // 创建星星粒子效果
        const particlesContainer = document.getElementById('particles');
        
        for (let i = 0; i < 50; i++) {
            const particle = document.createElement('div');
            particle.classList.add('particle');
            particle.style.left = `${Math.random() * 100}%`;
            particle.style.top = `${Math.random() * 100}%`;
            particle.style.animationDelay = `${Math.random() * 3}s`;
            particlesContainer.appendChild(particle);
        }
        
        // 鼠标跟随效果
        const cursorFollower = document.getElementById('cursorFollower');
        
        document.addEventListener('mousemove', e => {
            cursorFollower.style.left = `${e.clientX}px`;
            cursorFollower.style.top = `${e.pageY}px`;
            
            // 创建涟漪效果
            const ripple = document.createElement('div');
            ripple.classList.add('ripple');
            ripple.style.left = `${e.clientX}px`;
            ripple.style.top = `${e.pageY}px`;
            document.body.appendChild(ripple);
            
            // 自动移除涟漪元素
            setTimeout(() => {
                ripple.remove();
            }, 1500);
        });
        
        // 当鼠标在可交互元素上时放大跟随器
        const interactiveElements = document.querySelectorAll('.main-title, .subtitle, .description, .interactive-btn');
        
        interactiveElements.forEach(el => {
            el.addEventListener('mouseenter', () => {
                cursorFollower.style.width = '50px';
                cursorFollower.style.height = '50px';
                cursorFollower.style.background = 'radial-gradient(circle, rgba(138, 43, 226, 0.8) 0%, transparent 70%)';
            });
            
            el.addEventListener('mouseleave', () => {
                cursorFollower.style.width = '30px';
                cursorFollower.style.height = '30px';
                cursorFollower.style.background = 'radial-gradient(circle, rgba(138, 43, 226, 0.6) 0%, transparent 70%)';
            });
        });
        
        // 按钮互动效果
        const buttons = document.querySelectorAll('.interactive-btn');
        
        buttons.forEach(button => {
            button.addEventListener('click', () => {
                const clone = button.cloneNode(true);
                clone.style.position = 'fixed';
                clone.style.zIndex = '1000';
                clone.style.left = `${button.getBoundingClientRect().left}px`;
                clone.style.top = `${button.getBoundingClientRect().top}px`;
                document.body.appendChild(clone);
                
                // 按钮点击扩散动画
                setTimeout(() => {
                    clone.style.transform = 'scale(2)';
                    clone.style.opacity = '0';
                    clone.style.transition = 'all 0.6s ease';
                }, 50);
                
                setTimeout(() => {
                    clone.remove();
                }, 700);
            });
        });
    </script>
</body>
</html>
