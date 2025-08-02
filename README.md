# UNI
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>U.N.I - AI 대화 분석 서비스</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Pretendard', -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif;
            background: #ffffff;
            color: #333;
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            box-shadow: 0 2px 20px rgba(0,0,0,0.05);
            z-index: 1000;
            padding: 20px 0;
        }
        
        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo-nav {
            font-size: 32px;
            font-weight: 900;
            color: #667eea;
            text-decoration: none;
        }
        
        .nav-links {
            display: flex;
            gap: 30px;
            align-items: center;
        }
        
        .nav-links a {
            color: #666;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }
        
        .nav-links a:hover {
            color: #667eea;
        }
        
        .btn-start {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 10px 25px;
            border-radius: 25px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.3);
        }
        
        .btn-start:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(102, 126, 234, 0.4);
        }
        
        /* Hero Section */
        .hero {
            margin-top: 80px;
            padding: 80px 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            position: relative;
            overflow: hidden;
        }
        
        .hero::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            animation: pulse 6s ease-in-out infinite;
        }
        
        .hero-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
            position: relative;
            z-index: 1;
        }
        
        .hero-text h1 {
            font-size: 56px;
            color: white;
            font-weight: 900;
            margin-bottom: 20px;
            line-height: 1.2;
        }
        
        .hero-text .highlight {
            color: #BFFF00;
        }
        
        .hero-text p {
            font-size: 20px;
            color: rgba(255,255,255,0.9);
            margin-bottom: 30px;
            line-height: 1.6;
        }
        
        .hero-demo {
            background: white;
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.2);
        }
        
        .demo-tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .demo-tab {
            padding: 8px 16px;
            background: #f5f5f5;
            border-radius: 10px;
            font-size: 14px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .demo-tab.active {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }
        
        .demo-content {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 20px;
            min-height: 300px;
            position: relative;
        }
        
        .chat-message {
            margin-bottom: 15px;
            animation: slideIn 0.5s ease-out;
        }
        
        @keyframes slideIn {
            from { opacity: 0; transform: translateX(-20px); }
            to { opacity: 1; transform: translateX(0); }
        }
        
        .message-sent {
            text-align: right;
        }
        
        .message-bubble {
            display: inline-block;
            padding: 10px 15px;
            border-radius: 20px;
            max-width: 70%;
            font-size: 14px;
        }
        
        .message-sent .message-bubble {
            background: #667eea;
            color: white;
        }
        
        .message-received .message-bubble {
            background: white;
            color: #333;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }
        
        .analysis-result {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin-top: 20px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }
        
        .analysis-result h4 {
            color: #667eea;
            margin-bottom: 10px;
        }
        
        .cta-hero {
            background: #BFFF00;
            color: #333;
            padding: 15px 40px;
            border-radius: 50px;
            font-size: 18px;
            font-weight: 700;
            text-decoration: none;
            display: inline-block;
            transition: all 0.3s;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            border: 2px solid transparent;
        }
        
        .cta-hero:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.3);
            border-color: white;
        }
        
        /* Features Section */
        .features-section {
            padding: 100px 20px;
            background: #f8f9fa;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .section-header {
            text-align: center;
            margin-bottom: 60px;
        }
        
        .section-header h2 {
            font-size: 42px;
            color: #333;
            margin-bottom: 20px;
            font-weight: 800;
        }
        
        .section-header p {
            font-size: 18px;
            color: #666;
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
        }
        
        .feature-card {
            background: white;
            padding: 40px 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }
        
        .feature-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }
        
        .feature-icon {
            font-size: 48px;
            margin-bottom: 20px;
        }
        
        .feature-card h3 {
            font-size: 24px;
            color: #333;
            margin-bottom: 15px;
            font-weight: 700;
        }
        
        .feature-card p {
            color: #666;
            line-height: 1.6;
        }
        
        /* How It Works */
        .how-it-works {
            padding: 100px 20px;
            background: white;
        }
        
        .steps-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 900px;
            margin: 0 auto;
            position: relative;
        }
        
        .step-item {
            text-align: center;
            flex: 1;
            position: relative;
            z-index: 1;
        }
        
        .step-circle {
            width: 120px;
            height: 120px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 20px;
            font-size: 48px;
            color: white;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
        }
        
        .step-item h4 {
            font-size: 20px;
            color: #333;
            margin-bottom: 10px;
            font-weight: 700;
        }
        
        .step-item p {
            color: #666;
            font-size: 16px;
        }
        
        .step-arrow {
            position: absolute;
            top: 60px;
            width: 100px;
            height: 2px;
            background: #ddd;
            z-index: 0;
        }
        
        .step-arrow::after {
            content: '→';
            position: absolute;
            right: -10px;
            top: -10px;
            color: #ddd;
            font-size: 20px;
        }
        
        /* Pricing */
        .pricing-section {
            padding: 100px 20px;
            background: #f8f9fa;
        }
        
        .pricing-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            max-width: 900px;
            margin: 0 auto;
        }
        
        .pricing-card {
            background: white;
            border-radius: 20px;
            padding: 40px 30px;
            text-align: center;
            position: relative;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            transition: all 0.3s;
        }
        
        .pricing-card.featured {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            transform: scale(1.05);
            box-shadow: 0 20px 40px rgba(102, 126, 234, 0.3);
        }
        
        .pricing-card h3 {
            font-size: 28px;
            margin-bottom: 10px;
            font-weight: 700;
        }
        
        .price {
            font-size: 48px;
            font-weight: 900;
            margin-bottom: 5px;
        }
        
        .price-unit {
            font-size: 16px;
            opacity: 0.7;
        }
        
        .pricing-features {
            list-style: none;
            margin: 30px 0;
        }
        
        .pricing-features li {
            padding: 10px 0;
            border-bottom: 1px solid rgba(0,0,0,0.05);
        }
        
        .pricing-card.featured .pricing-features li {
            border-bottom-color: rgba(255,255,255,0.2);
        }
        
        .pricing-cta {
            background: #BFFF00;
            color: #333;
            padding: 12px 30px;
            border-radius: 25px;
            text-decoration: none;
            font-weight: 600;
            display: inline-block;
            transition: all 0.3s;
        }
        
        .pricing-cta:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
        }
        
        /* FAQ Section */
        .faq-section {
            padding: 100px 20px;
            background: white;
        }
        
        .faq-container {
            max-width: 800px;
            margin: 0 auto;
        }
        
        .faq-item {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .faq-item:hover {
            box-shadow: 0 5px 20px rgba(0,0,0,0.05);
        }
        
        .faq-question {
            font-size: 18px;
            font-weight: 600;
            color: #333;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .faq-icon {
            font-size: 24px;
            color: #667eea;
            transition: transform 0.3s;
        }
        
        .faq-answer {
            margin-top: 15px;
            color: #666;
            line-height: 1.6;
            display: none;
        }
        
        .faq-item.active .faq-answer {
            display: block;
        }
        
        .faq-item.active .faq-icon {
            transform: rotate(45deg);
        }
        
        /* Footer */
        footer {
            background: #333;
            color: white;
            padding: 50px 20px 30px;
            text-align: center;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .footer-logo {
            font-size: 36px;
            font-weight: 900;
            color: #BFFF00;
            margin-bottom: 20px;
        }
        
        .footer-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-bottom: 30px;
        }
        
        .footer-links a {
            color: rgba(255,255,255,0.7);
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-links a:hover {
            color: #BFFF00;
        }
        
        .copyright {
            color: rgba(255,255,255,0.5);
            font-size: 14px;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .hero-content {
                grid-template-columns: 1fr;
                text-align: center;
            }
            
            .hero-text h1 {
                font-size: 36px;
            }
            
            .features-grid {
                grid-template-columns: 1fr;
            }
            
            .steps-container {
                flex-direction: column;
                gap: 40px;
            }
            
            .step-arrow {
                display: none;
            }
            
            .nav-links {
                display: none;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="nav-container">
            <a href="#" class="logo-nav">U.N.I</a>
            <div class="nav-links">
                <a href="#features">기능</a>
                <a href="#how-it-works">사용법</a>
                <a href="#pricing">가격</a>
                <a href="#faq">FAQ</a>
                <a href="#" class="btn-start">무료로 시작하기</a>
            </div>
        </div>
    </nav>
    
    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <div class="hero-text">
                <h1>운명처럼 <span class="highlight">UNI</span>하게<br>우리 사이를 분석해요</h1>
                <p>카톡 대화를 붙여넣기만 하면<br>AI가 관계의 모든 것을 읽어드립니다</p>
                <a href="#" class="cta-hero">지금 무료로 분석하기</a>
            </div>
            <div class="hero-demo">
                <div class="demo-tabs">
                    <div class="demo-tab active">대화 분석</div>
                    <div class="demo-tab">AI 시뮬레이션</div>
                    <div class="demo-tab">관계 리포트</div>
                </div>
                <div class="demo-content">
                    <div class="chat-message message-received">
                        <div class="message-bubble">오늘 영화 어땠어?</div>
                    </div>
                    <div class="chat-message message-sent">
                        <div class="message-bubble">재밌었어! 다음에 같이 볼래?</div>
                    </div>
                    <div class="chat-message message-received">
                        <div class="message-bubble">음... 나중에 시간 되면!</div>
                    </div>
                    <div class="analysis-result">
                        <h4>🔍 AI 분석 결과</h4>
                        <p>상대방이 조심스러운 반응을 보이고 있어요. "나중에"라는 표현은 부담을 느낄 때 자주 사용되는 완곡한 거절 신호일 수 있습니다.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Features Section -->
    <section id="features" class="features-section">
        <div class="container">
            <div class="section-header">
                <h2>AI가 읽어주는 관계의 모든 것</h2>
                <p>복잡한 설치 없이, 대화만 붙여넣으면 10초 만에 분석 완료</p>
            </div>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">🔍</div>
                    <h3>숨은 의미 파악</h3>
                    <p>대화 속 진짜 의도와 감정을 정확히 읽어내고, 오해할 수 있는 부분을 짚어드립니다. 상황별 최적의 답장도 추천해드려요.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">💑</div>
                    <h3>MBTI 궁합 분석</h3>
                    <p>두 사람의 성격 유형과 나이를 고려한 맞춤형 궁합 리포트. 소통 스타일의 차이와 개선 방법까지 제시합니다.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🎮</div>
                    <h3>AI 대화 시뮬레이션</h3>
                    <p>상대방의 말투를 학습한 AI와 중요한 대화를 미리 연습해보세요. 고백, 사과, 제안 등 다양한 상황 대비 가능!</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">📊</div>
                    <h3>관계 밸런스 체크</h3>
                    <p>누가 대화를 주도하는지, 답장 속도와 길이는 어떤지 객관적으로 분석. 건강한 관계를 위한 인사이트 제공.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">💭</div>
                    <h3>호감도 분석</h3>
                    <p>답장 패턴과 언어 사용으로 상대방의 관심도 측정. 관계가 발전하는 신호인지, 거리를 두는 신호인지 구분해드립니다.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">📈</div>
                    <h3>관계 변화 추적</h3>
                    <p>시간에 따른 대화 온도와 친밀도 변화를 시각화. 관계의 전환점과 중요한 순간들을 포착합니다.</p>
                </div>
            </div>
        </div>
    </section>
    
    <!-- How It Works -->
    <section id="how-it-works" class="how-it-works">
        <div class="container">
            <div class="section-header">
                <h2>너무나 간단한 3단계</h2>
                <p>복잡한 가입 절차 없이 바로 시작하세요</p>
            </div>
            <div class="steps-container">
                <div class="step-item">
                    <div class="step-circle">📱</div>
                    <h4>대화 복사</h4>
                    <p>카톡이나 메신저에서<br>분석할 대화 복사</p>
                </div>
                <div class="step-arrow" style="left: 25%;"></div>
                <div class="step-item">
                    <div class="step-circle">📋</div>
                    <h4>붙여넣기</h4>
                    <p>UNI에 대화 내용<br>간단히 붙여넣기</p>
                </div>
                <div class="step-arrow" style="right: 25%;"></div>
                <div class="step-item">
                    <div class="step-circle">✨</div>
                    <h4>분석 완료</h4>
                    <p>10초 만에<br>AI 분석 결과 확인</p>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Pricing -->
    <section id="pricing" class="pricing-section">
        <div class="container">
            <div class="section-header">
                <h2>부담 없는 가격</h2>
                <p>무료로 시작하고 필요할 때만 결제하세요</p>
            </div>
            <div class="pricing-cards">
                <div class="pricing-card">
                    <h3>무료</h3>
                    <div class="price">0<span class="price-unit">원</span></div>
                    <ul class="pricing-features">
                        <li>하루 3회 기본 분석</li>
                        <li>감정 분석 리포트</li>
                        <li>관계 유형 진단</li>
                        <li>5분 챗봇 연습</li>
                    </ul>
                    <a href="#" class="pricing-cta" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); color: white;">무료로 시작</a>
                </div>
                <div class="pricing-card featured">
                    <h3>프리미엄</h3>
                    <div class="price">3,900<span class="price-unit">원/월</span></div>
                    <ul class="pricing-features">
                        <li>✨ 무제한 분석</li>
                        <li>✨ 심화 리포트</li>
                        <li>✨ AI 코칭 기능</li>
                        <li>✨ 무제한 시뮬레이션</li>
                        <li>✨ PDF 다운로드</li>
                        <li>✨ 광고 제거</li>
                    </ul>
                    <a href="#" class="pricing-cta">프리미엄 시작</a>
                </div>
                <div class="pricing-card">
                    <h3>연간 결제</h3>
                    <div class="price">19,000<span class="price-unit">원/년</span></div>
                    <ul class="pricing-features">
                        <li>🎁 7개월 무료 혜택</li>
                        <li>모든 프리미엄 기능</li>
                        <li>우선 고객 지원</li>
                        <li>신규 기능 먼저 체험</li>
                    </ul>
                    <a href="#" class="pricing-cta" style="background: #ff4757; color: white;">59% 할인</a>
                </div>
            </div>
            
            <!-- 추가 옵션 더보기 -->
            <div style="text-align: center; margin-top: 50px;">
                <button id="moreOptions" style="background: none; border: 2px solid #667eea; color: #667eea; padding: 12px 30px; border-radius: 25px; font-size: 16px; font-weight: 600; cursor: pointer; transition: all 0.3s;">
                    추가 패키지 더보기 ▼
                </button>
            </div>
            
            <div id="additionalOptions" style="display: none; margin-top: 40px;">
                <h3 style="text-align: center; margin-bottom: 30px; color: #333; font-size: 28px;">특별 패키지</h3>
                <div class="pricing-cards">
                    <div class="pricing-card">
                        <h3>💔 이별 극복</h3>
                        <div class="price">9,900<span class="price-unit">원</span></div>
                        <ul class="pricing-features">
                            <li>30일 집중 분석</li>
                            <li>AI 힐링 코칭</li>
                            <li>성장 포인트 발견</li>
                            <li>새출발 가이드</li>
                        </ul>
                        <a href="#" class="pricing-cta" style="background: #5f27cd; color: white;">구매하기</a>
                    </div>
                    <div class="pricing-card">
                        <h3>💕 고백 성공</h3>
                        <div class="price">7,900<span class="price-unit">원</span></div>
                        <ul class="pricing-features">
                            <li>무제한 시뮬레이션</li>
                            <li>성공 전략 리포트</li>
                            <li>타이밍 분석</li>
                            <li>실패 시 피드백</li>
                        </ul>
                        <a href="#" class="pricing-cta" style="background: #ff6b6b; color: white;">구매하기</a>
                    </div>
                    <div class="pricing-card">
                        <h3>💑 커플 패키지</h3>
                        <div class="price">14,900<span class="price-unit">원</span></div>
                        <ul class="pricing-features">
                            <li>2인 동시 이용</li>
                            <li>관계 개선 미션</li>
                            <li>서로 바꿔보기</li>
                            <li>1개월 무제한</li>
                        </ul>
                        <a href="#" class="pricing-cta" style="background: #48dbfb; color: white;">구매하기</a>
                    </div>
                </div>
                
                <h3 style="text-align: center; margin: 40px 0 30px; color: #333; font-size: 28px;">단건 이용권</h3>
                <div class="pricing-cards" style="max-width: 600px; margin: 0 auto;">
                    <div class="pricing-card" style="text-align: left;">
                        <h3 style="text-align: center;">🎯 필요할 때만</h3>
                        <ul class="pricing-features" style="margin: 20px 0;">
                            <li style="display: flex; justify-content: space-between;">
                                <span>1회 심화 분석</span>
                                <strong style="color: #667eea;">1,900원</strong>
                            </li>
                            <li style="display: flex; justify-content: space-between;">
                                <span>24시간 무제한</span>
                                <strong style="color: #667eea;">2,900원</strong>
                            </li>
                            <li style="display: flex; justify-content: space-between;">
                                <span>PDF 리포트 추출</span>
                                <strong style="color: #667eea;">900원</strong>
                            </li>
                            <li style="display: flex; justify-content: space-between;">
                                <span>긴급 분석 (즉시)</span>
                                <strong style="color: #667eea;">3,900원</strong>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <!-- FAQ -->
    <section id="faq" class="faq-section">
        <div class="container">
            <div class="section-header">
                <h2>자주 묻는 질문</h2>
                <p>궁금한 점이 있으신가요?</p>
            </div>
            <div class="faq-container">
                <div class="faq-item">
                    <div class="faq-question">
                        내 대화 내용은 안전한가요?
                        <span class="faq-icon">+</span>
                    </div>
                    <div class="faq-answer">
                        네, 완벽히 안전합니다. 입력된 대화는 분석 후 즉시 삭제되며, 서버에 저장되지 않습니다. 모든 데이터는 암호화되어 전송되고, 회원가입이 없어 개인정보와 연결되지 않습니다.
                    </div>
                </div>
                <div class="faq-item">
                    <div class="faq-question">
                        AI 분석은 얼마나 정확한가요?
                        <span class="faq-icon">+</span>
                    </div>
                    <div class="faq-answer">
                        UNI의 AI는 85-90%의 정확도를 보입니다. 다만 반어법, 은어, 문화적 맥락 등에서는 해석에 한계가 있을 수 있어요. 중요한 결정은 AI 분석만으로 하지 마시고 참고 자료로 활용하세요.
                    </div>
                </div>
                <div class="faq-item">
                    <div class="faq-question">
                        어떤 메신저를 지원하나요?
                        <span class="faq-icon">+</span>
                    </div>
                    <div class="faq-answer">
                        카카오톡, 라인, 텔레그램, 왓츠앱, 인스타그램 DM 등 텍스트로 복사 가능한 모든 메신저를 지원합니다. 한국어와 영어 모두 분석 가능하며, 최소 10개 이상의 주고받은 메시지가 필요합니다.
                    </div>
                </div>
                <div class="faq-item">
                    <div class="faq-question">
                        상대방 동의가 필요한가요?
                        <span class="faq-icon">+</span>
                    </div>
                    <div class="faq-answer">
                        법적으로는 문제없지만, 윤리적 사용을 권장합니다. 관계 개선이나 자기 성찰을 위한 목적으로 사용하시고, 분석 결과를 상대방과 함께 보며 소통하면 더욱 좋습니다.
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-logo">U.N.I</div>
            <div class="footer-links">
                <a href="#">이용약관</a>
                <a href="#">개인정보처리방침</a>
                <a href="#">고객센터</a>
                <a href="#">파트너십</a>
            </div>
            <p class="copyright">© 2025 U.N.I. All rights reserved.</p>
        </div>
    </footer>
    
    <script>
        // FAQ Toggle
        document.querySelectorAll('.faq-item').forEach(item => {
            item.addEventListener('click', () => {
                item.classList.toggle('active');
            });
        });
        
        // Demo Tab Switching
        document.querySelectorAll('.demo-tab').forEach(tab => {
            tab.addEventListener('click', () => {
                document.querySelectorAll('.demo-tab').forEach(t => t.classList.remove('active'));
                tab.classList.add('active');
            });
        });
        
        // More Options Toggle
        document.getElementById('moreOptions').addEventListener('click', function() {
            const additionalOptions = document.getElementById('additionalOptions');
            if (additionalOptions.style.display === 'none' || additionalOptions.style.display === '') {
                additionalOptions.style.display = 'block';
                this.innerHTML = '추가 패키지 접기 ▲';
                // Smooth scroll to show the additional options
                additionalOptions.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
            } else {
                additionalOptions.style.display = 'none';
                this.innerHTML = '추가 패키지 더보기 ▼';
            }
        });
    </script>
</body>
</html>
