<!DOCTYPE html>
<html lang="ja" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>〇〇農業高等学校 | オープンキャンパス特設サイト</title>
  
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            agriBlue: {
              50: '#f0f9ff',
              100: '#e0f2fe',
              500: '#0ea5e9',
              600: '#0284c7',
              700: '#0369a1',
              900: '#0c4a6e',
            },
            sproutGreen: {
              50: '#f0fdf4',
              100: '#dcfce7',
              500: '#22c55e',
              600: '#16a34a',
              700: '#15803d',
              900: '#14532d',
            }
          },
          fontFamily: {
            sans: ['Noto Sans JP', 'sans-serif'],
          }
        }
      }
    }
  </script>

  <!-- Google Fonts & Lucide Icons -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;500;700;900&display=swap" rel="stylesheet">
  <script src="https://unpkg.com/lucide@latest"></script>

  <style>
    body {
      font-family: 'Noto Sans JP', sans-serif;
    }
    .custom-gradient {
      background: linear-gradient(135deg, #f0fdf4 0%, #f0f9ff 100%);
    }
    .hero-pattern {
      background-image: linear-gradient(rgba(12, 74, 110, 0.8), rgba(20, 83, 45, 0.85)), url('https://images.unsplash.com/photo-1500937386664-56d1dfef3854?auto=format&fit=crop&q=80&w=1200');
      background-size: cover;
      background-position: center;
    }
    .perspective-highlight {
      transition: all 0.3s ease;
    }
  </style>
</head>
<body class="text-slate-800 bg-white selection:bg-sproutGreen-100 selection:text-sproutGreen-900">

  <!-- 1. ヘッダー -->
  <header class="sticky top-0 z-40 bg-white/90 backdrop-blur-md border-b border-slate-100">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
      <!-- ロゴ -->
      <a href="#" class="flex items-center space-x-2">
        <div class="w-10 h-10 bg-sproutGreen-600 rounded-xl flex items-center justify-center text-white shadow-md shadow-sproutGreen-200">
          <i data-lucide="sprout" class="w-6 h-6"></i>
        </div>
        <div>
          <span class="text-xs text-slate-500 block font-bold tracking-widest leading-none">FUTURE AGRICULTURE</span>
          <span class="text-lg font-black text-agriBlue-900 tracking-tight">〇〇農業高等学校</span>
        </div>
      </a>

      <!-- デスクトップナビゲーション -->
      <nav class="hidden md:flex items-center space-x-8 text-sm font-medium text-slate-600">
        <a href="#about" class="hover:text-sproutGreen-600 transition-colors">私たちの魅力</a>
        <a href="#courses" class="hover:text-sproutGreen-600 transition-colors">学科紹介</a>
        <a href="#voices" class="hover:text-sproutGreen-600 transition-colors">先輩の声</a>
        <a href="#faq" class="hover:text-sproutGreen-600 transition-colors">よくある質問</a>
        <a href="#apply" class="bg-gradient-to-r from-sproutGreen-600 to-agriBlue-600 text-white px-5 py-2.5 rounded-full hover:shadow-lg hover:shadow-sproutGreen-200 transition-all flex items-center space-x-2">
          <span>体験入学に申し込む</span>
          <i data-lucide="arrow-right" class="w-4 h-4"></i>
        </a>
      </nav>

      <!-- モバイルメニューボタン -->
      <button id="mobile-menu-btn" class="md:hidden p-2 text-slate-600 hover:text-slate-900 focus:outline-none">
        <i data-lucide="menu" id="menu-icon" class="w-6 h-6"></i>
      </button>
    </div>

    <!-- モバイルナビゲーション -->
    <div id="mobile-menu" class="hidden md:hidden bg-white border-t border-slate-100 px-4 pt-2 pb-6 space-y-3 absolute w-full left-0 shadow-lg">
      <a href="#about" class="block py-2 px-3 rounded-lg text-slate-700 hover:bg-slate-50 font-medium">私たちの魅力</a>
      <a href="#courses" class="block py-2 px-3 rounded-lg text-slate-700 hover:bg-slate-50 font-medium">学科紹介</a>
      <a href="#voices" class="block py-2 px-3 rounded-lg text-slate-700 hover:bg-slate-50 font-medium">先輩の声</a>
      <a href="#faq" class="block py-2 px-3 rounded-lg text-slate-700 hover:bg-slate-50 font-medium">よくある質問</a>
      <a href="#apply" class="block py-3 px-3 rounded-lg bg-gradient-to-r from-sproutGreen-600 to-agriBlue-600 text-white text-center font-bold">
        体験入学に申し込む
      </a>
    </div>
  </header>

  <!-- 2. モード切り替えバー (LPの独自プレミアム機能) -->
  <div class="bg-slate-50 border-b border-slate-100 py-3 sticky top-20 z-30 shadow-sm">
    <div class="max-w-7xl mx-auto px-4 flex flex-col sm:flex-row items-center justify-between gap-3 text-sm">
      <div class="flex items-center space-x-2 text-slate-500 font-medium">
        <i data-lucide="sparkles" class="w-4 h-4 text-amber-500 animate-pulse"></i>
        <span>表示モードを切り替えて、あなたに合った情報をチェック！</span>
      </div>
      <div class="flex bg-slate-200 p-1 rounded-full w-full sm:w-auto">
        <button id="btn-student" onclick="togglePerspective('student')" class="flex-1 sm:flex-initial px-5 py-1.5 rounded-full font-bold transition-all duration-300 bg-white text-sproutGreen-700 shadow-sm flex items-center justify-center space-x-1.5">
          <i data-lucide="graduation-cap" class="w-4 h-4"></i>
          <span>中学生向け</span>
        </button>
        <button id="btn-parent" onclick="togglePerspective('parent')" class="flex-1 sm:flex-initial px-5 py-1.5 rounded-full font-bold transition-all duration-300 text-slate-600 hover:text-slate-900 flex items-center justify-center space-x-1.5">
          <i data-lucide="shield-check" class="w-4 h-4"></i>
          <span>保護者向け</span>
        </button>
      </div>
    </div>
  </div>

  <!-- 3. ファーストビュー（FV） -->
  <section class="hero-pattern relative overflow-hidden py-24 md:py-36 flex items-center text-white">
    <!-- 背景オーナメント -->
    <div class="absolute inset-0 opacity-10 bg-[radial-gradient(#fff_1px,transparent_1px)] [background-size:16px_16px]"></div>
    
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 w-full">
      <div class="max-w-3xl space-y-6 md:space-y-8">
        <!-- バッジ -->
        <span class="inline-flex items-center gap-1.5 px-3 py-1 rounded-full text-xs font-bold bg-white/20 backdrop-blur-md text-white border border-white/10 tracking-wider">
          <span class="w-2 h-2 rounded-full bg-sproutGreen-400 animate-ping"></span>
          2026年度 体験入学・オープンキャンパス受付中
        </span>

        <!-- メインキャッチコピー -->
        <h1 class="text-4xl sm:text-5xl lg:text-6xl font-black tracking-tight leading-tight md:leading-tight">
          教科書を閉じて、<br class="sm:hidden">
          <span class="text-transparent bg-clip-text bg-gradient-to-r from-sproutGreen-400 to-sky-300">地球に触れよう。</span>
        </h1>
        
        <!-- サブコピー (中学生向けデフォルト) -->
        <p id="fv-sub-student" class="text-lg sm:text-xl text-slate-100 font-medium leading-relaxed max-w-2xl perspective-highlight">
          ここは、命を育て、未来の食をデザインする最先端のステージ。<br class="hidden sm:inline">
          スマート農業から食のビジネスまで、キミの「好き」をプロにする新しい学びが待っています！
        </p>
        <!-- サブコピー (保護者向け隠し) -->
        <p id="fv-sub-parent" class="hidden text-lg sm:text-xl text-slate-100 font-medium leading-relaxed max-w-2xl perspective-highlight">
          「個性を活かし、イキイキと輝ける場所へ。」<br class="hidden sm:inline">
          5年連続就職内定率100%、国公立・有名私立推薦多数。確かな未来を創り出す、実社会に最も近い実践型キャリア教育を提供します。
        </p>

        <!-- CTA ボタンエリア -->
        <div class="flex flex-col sm:flex-row gap-4 pt-4">
          <a href="#apply" class="px-8 py-4 rounded-xl bg-gradient-to-r from-sproutGreen-500 to-sproutGreen-600 text-white font-bold text-lg text-center hover:shadow-xl hover:shadow-sproutGreen-900/30 transition-all flex items-center justify-center space-x-2 transform hover:-translate-y-0.5">
            <span>未来の農業を体感！体験入学に申し込む</span>
            <i data-lucide="arrow-right-circle" class="w-5 h-5"></i>
          </a>
          <a href="#about" class="px-8 py-4 rounded-xl bg-white/10 hover:bg-white/20 text-white border border-white/20 font-bold text-center transition-all flex items-center justify-center space-x-2 backdrop-blur-sm">
            <span>詳しく見る</span>
            <i data-lucide="chevron-down" class="w-5 h-5"></i>
          </a>
        </div>
      </div>
    </div>
  </section>

  <!-- 4. ターゲットの悩み・共感（導入） -->
  <section class="py-20 custom-gradient relative">
    <div class="max-w-4xl mx-auto px-4 text-center space-y-10">
      <div class="space-y-4">
        <span class="text-sproutGreen-600 font-bold tracking-widest text-sm uppercase block">DO YOU FEEL THIS WAY?</span>
        <h2 id="trouble-title-student" class="text-2xl sm:text-3xl lg:text-4xl font-black text-slate-900 tracking-tight leading-snug perspective-highlight">
          「ただ机に向かう勉強だけで、<br class="sm:hidden">高校3年間が終わっちゃうのかな？」
        </h2>
        <h2 id="trouble-title-parent" class="hidden text-2xl sm:text-3xl lg:text-4xl font-black text-slate-900 tracking-tight leading-snug perspective-highlight">
          「我が子が本当に自分らしく、<br class="sm:hidden">イキイキと輝ける場所はあるだろうか？」
        </h2>
      </div>

      <div class="grid md:grid-cols-3 gap-6 text-left">
        <!-- 悩み 1 -->
        <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-100 flex flex-col justify-between">
          <p class="text-slate-600 font-medium leading-relaxed mb-4">
            「動物や植物は大好きだけど、ふつうの高校へ行って、その『好き』はどうなるんだろう…」
          </p>
          <div class="flex items-center space-x-2 text-slate-400">
            <i data-lucide="help-circle" class="w-5 h-5 text-sky-400"></i>
            <span class="text-xs font-bold">進路に悩む中学生</span>
          </div>
        </div>

        <!-- 悩み 2 -->
        <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-100 flex flex-col justify-between">
          <p class="text-slate-600 font-medium leading-relaxed mb-4">
            「暗記するだけの勉強はちょっと苦手。もっと実際に手を動かして、目に見える成果をつくりたい！」
          </p>
          <div class="flex items-center space-x-2 text-slate-400">
            <i data-lucide="help-circle" class="w-5 h-5 text-sky-400"></i>
            <span class="text-xs font-bold">学び方を変えたい中学生</span>
          </div>
        </div>

        <!-- 悩み 3 -->
        <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-100 flex flex-col justify-between">
          <p class="text-slate-600 font-medium leading-relaxed mb-4">
            「高校を出たあとの進路や就職が不安。今のうちから本当に役立つ『一生モノの強み』を身につけさせたい。」
          </p>
          <div class="flex items-center space-x-2 text-slate-400">
            <i data-lucide="help-circle" class="w-5 h-5 text-sky-400"></i>
            <span class="text-xs font-bold">見守る保護者様</span>
          </div>
        </div>
      </div>

      <div class="p-8 rounded-3xl bg-white shadow-xl shadow-slate-100/50 border border-slate-100 max-w-3xl mx-auto space-y-4">
        <p class="text-lg font-bold text-sproutGreen-700">もしあなたが、少しでもそう感じているなら。</p>
        <p class="text-slate-600 leading-relaxed text-sm sm:text-base">
          〇〇農業高校は、あなたの「好き」や「知的好奇心」が全力で主役になれる場所です。<br>
          ここにあるのは、暗記するだけの教科書の世界ではありません。自ら触れ、体験し、命を育て、社会に届ける。そんな興奮に満ちた「一生モノの青春」が、あなたを待っています。
        </p>
      </div>
    </div>
  </section>

  <!-- 5. 農業高校の3大魅力（ベネフィット） -->
  <section id="about" class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 space-y-16">
      <!-- セクション見出し -->
      <div class="text-center space-y-4">
        <span class="text-agriBlue-600 font-bold tracking-widest text-sm uppercase block">OUR STRENGTHS</span>
        <h2 class="text-3xl sm:text-4xl font-black text-slate-900 tracking-tight">
          キミの想像を超える、農業高校の「3つの新常識」
        </h2>
        <p class="text-slate-500 max-w-2xl mx-auto text-sm sm:text-base">
          従来の「きつい・汚い」という古いイメージを180度覆す、最先端・最高にクリエイティブなカリキュラムを紹介します。
        </p>
      </div>

      <!-- 魅力カード群 -->
      <div class="grid lg:grid-cols-3 gap-8">
        <!-- 魅力 1 -->
        <div class="group bg-slate-50 hover:bg-white rounded-3xl p-8 hover:shadow-2xl hover:shadow-slate-200/50 transition-all duration-300 border border-slate-100 flex flex-col justify-between">
          <div class="space-y-6">
            <div class="w-14 h-14 bg-sky-100 rounded-2xl flex items-center justify-center text-sky-600 group-hover:scale-110 transition-transform">
              <i data-lucide="cpu" class="w-8 h-8"></i>
            </div>
            <div class="space-y-3">
              <span class="text-xs font-bold text-sky-600 uppercase tracking-widest">01 / SMART TECH</span>
              <h3 class="text-xl font-bold text-slate-900">デジタルと命の融合。<br>ドローンやAIで挑む「スマート農業」</h3>
              <p class="text-slate-600 text-sm leading-relaxed">
                今の農業は、ただの肉体労働ではありません。ドローンによる生育状況解析、AI自動給餌管理、温室のIoT環境制御など、テクノロジーを駆使して最先端の持続可能な地球と食の未来を学びます。
              </p>
            </div>
          </div>
          <div class="pt-6 mt-6 border-t border-slate-100 flex items-center justify-between text-sky-600">
            <span class="text-xs font-black tracking-wider">未来のテクノロジーを学ぶ ＞</span>
            <i data-lucide="arrow-right" class="w-4 h-4 transform group-hover:translate-x-1 transition-transform"></i>
          </div>
        </div>

        <!-- 魅力 2 -->
        <div class="group bg-slate-50 hover:bg-white rounded-3xl p-8 hover:shadow-2xl hover:shadow-slate-200/50 transition-all duration-300 border border-slate-100 flex flex-col justify-between">
          <div class="space-y-6">
            <div class="w-14 h-14 bg-emerald-100 rounded-2xl flex items-center justify-center text-emerald-600 group-hover:scale-110 transition-transform">
              <i data-lucide="shopping-bag" class="w-8 h-8"></i>
            </div>
            <div class="space-y-3">
              <span class="text-xs font-bold text-emerald-600 uppercase tracking-widest">02 / BUSINESS</span>
              <h3 class="text-xl font-bold text-slate-900">作って、プロデュースする。<br>ヒットを生み出す「ビジネスのリアル」</h3>
              <p class="text-slate-600 text-sm leading-relaxed">
                育てるだけで終わりではありません。自分たちで育てた食材を使った新商品開発、デザイン、地元大手企業との共同マーケティング、SNSを使った販路開拓まで。高校生のうちから社会経済のルールを実践で習得します。
              </p>
            </div>
          </div>
          <div class="pt-6 mt-6 border-t border-slate-100 flex items-center justify-between text-emerald-600">
            <span class="text-xs font-black tracking-wider">マーケティングの裏側を学ぶ ＞</span>
            <i data-lucide="arrow-right" class="w-4 h-4 transform group-hover:translate-x-1 transition-transform"></i>
          </div>
        </div>

        <!-- 魅力 3 -->
        <div class="group bg-slate-50 hover:bg-white rounded-3xl p-8 hover:shadow-2xl hover:shadow-slate-200/50 transition-all duration-300 border border-slate-100 flex flex-col justify-between">
          <div class="space-y-6">
            <div class="w-14 h-14 bg-rose-100 rounded-2xl flex items-center justify-center text-rose-600 group-hover:scale-110 transition-transform">
              <i data-lucide="heart" class="w-8 h-8"></i>
            </div>
            <div class="space-y-3">
              <span class="text-xs font-bold text-rose-600 uppercase tracking-widest">03 / HUMANITY</span>
              <h3 class="text-xl font-bold text-slate-900">言葉を超えた絆を育む。<br>24時間、命と向き合う「一生の感動」</h3>
              <p class="text-slate-600 text-sm leading-relaxed">
                動物たちの出産に立ち会い、新しい命の誕生をその手で迎える。日々の体調管理から食事の世話まで、言葉の通じないパートナーと全力で向き合います。ここで育まれるのは、優しさと、揺るぎない責任感。あなたの人間性を大きく成長させます。
              </p>
            </div>
          </div>
          <div class="pt-6 mt-6 border-t border-slate-100 flex items-center justify-between text-rose-600">
            <span class="text-xs font-black tracking-wider">命の温もりを体感する ＞</span>
            <i data-lucide="arrow-right" class="w-4 h-4 transform group-hover:translate-x-1 transition-transform"></i>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- 6. 学科紹介 & キャンパスライフ -->
  <section id="courses" class="py-20 bg-slate-50 border-y border-slate-100">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 space-y-16">
      
      <!-- セクション見出し -->
      <div class="text-center space-y-4">
        <span class="text-sproutGreen-600 font-bold tracking-widest text-sm uppercase block">OUR DEPARTMENTS</span>
        <h2 class="text-3xl sm:text-4xl font-black text-slate-900 tracking-tight">
          なりたい自分に合わせて選べる「3つの学科」
        </h2>
        <p class="text-slate-500 max-w-2xl mx-auto text-sm sm:text-base">
          専門性に特化した独自のカリキュラム。各分野のプロフェッショナルな教員と最新の設備が、あなたの夢をサポートします。
        </p>
      </div>

      <!-- 学科詳細 -->
      <div class="space-y-12">
        <!-- 学科 1 -->
        <div class="bg-white rounded-3xl p-6 sm:p-8 lg:p-12 shadow-sm border border-slate-100 flex flex-col lg:flex-row gap-8 items-center">
          <div class="w-full lg:w-1/2 rounded-2xl overflow-hidden aspect-video relative group">
            <img src="https://images.unsplash.com/photo-1585320806297-9794b3e4eeae?auto=format&fit=crop&q=80&w=800" alt="園芸科学科" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500">
            <span class="absolute top-4 left-4 bg-sproutGreen-600 text-white font-bold text-xs tracking-widest px-3 py-1.5 rounded-full">園芸科学科</span>
          </div>
          <div class="w-full lg:w-1/2 space-y-6">
            <div class="space-y-2">
              <span class="text-sproutGreen-600 font-bold text-sm tracking-wider">🌱 スマートグリーン・コース</span>
              <h3 class="text-2xl sm:text-3xl font-bold text-slate-900">大地から「未来の食とみどり」をクリエイトする</h3>
            </div>
            <p class="text-slate-600 leading-relaxed text-sm sm:text-base">
              最新のコンピューター温室管理システムを使い、ハイクオリティな野菜や美しい花々を栽培。バイオテクノロジーの基礎から、都市型農業・緑化デザインの可能性までを幅広く探求します。
            </p>
            <div class="bg-slate-50 p-4 rounded-xl flex items-center space-x-3">
              <i data-lucide="tag" class="w-5 h-5 text-sproutGreen-600"></i>
              <span class="text-xs sm:text-sm text-slate-500 font-medium">キーワード：IoT栽培、植物工場、バイオテクノロジー、フラワーアレンジメント</span>
            </div>
          </div>
        </div>

        <!-- 学科 2 -->
        <div class="bg-white rounded-3xl p-6 sm:p-8 lg:p-12 shadow-sm border border-slate-100 flex flex-col lg:flex-row-reverse gap-8 items-center">
          <div class="w-full lg:w-1/2 rounded-2xl overflow-hidden aspect-video relative group">
            <img src="https://images.unsplash.com/photo-1484557052118-f32bd25b45b5?auto=format&fit=crop&q=80&w=800" alt="動物科学科" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500">
            <span class="absolute top-4 left-4 bg-sky-600 text-white font-bold text-xs tracking-widest px-3 py-1.5 rounded-full">動物科学科</span>
          </div>
          <div class="w-full lg:w-1/2 space-y-6">
            <div class="space-y-2">
              <span class="text-sky-600 font-bold text-sm tracking-wider">🐑 アニマルライフ・コース</span>
              <h3 class="text-2xl sm:text-3xl font-bold text-slate-900">命の温もりに触れ、「アニマルケア」のプロへ</h3>
            </div>
            <p class="text-slate-600 leading-relaxed text-sm sm:text-base">
              牛、羊などの大動物から、犬やウサギなどの愛玩動物の飼育管理を実践。最先端の動物福祉を基軸に置き、命の尊さを学びながら、将来の獣医師、トリマー、動物看護師、飼育員としての確かなステップを築きます。
            </p>
            <div class="bg-slate-50 p-4 rounded-xl flex items-center space-x-3">
              <i data-lucide="tag" class="w-5 h-5 text-sky-600"></i>
              <span class="text-xs sm:text-sm text-slate-500 font-medium">キーワード：アニマルセラピー、乳製品加工、動物福祉学、トリミング技術</span>
            </div>
          </div>
        </div>

        <!-- 学科 3 -->
        <div class="bg-white rounded-3xl p-6 sm:p-8 lg:p-12 shadow-sm border border-slate-100 flex flex-col lg:flex-row gap-8 items-center">
          <div class="w-full lg:w-1/2 rounded-2xl overflow-hidden aspect-video relative group">
            <img src="https://images.unsplash.com/photo-1509440159596-0249088772ff?auto=format&fit=crop&q=80&w=800" alt="食品ビジネス科" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500">
            <span class="absolute top-4 left-4 bg-amber-600 text-white font-bold text-xs tracking-widest px-3 py-1.5 rounded-full">食品ビジネス科</span>
          </div>
          <div class="w-full lg:w-1/2 space-y-6">
            <div class="space-y-2">
              <span class="text-amber-600 font-bold text-sm tracking-wider">🥖 フードデザイン・コース</span>
              <h3 class="text-2xl sm:text-3xl font-bold text-slate-900">「おいしい」をデザインし、食卓の笑顔を届ける</h3>
            </div>
            <p class="text-slate-600 leading-relaxed text-sm sm:text-base">
              食品加工（製パン、製菓、醸造）の高度なプロフェッショナル技術の修得から、食の安全管理（HACCP）、商品開発プロデュース、流通ビジネス設計までを一貫して学び、「食と経済」をつなぐ次世代の人材を育成します。
            </p>
            <div class="bg-slate-50 p-4 rounded-xl flex items-center space-x-3">
              <i data-lucide="tag" class="w-5 h-5 text-amber-600"></i>
              <span class="text-xs sm:text-sm text-slate-500 font-medium">キーワード：本格製パン、食品微生物、パッケージデザイン、マーケティング</span>
            </div>
          </div>
        </div>
      </div>

      <!-- キャンパスライフ ミニギャラリー -->
      <div class="pt-8">
        <h4 class="text-center text-lg font-bold text-slate-900 mb-8 flex items-center justify-center space-x-2">
          <i data-lucide="camera" class="w-5 h-5 text-sproutGreen-600"></i>
          <span>一瞬一瞬が一生モノ！放課後＆年間イベント</span>
        </h4>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
          <div class="group relative rounded-2xl overflow-hidden aspect-square">
            <img src="https://images.unsplash.com/photo-1516253593875-bd7ba052fbc5?auto=format&fit=crop&q=80&w=450" alt="春の実習" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-300">
            <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity flex items-end p-3">
              <span class="text-white text-xs font-bold">4月：新緑の実習スタート</span>
            </div>
          </div>
          <div class="group relative rounded-2xl overflow-hidden aspect-square">
            <img src="https://images.unsplash.com/photo-1595855759920-86582396756a?auto=format&fit=crop&q=80&w=450" alt="夏の実習" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-300">
            <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity flex items-end p-3">
              <span class="text-white text-xs font-bold">7月：真夏の汗とスイカの収穫</span>
            </div>
          </div>
          <div class="group relative rounded-2xl overflow-hidden aspect-square">
            <img src="https://images.unsplash.com/photo-1530595467537-0b5996c41f2d?auto=format&fit=crop&q=80&w=450" alt="秋の農業祭" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-300">
            <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity flex items-end p-3">
              <span class="text-white text-xs font-bold">11月：大熱狂！『秋の農業祭』</span>
            </div>
          </div>
          <div class="group relative rounded-2xl overflow-hidden aspect-square">
            <img src="https://images.unsplash.com/photo-1545468117-10940cc7f164?auto=format&fit=crop&q=80&w=450" alt="冬の生命" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-300">
            <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity flex items-end p-3">
              <span class="text-white text-xs font-bold">2月：命の誕生を見守る冬</span>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>

  <!-- 7. 先輩の声 / 卒業生の進路 -->
  <section id="voices" class="py-20 bg-white">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 space-y-16">
      
      <!-- セクション見出し -->
      <div class="text-center space-y-4">
        <span class="text-agriBlue-600 font-bold tracking-widest text-sm uppercase block">VOICES & CAREER</span>
        <h2 class="text-3xl sm:text-4xl font-black text-slate-900 tracking-tight">
          「ここに来て、私の世界は180度変わった」
        </h2>
        <p class="text-slate-500 max-w-2xl mx-auto text-sm sm:text-base">
          実際に学び、夢に向かって突き進む在校生や卒業生。彼らの等身大のメッセージをご覧ください。
        </p>
      </div>

      <!-- インタビューセクション -->
      <div class="grid md:grid-cols-2 gap-8">
        <!-- 在校生の声 -->
        <div class="bg-gradient-to-b from-sproutGreen-50 to-white rounded-3xl p-8 border border-sproutGreen-100 space-y-6">
          <div class="flex items-center space-x-4">
            <div class="w-16 h-16 bg-slate-200 rounded-full overflow-hidden border-2 border-sproutGreen-500">
              <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=200" alt="在校生" class="w-full h-full object-cover">
            </div>
            <div>
              <span class="text-xs font-bold text-sproutGreen-600 block">動物科学科 2年生（非農家出身）</span>
              <span class="text-lg font-bold text-slate-900">S.K さん</span>
            </div>
          </div>
          <div class="space-y-3 relative">
            <i data-lucide="quote" class="absolute -top-3 -left-3 w-8 h-8 text-sproutGreen-200 -z-10 rotate-180"></i>
            <h3 class="text-lg font-bold text-slate-900">
              「最初は虫も触れない、動物も怖い初心者でした。でも、今は毎日学校が楽しくて仕方ない！」
            </h3>
            <p class="text-slate-600 text-sm leading-relaxed">
              中学生の頃は、机の勉強が窮屈で仕方ありませんでした。でもここなら、学んだ瞬間、目の前のヤギや牛に愛情で返ってきます。命をお世話する中で責任感が芽生え、「将来は動物看護師になりたい」という初めての夢ができました！
            </p>
          </div>
        </div>

        <!-- 卒業生の声 -->
        <div class="bg-gradient-to-b from-agriBlue-50 to-white rounded-3xl p-8 border border-agriBlue-100 space-y-6">
          <div class="flex items-center space-x-4">
            <div class="w-16 h-16 bg-slate-200 rounded-full overflow-hidden border-2 border-agriBlue-500">
              <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&q=80&w=200" alt="卒業生" class="w-full h-full object-cover">
            </div>
            <div>
              <span class="text-xs font-bold text-agriBlue-600 block">大手食品メーカー勤務（卒業3年目）</span>
              <span class="text-lg font-bold text-slate-900">T.H さん</span>
            </div>
          </div>
          <div class="space-y-3 relative">
            <i data-lucide="quote" class="absolute -top-3 -left-3 w-8 h-8 text-agriBlue-200 -z-10 rotate-180"></i>
            <h3 class="text-lg font-bold text-slate-900">
              「高校時代にゼロから商品を開発した経験。これが私のビジネスパーソンとしての強み」
            </h3>
            <p class="text-slate-600 text-sm leading-relaxed">
              地域特産の果物を使ったスイーツを開発し、地元デパートで売る。高校生としては破格の実践型カリキュラムが、普通科では絶対得られない財産です。企業採用の際にも、誰よりも熱く具体的に自分をアピールできました。
            </p>
          </div>
        </div>
      </div>

      <!-- 保護者向けキャリア実績（特に保護者モードで強調） -->
      <div id="parent-stat-box" class="bg-slate-50 rounded-3xl p-8 lg:p-12 border border-slate-100 space-y-8 transition-all duration-300">
        <div class="flex flex-col md:flex-row md:items-center justify-between gap-6">
          <div class="space-y-2">
            <span class="text-xs font-bold text-slate-400 uppercase tracking-widest">FOR PARENTS</span>
            <h3 class="text-2xl font-bold text-slate-900">就職にも進学にも強い、驚きの進路実績</h3>
            <p class="text-slate-500 text-sm">農業の知識は、あらゆる生命科学、先端IT、グローバルビジネスの基礎。多様な選択肢が拓けています。</p>
          </div>
          <div class="bg-white px-8 py-6 rounded-2xl text-center border border-slate-100 shadow-sm flex flex-col justify-center shrink-0">
            <span class="text-xs font-bold text-sproutGreen-600 block tracking-widest mb-1">5年連続</span>
            <span class="text-4xl font-black text-slate-900 tracking-tight">就職内定率 <span class="text-sproutGreen-500 text-5xl">100</span> %</span>
          </div>
        </div>

        <div class="grid sm:grid-cols-2 gap-8 pt-6 border-t border-slate-200">
          <div class="space-y-4">
            <h4 class="font-bold text-slate-900 flex items-center space-x-2">
              <i data-lucide="building" class="w-5 h-5 text-agriBlue-600"></i>
              <span>主な就職業界</span>
            </h4>
            <ul class="space-y-2 text-sm text-slate-600">
              <li class="flex items-center space-x-2"><span class="w-1.5 h-1.5 rounded-full bg-slate-400"></span> <span>大手食品メーカー（製造、開発、品質管理）</span></li>
              <li class="flex items-center space-x-2"><span class="w-1.5 h-1.5 rounded-full bg-slate-400"></span> <span>JAグループ各機関、公務員（農業職・行政職）</span></li>
              <li class="flex items-center space-x-2"><span class="w-1.5 h-1.5 rounded-full bg-slate-400"></span> <span>スマート農業、バイオベンチャー企業、ドローン開発会社</span></li>
              <li class="flex items-center space-x-2"><span class="w-1.5 h-1.5 rounded-full bg-slate-400"></span> <span>有名ホテル・観光リゾート、ペット医療機関、動物園・牧場</span></li>
            </ul>
          </div>
          <div class="space-y-4">
            <h4 class="font-bold text-slate-900 flex items-center space-x-2">
              <i data-lucide="graduation-cap" class="w-5 h-5 text-agriBlue-600"></i>
              <span>進学・キャリアアップ</span>
            </h4>
            <p class="text-sm text-slate-600 leading-relaxed">
              農業高校における「課題研究」「地域活動」の実績は、国公立大学や有名私立大学の**総合型選抜（AO入試）**において、他校の生徒に圧倒的なアドバンテージを発揮します。
              農学部、獣医学部、バイオ環境分野などへの指定校推薦枠も豊富です。
            </p>
          </div>
        </div>
      </div>

    </div>
  </section>

  <!-- 8. よくある質問（FAQ） -->
  <section id="faq" class="py-20 bg-slate-50 border-t border-slate-100">
    <div class="max-w-4xl mx-auto px-4 space-y-12">
      <!-- セクション見出し -->
      <div class="text-center space-y-4">
        <span class="text-sproutGreen-600 font-bold tracking-widest text-sm uppercase block">FAQ</span>
        <h2 class="text-3xl sm:text-4xl font-black text-slate-900 tracking-tight">
          よくあるご質問
        </h2>
        <p class="text-slate-500 text-sm sm:text-base">不安を取り除き、安心して一歩を踏み出してください。</p>
      </div>

      <!-- アコーディオン -->
      <div class="space-y-4">
        <!-- Q1 -->
        <div class="bg-white rounded-2xl border border-slate-100 shadow-sm overflow-hidden transition-all duration-300">
          <button onclick="toggleFaq(1)" class="w-full p-6 text-left flex items-center justify-between font-bold text-slate-900 gap-4 hover:bg-slate-50">
            <span class="flex items-center space-x-3 text-sm sm:text-base">
              <span class="w-8 h-8 rounded-full bg-sproutGreen-100 text-sproutGreen-700 flex items-center justify-center text-sm font-black shrink-0">Q</span>
              <span>農業の家系ではありませんが、ついていけますか？</span>
            </span>
            <i data-lucide="chevron-down" id="faq-icon-1" class="w-5 h-5 text-slate-400 transform transition-transform"></i>
          </button>
          <div id="faq-ans-1" class="hidden px-6 pb-6 pt-2 border-t border-slate-100 text-slate-600 text-sm leading-relaxed">
            <strong class="text-slate-800">まったく問題ありません！</strong> 生徒の約8割が非農家の一般家庭から入学しています。
            農機具の扱い方から、植物の植え方、動物との付き合い方まで、先生と頼れる先輩たちが「基本の『き』」からマンツーマンで指導します。スタートラインはみんなゼロからなのでご安心ください。
          </div>
        </div>

        <!-- Q2 -->
        <div class="bg-white rounded-2xl border border-slate-100 shadow-sm overflow-hidden transition-all duration-300">
          <button onclick="toggleFaq(2)" class="w-full p-6 text-left flex items-center justify-between font-bold text-slate-900 gap-4 hover:bg-slate-50">
            <span class="flex items-center space-x-3 text-sm sm:text-base">
              <span class="w-8 h-8 rounded-full bg-sproutGreen-100 text-sproutGreen-700 flex items-center justify-center text-sm font-black shrink-0">Q</span>
              <span>普通科のような、国語や英語、数学などの勉強もしますか？</span>
            </span>
            <i data-lucide="chevron-down" id="faq-icon-2" class="w-5 h-5 text-slate-400 transform transition-transform"></i>
          </button>
          <div id="faq-ans-2" class="hidden px-6 pb-6 pt-2 border-t border-slate-100 text-slate-600 text-sm leading-relaxed">
            <strong class="text-slate-800">はい、高校卒業に必要な主要一般科目もバランス良く履修します。</strong>
            さらに、専門科目にまつわる「生物（生きもの科学）」や「社会（ビジネス・流通経済）」を、農場や加工場といった『実地』と結びつけながら五感で深く理解するため、一般的な机の上の受験勉強よりも、かえって勉強がおもしろくなる生徒が数多くいます。
          </div>
        </div>

        <!-- Q3 -->
        <div class="bg-white rounded-2xl border border-slate-100 shadow-sm overflow-hidden transition-all duration-300">
          <button onclick="toggleFaq(3)" class="w-full p-6 text-left flex items-center justify-between font-bold text-slate-900 gap-4 hover:bg-slate-50">
            <span class="flex items-center space-x-3 text-sm sm:text-base">
              <span class="w-8 h-8 rounded-full bg-sproutGreen-100 text-sproutGreen-700 flex items-center justify-center text-sm font-black shrink-0">Q</span>
              <span>卒業後は、やはり全員が農業系の就職・進学になりますか？</span>
            </span>
            <i data-lucide="chevron-down" id="faq-icon-3" class="w-5 h-5 text-slate-400 transform transition-transform"></i>
          </button>
          <div id="faq-ans-3" class="hidden px-6 pb-6 pt-2 border-t border-slate-100 text-slate-600 text-sm leading-relaxed">
            <strong class="text-slate-800">いいえ、多種多様な一般業界・他学部へ進む生徒が多数です。</strong>
            「商品開発」や「流通ビジネス」の経験を武器に、一般のIT企業、広告代理店、小売サービス業、金融機関、さらに警察官や市役所といった一般公務員になる卒業生も大勢います。また、教育学部や経営学部の大学へ進学する道もあります。
          </div>
        </div>

        <!-- Q4 -->
        <div class="bg-white rounded-2xl border border-slate-100 shadow-sm overflow-hidden transition-all duration-300">
          <button onclick="toggleFaq(4)" class="w-full p-6 text-left flex items-center justify-between font-bold text-slate-900 gap-4 hover:bg-slate-50">
            <span class="flex items-center space-x-3 text-sm sm:text-base">
              <span class="w-8 h-8 rounded-full bg-sproutGreen-100 text-sproutGreen-700 flex items-center justify-center text-sm font-black shrink-0">Q</span>
              <span>体験入学には、保護者も同行した方が良いでしょうか？</span>
            </span>
            <i data-lucide="chevron-down" id="faq-icon-4" class="w-5 h-5 text-slate-400 transform transition-transform"></i>
          </button>
          <div id="faq-ans-4" class="hidden px-6 pb-6 pt-2 border-t border-slate-100 text-slate-600 text-sm leading-relaxed">
            <strong class="text-slate-800">ぜひ、ご一緒に親子でのご参加をおすすめします。</strong>
            当日は広大な農場や最先端設備を実際に見学いただき、安全への配慮、学校全体の生き生きとした明るい雰囲気を確認いただけます。また、保護者様向けの「個別進路・就職実績説明会」や、奨学金に関する専門相談ブースも同日設置いたします。
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- 9. フッター / 最終CTA -->
  <section id="apply" class="py-20 bg-gradient-to-b from-agriBlue-900 to-slate-950 text-white relative overflow-hidden">
    <!-- 背景グラフィック -->
    <div class="absolute inset-0 opacity-10 bg-[radial-gradient(#22c55e_1px,transparent_1px)] [background-size:24px_24px]"></div>
    
    <div class="max-w-4xl mx-auto px-4 relative z-10 space-y-12">
      <!-- メッセージ -->
      <div class="text-center space-y-4">
        <span class="text-sproutGreen-400 font-bold tracking-widest text-sm uppercase block">EXPERIENCE FUTURE AGRICULTURE</span>
        <h2 class="text-3xl sm:text-4xl font-black tracking-tight leading-snug">
          百聞は一見にしかず。<br>
          キミの五感で、全く新しい「放課後」を体験しよう！
        </h2>
        <p class="text-slate-300 max-w-2xl mx-auto text-sm sm:text-base">
          〇〇農業高校の新鮮な空気、動物の温もり、そして最先端のテクノロジー。<br>
          画面を眺めるだけでは伝わらない「感動」を、体験入学でお待ちしています！
        </p>
      </div>

      <!-- イベント詳細・フォーム -->
      <div class="bg-white/5 border border-white/10 rounded-3xl p-6 sm:p-10 backdrop-blur-md grid md:grid-cols-5 gap-8 items-start">
        
        <!-- イベント情報 -->
        <div class="md:col-span-2 space-y-6">
          <h3 class="text-xl font-bold text-sproutGreen-400 flex items-center space-x-2">
            <i data-lucide="calendar" class="w-5 h-5"></i>
            <span>開催概要</span>
          </h3>
          <div class="space-y-4 text-sm text-slate-200">
            <div>
              <span class="block text-xs text-slate-400 font-medium">日時</span>
              <span class="text-base font-bold text-white">〇月〇日（土）・〇月〇日（日）</span>
              <span class="block text-xs text-sproutGreen-300">10:00〜15:00（受付開始 9:30）</span>
            </div>
            <div>
              <span class="block text-xs text-slate-400 font-medium">場所</span>
              <span class="text-base font-bold text-white">〇〇農業高等学校 キャンパス</span>
              <span class="block text-xs text-slate-300">※主要駅から無料スクールバス運行あり</span>
            </div>
            <div>
              <span class="block text-xs text-slate-400 font-medium">持ち物・服装</span>
              <span class="text-sm">動きやすい服装（長ズボン推奨）、筆記用具、上履き、ワクワクする好奇心！</span>
            </div>
          </div>
        </div>

        <!-- 申し込みフォーム -->
        <div class="md:col-span-3 bg-white text-slate-800 p-6 rounded-2xl shadow-xl space-y-6">
          <h4 class="text-lg font-bold text-slate-900 border-b border-slate-100 pb-3 flex items-center justify-between">
            <span>体験入学 申し込み</span>
            <span class="text-xs bg-red-100 text-red-600 font-bold px-2 py-0.5 rounded">簡単3分</span>
          </h4>
          
          <form id="oc-form" onsubmit="handleFormSubmit(event)" class="space-y-4">
            <!-- 区分 -->
            <div>
              <label class="block text-xs font-bold text-slate-500 mb-1">お名前（ふりがな）</label>
              <div class="grid grid-cols-2 gap-2">
                <input type="text" placeholder="姓" required class="w-full px-3 py-2 border border-slate-200 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-sproutGreen-500">
                <input type="text" placeholder="名" required class="w-full px-3 py-2 border border-slate-200 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-sproutGreen-500">
              </div>
            </div>

            <!-- メールアドレス -->
            <div>
              <label class="block text-xs font-bold text-slate-500 mb-1">連絡用メールアドレス</label>
              <input type="email" placeholder="example@gmail.com" required class="w-full px-3 py-2 border border-slate-200 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-sproutGreen-500">
            </div>

            <!-- 希望学科コース -->
            <div>
              <label class="block text-xs font-bold text-slate-500 mb-1">興味のある学科（当日体験コース）</label>
              <select required class="w-full px-3 py-2 border border-slate-200 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-sproutGreen-500 bg-white">
                <option value="">体験コースを選択してください</option>
                <option value="horticulture">🌱 園芸科学科（温室＆バイオテクノロジー体験）</option>
                <option value="animal">🐑 動物科学科（ヤギ・大動物とのふれあい体験）</option>
                <option value="food">🥖 食品ビジネス科（窯焼きパン＆マーケティング体験）</option>
              </select>
            </div>

            <!-- 同伴者 -->
            <div>
              <label class="block text-xs font-bold text-slate-500 mb-1">ご同行者様</label>
              <div class="flex items-center space-x-4 text-sm mt-1">
                <label class="flex items-center space-x-1.5 cursor-pointer">
                  <input type="checkbox" name="companion" value="parent" class="w-4 h-4 text-sproutGreen-600 focus:ring-sproutGreen-500 rounded">
                  <span>保護者</span>
                </label>
                <label class="flex items-center space-x-1.5 cursor-pointer">
                  <input type="checkbox" name="companion" value="friend" class="w-4 h-4 text-sproutGreen-600 focus:ring-sproutGreen-500 rounded">
                  <span>友人</span>
                </label>
              </div>
            </div>

            <!-- ボタン -->
            <button type="submit" class="w-full bg-gradient-to-r from-sproutGreen-600 to-agriBlue-600 text-white font-bold py-3.5 px-4 rounded-xl hover:shadow-lg hover:shadow-sproutGreen-100 transition-all flex items-center justify-center space-x-2">
              <i data-lucide="check-circle" class="w-5 h-5"></i>
              <span>この内容で送信する</span>
            </button>
            <p class="text-[10px] text-slate-400 text-center leading-relaxed">※ご登録いただいた情報は、体験入学に関するご案内および個人情報の厳正な管理方針にのみ基づいて使用されます。</p>
          </form>
        </div>

      </div>
    </div>
  </section>

  <!-- 10. フッター -->
  <footer class="bg-slate-950 border-t border-slate-900 py-12 text-slate-500 text-xs text-center">
    <div class="max-w-7xl mx-auto px-4 space-y-6">
      <div class="flex flex-wrap justify-center gap-6 text-sm font-medium text-slate-400">
        <a href="#" class="hover:text-white transition-colors">学校案内HP</a>
        <a href="#" class="hover:text-white transition-colors">プライバシーポリシー</a>
        <a href="#" class="hover:text-white transition-colors">アクセスガイド</a>
        <a href="#" class="hover:text-white transition-colors">お問い合わせ</a>
      </div>
      <p class="max-w-md mx-auto text-[11px] leading-relaxed">
        〒000-0000 〇〇県〇〇市農業1-1-1<br>
        〇〇農業高等学校 事務局広報課
      </p>
      <p class="text-slate-600">© 〇〇農業高等学校 All Rights Reserved.</p>
    </div>
  </footer>

  <!-- 11. 送信完了モーダル (ブラウザのalertの代わり) -->
  <div id="success-modal" class="hidden fixed inset-0 z-50 overflow-y-auto bg-slate-900/80 backdrop-blur-sm flex items-center justify-center p-4">
    <div class="bg-white rounded-3xl p-8 max-w-md w-full shadow-2xl border border-slate-100 text-center space-y-6 transform scale-95 transition-transform">
      <div class="w-16 h-16 bg-sproutGreen-100 rounded-full flex items-center justify-center text-sproutGreen-600 mx-auto animate-bounce">
        <i data-lucide="badge-check" class="w-10 h-10"></i>
      </div>
      <div class="space-y-2">
        <h3 class="text-2xl font-black text-slate-900">申し込みが完了しました！</h3>
        <p class="text-slate-500 text-sm leading-relaxed">
          ご登録ありがとうございます。<br>
          後ほど、体験入学案内書と無料スクールバスの時刻表をメールにてお送りいたします。どうぞお楽しみに！
        </p>
      </div>
      <button onclick="closeModal()" class="w-full bg-slate-100 hover:bg-slate-200 text-slate-700 font-bold py-3 px-4 rounded-xl transition-colors">
        閉じる
      </button>
    </div>
  </div>

  <!-- JavaScriptによるインタラクション実装 -->
  <script>
    // Lucide アイコン初期化
    lucide.createIcons();

    // モバイルメニュー制御
    const mobileMenuBtn = document.getElementById('mobile-menu-btn');
    const mobileMenu = document.getElementById('mobile-menu');
    mobileMenuBtn.addEventListener('click', () => {
      mobileMenu.classList.toggle('hidden');
    });

    // 視点切り替え機能（中学生向け・保護者向け）
    function togglePerspective(mode) {
      const btnStudent = document.getElementById('btn-student');
      const btnParent = document.getElementById('btn-parent');
      
      const fvSubStudent = document.getElementById('fv-sub-student');
      const fvSubParent = document.getElementById('fv-sub-parent');
      
      const troubleTitleStudent = document.getElementById('trouble-title-student');
      const troubleTitleParent = document.getElementById('trouble-title-parent');
      
      const parentStatBox = document.getElementById('parent-stat-box');

      if (mode === 'student') {
        // ボタンのデザイン
        btnStudent.className = "flex-1 sm:flex-initial px-5 py-1.5 rounded-full font-bold transition-all duration-300 bg-white text-sproutGreen-700 shadow-sm flex items-center justify-center space-x-1.5";
        btnParent.className = "flex-1 sm:flex-initial px-5 py-1.5 rounded-full font-bold transition-all duration-300 text-slate-600 hover:text-slate-900 flex items-center justify-center space-x-1.5";
        
        // FVの切り替え
        fvSubStudent.classList.remove('hidden');
        fvSubParent.classList.add('hidden');
        
        // 共感セクション見出しの切り替え
        troubleTitleStudent.classList.remove('hidden');
        troubleTitleParent.classList.add('hidden');
        
        // 進路データ枠の演出（中学生向けは通常）
        parentStatBox.classList.remove('ring-4', 'ring-sproutGreen-500/20');
      } else {
        // ボタンのデザイン
        btnParent.className = "flex-1 sm:flex-initial px-5 py-1.5 rounded-full font-bold transition-all duration-300 bg-white text-sproutGreen-700 shadow-sm flex items-center justify-center space-x-1.5";
        btnStudent.className = "flex-1 sm:flex-initial px-5 py-1.5 rounded-full font-bold transition-all duration-300 text-slate-600 hover:text-slate-900 flex items-center justify-center space-x-1.5";
        
        // FVの切り替え
        fvSubStudent.classList.add('hidden');
        fvSubParent.classList.remove('hidden');
        
        // 共感セクション見出しの切り替え
        troubleTitleStudent.classList.add('hidden');
        troubleTitleParent.classList.remove('hidden');
        
        // 進路データ枠の演出（保護者向けに強調）
        parentStatBox.classList.add('ring-4', 'ring-sproutGreen-500/20');
      }
    }

    // FAQアコーディオン制御
    function toggleFaq(id) {
      const answer = document.getElementById(`faq-ans-${id}`);
      const icon = document.getElementById(`faq-icon-${id}`);
      
      if (answer.classList.contains('hidden')) {
        answer.classList.remove('hidden');
        icon.classList.add('rotate-180');
      } else {
        answer.classList.add('hidden');
        icon.classList.remove('rotate-180');
      }
    }

    // フォーム送信アクション
    function handleFormSubmit(event) {
      event.preventDefault(); // デフォルト動作（再読み込み）を防ぐ
      
      const modal = document.getElementById('success-modal');
      modal.classList.remove('hidden'); // モーダル表示
      
      // フォームの入力内容を初期化
      document.getElementById('oc-form').reset();
    }

    // モーダルクローズ
    function closeModal() {
      const modal = document.getElementById('success-modal');
      modal.classList.add('hidden');
    }
  </script>
</body>
</html>
