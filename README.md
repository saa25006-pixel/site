<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>愛媛県立西条農業高等学校</title>
    <style>
        /* 全体のリセットと共通スタイル */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
            color: #333;
            background-color: #fcfdfa;
            line-height: 1.6;
        }
        a {
            text-decoration: none;
            color: inherit;
        }

        /* ヘッダー */
        header {
            background-color: #ffffff;
            border-bottom: 3px solid #2d6a4f; /* 西農グリーン */
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        .logo h1 {
            font-size: 1.4rem;
            color: #2d6a4f;
            font-weight: bold;
        }
        .logo p {
            font-size: 0.8rem;
            color: #666;
        }
        nav ul {
            display: flex;
            list-style: none;
            gap: 20px;
        }
        nav ul li a {
            font-weight: bold;
            font-size: 0.95rem;
            color: #444;
            transition: color 0.2s;
        }
        nav ul li a:hover {
            color: #2d6a4f;
        }

        /* メインビジュアル */
        .hero {
            background: linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.3)), url('https://images.unsplash.com/photo-1592417817098-8f3d6eb19675?auto=format&fit=crop&w=1200&q=80') no-repeat center center/cover;
            height: 450px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: #fff;
            text-align: center;
            padding: 0 20px;
        }
        .hero h2 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.6);
            letter-spacing: 2px;
        }
        .hero p {
            font-size: 1.2rem;
            text-shadow: 1px 1px 3px rgba(0,0,0,0.6);
        }

        /* コンテンツ共通 */
        section {
            padding: 60px 10%;
        }
        .section-title {
            text-align: center;
            font-size: 1.8rem;
            color: #2d6a4f;
            margin-bottom: 40px;
            position: relative;
            padding-bottom: 10px;
        }
        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 3px;
            background-color: #b7e4c7;
        }

        /* お知らせ・ニュース */
        .news-list {
            background: #fff;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }
        .news-item {
            display: flex;
            padding: 15px 0;
            border-bottom: 1px solid #eee;
        }
        .news-item:last-child {
            border-bottom: none;
        }
        .news-date {
            width: 120px;
            color: #888;
            font-size: 0.9rem;
        }
        .news-category {
            background-color: #e8f5e9;
            color: #2d6a4f;
            padding: 2px 8px;
            border-radius: 4px;
            font-size: 0.8rem;
            margin-right: 15px;
            height: fit-content;
        }
        .news-title {
            flex: 1;
            font-size: 0.95rem;
        }

        /* 学科紹介 */
        .departments {
            background-color: #f4f9f4;
        }
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
        }
        .card {
            background: #fff;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0,0,0,0.05);
            transition: transform 0.3s;
        }
        .card:hover {
            transform: translateY(-50px); /* 浮き上がるエフェクト */
            transform: scale(1.03);
        }
        .card-img {
            height: 160px;
            background-size: cover;
            background-position: center;
        }
        .card-content {
            padding: 20px;
        }
        .card-title {
            font-size: 1.2rem;
            color: #2d6a4f;
            margin-bottom: 10px;
            font-weight: bold;
        }
        .card-text {
            font-size: 0.85rem;
            color: #666;
            line-height: 1.5;
        }

        /* フッター */
        footer {
            background-color: #1b4332;
            color: #fff;
            padding: 40px 10% 20px;
            font-size: 0.9rem;
        }
        .footer-container {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 30px;
            margin-bottom: 30px;
        }
        .footer-info h3 {
            margin-bottom: 10px;
            font-size: 1.2rem;
        }
        .footer-links ul {
            list-style: none;
        }
        .footer-links ul li {
            margin-bottom: 8px;
        }
        .footer-links ul li a:hover {
            text-decoration: underline;
        }
        .copyright {
            text-align: center;
            color: #85a392;
            font-size: 0.8rem;
            border-top: 1px solid #2d6a4f;
            padding-top: 20px;
        }

        /* レスポンシブ */
        @media (max-width: 768px) {
            header {
                flex-direction: column;
                gap: 15px;
            }
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
                gap: 10px;
            }
            .hero h2 {
                font-size: 1.8rem;
            }
            .footer-container {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>

    <header>
        <div class="logo">
            <h1>愛媛県立西条農業高等学校</h1>
            <p>豊かな自然とはぐくむ、未来の知恵と技術</p>
        </div>
        <nav>
            <ul>
                <li><a href="#home">学校紹介</a></li>
                <li><a href="#news">西農ニュース</a></li>
                <li><a href="#departments">学科紹介</a></li>
                <li><a href="#life">学校生活</a></li>
            </ul>
        </nav>
    </header>

    <div class="hero" id="home">
        <h2>大地を学び、未来を育てる。</h2>
        <p>西条の豊かな水と石鎚の山々に見守られ、明日の農業をデザインする</p>
    </div>

    <section id="news">
        <h2 class="section-title">西農ニュース</h2>
        <div class="news-list">
            <div class="news-item">
                <div class="news-date">2026.06.01</div>
                <div class="news-category">農場通信</div>
                <div class="news-title">【食農科学科】夏野菜の収穫と即売会のお知らせ</div>
            </div>
            <div class="news-item">
                <div class="news-date">2026.05.20</div>
                <div class="news-category">学校行事</div>
                <div class="news-title">令和8年度 農業クラブ校内意見発表会を開催しました</div>
            </div>
            <div class="news-item">
                <div class="news-date">2026.04.10</div>
                <div class="news-category">お知らせ</div>
                <div class="news-title">新入生を迎え、新しい農場実習がスタートしました</div>
            </div>
        </div>
    </section>

    <section id="departments">
        <h2 class="section-title">個性を伸ばす学科紹介</h2>
        <div class="grid">
            <div class="card">
                <div class="card-img" style="background-image: url('https://images.unsplash.com/photo-1593113598332-cd288d649433?auto=format&fit=crop&w=400&q=80');"></div>
                <div class="card-content">
                    <div class="card-title">食農科学科</div>
                    <div class="card-text">作物の栽培技術から食品加工、さらには流通までを総合的に学び、安全で美味しい「食」の未来を創造します。</div>
                </div>
            </div>
            <div class="card">
                <div class="card-img" style="background-image: url('https://images.unsplash.com/photo-1416879595882-3373a0480b5b?auto=format&fit=crop&w=400&q=80');"></div>
                <div class="card-content">
                    <div class="card-title">環境未来科</div>
                    <div class="card-text">地域環境の保全やバイオテクノロジー、西条の豊かな水資源を守る技術など、持続可能な社会を支える力を養います。</div>
                </div>
            </div>
            <div class="card">
                <div class="card-img" style="background-image: url('https://images.unsplash.com/photo-1585320806297-9794b3e4eeae?auto=format&fit=crop&w=400&q=80');"></div>
                <div class="card-content">
                    <div class="card-title">生活デザイン科</div>
                    <div class="card-text">草花を活用した空間デザインや、保育・福祉、調理衣飾など、生活を豊かに彩るクリエイティブな技術を学びます。</div>
                </div>
            </div>
        </div>
    </section>

    <footer>
        <div class="footer-container">
            <div class="footer-info">
                <h3>愛媛県立西条農業高等学校</h3>
                <p>〒793-0006 愛媛県西条市下島山甲166</p>
                <p>TEL: 0897-XX-XXXX / FAX: 0897-XX-XXXX</p>
            </div>
            <div class="footer-links">
                <ul>
                    <li><a href="#">▶ 在校生・保護者の方へ</a></li>
                    <li><a href="#">▶ 中学生の皆さんへ</a></li>
                    <li><a href="#">▶ 卒業生の方へ</a></li>
                    <li><a href="#">▶ プライバシーポリシー</a></li>
                </ul>
            </div>
        </div>
        <div class="copyright">
            &copy; 2026 Saijo Agricultural High School. All Rights Reserved. (Concept Design)
        </div>
    </footer>

</body>
</html>
