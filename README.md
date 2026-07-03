<!DOCTYPE html>
<html lang="ja" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>名水が育む西条の「推し」特産品</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Alpine.js Core and Initialization (Fixed Load Order) -->
    <script>
        document.addEventListener('alpine:init', () => {
            Alpine.data('saijoApp', () => ({
                // Modals
                modalOpen: false,
                activeKey: '',
                activeItem: {},
                
                // Voting (push count simulation)
                votes: {
                    nasu: 148,
                    tea: 89,
                    persimmon: 124
                },
                voted: {
                    nasu: false,
                    tea: false,
                    persimmon: false
                },

                // Selection for Pairing Game
                selected: [],

                // Toast status
                toastShow: false,
                toastTitle: '',
                toastMsg: '',

                // Mock Data for Specialties Detailed modal
                itemsDetails: {
                    nasu: {
                        title: '絹皮ナス (きぬかわなす)',
                        img: 'image_c149a2.jpg',
                        longDesc: '「絹皮ナス」は、愛媛県西条市の肥沃な土地と、日本屈指の名水「うちぬき」によってのみ育つ伝説的なナスです。その最大の特徴は、文字通り「絹のようになめらかで、噛むことを忘れてしまうほど極薄の皮」。一般のナスに比べて灰汁が極めて少なく、果肉が驚くほど水分に満ちており、瑞々しい甘さを放ちます。収穫期には、まさに水を絞り出せるほどのみずみずしさを宿します。',
                        tip: '熱を入れすぎず、まずはシンプルに生のまま「生スライス」にし、生姜醤油や塩・極上のオリーブオイルだけでどうぞ。うちぬきの清涼な味わいがダイレクトに鼻に抜けます。あるいは、さっと冷たいお出汁に浸した「浅漬け」も最高です。'
                    },
                    tea: {
                        title: '石鎚黒茶 (いしづちくろちゃ)',
                        img: 'image_c14c84.jpg',
                        longDesc: '日本国内にわずか4例（高知の碁石茶、徳島の阿波晩茶など）しか現存しない「微生物で発酵させる希少な日本茶（後発酵茶）」のひとつ。その中でも石鎚黒茶は、カビによる好気的発酵と、乳酸菌による嫌気的二段発酵を行うという、世界的にも極めて珍しい独自のプロセスを経て生み出されます。黄金色の透き通った茶湯からは、高貴な酸味とすっきりした甘い香りが漂い、体に染み渡るような贅沢感を楽しめます。',
                        tip: '急須に茶葉を入れ、完全に沸騰した熱湯（名水「うちぬき」が最適！）を注ぎ、2分ほど置いて乳酸菌由来の高貴な酸味を引き出してください。冷やして飲むと、夏の暑い日に心からリフレッシュできる、贅沢な和の酸味ドリンクになります。'
                    },
                    persimmon: {
                        title: '愛宕柿の干し柿 (ほしがき)',
                        img: 'image_c14ca7.jpg',
                        longDesc: '西条の晩秋から初冬を代表する絶景。それは民家の軒先にびっしりと黄金色に吊るされた愛宕柿（あたごがき）の姿です。愛宕柿は元々強い渋柿ですが、皮を剥いて吊るし、石鎚山から吹き降ろす冷たく澄んだ寒風にさらすことで、劇的に変化します。渋みがすべて凝縮した上品な糖分へと転化し、果肉はまるで上質な和菓子、羊羹のようにねっとりとした質感になります。自然の気候と、職人の優しい手もみ作業が極上の「至宝の甘み」を作り出します。',
                        tip: 'そのまま渋いお茶や珈琲に合わせるのが王道ですが、薄くスライスして「クリームチーズ」や「発酵バター」を乗せてみてください。濃厚な乳脂肪分と極上の柿の甘さが、お酒（ワインや日本酒）のアテとして逆転の発想で最高のマリアージュを奏でます。'
                    }
                },

                // Pairing output calculation
                pairingMatrix: {
                    'nasu,tea': {
                        tag: '爽やか名水仕立て',
                        title: '絹皮ナスの浅漬け × 冷製石鎚黒茶',
                        description: '絹皮ナスの瑞々しい水分とわずかな塩味に、石鎚黒茶特有のフルーティーな酸味が合わさることで、まるで高原の朝を思わせる極上の清涼感が生まれます。お互いに「発酵」と「極上の水」を背景に持つ、究極に体に優しい現代的なペアリングです。',
                        scene: '暑い夏の午後のおもてなしや、食欲が落ちやすい季節の始まりに。'
                    },
                    'tea,persimmon': {
                        tag: '至高の和風マリアージュ',
                        title: '石鎚黒茶の深み × 天日干し柿の極甘',
                        description: 'これぞ西条・石鎚山麓の「伝統」が生み出した奇跡のペアリング。干し柿の、ハチミツのようになめらかで濃厚な甘みを、石鎚黒茶のすっきりとした上品な乳酸発酵の酸味がやさしく包み込みます。甘みと酸味が口の中で溶け合い、いつまでも余韻を楽しめます。',
                        scene: '澄み切った秋の夜、少し贅沢な自分へのご褒美やお茶会に。'
                    },
                    'nasu,persimmon': {
                        tag: '異色のマリアージュ（驚き）',
                        title: '絹皮ナスのグリル × 干し柿のチーズ包み',
                        description: '意外な組み合わせに見えますが、オリーブオイルでさっと香ばしくソテーした絹皮ナスのなめらかなコクと、干し柿の甘みは最高にマッチします。ここに少し塩気の効いたチーズを添えると、フレンチやイタリアンの前菜のようなモダンなひとさらに変貌します。',
                        scene: 'ワインをあける日のディナーの始まりや、特別なホームパーティーで。'
                    }
                },

                // Get pairing result for alpine template
                get currentMatch() {
                    if (this.selected.length !== 2) return {};
                    // Sort keys to look up correctly
                    const sortedKeys = [...this.selected].sort().join(',');
                    return this.pairingMatrix[sortedKeys] || {
                        tag: 'おすすめ',
                        title: '西条のおすすめ逸品',
                        description: 'この2つも、西条の水によって美しく引き立ちます。ぜひ一緒にお召し上がりください。',
                        scene: '日常を彩る特別な時間に。'
                    };
                },

                // Vote method
                vote(key) {
                    if (!this.voted[key]) {
                        this.votes[key]++;
                        this.voted[key] = true;
                        
                        // Show success toast
                        this.toastTitle = "「推し！」の応援ありがとうございました！";
                        this.toastMsg = "あなたの応援が西条市の生産者の力になります。";
                        this.toastShow = true;
                        setTimeout(() => this.toastShow = false, 4000);
                    } else {
                        // Toggle back
                        this.votes[key]--;
                        this.voted[key] = false;
                    }
                },

                // Modal control
                openModal(key) {
                    this.activeKey = key;
                    this.activeItem = this.itemsDetails[key];
                    this.modalOpen = true;
                },
                closeModal() {
                    this.modalOpen = false;
                },

                // Selector logic for pairing simulation
                toggleSelect(key) {
                    if (this.selected.includes(key)) {
                        this.selected = this.selected.filter(i => i !== key);
                    } else {
                        if (this.selected.length >= 2) {
                            // Replace the first selected item
                            this.selected.shift();
                        }
                        this.selected.push(key);
                    }
                },
                isSelected(key) {
                    return this.selected.includes(key);
                },
                resetSelect() {
                    this.selected = [];
                },

                // Share button custom feedback
                showShareAlert() {
                    this.toastTitle = "ペアリング情報をクリップボードにコピーしました！";
                    this.toastMsg = "SNSなどに貼り付けてお友達におすすめしてください。";
                    this.toastShow = true;
                    
                    // Simple clipboard action (safer for iframe context using text copy)
                    const tempText = `【西条市 特産品ペアリング推し！】「${this.currentMatch.title}」が最高！お家で試したい究極のマリアージュ。 #愛媛県西条市 #特産品 #うちぬき`;
                    const tempInput = document.createElement("input");
                    tempInput.value = tempText;
                    document.body.appendChild(tempInput);
                    tempInput.select();
                    document.execCommand("copy");
                    document.body.removeChild(tempInput);

                    setTimeout(() => this.toastShow = false, 4000);
                }
            }));
        });
    </script>
    <!-- Load Alpine.js defer after registration logic -->
    <script src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>

    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Noto Sans JP & Shippori Mincho for beautiful Japanese typography -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400;500;700&family=Shippori+Mincho:wght@400;600;700&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Noto Sans JP', 'sans-serif'],
                        serif: ['Shippori Mincho', 'serif'],
                    },
                    colors: {
                        indigo: {
                            50: '#f0f3ff',
                            900: '#1e1b4b',
                            950: '#0f0e26',
                        },
                        amber: {
                            500: '#f59e0b',
                            600: '#d97706',
                            700: '#b45309',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        .serif-title {
            font-family: 'Shippori Mincho', serif;
        }
        .bg-silk-blue {
            background-color: #0d1b2a;
        }
        /* Glassmorphism for card detailing */
        .glass-panel {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
        }
        /* Custom Keyframe Animations */
        @keyframes heartBeat {
            0% { transform: scale(1); }
            14% { transform: scale(1.1); }
            28% { transform: scale(1); }
            42% { transform: scale(1.15); }
            70% { transform: scale(1); }
        }
        .heart-beat {
            animation: heartBeat 0.8s infinite alternate ease-in-out;
        }
    </style>
</head>
<body class="bg-stone-50 text-stone-800 font-sans antialiased overflow-x-hidden" x-data="saijoApp">

    <!-- Header Navigation -->
    <header class="sticky top-0 z-50 bg-white/90 backdrop-blur-md border-b border-stone-200 transition-all duration-300">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <a href="#" class="flex items-center space-x-3">
                <div class="bg-indigo-900 text-white p-2 rounded-lg flex items-center justify-center">
                    <span class="serif-title font-bold tracking-wider text-xl">西条</span>
                </div>
                <div>
                    <span class="text-xs text-stone-500 uppercase tracking-widest block font-bold">名水うるおす都</span>
                    <span class="serif-title font-bold text-lg text-indigo-900 tracking-wide">西条の推し特産品</span>
                </div>
            </a>
            <nav class="hidden md:flex space-x-8 text-sm font-medium">
                <a href="#about" class="text-stone-600 hover:text-indigo-900 transition">西条の恵みとは</a>
                <a href="#specialties" class="text-stone-600 hover:text-indigo-900 transition">三つの極上名産</a>
                <a href="#marriage" class="text-stone-600 hover:text-indigo-900 transition font-semibold text-amber-700"><i class="fa-solid fa-wand-magic-sparkles mr-1"></i>体験マリアージュ</a>
                <a href="#community" class="text-stone-600 hover:text-indigo-900 transition">みんなの推し声</a>
            </nav>
            <div class="flex items-center space-x-3">
                <a href="#marriage" class="bg-amber-600 text-white px-4 py-2 rounded-full text-xs font-bold tracking-wider hover:bg-amber-700 transition flex items-center gap-1">
                    <i class="fa-solid fa-star"></i> 推しを組み合わせる
                </a>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="relative bg-indigo-950 text-white min-h-[85vh] flex items-center justify-center overflow-hidden py-16 px-4">
        <!-- Abstract Water Pattern Background -->
        <div class="absolute inset-0 opacity-20 pointer-events-none">
            <div class="absolute top-[-20%] left-[-20%] w-[80vw] h-[80vw] rounded-full bg-blue-500 blur-3xl animate-pulse"></div>
            <div class="absolute bottom-[-10%] right-[-10%] w-[60vw] h-[60vw] rounded-full bg-cyan-400 blur-3xl animate-pulse" style="animation-delay: 2s;"></div>
        </div>

        <div class="relative max-w-5xl mx-auto text-center z-10 space-y-8">
            <div class="inline-flex items-center space-x-2 bg-white/10 px-4 py-1.5 rounded-full text-xs sm:text-sm tracking-widest font-semibold text-blue-300 uppercase">
                <i class="fa-solid fa-droplet text-blue-400"></i>
                <span>名水百選「うちぬき」が育む奇跡</span>
            </div>
            
            <h1 class="serif-title text-4xl sm:text-6xl lg:text-7xl font-bold leading-tight tracking-wide text-stone-100">
                ひとくちで、<br class="sm:hidden">西条の美しい自然に<br class="md:hidden">出逢う。
            </h1>

            <p class="max-w-2xl mx-auto text-stone-300 text-base sm:text-lg leading-relaxed font-light">
                日本一美味しいと言われる地下水「うちぬき」が自噴する愛媛県西条市。<br class="hidden sm:inline">
                霊峰石鎚山のふもと、潤いあふれる風土が生み出した、全国に誇る「三つの自慢の逸品」をご紹介します。
            </p>

            <div class="flex flex-col sm:flex-row justify-center gap-4 pt-4">
                <a href="#specialties" class="bg-stone-100 text-indigo-950 px-8 py-3.5 rounded-full font-bold shadow-lg hover:bg-stone-200 transition text-sm tracking-wider">
                    特産品を詳しく見る <i class="fa-solid fa-arrow-down ml-2"></i>
                </a>
                <a href="#marriage" class="border border-white/30 text-white px-8 py-3.5 rounded-full font-bold hover:bg-white/10 transition text-sm tracking-wider">
                    <i class="fa-solid fa-mug-hot mr-2"></i> ペアリングを試す
                </a>
            </div>

            <!-- Stats/Floating Badges -->
            <div class="grid grid-cols-3 gap-4 max-w-lg mx-auto pt-8 text-center border-t border-white/10">
                <div>
                    <span class="block text-2xl sm:text-3xl font-extrabold text-blue-400 serif-title">NO.1</span>
                    <span class="text-xs text-stone-400">全国水の郷百選</span>
                </div>
                <div>
                    <span class="block text-2xl sm:text-3xl font-extrabold text-amber-500 serif-title">1980m</span>
                    <span class="text-xs text-stone-400">西日本最高峰 石鎚山</span>
                </div>
                <div>
                    <span class="block text-2xl sm:text-3xl font-extrabold text-emerald-400 serif-title">100%</span>
                    <span class="text-xs text-stone-400">完全自然栽培あり</span>
                </div>
            </div>
        </div>
        
        <!-- Elegant Bottom Curve -->
        <div class="absolute bottom-0 inset-x-0">
            <svg class="text-stone-50 w-full h-12 fill-current" viewBox="0 0 1440 48" preserveAspectRatio="none">
                <path d="M0,48 L1440,48 L1440,0 C1080,36 360,36 0,0 Z"></path>
            </svg>
        </div>
    </section>

    <!-- Section: About Water -->
    <section id="about" class="py-16 bg-stone-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="bg-white rounded-3xl p-8 sm:p-12 shadow-xl border border-stone-200 relative overflow-hidden">
                <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center">
                    <div class="lg:col-span-5 space-y-6">
                        <span class="text-indigo-900 font-bold tracking-widest text-sm uppercase block"><i class="fa-solid fa-droplet text-blue-500 mr-1"></i> 西条の名水「うちぬき」</span>
                        <h2 class="serif-title text-3xl sm:text-4xl font-bold text-stone-900 leading-tight">美味しい理由、すべてはここから始まる。</h2>
                        <p class="text-stone-600 leading-relaxed text-sm sm:text-base">
                            石鎚山系に降り注いだ雨や雪が、長い年月をかけて何層もの岩盤を通ってろ過され、西条平野の地下を流れます。これがいわゆる「うちぬき」と呼ばれる自噴水です。
                        </p>
                        <p class="text-stone-600 leading-relaxed text-sm sm:text-base">
                            ミネラルが適度に含まれ、クセがなく非常にまろやかな水は、瑞々しい「ナス」をふっくら育て、香りを最大限に引き出す「茶葉」を潤し、甘みを凝縮する「柿」の故郷の源泉となっています。
                        </p>
                        <div class="pt-2">
                            <span class="inline-block bg-blue-50 border border-blue-200 text-blue-800 text-xs font-bold px-3 py-1 rounded-md">
                                <i class="fa-solid fa-circle-check mr-1"></i> 昭和・平成の名水百選 連続選出
                            </span>
                        </div>
                    </div>
                    <!-- Quick Quiz/Stat Interactive Area -->
                    <div class="lg:col-span-7 bg-indigo-50/50 rounded-2xl p-6 sm:p-8 border border-indigo-100">
                        <h3 class="serif-title text-xl font-bold text-indigo-900 mb-4 flex items-center gap-2">
                            <i class="fa-solid fa-lightbulb text-amber-500"></i> 西条の「名水」プチ雑学
                        </h3>
                        <div class="space-y-4">
                            <div class="bg-white p-4 rounded-xl border border-indigo-100/50 shadow-sm transition hover:shadow-md">
                                <span class="font-bold text-xs text-indigo-900 uppercase block tracking-wider mb-1">Q. 「うちぬき」ってどういう意味？</span>
                                <p class="text-stone-600 text-xs sm:text-sm">
                                    鉄のパイプを地面に「打ち抜き」、そこに竹などを通して自噴させたことから、そのままその名水や仕組みそのものを「うちぬき」と呼んでいます。市内には今でも多数 of 自噴箇所があり、誰でも自由に飲むことができます。
                                </p>
                            </div>
                            <div class="bg-white p-4 rounded-xl border border-indigo-100/50 shadow-sm transition hover:shadow-md">
                                <span class="font-bold text-xs text-indigo-900 uppercase block tracking-wider mb-1">Q. 冬でも夏でも適温？</span>
                                <p class="text-stone-600 text-xs sm:text-sm">
                                    地下を巡って湧き出る水は、年間を通して約14〜15℃前後に保たれています。そのため夏はひんやりと冷たく、冬は心地よく温かく感じられ、農作物や人々の生活を絶えず潤し続けています。
                                </p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Main Section: The Three Specialties Showcase -->
    <section id="specialties" class="py-20 bg-stone-100 relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-16 space-y-4">
                <span class="text-xs tracking-widest font-bold text-indigo-900 bg-indigo-100 px-3 py-1 rounded-full uppercase">THE THREE PRIDES</span>
                <h2 class="serif-title text-3xl sm:text-5xl font-bold text-stone-900">
                    西条が生んだ、<br class="xs:inline md:hidden">至高の「三つ」の推し。
                </h2>
                <p class="text-stone-600 text-sm sm:text-base">
                    それぞれの写真に秘められた、美しき実力。タップ（クリック）して詳細を開き、その圧倒的なこだわりをぜひご覧ください。
                </p>
            </div>

            <!-- Grid Content -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                
                <!-- Specialty 1: Kinukawa Nasu -->
                <div class="bg-white rounded-3xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300 border border-stone-200 flex flex-col group">
                    <div class="relative overflow-hidden aspect-[16/9] bg-stone-200">
                        <img src="image_c149a2.jpg" alt="特産 絹皮ナス" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500">
                        <div class="absolute top-4 left-4 bg-indigo-900/90 text-white text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider backdrop-blur-sm">
                            夏の最高傑作
                        </div>
                    </div>
                    <div class="p-6 sm:p-8 flex-1 flex flex-col justify-between">
                        <div class="space-y-4">
                            <div class="flex justify-between items-start">
                                <div>
                                    <span class="text-xs text-stone-500 font-semibold tracking-wide">愛媛県西条市産 / 特産</span>
                                    <h3 class="serif-title text-2xl font-bold text-stone-900 mt-1">絹皮ナス (きぬかわなす)</h3>
                                </div>
                                <span class="bg-indigo-50 text-indigo-900 p-2 rounded-full text-lg"><i class="fa-solid fa-egg"></i></span>
                            </div>
                            
                            <p class="text-stone-600 text-sm leading-relaxed">
                                まるで絹のように極薄で柔らかな皮と、驚くほど高密度で極上の甘みを持つ西条の伝統ナス。ひとくち噛めば、たっぷり溜め込んだ水質日本一の「うちぬき水」がじゅわっと口いっぱいに広がります。
                            </p>

                            <!-- Mini Badges -->
                            <div class="flex flex-wrap gap-2 pt-2">
                                <span class="bg-stone-100 text-stone-800 text-xs px-2.5 py-1 rounded-full"><i class="fa-solid fa-circle text-purple-600 mr-1 text-[8px]"></i>超極薄の皮</span>
                                <span class="bg-stone-100 text-stone-800 text-xs px-2.5 py-1 rounded-full"><i class="fa-solid fa-tint text-blue-500 mr-1"></i>水分含有量抜群</span>
                                <span class="bg-stone-100 text-stone-800 text-xs px-2.5 py-1 rounded-full"><i class="fa-solid fa-cookie mr-1"></i>生でも甘い</span>
                            </div>
                        </div>

                        <!-- Interative Footer -->
                        <div class="mt-8 pt-6 border-t border-stone-100 flex items-center justify-between">
                            <button @click="openModal('nasu')" class="text-xs text-indigo-900 font-bold hover:text-indigo-950 transition flex items-center gap-1.5">
                                <i class="fa-solid fa-circle-info"></i> 美味しい食べ方・詳細
                            </button>
                            <button @click="vote('nasu')" class="flex items-center gap-1.5 bg-indigo-900 hover:bg-indigo-950 text-white px-4 py-2 rounded-full text-xs font-bold transition shadow-sm">
                                <i class="fa-solid fa-heart" :class="voted['nasu'] ? 'text-red-500 scale-125' : ''"></i> 
                                <span>推し!</span> 
                                <span class="bg-white/20 text-white rounded-md px-1.5 py-0.5 ml-1 text-[10px]" x-text="votes['nasu']"></span>
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Specialty 2: Ishizuchi Kurocha -->
                <div class="bg-white rounded-3xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300 border border-stone-200 flex flex-col group">
                    <div class="relative overflow-hidden aspect-[16/9] bg-stone-200">
                        <img src="image_c14c84.jpg" alt="石鎚黒茶" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500">
                        <div class="absolute top-4 left-4 bg-amber-700/95 text-white text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider backdrop-blur-sm">
                            日本に数例のみの幻
                        </div>
                    </div>
                    <div class="p-6 sm:p-8 flex-1 flex flex-col justify-between">
                        <div class="space-y-4">
                            <div class="flex justify-between items-start">
                                <div>
                                    <span class="text-xs text-stone-500 font-semibold tracking-wide">愛媛県 / 伝統二段発酵茶</span>
                                    <h3 class="serif-title text-2xl font-bold text-stone-900 mt-1">石鎚黒茶 (いしづちくろちゃ)</h3>
                                </div>
                                <span class="bg-amber-50 text-amber-700 p-2 rounded-full text-lg"><i class="fa-solid fa-mug-hot"></i></span>
                            </div>
                            
                            <p class="text-stone-600 text-sm leading-relaxed">
                                霊峰石鎚山の麓で伝統的に受け継がれてきた後発酵茶。カビによる一次発酵と、乳酸菌による二次発酵を行う「世界的に極めて稀な二段発酵」により、独特の澄んだ酸味と深いコクが生まれます。
                            </p>

                            <!-- Mini Badges -->
                            <div class="flex flex-wrap gap-2 pt-2">
                                <span class="bg-stone-100 text-stone-800 text-xs px-2.5 py-1 rounded-full"><i class="fa-solid fa-circle text-amber-800 mr-1 text-[8px]"></i>乳酸菌発酵</span>
                                <span class="bg-stone-100 text-stone-800 text-xs px-2.5 py-1 rounded-full"><i class="fa-solid fa-leaf text-green-600 mr-1"></i>幻の製茶技法</span>
                                <span class="bg-stone-100 text-stone-800 text-xs px-2.5 py-1 rounded-full"><i class="fa-solid fa-shield-halved text-blue-600 mr-1"></i>健康に嬉しい</span>
                            </div>
                        </div>

                        <!-- Interative Footer -->
                        <div class="mt-8 pt-6 border-t border-stone-100 flex items-center justify-between">
                            <button @click="openModal('tea')" class="text-xs text-indigo-900 font-bold hover:text-indigo-950 transition flex items-center gap-1.5">
                                <i class="fa-solid fa-circle-info"></i> 秘められた物語・詳細
                            </button>
                            <button @click="vote('tea')" class="flex items-center gap-1.5 bg-indigo-900 hover:bg-indigo-950 text-white px-4 py-2 rounded-full text-xs font-bold transition shadow-sm">
                                <i class="fa-solid fa-heart" :class="voted['tea'] ? 'text-red-500 scale-125' : ''"></i> 
                                <span>推し!</span> 
                                <span class="bg-white/20 text-white rounded-md px-1.5 py-0.5 ml-1 text-[10px]" x-text="votes['tea']"></span>
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Specialty 3: Hoshigaki (Atago Persimmon) -->
                <div class="bg-white rounded-3xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300 border border-stone-200 flex flex-col group">
                    <div class="relative overflow-hidden aspect-[16/9] bg-stone-200">
                        <img src="image_c14ca7.jpg" alt="伝統の干し柿" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500">
                        <div class="absolute top-4 left-4 bg-orange-600/95 text-white text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider backdrop-blur-sm">
                            初冬の豊かな実り
                        </div>
                    </div>
                    <div class="p-6 sm:p-8 flex-1 flex flex-col justify-between">
                        <div class="space-y-4">
                            <div class="flex justify-between items-start">
                                <div>
                                    <span class="text-xs text-stone-500 font-semibold tracking-wide">愛媛西条の里山 / 秋の風物詩</span>
                                    <h3 class="serif-title text-2xl font-bold text-stone-900 mt-1">愛宕柿の干し柿 (ほしがき)</h3>
                                </div>
                                <span class="bg-orange-50 text-orange-600 p-2 rounded-full text-lg"><i class="fa-solid fa-cookie"></i></span>
                            </div>
                            
                            <p class="text-stone-600 text-sm leading-relaxed">
                                渋柿の王様「愛宕柿（あたごがき）」を、西条の冷たい澄んだ寒風のなかでじっくり干し上げる。渋みが上品でとろけるような甘みに変わり、果肉はねっとりと極上和菓子のように洗練されます。
                            </p>

                            <!-- Mini Badges -->
                            <div class="flex flex-wrap gap-2 pt-2">
                                <span class="bg-stone-100 text-stone-800 text-xs px-2.5 py-1 rounded-full"><i class="fa-solid fa-circle text-orange-500 mr-1 text-[8px]"></i>愛宕柿を使用</span>
                                <span class="bg-stone-100 text-stone-800 text-xs px-2.5 py-1 rounded-full"><i class="fa-solid fa-wind mr-1"></i>天日・寒風干し</span>
                                <span class="bg-stone-100 text-stone-800 text-xs px-2.5 py-1 rounded-full"><i class="fa-solid fa-wand-magic-sparkles mr-1"></i>自然のとろける極甘</span>
                            </div>
                        </div>

                        <!-- Interative Footer -->
                        <div class="mt-8 pt-6 border-t border-stone-100 flex items-center justify-between">
                            <button @click="openModal('persimmon')" class="text-xs text-indigo-900 font-bold hover:text-indigo-950 transition flex items-center gap-1.5">
                                <i class="fa-solid fa-circle-info"></i> 歴史と手仕事・詳細
                            </button>
                            <button @click="vote('persimmon')" class="flex items-center gap-1.5 bg-indigo-900 hover:bg-indigo-950 text-white px-4 py-2 rounded-full text-xs font-bold transition shadow-sm">
                                <i class="fa-solid fa-heart" :class="voted['persimmon'] ? 'text-red-500 scale-125' : ''"></i> 
                                <span>推し!</span> 
                                <span class="bg-white/20 text-white rounded-md px-1.5 py-0.5 ml-1 text-[10px]" x-text="votes['persimmon']"></span>
                            </button>
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- Interactive Section: Taste Pairing Simulator -->
    <section id="marriage" class="py-20 bg-indigo-950 text-white relative">
        <!-- Decoration background -->
        <div class="absolute inset-0 bg-gradient-to-b from-indigo-900 to-indigo-950 opacity-100"></div>
        
        <div class="relative max-w-5xl mx-auto px-4 sm:px-6 lg:px-8 z-10">
            <div class="text-center max-w-3xl mx-auto mb-16 space-y-4">
                <span class="text-xs tracking-widest font-bold text-amber-400 bg-white/10 px-3 py-1 rounded-full uppercase"><i class="fa-solid fa-utensils mr-1"></i> SPECIAL INTERACTIVE EXPERIENCE</span>
                <h2 class="serif-title text-3xl sm:text-5xl font-bold text-stone-100">
                    味覚の至福マリアージュ
                </h2>
                <p class="text-indigo-200 text-sm sm:text-base">
                    西条が育んだ名産たちは、組み合わせることでさらなる極上の美味しさを引き出します。<br>
                    食材をタップ（選択）して、あなただけの「推し掛け合わせ」を体験しましょう。
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-12 gap-8 items-stretch">
                <!-- Left panel: Selection -->
                <div class="md:col-span-5 bg-white/5 border border-white/10 p-6 sm:p-8 rounded-3xl flex flex-col justify-between">
                    <div>
                        <h3 class="serif-title text-lg font-bold text-amber-400 mb-6 flex items-center gap-2">
                            <span class="flex items-center justify-center w-6 h-6 bg-amber-400 text-indigo-950 rounded-full text-xs font-bold">1</span>
                            食材を2つ選ぶ：
                        </h3>
                        
                        <div class="space-y-3">
                            <!-- Choice 1 -->
                            <button @click="toggleSelect('nasu')" 
                                    :class="isSelected('nasu') ? 'border-amber-400 bg-amber-500/10 text-white' : 'border-white/10 hover:bg-white/5 text-stone-300'"
                                    class="w-full text-left p-4 rounded-2xl border transition duration-200 flex items-center justify-between">
                                <div class="flex items-center gap-3">
                                    <div class="w-12 h-12 rounded-lg overflow-hidden bg-stone-300 flex-shrink-0">
                                        <img src="image_c149a2.jpg" alt="Nasu" class="w-full h-full object-cover">
                                    </div>
                                    <div>
                                        <span class="block font-bold text-sm">絹皮ナス</span>
                                        <span class="text-xs text-stone-400">極薄の皮とみずみずしい甘み</span>
                                    </div>
                                </div>
                                <i class="fa-solid fa-circle-check" :class="isSelected('nasu') ? 'text-amber-400' : 'text-stone-600'"></i>
                            </button>

                            <!-- Choice 2 -->
                            <button @click="toggleSelect('tea')" 
                                    :class="isSelected('tea') ? 'border-amber-400 bg-amber-500/10 text-white' : 'border-white/10 hover:bg-white/5 text-stone-300'"
                                    class="w-full text-left p-4 rounded-2xl border transition duration-200 flex items-center justify-between">
                                <div class="flex items-center gap-3">
                                    <div class="w-12 h-12 rounded-lg overflow-hidden bg-stone-300 flex-shrink-0">
                                        <img src="image_c14c84.jpg" alt="Tea" class="w-full h-full object-cover">
                                    </div>
                                    <div>
                                        <span class="block font-bold text-sm">石鎚黒茶</span>
                                        <span class="text-xs text-stone-400">酸味豊かな伝統の二段発酵茶</span>
                                    </div>
                                </div>
                                <i class="fa-solid fa-circle-check" :class="isSelected('tea') ? 'text-amber-400' : 'text-stone-600'"></i>
                            </button>

                            <!-- Choice 3 -->
                            <button @click="toggleSelect('persimmon')" 
                                    :class="isSelected('persimmon') ? 'border-amber-400 bg-amber-500/10 text-white' : 'border-white/10 hover:bg-white/5 text-stone-300'"
                                    class="w-full text-left p-4 rounded-2xl border transition duration-200 flex items-center justify-between">
                                <div class="flex items-center gap-3">
                                    <div class="w-12 h-12 rounded-lg overflow-hidden bg-stone-300 flex-shrink-0">
                                        <img src="image_c14ca7.jpg" alt="Persimmon" class="w-full h-full object-cover">
                                    </div>
                                    <div>
                                        <span class="block font-bold text-sm">干し柿（愛宕柿）</span>
                                        <span class="text-xs text-stone-400">ねっとり極上、和菓子の甘さ</span>
                                    </div>
                                </div>
                                <i class="fa-solid fa-circle-check" :class="isSelected('persimmon') ? 'text-amber-400' : 'text-stone-600'"></i>
                            </button>
                        </div>
                    </div>

                    <div class="mt-6 pt-4 border-t border-white/10 text-center text-xs text-indigo-300">
                        <i class="fa-solid fa-circle-info mr-1"></i> 一度に選択できるのは最大2つです
                    </div>
                </div>

                <!-- Right panel: Combination Result output -->
                <div class="md:col-span-7 bg-white text-indigo-950 p-6 sm:p-10 rounded-3xl flex flex-col justify-between shadow-2xl relative overflow-hidden">
                    <!-- Dynamic Wave Decoration -->
                    <div class="absolute right-0 bottom-0 opacity-10 pointer-events-none">
                        <i class="fa-solid fa-droplet text-blue-900 text-[200px]"></i>
                    </div>

                    <div class="relative z-10 h-full flex flex-col justify-between">
                        <div>
                            <h3 class="serif-title text-lg font-bold text-indigo-900 mb-6 flex items-center gap-2">
                                <span class="flex items-center justify-center w-6 h-6 bg-indigo-900 text-white rounded-full text-xs font-bold">2</span>
                                ペアリング分析結果：
                            </h3>

                            <!-- Condition: 0 items selected -->
                            <div x-show="selected.length === 0" class="py-12 text-center space-y-4">
                                <div class="text-5xl text-indigo-200 animate-bounce"><i class="fa-solid fa-wand-magic-sparkles"></i></div>
                                <p class="text-stone-500 font-medium text-sm">左側のリストから特産品を2つ選択してください。</p>
                                <p class="text-stone-400 text-xs">感動的な美食の相乗効果がここに生まれます。</p>
                            </div>

                            <!-- Condition: 1 item selected -->
                            <div x-show="selected.length === 1" class="py-12 text-center space-y-4">
                                <div class="text-5xl text-amber-400"><i class="fa-solid fa-plus-circle"></i></div>
                                <p class="text-stone-500 font-medium text-sm">もう1つの組み合わせ素材を選んでください！</p>
                                <p class="text-stone-400 text-xs">お茶とスイーツ？ それとも意外な組み合わせ？</p>
                            </div>

                            <!-- Condition: 2 items selected (Calculated match) -->
                            <div x-show="selected.length === 2" class="space-y-6" x-transition>
                                <div class="flex items-center gap-2">
                                    <span class="bg-amber-100 text-amber-800 text-xs font-bold px-3 py-1 rounded-full" x-text="currentMatch.tag"></span>
                                    <div class="flex text-amber-500 text-sm">
                                        <i class="fa-solid fa-star"></i>
                                        <i class="fa-solid fa-star"></i>
                                        <i class="fa-solid fa-star"></i>
                                        <i class="fa-solid fa-star"></i>
                                        <i class="fa-solid fa-star"></i>
                                    </div>
                                </div>
                                
                                <h4 class="serif-title text-3xl font-bold text-indigo-950 leading-tight" x-text="currentMatch.title"></h4>
                                
                                <p class="text-stone-600 text-sm sm:text-base leading-relaxed" x-text="currentMatch.description"></p>

                                <div class="bg-stone-50 p-4 rounded-xl border border-stone-200/60 space-y-2">
                                    <span class="block text-xs font-bold text-indigo-900 tracking-wider"><i class="fa-solid fa-heart-circle-check mr-1"></i> おすすめシーン：</span>
                                    <p class="text-stone-600 text-xs sm:text-sm" x-text="currentMatch.scene"></p>
                                </div>
                            </div>
                        </div>

                        <!-- Reset / Share block -->
                        <div x-show="selected.length === 2" class="mt-8 pt-6 border-t border-stone-100 flex flex-col sm:flex-row gap-3 justify-between items-center">
                            <span class="text-xs text-stone-500">
                                <i class="fa-regular fa-lightbulb"></i> 実はもう1通りの組み合わせも抜群です。
                            </span>
                            <div class="flex gap-2">
                                <button @click="resetSelect()" class="text-xs border border-stone-300 hover:bg-stone-50 text-stone-600 px-4 py-2 rounded-full font-bold transition">
                                    クリア
                                </button>
                                <button @click="showShareAlert()" class="bg-indigo-900 hover:bg-indigo-950 text-white text-xs px-4 py-2 rounded-full font-bold transition flex items-center gap-1.5">
                                    <i class="fa-solid fa-share-nodes"></i> 推しをシェアする
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Social Proof Section: User "Oshi" voice -->
    <section id="community" class="py-20 bg-stone-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-16 space-y-4">
                <span class="text-xs tracking-widest font-bold text-indigo-900 bg-indigo-100 px-3 py-1 rounded-full uppercase">USER VOICES</span>
                <h2 class="serif-title text-3xl sm:text-4xl font-bold text-stone-900">
                    みんなの「西条推し」ボイス
                </h2>
                <p class="text-stone-600 text-sm">
                    実際に西条を訪れ、あるいは取り寄せで名産に出会ったファンのリアルな絶賛の声をご紹介します。
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Testimonial 1 -->
                <div class="bg-white p-8 rounded-3xl shadow-md border border-stone-100 flex flex-col justify-between">
                    <p class="text-stone-600 italic text-sm leading-relaxed mb-6">
                        「絹皮ナスは、包丁を入れた瞬間に水分がにじみ出てくるほどみずみずしくて感動しました！浅漬けにしたのですが、皮を一切剥かなくても、口の中に全く残りません。極上の口どけとはまさにこのこと。」
                    </p>
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full bg-indigo-100 text-indigo-900 flex items-center justify-center font-bold text-xs">
                            KM
                        </div>
                        <div>
                            <span class="block font-bold text-xs text-stone-800">美食ライター / KM様</span>
                            <span class="text-[10px] text-stone-400">松山市から訪問</span>
                        </div>
                    </div>
                </div>

                <!-- Testimonial 2 -->
                <div class="bg-white p-8 rounded-3xl shadow-md border border-stone-100 flex flex-col justify-between">
                    <p class="text-stone-600 italic text-sm leading-relaxed mb-6">
                        「石鎚黒茶を初めて飲んだとき、そのフルーティーな酸味に驚きました。紅茶とも麦茶とも違う、和の極上ハーブティーのよう。干し柿と一緒にいただくのがマイブームで、最高の贅沢を味わっています。」
                    </p>
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full bg-amber-100 text-amber-800 flex items-center justify-center font-bold text-xs">
                            YK
                        </div>
                        <div>
                            <span class="block font-bold text-xs text-stone-800">日本茶ソムリエ / YK様</span>
                            <span class="text-[10px] text-stone-400">東京都からお取り寄せ</span>
                        </div>
                    </div>
                </div>

                <!-- Testimonial 3 -->
                <div class="bg-white p-8 rounded-3xl shadow-md border border-stone-100 flex flex-col justify-between">
                    <p class="text-stone-600 italic text-sm leading-relaxed mb-6">
                        「軒先にずらりと吊るされた愛宕柿。西条の里山の冬景色はいつ見ても絵になります。その干し柿は、外はカリッ、中はトロトロ。自然の力だけでこれほど芳醇なハチミツのような甘さになるのが不思議です。」
                    </p>
                    <div class="flex items-center gap-3">
                        <div class="w-10 h-10 rounded-full bg-orange-100 text-orange-600 flex items-center justify-center font-bold text-xs">
                            ST
                        </div>
                        <div>
                            <span class="block font-bold text-xs text-stone-800">写真家 / ST様</span>
                            <span class="text-[10px] text-stone-400">西条市在住</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer with informative links and local disclaimer -->
    <footer class="bg-stone-900 text-stone-400 py-12 border-t border-stone-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center space-y-6">
            <div class="serif-title text-2xl font-bold text-white tracking-widest flex items-center justify-center gap-2">
                <i class="fa-solid fa-droplet text-blue-500"></i>
                <span>愛媛県西条市 特産品推し紹介</span>
            </div>
            <p class="max-w-md mx-auto text-xs leading-relaxed text-stone-500">
                本特産紹介サイトは、西条市が誇る最高峰の恵み「絹皮ナス」「石鎚黒茶」「愛宕柿の干し柿」の素晴らしさを多くの方へ届けるために制作された特別ビジュアルサイトです。
            </p>
            <div class="flex justify-center space-x-6 text-sm">
                <a href="#about" class="hover:text-white transition">名水うちぬきについて</a>
                <a href="#specialties" class="hover:text-white transition">極上名産</a>
                <a href="#marriage" class="hover:text-white transition">マリアージュ体験</a>
            </div>
            <p class="text-[10px] text-stone-600">
                &copy; 2026 Saijo City specialty promotion group. All rights reserved. Built beautifully.
            </p>
        </div>
    </footer>


    <!-- ================= MODALS SECTION ================= -->
    
    <!-- Custom Modal Backdrop -->
    <div x-show="modalOpen" 
         class="fixed inset-0 z-50 overflow-y-auto flex items-center justify-center p-4 bg-stone-900/80 backdrop-blur-sm"
         x-transition
         style="display: none;">
        
        <!-- Modal Content Box -->
        <div class="bg-white rounded-3xl max-w-lg w-full overflow-hidden shadow-2xl border border-stone-200"
             @click.away="closeModal()">
            
            <!-- Image Header inside Modal -->
            <div class="relative h-48 bg-stone-300">
                <img :src="activeItem.img" alt="Active modal crop" class="w-full h-full object-cover">
                <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
                <h3 class="absolute bottom-4 left-6 serif-title text-2xl font-bold text-white" x-text="activeItem.title"></h3>
                <button @click="closeModal()" class="absolute top-4 right-4 bg-black/40 text-white hover:bg-black/60 w-8 h-8 rounded-full flex items-center justify-center transition">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>

            <!-- Content Area -->
            <div class="p-6 sm:p-8 space-y-6">
                <div>
                    <span class="text-xs text-indigo-900 uppercase tracking-widest font-bold block mb-1">西条ならではのこだわり</span>
                    <p class="text-stone-600 text-sm leading-relaxed" x-text="activeItem.longDesc"></p>
                </div>

                <!-- Highlight Box -->
                <div class="bg-stone-50 p-4 rounded-2xl border border-stone-200/80 space-y-2">
                    <span class="text-xs font-bold text-stone-800 flex items-center gap-1.5">
                        <i class="fa-solid fa-star text-amber-500"></i>
                        <span>美味しい食べ方・コツ：</span>
                    </span>
                    <p class="text-stone-600 text-xs leading-relaxed" x-text="activeItem.tip"></p>
                </div>

                <!-- Footer with Vote button inside Modal -->
                <div class="flex items-center justify-between pt-4 border-t border-stone-100">
                    <span class="text-xs text-stone-400">水質日本一の西条の恵み</span>
                    <button @click="vote(activeKey); closeModal()" class="flex items-center gap-1.5 bg-indigo-900 hover:bg-indigo-950 text-white px-5 py-2.5 rounded-full text-xs font-bold transition shadow">
                        <i class="fa-solid fa-heart"></i>
                        <span>この品を推す！</span>
                    </button>
                </div>
            </div>
        </div>
    </div>


    <!-- Custom Toast Alert -->
    <div x-show="toastShow" 
         class="fixed bottom-6 right-6 z-50 bg-indigo-900 text-white px-5 py-3.5 rounded-2xl shadow-xl flex items-center gap-3 border border-indigo-800/50"
         x-transition
         style="display: none;">
        <span class="bg-amber-400 text-indigo-950 p-1.5 rounded-lg text-xs flex items-center justify-center"><i class="fa-solid fa-heart-circle-check"></i></span>
        <div>
            <span class="block font-bold text-xs" x-text="toastTitle"></span>
            <span class="text-[10px] text-indigo-200" x-text="toastMsg"></span>
        </div>
    </div>

</body>
</html>
