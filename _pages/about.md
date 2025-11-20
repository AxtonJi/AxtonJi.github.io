---
permalink: /
title: "JI YIZHOU"
excerpt: "M.A. in Economics - Peking University HSBC Business School"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

<!-- Loading overlay -->
<div id="loading-overlay">
  <div class="loading-content">
    <p class="loading-text">简历加载中...</p>
    <div class="loading-bar">
      <div class="loading-progress" id="loading-progress"></div>
    </div>
  </div>
</div>

<style>
#loading-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

.loading-content {
  text-align: center;
}

.loading-text {
  font-size: 1.2em;
  color: #1565c0;
  margin-bottom: 20px;
  font-family: "SimKai", "KaiTi", serif;
}

.loading-bar {
  width: 200px;
  height: 6px;
  background: #e0e0e0;
  border-radius: 3px;
  overflow: hidden;
}

.loading-progress {
  width: 0%;
  height: 100%;
  background: #1565c0;
  border-radius: 3px;
  transition: width 0.3s ease;
}
</style>

<script>
(function() {
  var progress = document.getElementById('loading-progress');
  var overlay = document.getElementById('loading-overlay');
  var loaded = false;

  // Simulate progress
  var currentProgress = 0;
  var progressInterval = setInterval(function() {
    if (currentProgress < 90 && !loaded) {
      currentProgress += Math.random() * 10;
      progress.style.width = Math.min(currentProgress, 90) + '%';
    }
  }, 200);

  // Load font
  var font = new FontFace('SimKai', 'url(../../simkai.ttf)');

  font.load().then(function(loadedFont) {
    document.fonts.add(loadedFont);
    loaded = true;
    clearInterval(progressInterval);
    progress.style.width = '100%';

    setTimeout(function() {
      overlay.style.opacity = '0';
      overlay.style.transition = 'opacity 0.3s ease';
      setTimeout(function() {
        overlay.style.display = 'none';
      }, 300);
    }, 300);
  }).catch(function(error) {
    // Font failed to load, hide overlay anyway
    console.error('Font load error:', error);
    loaded = true;
    clearInterval(progressInterval);
    progress.style.width = '100%';
    setTimeout(function() {
      overlay.style.display = 'none';
    }, 500);
  });

  // Fallback timeout - hide after 5 seconds regardless
  setTimeout(function() {
    if (overlay.style.display !== 'none') {
      overlay.style.display = 'none';
    }
  }, 5000);
})();
</script>

<div class="lang-switch">
  <button id="btn-en" class="lang-btn active" onclick="switchLang('en')">EN</button>
  <button id="btn-zh" class="lang-btn" onclick="switchLang('zh')">中文</button>
</div>

<button class="print-cv-btn" onclick="window.print()">Print CV / 打印简历</button>

<!-- Print header (only shows when printing) -->
<div class="print-header">
  <h1>JI YIZHOU / 季一舟</h1>
  <p>Phone: (+86) 184-5133-3081 | Email: yzji25@stu.pku.edu.cn</p>
  <p>M.A. in Economics, Peking University HSBC Business School</p>
</div>

<!-- English Version -->
<div id="content-en" class="lang-content" markdown="1">

**Phone:** (+86) 184-5133-3081 &nbsp;&nbsp; **Email:** yzji25@stu.pku.edu.cn

# Education

**Peking University, HSBC Business School** &nbsp; M.A. in Economics
<span class="date-right">2025.09 - Present</span>

**Shandong University, School of Economics** &nbsp; B.A. in Finance
<span class="date-right">2021.09 - 2025.06</span>

- **GPA:** 93.26/100 (Rank: 1/70) &nbsp;&nbsp;&nbsp; **English:** IELTS 7.5 (Speaking 7.0); CET-6 616
- **Core Courses:** Big Data Analytics (99), Microeconomics (99), Statistics (98), Python Data Analysis (99)
- **Honors:** National Scholarship; Internet+ Competition (National Gold & Silver, 2 yrs); National Innovation Program Lead; Energy Conservation Contest (National 1st); Math Competition (National 2nd); Lanqiao Cup Python (Provincial 1st); Math Modeling (Provincial 2nd)

# Internship Experience

**ByteDance (TikTok Global Payments)** &nbsp; Business Analyst Intern
<span class="date-right">2025.01 - 2025.07</span>

- Conducted payment data analysis across multiple business lines; developed SQL templates for querying and monitoring
- Built dashboards to track GMV, transaction rates, and cost metrics; configured automated reports for global BD teams
- Coordinated expert interviews with consulting firms on competitor strategies; led English expert calls
- Synthesized research to formulate cost optimization strategies; produced strategic reports
- Developed multi-country budget forecasts incorporating cross-departmental inputs
- Worked in intensive English-dominant environment (80%); received high commendation and return offer

**BOC International Securities** &nbsp; Macro Research Intern
<span class="date-right">2023.07 - 2023.09</span>

- Monitored RMB/USD exchange rates; analyzed fluctuations and wrote predictive commentary
- Built economic analysis panels for key indicators; assisted in drafting macroeconomic forecast reports
- Evaluated corporate bonds using Wind; wrote analytical reports to support portfolio building

# Skills & Other

- **Programming:** Python (Advanced), STATA (Advanced), MATLAB, Gephi
- **Tools:** Wind Terminal (Advanced), MS Office (Advanced)
- **Other:** Physics Olympiad (Provincial 1st); Biology Olympiad (Provincial 1st); Head, SDU Global Governance Association

</div>

<!-- Chinese Version -->
<div id="content-zh" class="lang-content" style="display:none;" markdown="1">

**电话:** (+86)18451333081 &nbsp;&nbsp; **邮箱:** sinhxcoshx@163.com &nbsp;&nbsp; **政治面貌:** 中共预备党员

# 教育背景

**北京大学 汇丰商学院 经济学**
<span class="date-right">2025.09 - 至今</span>

**山东大学 经济学院 金融学**
<span class="date-right">2021.09 - 2025.06</span>

- **学习成绩:** 93.26/100（1/70） &nbsp;&nbsp;&nbsp; **英语成绩:** IELTS-7.5（口语7.0）；CET6-616
- **主修课程:** 大数据分析（99）、中级微观经济学（99）、统计学（98）、Python数据分析（99）、Python程序设计（98）
- **荣誉奖项:** 国家奖学金、互联网+国家级银奖/金奖（连续两年）、大创国家级立项、节能减排大赛国一、数学竞赛国二、蓝桥杯Python省一、数学建模省二

# 实习经历

**字节跳动 TikTok Global Payments** &nbsp; 商业分析实习生
<span class="date-right">2025.01 - 2025.07</span>

- 负责多业务线支付数据分析；撰写SQL代码模版进行数据查询与监控
- 搭建数据看板追踪GMV、交易渗透率、成本指标；配置自动化报表推送全球BD
- 对接咨询公司进行竞对支付战略专家访谈；主持英文Expert Call
- 整合内外部研究制定成本优化策略；产出战略分析报告
- 编制多国多渠道预算目标，综合跨部门需求
- 工作语言80%英文，高强度线下参与；获高度评价及留用意向

**中银国际证券** &nbsp; 宏观研究实习生
<span class="date-right">2023.07 - 2023.09</span>

- 监测人民币汇率波动；分析原因并撰写货币政策预测评论
- 搭建经济指标分析面板；协助撰写宏观经济推演深度报告
- 利用Wind评估公司债；撰写分析报告协助构建自营组合

# 专业技能

- **编程:** Python（精通）、STATA（精通）、MATLAB、Gephi
- **工具:** Wind终端（精通）、Office（精通）
- **其他:** 物理竞赛省一、生物竞赛省一、校全球治理协会负责人

</div>

<script>
function switchLang(lang) {
  const enContent = document.getElementById('content-en');
  const zhContent = document.getElementById('content-zh');
  const btnEn = document.getElementById('btn-en');
  const btnZh = document.getElementById('btn-zh');

  // Switch main content
  if (lang === 'en') {
    enContent.style.display = 'block';
    zhContent.style.display = 'none';
    btnEn.classList.add('active');
    btnZh.classList.remove('active');
  } else {
    enContent.style.display = 'none';
    zhContent.style.display = 'block';
    btnEn.classList.remove('active');
    btnZh.classList.add('active');
  }

  // Switch sidebar content
  const enElements = document.querySelectorAll('.bio-en, .desc-en, .loc-en, .email-en');
  const zhElements = document.querySelectorAll('.bio-zh, .desc-zh, .loc-zh, .email-zh');

  if (lang === 'en') {
    enElements.forEach(el => el.style.display = '');
    zhElements.forEach(el => el.style.display = 'none');
  } else {
    enElements.forEach(el => el.style.display = 'none');
    zhElements.forEach(el => el.style.display = '');
  }
}
</script>
