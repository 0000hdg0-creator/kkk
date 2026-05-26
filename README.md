<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>David | Personal Portfolio</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Urbanist:wght@400;500;600;700&family=Noto+Sans+SC:wght@300;400;500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        /* 全局重置与设计规范 */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            scroll-behavior: smooth;
        }

        :root {
            --bg-main: #020617;        /* 深邃夜空黑 */
            --bg-card: rgba(30, 41, 59, 0.4); /* 半透明卡片背景 */
            --border-color: rgba(255, 255, 255, 0.08);
            --text-primary: #f8fafc;
            --text-secondary: #94a3b8;
            --accent-green: #22c55e;   /* 霓虹绿 */
            --accent-blue: #3b82f6;    /* 科技蓝 */
            --accent-purple: #a855f7;  /* 幻彩紫 */
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-primary);
            font-family: 'Urbanist', 'Noto Sans SC', sans-serif;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* 抽象流体光影背景装饰 */
        .bg-glow {
            position: fixed;
            width: 100vw;
            height: 100vh;
            top: 0;
            left: 0;
            z-index: -1;
            pointer-events: none;
            background: 
                radial-gradient(circle at 15% 20%, rgba(34, 197, 94, 0.1) 0%, transparent 45%),
                radial-gradient(circle at 85% 70%, rgba(59, 130, 246, 0.12) 0%, transparent 50%),
                radial-gradient(circle at 50% 50%, rgba(168, 85, 247, 0.06) 0%, transparent 60%);
        }

        /* 现代悬浮导航栏 */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            background: rgba(2, 6, 23, 0.7);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--border-color);
        }

        .nav-container {
            max-width: 1300px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 40px;
        }

        .logo {
            font-size: 22px;
            font-weight: 700;
            letter-spacing: -0.5px;
            background: linear-gradient(to right, #ffffff, var(--text-secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .logo span {
            color: var(--accent-green);
            -webkit-text-fill-color: var(--accent-green);
        }

        nav {
            display: flex;
            gap: 35px;
        }

        nav a {
            text-decoration: none;
            color: var(--text-secondary);
            font-size: 15px;
            font-weight: 500;
            transition: color 0.3s ease, transform 0.3s ease;
        }

        nav a:hover {
            color: var(--text-primary);
        }

        nav a.active-link {
            color: var(--accent-green);
        }

        /* 统一页面大板块样式 */
        section {
            max-width: 1300px;
            margin: 0 auto;
            padding: 120px 40px 60px 40px;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .section-title {
            font-size: 40px;
            font-weight: 700;
            letter-spacing: -1px;
            margin-bottom: 50px;
            border-left: 5px solid var(--accent-green);
            padding-left: 20px;
        }

        .section-title span {
            color: var(--accent-green);
        }

        /* ==================== 首页/欢迎板块 ==================== */
        .hero-container {
            display: grid;
            grid-template-columns: 1.2fr 0.8fr;
            gap: 60px;
            align-items: center;
            width: 100%;
        }

        .hero-text h1 {
            font-size: 56px;
            line-height: 1.15;
            font-weight: 700;
            margin-bottom: 25px;
            letter-spacing: -1.5px;
        }

        .hero-text h1 span.gradient {
            background: linear-gradient(to right, var(--accent-green), #6ee7b7);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-text p {
            font-size: 18px;
            color: var(--text-secondary);
            margin-bottom: 40px;
            max-width: 580px;
            font-weight: 300;
        }

        .cta-group {
            display: flex;
            gap: 20px;
        }

        .btn-primary {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            padding: 14px 30px;
            background-color: var(--accent-green);
            color: #020617;
            text-decoration: none;
            border-radius: 30px;
            font-weight: 600;
            font-size: 15px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 20px rgba(34, 197, 94, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 25px rgba(34, 197, 94, 0.5);
        }

        .btn-secondary {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            padding: 14px 30px;
            background-color: transparent;
            color: var(--text-primary);
            border: 1px solid var(--border-color);
            text-decoration: none;
            border-radius: 30px;
            font-weight: 500;
            font-size: 15px;
            transition: all 0.3s ease;
        }

        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.05);
            border-color: rgba(255, 255, 255, 0.2);
        }

        /* 右侧霓虹仪表盘/数字图表 */
        .hero-visual {
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .dashboard-mockup {
            background: rgba(15, 23, 42, 0.6);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            padding: 40px;
            width: 100%;
            max-width: 420px;
            box-shadow: 0 40px 80px rgba(0,0,0,0.5);
            backdrop-filter: blur(20px);
        }

        .chart-circle {
            width: 200px;
            height: 200px;
            margin: 0 auto 30px auto;
            border-radius: 50%;
            background: conic-gradient(var(--accent-green) 0% 70%, var(--accent-blue) 70% 90%, #1e293b 90% 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            box-shadow: 0 0 30px rgba(34, 197, 94, 0.15);
        }

        .chart-circle::after {
            content: '';
            position: absolute;
            width: 160px;
            height: 160px;
            background: #0b1329;
            border-radius: 50%;
        }

        .chart-inner-text {
            position: relative;
            z-index: 2;
            text-align: center;
        }

        .chart-inner-text h3 {
            font-size: 36px;
            font-weight: 700;
        }

        .chart-inner-text p {
            font-size: 12px;
            color: var(--text-secondary);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .stat-legend {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .stat-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 14px;
        }

        .stat-label {
            display: flex;
            align-items: center;
            gap: 10px;
            color: var(--text-secondary);
        }

        .dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
        }

        .dot.green { background-color: var(--accent-green); box-shadow: 0 0 8px var(--accent-green); }
        .dot.blue { background-color: var(--accent-blue); box-shadow: 0 0 8px var(--accent-blue); }

        /* ==================== 关于我板块 ==================== */
        .about-grid {
            display: grid;
            grid-template-columns: 0.8fr 1.2fr;
            gap: 60px;
            align-items: start;
        }

        .profile-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            padding: 40px;
            text-align: center;
        }

        .avatar-container {
            width: 140px;
            height: 140px;
            border-radius: 50%;
            margin: 0 auto 25px auto;
            background: linear-gradient(135deg, var(--accent-green), var(--accent-blue));
            padding: 4px;
        }

        .avatar-placeholder {
            width: 100%;
            height: 100%;
            background: #0f172a;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 32px;
            color: var(--accent-green);
        }

        .profile-card h3 {
            font-size: 24px;
            margin-bottom: 5px;
        }

        .profile-card p {
            color: var(--text-secondary);
            font-size: 14px;
            margin-bottom: 25px;
        }

        .social-row {
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .social-icon {
            width: 42px;
            height: 42px;
            border-radius: 50%;
            background: rgba(255,255,255,0.03);
            border: 1px solid var(--border-color);
            color: var(--text-secondary);
            display: flex;
            justify-content: center;
            align-items: center;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .social-icon:hover {
            color: var(--text-primary);
            border-color: rgba(255,255,255,0.2);
            background: rgba(255,255,255,0.08);
            transform: translateY(-2px);
        }

        .biography h3 {
            font-size: 22px;
            margin-bottom: 20px;
            color: #ffffff;
        }

        .biography p {
            color: var(--text-secondary);
            font-size: 16px;
            margin-bottom: 35px;
            font-weight: 300;
        }

        .bio-facts {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
        }

        .fact-box {
            background: rgba(255, 255, 255, 0.02);
            border-left: 3px solid var(--accent-blue);
            padding: 15px 20px;
            border-radius: 0 12px 12px 0;
        }

        .fact-box h4 {
            font-size: 14px;
            color: var(--text-secondary);
            margin-bottom: 5px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .fact-box p {
            font-size: 16px;
            margin-bottom: 0;
            color: var(--text-primary);
            font-weight: 500;
        }

        /* ==================== 核心能力板块 ==================== */
        .skills-container {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 30px;
        }

        .skill-tile {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            padding: 40px;
            transition: all 0.3s ease;
        }

        .skill-tile:hover {
            transform: translateY(-5px);
            border-color: rgba(34, 197, 94, 0.3);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        .skill-tile .icon-box {
            width: 60px;
            height: 60px;
            background: rgba(34, 197, 94, 0.1);
            border-radius: 16px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 24px;
            color: var(--accent-green);
            margin-bottom: 30px;
        }

        .skill-tile h3 {
            font-size: 22px;
            margin-bottom: 15px;
            font-weight: 600;
        }

        .skill-tile p {
            color: var(--text-secondary);
            font-size: 15px;
            line-height: 1.6;
        }

        /* ==================== 精选作品板块 ==================== */
        .project-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
        }

        .project-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            transition: all 0.3s ease;
        }

        .project-card:hover {
            border-color: rgba(255,255,255,0.15);
            transform: translateY(-4px);
        }

        .project-banner {
            height: 240px;
            background: linear-gradient(135deg, #1e293b, #0f172a);
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            border-bottom: 1px solid var(--border-color);
        }

        /* 内置抽象极简图形代替图片占位符 */
        .project-graphic {
            width: 70%;
            height: 50%;
            border: 2px dashed rgba(255,255,255,0.1);
            border-radius: 12px;
            display: flex;
            justify-content: center;
            align-items: center;
            color: rgba(255,255,255,0.2);
            font-size: 14px;
            letter-spacing: 1px;
        }

        .project-card:nth-child(2) .project-banner {
            background: linear-gradient(135deg, #0f172a, #2e1065);
        }

        .project-badge {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(2, 6, 23, 0.6);
            backdrop-filter: blur(8px);
            border: 1px solid var(--border-color);
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 500;
            color: var(--accent-green);
        }

        .project-body {
            padding: 35px;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
        }

        .project-body h3 {
            font-size: 24px;
            margin-bottom: 12px;
            font-weight: 600;
        }

        .project-body p {
            color: var(--text-secondary);
            font-size: 15px;
            margin-bottom: 30px;
            flex-grow: 1;
        }

        .project-tags {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .tag {
            font-size: 12px;
            background: rgba(255,255,255,0.04);
            border: 1px solid var(--border-color);
            padding: 4px 12px;
            border-radius: 6px;
            color: var(--text-secondary);
            font-family: 'Urbanist', sans-serif;
        }

        /* ==================== 联系与页脚 ==================== */
        #contact {
            min-height: auto;
            padding-top: 100px;
            padding-bottom: 100px;
        }

        .contact-box {
            background: linear-gradient(135deg, rgba(30, 41, 59, 0.4) 0%, rgba(2, 6, 23, 0.8) 100%);
            border: 1px solid var(--border-color);
            border-radius: 32px;
            padding: 60px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .contact-box h2 {
            font-size: 36px;
            margin-bottom: 15px;
            font-weight: 700;
        }

        .contact-box p {
            color: var(--text-secondary);
            font-size: 16px;
            max-width: 500px;
            margin: 0 auto 40px auto;
        }

        .mail-link {
            font-size: 28px;
            color: var(--accent-green);
            text-decoration: none;
            font-weight: 700;
            letter-spacing: -0.5px;
            transition: opacity 0.3s ease;
        }

        .mail-link:hover {
            opacity: 0.8;
        }

        footer {
            max-width: 1300px;
            margin: 0 auto;
            padding: 40px;
            border-top: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
            color: #475569;
            font-size: 14px;
        }

        /* 响应式媒体查询：完美适配移动端 */
        @media (max-width: 1024px) {
            .hero-container, .about-grid {
                grid-template-columns: 1fr;
                gap: 50px;
            }
            .skills-container {
                grid-template-columns: 1fr 1fr;
            }
            .project-grid {
                grid-template-columns: 1fr;
            }
            .hero-visual {
                order: -1; /* 移动端图表排在上方 */
            }
        }

        @media (max-width: 768px) {
            .nav-container {
                padding: 20px;
            }
            nav {
                display: none; /* 移动端可隐藏或转为汉堡菜单，此处精简 */
            }
            section {
                padding: 100px 20px 40px 20px;
            }
            .hero-text h1 {
                font-size: 40px;
            }
            .skills-container {
                grid-template-columns: 1fr;
            }
            .bio-facts {
                grid-template-columns: 1fr;
            }
            .contact-box {
                padding: 40px 20px;
            }
            .mail-link {
                font-size: 20px;
            }
            footer {
                flex-direction: column;
                gap: 15px;
                text-align: center;
                padding: 30px 20px;
            }
        }
    </style>
</head>
<body>

    <!-- 背景漫反射光效 -->
    <div class="bg-glow"></div>

    <!-- 顶栏导航 -->
    <header>
        <div class="nav-container">
            <div class="logo">PORT<span>FOLIO.</span></div>
            <nav>
                <a href="#home" class="active-link">首页</a>
                <a href="#about">关于</a>
                <a href="#skills">核心能力</a>
                <a href="#projects">精选作品</a>
                <a href="#contact">联系</a>
            </nav>
        </div>
    </header>

    <!-- 首页 / 欢迎板块 -->
    <section id="home">
        <div class="hero-container">
            <div class="hero-text">
                <h1>打造具有<br><span class="gradient">数据洞察力</span>的职业名片</h1>
                <p>你好，我是david。专注于将复杂的信息与业务逻辑转化为直观、高效的数字体验。坚持理性思考与现代美学的融合。</p>
                <div class="cta-group">
                    <a href="#projects" class="btn-primary">浏览精选作品 <i class="fa-solid fa-arrow-right"></i></a>
                    <a href="#contact" class="btn-secondary">保持联系</a>
                </div>
            </div>
            <div class="hero-visual">
                <!-- 霓虹暗黑仪表盘视觉元素 -->
                <div class="dashboard-mockup">
                    <div class="chart-circle">
                        <div class="chart-inner-text">
                            <h3>85%</h3>
                            <p>专业匹配度</p>
                        </div>
                    </div>
                    <div class="stat-legend">
                        <div class="stat-item">
                            <span class="stat-label"><span class="dot green"></span>战略咨询与核心硬技能</span>
                            <span>70%</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-label"><span class="dot blue"></span>设计美学与创新思维</span>
                            <span>15%</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 关于我板块 -->
    <section id="about">
        <h2 class="section-title">关于<span>我.</span></h2>
        <div class="about-grid">
            <div class="profile-card">
                <div class="avatar-container">
                    <div class="avatar-placeholder">
                        <i class="fa-regular fa-user"></i>
                    </div>
                </div>
                <h3>David</h3>
                <p>学生 / 独立创作者</p>
                <div class="social-row">
                    <a href="#" class="social-icon"><i class="fa-brands fa-github"></i></a>
                    <a href="#" class="social-icon"><i class="fa-brands fa-linkedin-in"></i></a>
                    <a href="#" class="social-icon"><i class="fa-regular fa-envelope"></i></a>
                </div>
            </div>
            <div class="biography">
                <h3>职业履历与背景</h3>
                <p>这里是一段更加高级、注重逻辑的自我介绍。您可以写您在垂直领域深耕的年限、成功交付过什么量级的项目，或者您区别于他人的核心竞争优势。致力于通过严谨的架构思维和敏锐的商业嗅觉为组织和产品赋能。</p>
                <div class="bio-facts">
                    <div class="fact-box">
                        <h4>定位 / Location</h4>
                        <p>中国 · 珠海 / 澳门</p>
                    </div>
                    <div class="fact-box">
                        <h4>经验 / Experience</h4>
                        <p>5+ 年专业领域深耕</p>
                    </div>
                    <div class="fact-box">
                        <h4>教育 / Education</h4>
                        <p>名校商学院 / 计算机学士</p>
                    </div>
                    <div class="fact-box">
                        <h4>状态 / Status</h4>
                        <p>开放长期合作与咨询</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 核心能力板块 -->
    <section id="skills">
        <h2 class="section-title">核心<span>能力.</span></h2>
        <div class="skills-container">
            <div class="skill-tile">
                <div class="icon-box"><i class="fa-solid fa-chart-line"></i></div>
                <h3>战略与商业分析</h3>
                <p>具备敏锐的行业洞察力，能够独立完成市场调研、竞品拆解、以及量化数理模型的搭建，为业务决策提供有力支撑。</p>
            </div>
            <div class="skill-tile">
                <div class="icon-box"><i class="fa-solid fa-layer-group"></i></div>
                <h3>架构设计与技术栈</h3>
                <p>精通前沿系统架构，注重代码规范与执行效率。能够完美兼顾高并发逻辑与前端的极致视觉还原。</p>
            </div>
            <div class="skill-tile">
                <div class="icon-box"><i class="fa-solid fa-wand-magic-sparkles"></i></div>
                <h3>数字化产品创新</h3>
                <p>专注于全链路产品全生命周期管理，从0到1梳理复杂的用户旅程，通过精益画布快速验证市场PMF。</p>
            </div>
        </div>
    </section>

    <!-- 精选作品板块 -->
    <section id="projects">
        <h2 class="section-title">精选<span>作品.</span></h2>
        <div class="project-grid">
            <div class="project-card">
                <div class="project-banner">
                    <span class="project-badge">商业咨询</span>
                    <div class="project-graphic">DATA VISUALIZATION INTERFACE</div>
                </div>
                <div class="project-body">
                    <h3>某零售巨头数字化转型战略白皮书</h3>
                    <p>主导该集团核心零售板块的数字化体系重构，基于全渠道数据中台，协助客户实现全链路库存周转率提升23%，定制了全套商业智能可视化看板。</p>
                    <div class="project-tags">
                        <span class="tag">商业战略</span>
                        <span class="tag">Tableau</span>
                        <span class="tag">数据治理</span>
                    </div>
                </div>
            </div>
            <div class="project-card">
                <div class="project-banner">
                    <span class="project-badge">产品研发</span>
                    <div class="project-graphic">SAAS PLATFORM ARCHITECTURE</div>
                </div>
                <div class="project-body">
                    <h3>新一代敏捷团队资产管理 SaaS 系统</h3>
                    <p>作为独立架构师与产品主理人，从零构建了一套面向出海企业的数字资产看板。采用无服务架构（Serverless）设计，目前已稳定运行并盈利。</p>
                    <div class="project-tags">
                        <span class="tag">SaaS 产品</span>
                        <span class="tag">Next.js</span>
                        <span class="tag">Cloudflare</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 联系我们板块 -->
    <section id="contact">
        <div class="contact-box">
            <h2>让我们聊聊新的可能</h2>
            <p>如果您正在寻找一位兼具严谨商业逻辑与数字化落地能力的合作伙伴，随时欢迎给我来信。</p>
            <a href="mailto:your_email@example.com" class="mail-link">your_email@example.com</a>
        </div>
    </section>

    <!-- 页脚 -->
    <footer>
        <p>&copy; 2026 YOUR NAME. 保留所有权利。</p>
        <p>Designed with Logic & Aesthetic</p>
    </footer>

    <!-- 简单的导航高亮切换脚本 -->
    <script>
        const sections = document.querySelectorAll('section');
        const navLinks = document.querySelectorAll('nav a');

        window.addEventListener('scroll', () => {
            let current = '';
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                const sectionHeight = section.clientHeight;
                if (pageYOffset >= (sectionTop - sectionHeight / 3)) {
                    current = section.getAttribute('id');
                }
            });

            navLinks.forEach(a => {
                a.classList.remove('active-link');
                if (a.getAttribute('href').includes(current)) {
                    a.classList.add('active-link');
                }
            });
        });
    </script>
</body>
</html>
