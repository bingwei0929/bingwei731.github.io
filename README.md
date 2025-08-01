<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <meta name="referrer" content="always">
    <meta name="format-detection" content="telephone=no">
    <meta name="theme-color" content="#0f172a">
    <meta property="og:type" content="article">
    <meta property="og:title" content="冰威茶话会 - 历史回顾与和平思考">
    <meta property="og:description" content="历史事件回顾与反思，珍惜和平生活">
    <title>冰威茶话会 - 历史回顾与和平思考</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.8/dist/chart.umd.min.js"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#0f172a',
                        secondary: '#1e293b',
                        accent: '#ef4444',
                        light: '#f1f5f9',
                    },
                    fontFamily: {
                        sans: ['Noto Sans SC', 'sans-serif'],
                        display: ['Noto Serif SC', 'serif'],
                    },
                }
            }
        }
    </script>
    <style type="text/tailwindcss">
        @layer utilities {
            .text-shadow {
                text-shadow: 0 2px 10px rgba(0, 0, 0, 0.7);
            }
            .text-shadow-lg {
                text-shadow: 0 4px 20px rgba(0, 0, 0, 0.9);
            }
            .bg-glass {
                background: rgba(15, 23, 42, 0.6);
                backdrop-filter: blur(12px);
                -webkit-backdrop-filter: blur(12px);
            }
            .page-transition {
                transition: transform 0.8s cubic-bezier(0.645, 0.045, 0.355, 1.000);
            }
            .history-timeline-item::before {
                content: '';
                position: absolute;
                left: -29px;
                top: 0;
                height: 100%;
                width: 2px;
                background-color: rgba(239, 68, 68, 0.5);
            }
            .history-timeline-item::after {
                content: '';
                position: absolute;
                left: -35px;
                top: 8px;
                height: 14px;
                width: 14px;
                border-radius: 50%;
                background-color: #ef4444;
            }
            .animate-fade-in {
                animation: fadeIn 1s ease-out forwards;
            }
            .animate-slide-up {
                animation: slideUp 0.8s ease-out forwards;
            }
            .animate-pulse-slow {
                animation: pulse 4s cubic-bezier(0.4, 0, 0.6, 1) infinite;
            }
            .animate-float {
                animation: float 6s ease-in-out infinite;
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
            100% { transform: translateY(0px); }
        }
    </style>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@400;500;700;900&family=Noto+Serif+SC:wght@700;900&display=swap" rel="stylesheet">
</head>
<body class="font-sans text-light overflow-x-hidden bg-primary">
    <!-- 微信打开提示 -->
    <div id="wechat-tip" class="fixed top-0 left-0 right-0 bg-accent/90 text-white p-3 text-center z-50 hidden">
        <p class="text-sm">若内容无法正常显示，请点击右上角选择"在浏览器中打开"</p>
        <button id="close-tip" class="mt-1 text-xs bg-white/20 px-2 py-1 rounded">关闭</button>
    </div>

    <!-- 背景音乐元素 -->
    <audio id="background-music" loop>
        <source src="https://music.163.com/song/media/outer/url?id=28775639.mp3" type="audio/mpeg">
        <source src="https://music.163.com/song/media/outer/url?id=5267761.mp3" type="audio/mpeg">
        <source src="https://music.163.com/song/media/outer/url?id=26301559.mp3" type="audio/mpeg">
    </audio>

    <!-- 音乐控制按钮 - 固定在右上角 -->
    <div class="fixed top-4 right-4 z-40 bg-glass p-3 rounded-full shadow-lg border border-white/20">
        <button id="music-control" class="text-white hover:text-accent transition-colors duration-300">
            <i class="fa fa-volume-off text-xl"></i>
        </button>
    </div>

    <!-- 音乐加载状态提示 -->
    <div id="music-status" class="fixed top-4 left-4 z-40 bg-glass px-4 py-2 rounded-lg shadow-lg border border-white/20 text-sm hidden">
        <span id="music-status-text">正在加载音乐...</span>
    </div>

    <!-- 动态背景 -->
    <div id="dynamic-bg" class="fixed inset-0 z-0">
        <div class="absolute inset-0 bg-gradient-to-b from-primary via-secondary to-black opacity-90"></div>
        <div class="absolute inset-0 bg-[url('https://picsum.photos/id/1036/1920/1080')] bg-cover bg-center opacity-20"></div>

        <!-- 动态粒子效果 -->
        <div class="absolute inset-0" id="particles"></div>

        <!-- 扫描线效果 -->
        <div class="absolute inset-0 overflow-hidden pointer-events-none">
            <div id="scanline" class="absolute h-1 w-full bg-accent/30 animate-pulse-slow" style="top: 0%"></div>
        </div>
    </div>

    <!-- 翻页容器 -->
    <div class="relative h-screen preserve-3d overflow-hidden">
        <!-- 第1页：封面 -->
        <div id="page-1" class="absolute inset-0 page-transition transform-gpu">
            <div class="h-full flex flex-col justify-between px-4 z-10 relative">
                <!-- 顶部装饰元素 -->
                <div class="w-full py-6 flex justify-center">
                    <div class="w-24 h-1 bg-accent/70 rounded-full"></div>
                </div>

                <!-- 主要内容 -->
                <div class="flex-1 flex flex-col justify-center">
                    <!-- 大标题 - 保留"冰威茶话会" -->
                    <div class="mb-10 animate-fade-in">
                        <h1 class="font-display font-black text-[clamp(2.5rem,12vw,6rem)] text-white leading-none text-shadow-lg tracking-tighter text-center">
                            冰威茶话会
                        </h1>
                        <div class="w-48 h-1 bg-accent mx-auto mt-3"></div>
                    </div>

                    <!-- 主题与副标题 -->
                    <div class="max-w-4xl mx-auto animate-slide-up" style="animation-delay: 0.5s">
                        <h2 class="text-[clamp(1.5rem,4vw,2.8rem)] font-bold mb-6 text-shadow text-center">
                            历史回顾与和平思考
                        </h2>
                        <p class="text-[clamp(0.9rem,2.5vw,1.2rem)] text-gray-300 mb-10 max-w-2xl mx-auto text-center">
                            历史事件回顾 · 和平理念传承 · 以史为鉴
                        </p>
                    </div>

                    <!-- 时间线摘要 -->
                    <div class="max-w-3xl mx-auto mb-12 animate-slide-up" style="animation-delay: 0.8s">
                        <div class="relative pl-10 ml-6 space-y-8">
                            <div class="history-timeline-item relative">
                                <h3 class="text-lg md:text-xl font-bold text-accent mb-2">1935年</h3>
                                <p class="text-gray-300 text-sm md:text-base">日本在哈尔滨建立秘密军事单位，进行细菌武器研究</p>
                            </div>
                            <div class="history-timeline-item relative">
                                <h3 class="text-lg md:text-xl font-bold text-accent mb-2">1937-1945年</h3>
                                <p class="text-gray-300 text-sm md:text-base">该单位对无辜平民和战俘进行不人道实验，造成大量人员伤亡</p>
                            </div>
                            <div class="history-timeline-item relative">
                                <h3 class="text-lg md:text-xl font-bold text-accent mb-2">至今</h3>
                                <p class="text-gray-300 text-sm md:text-base">历史真相需要被铭记，以史为鉴，维护世界和平与正义</p>
                            </div>
                        </div>
                    </div>

                    <!-- 纪念标语 -->
                    <div class="max-w-xl mx-auto animate-slide-up" style="animation-delay: 1.1s">
                        <div class="bg-glass/50 p-5 rounded-xl border border-white/10 backdrop-blur-sm">
                            <p class="text-center text-gray-200 italic text-sm md:text-base">
                                "忘记历史就意味着背叛，否认罪责就意味着重犯"
                            </p>
                        </div>
                    </div>
                </div>

                <!-- 翻页提示 -->
                <div class="pb-16 text-center animate-bounce">
                    <button id="next-to-page-2" class="text-white/80 hover:text-white transition-colors duration-300 flex flex-col items-center mx-auto">
                        <span class="mb-2 text-sm md:text-base">了解历史事实</span>
                        <i class="fa fa-chevron-down text-xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- 第2页：历史真相 -->
        <div id="page-2" class="absolute inset-0 page-transition transform-gpu translate-x-full">
            <div class="h-full flex flex-col">
                <!-- 页头 -->
                <div class="p-4 md:p-6 bg-glass border-b border-white/10">
                    <h2 class="text-[clamp(1.3rem,3vw,2rem)] font-display font-bold">历史事实</h2>
                </div>

                <!-- 内容区 -->
                <div class="flex-1 overflow-y-auto p-4 md:p-6">
                    <div class="max-w-6xl mx-auto space-y-10 md:space-y-16">
                        <!-- 历史概述 -->
                        <div class="animate-slide-up">
                            <div class="grid grid-cols-1 gap-6 md:grid-cols-2 md:gap-10 items-center">
                                <div>
                                    <h3 class="text-xl md:text-2xl font-bold mb-4 text-accent">历史背景与事实</h3>
                                    <p class="text-gray-300 mb-3 leading-relaxed text-sm md:text-base">
                                        20世纪30-40年代，日本军国主义在第二次世界大战期间，在中国东北建立了代号为"731"的秘密部队，对外称"关东军防疫给水部"。
                                    </p>
                                    <p class="text-gray-300 mb-3 leading-relaxed text-sm md:text-base">
                                        该部队1935年正式建立，总部位于哈尔滨平房区，占地约6平方公里，拥有3000多名工作人员，是当时规模庞大的生物武器研究基地。
                                    </p>
                                    <p class="text-gray-300 leading-relaxed text-sm md:text-base">
                                        历史研究表明，这支部队以"防疫研究"为名义，实则对活人进行残酷的生物和化学武器实验，违反了国际人道主义法。
                                    </p>
                                </div>
                                <div class="relative rounded-xl overflow-hidden shadow-2xl transform transition-all duration-700 hover:scale-[1.02]">
                                    <img src="https://picsum.photos/id/1019/800/600" alt="历史遗迹照片" class="w-full h-auto">
                                    <div class="absolute inset-0 bg-gradient-to-t from-primary/80 to-transparent"></div>
                                    <div class="absolute bottom-3 left-3 right-3 text-xs md:text-sm text-gray-200">
                                        历史遗址照片
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- 受害者情况 -->
                        <div class="animate-slide-up" style="animation-delay: 0.2s">
                            <div class="grid grid-cols-1 gap-6 md:grid-cols-2 md:gap-10 items-center md:flex-row-reverse">
                                <div>
                                    <h3 class="text-xl md:text-2xl font-bold mb-4 text-accent">历史受害者</h3>
                                    <p class="text-gray-300 mb-3 leading-relaxed text-sm md:text-base">
                                        据历史研究，该部队将实验对象称为"马路大"（日语"原木"之意），主要包括中国平民、战俘，还有朝鲜人、苏联人等。
                                    </p>
                                    <p class="text-gray-300 mb-3 leading-relaxed text-sm md:text-base">
                                        这些无辜者被迫接受了各种不人道实验，包括细菌感染、冻伤实验、毒气实验等，遭受了巨大的痛苦。
                                    </p>
                                    <p class="text-gray-300 leading-relaxed text-sm md:text-base">
                                        历史资料显示，至少有3000名无辜者在这些实验中丧生，实际数字可能更高，许多受害者甚至没有留下任何记录。
                                    </p>
                                </div>
                                <div class="relative rounded-xl overflow-hidden shadow-2xl transform transition-all duration-700 hover:scale-[1.02]">
                                    <img src="https://picsum.photos/id/1058/800/600" alt="历史纪念馆照片" class="w-full h-auto">
                                    <div class="absolute inset-0 bg-gradient-to-t from-primary/80 to-transparent"></div>
                                    <div class="absolute bottom-3 left-3 right-3 text-xs md:text-sm text-gray-200">
                                        历史纪念馆中的纪念墙
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- 历史证据 -->
                        <div class="animate-slide-up" style="animation-delay: 0.4s">
                            <h3 class="text-xl md:text-2xl font-bold mb-6 text-accent text-center">历史证据</h3>
                            <div class="grid grid-cols-1 gap-6 md:grid-cols-3 md:gap-8">
                                <div class="bg-glass p-5 rounded-xl border border-white/10 shadow-lg hover:shadow-2xl transition-all duration-500">
                                    <div class="text-accent text-3xl mb-4 text-center">
                                        <i class="fa fa-map-marker"></i>
                                    </div>
                                    <h4 class="text-base md:text-xl font-bold mb-3 text-center">遗址证据</h4>
                                    <p class="text-gray-300 text-center text-xs md:text-sm">
                                        哈尔滨平房区的遗址保存了大量实验室、监狱、焚尸炉等设施遗迹，是历史事实的直接见证。
                                    </p>
                                </div>

                                <div class="bg-glass p-5 rounded-xl border border-white/10 shadow-lg hover:shadow-2xl transition-all duration-500">
                                    <div class="text-accent text-3xl mb-4 text-center">
                                        <i class="fa fa-file-text-o"></i>
                                    </div>
                                    <h4 class="text-base md:text-xl font-bold mb-3 text-center">文献记录</h4>
                                    <p class="text-gray-300 text-center text-xs md:text-sm">
                                        大量历史文献、实验报告和战后证词，详细记录了相关历史事件的过程和结果。
                                    </p>
                                </div>

                                <div class="bg-glass p-5 rounded-xl border border-white/10 shadow-lg hover:shadow-2xl transition-all duration-500">
                                    <div class="text-accent text-3xl mb-4 text-center">
                                        <i class="fa fa-comments-o"></i>
                                    </div>
                                    <h4 class="text-base md:text-xl font-bold mb-3 text-center">证人证词</h4>
                                    <p class="text-gray-300 text-center text-xs md:text-sm">
                                        幸存者和附近居民的证词，记录了当时的历史情况和受害者的遭遇。
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- 翻页控制 -->
                <div class="p-4 md:p-6 bg-glass border-t border-white/10 flex justify-between items-center">
                    <button id="back-to-page-1" class="text-white/80 hover:text-white transition-colors duration-300 flex items-center">
                        <i class="fa fa-chevron-left mr-2"></i>
                        <span class="text-sm">返回</span>
                    </button>
                    <button id="next-to-page-3" class="text-white/80 hover:text-white transition-colors duration-300 flex items-center">
                        <span class="text-sm">和平纪念</span>
                        <i class="fa fa-chevron-right ml-2"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- 第3页：和平纪念 -->
        <div id="page-3" class="absolute inset-0 page-transition transform-gpu translate-x-full">
            <div class="h-full flex flex-col">
                <!-- 页头 -->
                <div class="p-4 md:p-6 bg-glass border-b border-white/10">
                    <h2 class="text-[clamp(1.3rem,3vw,2rem)] font-display font-bold">和平纪念</h2>
                </div>

                <!-- 内容区 -->
                <div class="flex-1 overflow-y-auto p-4 md:p-6">
                    <div class="max-w-4xl mx-auto text-center space-y-10 md:space-y-16">
                        <!-- 默哀区 -->
                        <div class="animate-slide-up">
                            <h3 class="text-xl md:text-2xl font-bold mb-8">为历史受害者默哀</h3>

                            <div class="relative mb-10">
                                <!-- 蜡烛动画 -->
                                <div class="w-28 h-64 mx-auto relative">
                                    <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-10 h-48 bg-yellow-700 rounded-t-full shadow-lg shadow-yellow-500/30"></div>
                                    <div id="flame" class="absolute top-3 left-1/2 transform -translate-x-1/2 w-6 h-10 bg-yellow-300 rounded-full blur-sm opacity-0 shadow-lg shadow-yellow-500/50"></div>
                                </div>
                            </div>

                            <!-- 计时器 -->
                            <div id="memorial-clock" class="text-4xl md:text-6xl font-black mb-8 text-white font-mono tracking-wider">
                                00:00
                            </div>

                            <!-- 默哀按钮 -->
                            <button id="mourn-button" class="bg-accent hover:bg-accent/90 text-white font-bold py-3 px-10 rounded-lg transition-all duration-300 text-sm md:text-lg mb-8 shadow-lg hover:shadow-accent/30 transform hover:scale-105">
                                <i class="fa fa-bell-o mr-2"></i>开始默哀
                            </button>

                            <!-- 默哀信息 -->
                            <div id="mourning-message" class="hidden mt-8">
                                <div class="w-24 h-24 mx-auto border-4 border-white/30 rounded-full flex items-center justify-center mb-6">
                                    <i class="fa fa-hourglass-half text-4xl text-accent"></i>
                                </div>
                                <p class="text-xl md:text-2xl italic text-gray-300">"愿逝者安息，愿历史不再重演"</p>
                            </div>
                        </div>

                        <!-- 纪念墙 -->
                        <div class="animate-slide-up" style="animation-delay: 0.3s">
                            <h3 class="text-xl md:text-2xl font-bold mb-8">历史受害者纪念</h3>

                            <div class="relative rounded-xl overflow-hidden shadow-2xl mb-6">
                                <img src="https://picsum.photos/id/1056/1200/600" alt="纪念墙" class="w-full h-auto">
                                <div class="absolute inset-0 bg-gradient-to-t from-primary/90 via-primary/40 to-transparent"></div>
                                <div class="absolute bottom-6 left-0 right-0 text-center">
                                    <p class="text-xl text-white text-shadow">我们永远不会忘记历史</p>
                                </div>
                            </div>

                            <p class="text-gray-300 max-w-2xl mx-auto leading-relaxed text-sm md:text-base">
                                每一个在战争中无辜逝去的生命都值得被铭记。他们的遭遇是人类历史上的深刻教训，提醒我们战争的残酷和人性的脆弱。
                                铭记历史，是为了缅怀逝者，更是为了防止历史悲剧重演。
                            </p>
                        </div>
                    </div>
                </div>

                <!-- 翻页控制 -->
                <div class="p-4 md:p-6 bg-glass border-t border-white/10 flex justify-between items-center">
                    <button id="back-to-page-2" class="text-white/80 hover:text-white transition-colors duration-300 flex items-center">
                        <i class="fa fa-chevron-left mr-2"></i>
                        <span class="text-sm">历史事实</span>
                    </button>
                    <button id="next-to-page-4" class="text-white/80 hover:text-white transition-colors duration-300 flex items-center">
                        <span class="text-sm">和平展望</span>
                        <i class="fa fa-chevron-right ml-2"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- 第4页：和平展望 -->
        <div id="page-4" class="absolute inset-0 page-transition transform-gpu translate-x-full">
            <div class="h-full flex flex-col">
                <!-- 页头 -->
                <div class="p-4 md:p-6 bg-glass border-b border-white/10">
                    <h2 class="text-[clamp(1.3rem,3vw,2rem)] font-display font-bold">和平展望</h2>
                </div>

                <!-- 内容区 -->
                <div class="flex-1 overflow-y-auto p-4 md:p-6">
                    <div class="max-w-6xl mx-auto space-y-10 md:space-y-16">
                        <!-- 铭记的意义 -->
                        <div class="animate-slide-up">
                            <h3 class="text-xl md:text-2xl font-bold mb-6 text-accent text-center">铭记历史的意义</h3>

                            <div class="grid grid-cols-1 gap-6 lg:grid-cols-2 lg:gap-12 items-center">
                                <div>
                                    <p class="text-gray-300 mb-4 leading-relaxed text-sm md:text-base">
                                        我们铭记这段历史，不是为了延续仇恨，而是为了以史为鉴，警惕战争悲剧重演，珍惜当下的和平生活。
                                    </p>
                                    <p class="text-gray-300 mb-4 leading-relaxed text-sm md:text-base">
                                        这段历史告诉我们，当科学失去伦理约束，当人权被肆意践踏，当军国主义思想抬头，人类将面临何等可怕的灾难。
                                    </p>
                                    <p class="text-gray-300 leading-relaxed text-sm md:text-base">
                                        只有正视历史、铭记历史，才能避免历史悲剧的重演，才能构建一个更加公正、和平的世界。
                                    </p>
                                </div>
                                <div class="relative rounded-xl overflow-hidden shadow-2xl">
                                    <img src="https://picsum.photos/id/1048/800/600" alt="和平纪念" class="w-full h-auto">
                                    <div class="absolute inset-0 bg-gradient-to-t from-primary/80 to-transparent"></div>
                                </div>
                            </div>
                        </div>

                        <!-- 行动方向 -->
                        <div class="animate-slide-up" style="animation-delay: 0.3s">
                            <h3 class="text-xl md:text-2xl font-bold mb-8 text-accent text-center">以史为鉴 开创未来</h3>

                            <div class="grid grid-cols-1 gap-6 md:grid-cols-3 md:gap-8">
                                <div class="bg-glass p-6 rounded-xl border border-white/10 shadow-lg hover:shadow-2xl transition-all duration-500 transform hover:-translate-y-2">
                                    <div class="w-16 h-16 bg-accent/20 rounded-full flex items-center justify-center mb-4 mx-auto">
                                        <i class="fa fa-flag text-accent text-3xl"></i>
                                    </div>
                                    <h4 class="text-base font-bold mb-3 text-center">传承爱国精神</h4>
                                    <p class="text-gray-300 text-center text-xs md:text-sm">
                                        传承和弘扬爱国主义精神，凝聚民族力量，为国家的强大和民族的复兴而努力，这是对历史最好的告慰。
                                    </p>
                                </div>

                                <div class="bg-glass p-6 rounded-xl border border-white/10 shadow-lg hover:shadow-2xl transition-all duration-500 transform hover:-translate-y-2">
                                    <div class="w-16 h-16 bg-accent/20 rounded-full flex items-center justify-center mb-4 mx-auto">
                                        <i class="fa fa-graduation-cap text-accent text-3xl"></i>
                                    </div>
                                    <h4 class="text-base font-bold mb-3 text-center">追求科学真理</h4>
                                    <p class="text-gray-300 text-center text-xs md:text-sm">
                                        推动科学进步的同时，坚守伦理底线，确保科技发展始终服务于人类福祉，而非成为伤害他人的工具。
                                    </p>
                                </div>

                                <div class="bg-glass p-6 rounded-xl border border-white/10 shadow-lg hover:shadow-2xl transition-all duration-500 transform hover:-translate-y-2">
                                    <div class="w-16 h-16 bg-accent/20 rounded-full flex items-center justify-center mb-4 mx-auto">
                                        <i class="fa fa-handshake-o text-accent text-3xl"></i>
                                    </div>
                                    <h4 class="text-base font-bold mb-3 text-center">维护世界和平</h4>
                                    <p class="text-gray-300 text-center text-xs md:text-sm">
                                        致力于推动国际合作，促进世界和平与发展，反对任何形式的侵略行为和战争罪行，共建人类命运共同体。
                                    </p>
                                </div>
                            </div>
                        </div>

                        <!-- 和平展望 -->
                        <div class="animate-slide-up" style="animation-delay: 0.6s">
                            <div class="bg-glass p-6 md:p-10 rounded-xl border border-white/10 shadow-xl">
                                <h3 class="text-xl md:text-2xl font-bold mb-6 text-center">珍惜和平 开创未来</h3>
                                <p class="text-gray-300 text-center max-w-3xl mx-auto text-sm md:text-base leading-relaxed">
                                    铭记历史，不是为了沉湎于过去的苦难，而是为了从中汲取力量，开创更加美好的未来。
                                    作为新时代的中国人，我们应当传承民族精神，努力学习，勤奋工作，为实现中华民族伟大复兴贡献自己的力量，
                                    让历史的悲剧永远不再重演。
                                </p>
                            </div>
                        </div>

                        <!-- 留言区 -->
                        <div class="animate-slide-up" style="animation-delay: 0.9s">
                            <h3 class="text-xl md:text-2xl font-bold mb-8 text-accent text-center">和平留言</h3>

                            <div class="max-w-4xl mx-auto">
                                <form id="message-form" class="mb-10 bg-glass p-6 rounded-xl shadow-lg border border-white/10">
                                    <div class="mb-4">
                                        <label for="name" class="block text-gray-200 font-medium mb-2 text-sm">您的姓名</label>
                                        <input type="text" id="name" class="w-full px-4 py-2 bg-white/5 border border-white/20 rounded-lg focus:outline-none focus:ring-2 focus:ring-accent focus:border-transparent transition-all duration-300 text-sm" placeholder="请输入您的姓名" required>
                                    </div>
                                    <div class="mb-4">
                                        <label for="message" class="block text-gray-200 font-medium mb-2 text-sm">您的留言</label>
                                        <textarea id="message" rows="4" class="w-full px-4 py-2 bg-white/5 border border-white/20 rounded-lg focus:outline-none focus:ring-2 focus:ring-accent focus:border-transparent transition-all duration-300 text-sm" placeholder="请留下您对和平的期盼..." required></textarea>
                                    </div>
                                    <button type="submit" class="bg-accent hover:bg-accent/90 text-white font-bold py-2 px-6 rounded-lg transition-all duration-300 transform hover:scale-105 shadow-lg text-sm">
                                        <i class="fa fa-paper-plane mr-2"></i>提交留言
                                    </button>
                                </form>

                                <div id="messages-container" class="space-y-4">
                                    <!-- 留言将通过JavaScript动态添加 -->
                                    <div class="bg-glass p-5 rounded-xl shadow-lg border border-white/10 transform transition-all duration-500 hover:shadow-xl hover:border-white/20">
                                        <div class="flex justify-between items-start mb-3">
                                            <h4 class="font-bold text-white text-base">茶话会成员</h4>
                                            <span class="text-gray-400 text-xs">今天</span>
                                        </div>
                                        <p class="text-gray-300 text-sm">铭记历史，珍惜和平，吾辈当自强！愿祖国日益强大，永远不再遭受侵略之苦。</p>
                                    </div>

                                    <div class="bg-glass p-5 rounded-xl shadow-lg border border-white/10 transform transition-all duration-500 hover:shadow-xl hover:border-white/20">
                                        <div class="flex justify-between items-start mb-3">
                                            <h4 class="font-bold text-white text-base">一位网友</h4>
                                            <span class="text-gray-400 text-xs">今天</span>
                                        </div>
                                        <p class="text-gray-300 text-sm">历史不能忘记，悲剧不能重演。愿逝者安息，愿世界和平。我们要以史为鉴，珍惜现在的和平生活，努力让国家更加强大。</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- 翻页控制 -->
                <div class="p-4 md:p-6 bg-glass border-t border-white/10 flex justify-between items-center">
                    <button id="back-to-page-3" class="text-white/80 hover:text-white transition-colors duration-300 flex items-center">
                        <i class="fa fa-chevron-left mr-2"></i>
                        <span class="text-sm">和平纪念</span>
                    </button>
                    <button id="back-to-cover" class="text-white/80 hover:text-white transition-colors duration-300 flex items-center">
                        <span class="text-sm">返回首页</span>
                        <i class="fa fa-home ml-2"></i>
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- 页脚信息 -->
    <footer class="fixed bottom-3 left-0 right-0 text-center text-gray-500 text-xs z-20 pointer-events-none">
        <p>© 冰威茶话会 - 历史回顾与和平思考</p>
    </footer>

    <script>
        // 页面加载完成后执行
        document.addEventListener('DOMContentLoaded', function() {
            // 检测是否在微信中打开
            checkWechatBrowser();

            // 音乐控制功能
            setupMusicControl();

            // 创建粒子背景
            createParticles();

            // 扫描线动画
            animateScanline();

            // 翻页功能
            setupPageNavigation();

            // 默哀功能
            setupMourningFunctionality();

            // 留言功能
            setupMessageFunctionality();
        });

        // 检测是否在微信浏览器中打开
        function checkWechatBrowser() {
            const userAgent = navigator.userAgent.toLowerCase();
            const isWechat = /micromessenger/.test(userAgent);
            const wechatTip = document.getElementById('wechat-tip');
            const closeTip = document.getElementById('close-tip');

            if (isWechat) {
                // 在微信中打开，显示提示
                wechatTip.classList.remove('hidden');

                // 关闭提示
                closeTip.addEventListener('click', function() {
                    wechatTip.classList.add('hidden');
                });
            }
        }

        // 音乐控制功能
        function setupMusicControl() {
            const music = document.getElementById('background-music');
            const musicControl = document.getElementById('music-control');
            const musicIcon = musicControl.querySelector('i');
            const musicStatus = document.getElementById('music-status');
            const musicStatusText = document.getElementById('music-status-text');
            let isPlaying = false;
            let isLoading = false;

            // 显示音乐状态
            function showMusicStatus(text, duration = 3000) {
                musicStatusText.textContent = text;
                musicStatus.classList.remove('hidden');

                if (duration) {
                    setTimeout(() => {
                        musicStatus.classList.add('hidden');
                    }, duration);
                }
            }

            // 隐藏音乐状态
            function hideMusicStatus() {
                musicStatus.classList.add('hidden');
            }

            // 尝试预加载音乐
            music.load();

            // 监听音乐加载事件
            music.addEventListener('loadedmetadata', function() {
                isLoading = false;
                showMusicStatus('音乐加载完成，点击播放', 3000);
            });

            music.addEventListener('error', function() {
                isLoading = false;
                showMusicStatus('音乐加载失败，尝试其他音源...', 3000);

                // 尝试下一个音源
                const sources = music.querySelectorAll('source');
                for (let i = 0; i < sources.length; i++) {
                    if (sources[i].src === music.currentSrc) {
                        const nextSource = sources[(i + 1) % sources.length];
                        music.src = nextSource.src;
                        music.load();
                        return;
                    }
                }
            });

            musicControl.addEventListener('click', function() {
                if (isPlaying) {
                    // 暂停音乐
                    music.pause();
                    musicIcon.classList.remove('fa-volume-up');
                    musicIcon.classList.add('fa-volume-off');
                    isPlaying = false;
                    showMusicStatus('音乐已暂停', 2000);
                } else {
                    if (isLoading) {
                        showMusicStatus('音乐正在加载中...', 2000);
                        return;
                    }

                    // 播放音乐
                    isLoading = true;
                    showMusicStatus('正在播放音乐...', 2000);

                    music.play().then(() => {
                        isLoading = false;
                        musicIcon.classList.remove('fa-volume-off');
                        musicIcon.classList.add('fa-volume-up');
                        isPlaying = true;
                        music.volume = 0.2;
                    }).catch(e => {
                        isLoading = false;
                        console.log('播放失败:', e);
                        showMusicStatus('播放失败，请尝试点击重试', 5000);
                    });
                }
            });

            // 当音乐播放状态改变时更新图标
            music.addEventListener('play', function() {
                musicIcon.classList.remove('fa-volume-off');
                musicIcon.classList.add('fa-volume-up');
                isPlaying = true;
            });

            music.addEventListener('pause', function() {
                musicIcon.classList.remove('fa-volume-up');
                musicIcon.classList.add('fa-volume-off');
                isPlaying = false;
            });

            // 自动提示
            setTimeout(() => {
                if (!isPlaying && !isLoading) {
                    showMusicStatus('点击右上角播放音乐', 5000);
                }
            }, 3000);
        }

        // 创建粒子背景
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = window.innerWidth < 768 ? 40 : 80;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');

                // 随机属性
                const size = Math.random() * 4 + 1;
                const posX = Math.random() * 100;
                const posY = Math.random() * 100;
                const duration = Math.random() * 30 + 20;
                const delay = Math.random() * 10;
                const opacity = Math.random() * 0.7 + 0.3;

                // 设置样式
                particle.style.cssText = `
                    position: absolute;
                    width: ${size}px;
                    height: ${size}px;
                    background: ${i % 5 === 0 ? 'rgba(239, 68, 68, 0.8)' : 'rgba(255, 255, 255, 0.6)'};
                    border-radius: 50%;
                    top: ${posY}%;
                    left: ${posX}%;
                    box-shadow: 0 0 ${size * 5}px ${i % 5 === 0 ? 'rgba(239, 68, 68, 0.6)' : 'rgba(255, 255, 255, 0.4)'};
                    animation: float ${duration}s ease-in-out ${delay}s infinite;
                    opacity: ${opacity};
                    z-index: 0;
                `;

                particlesContainer.appendChild(particle);
            }

            // 添加粒子浮动动画
            const style = document.createElement('style');
            style.textContent = `
                @keyframes float {
                    0% { transform: translate(0, 0) rotate(0deg); }
                    25% { transform: translate(15px, -10px) rotate(5deg); }
                    50% { transform: translate(5px, -20px) rotate(0deg); }
                    75% { transform: translate(-10px, -5px) rotate(-5deg); }
                    100% { transform: translate(0, 0) rotate(0deg); }
                }
            `;
            document.head.appendChild(style);
        }

        // 扫描线动画
        function animateScanline() {
            const scanline = document.getElementById('scanline');
            let position = 0;

            setInterval(() => {
                position = (position + 0.5) % 100;
                scanline.style.top = `${position}%`;
            }, 50);
        }

        // 翻页导航功能
        function setupPageNavigation() {
            // 页面元素
            const page1 = document.getElementById('page-1');
            const page2 = document.getElementById('page-2');
            const page3 = document.getElementById('page-3');
            const page4 = document.getElementById('page-4');

            // 按钮元素
            const nextToPage2 = document.getElementById('next-to-page-2');
            const backToPage1 = document.getElementById('back-to-page-1');
            const nextToPage3 = document.getElementById('next-to-page-3');
            const backToPage2 = document.getElementById('back-to-page-2');
            const nextToPage4 = document.getElementById('next-to-page-4');
            const backToPage3 = document.getElementById('back-to-page-3');
            const backToCover = document.getElementById('back-to-cover');

            // 翻页到第2页
            nextToPage2.addEventListener('click', () => {
                page1.style.transform = 'translateX(-100%)';
                page2.style.transform = 'translateX(0)';
                resetAnimations(page2);
            });

            // 返回第1页
            backToPage1.addEventListener('click', () => {
                page1.style.transform = 'translateX(0)';
                page2.style.transform = 'translateX(100%)';
            });

            // 翻页到第3页
            nextToPage3.addEventListener('click', () => {
                page2.style.transform = 'translateX(-100%)';
                page3.style.transform = 'translateX(0)';
                resetAnimations(page3);
            });

            // 返回第2页
            backToPage2.addEventListener('click', () => {
                page2.style.transform = 'translateX(0)';
                page3.style.transform = 'translateX(100%)';
            });

            // 翻页到第4页
            nextToPage4.addEventListener('click', () => {
                page3.style.transform = 'translateX(-100%)';
                page4.style.transform = 'translateX(0)';
                resetAnimations(page4);
            });

            // 返回第3页
            backToPage3.addEventListener('click', () => {
                page3.style.transform = 'translateX(0)';
                page4.style.transform = 'translateX(100%)';
            });

            // 返回封面
            backToCover.addEventListener('click', () => {
                page1.style.transform = 'translateX(0)';
                page4.style.transform = 'translateX(100%)';
            });

            // 重置页面动画
            function resetAnimations(page) {
                const animatedElements = page.querySelectorAll('.animate-slide-up, .animate-fade-in');
                animatedElements.forEach(el => {
                    el.style.opacity = '0';
                    if (el.classList.contains('animate-slide-up')) {
                        el.style.transform = 'translateY(50px)';
                    }

                    // 强制重绘
                    void el.offsetWidth;

                    // 重新启用动画
                    el.style.opacity = '';
                    el.style.transform = '';
                });
            }
        }

        // 默哀功能
        function setupMourningFunctionality() {
            const mournButton = document.getElementById('mourn-button');
            const memorialClock = document.getElementById('memorial-clock');
            const mourningMessage = document.getElementById('mourning-message');
            const flame = document.getElementById('flame');
            const music = document.getElementById('background-music');
            let isMourning = false;
            let countdown;
            let musicVolumeBeforeMourning;

            mournButton.addEventListener('click', function() {
                if (!isMourning) {
                    startMourning();
                } else {
                    endMourning();
                }
            });

            function startMourning() {
                isMourning = true;
                mournButton.innerHTML = '<i class="fa fa-stop mr-2"></i>结束默哀';
                mournButton.classList.remove('bg-accent', 'hover:bg-accent/90');
                mournButton.classList.add('bg-gray-600', 'hover:bg-gray-700');

                // 显示默哀信息
                mourningMessage.classList.remove('hidden');

                // 点燃蜡烛
                flame.classList.remove('opacity-0');
                flame.classList.add('animate-pulse-slow', 'opacity-100');

                // 降低或暂停背景音乐
                if (!music.paused) {
                    musicVolumeBeforeMourning = music.volume;
                    music.volume = 0.1;
                } else {
                    // 如果音乐没在播放，尝试播放
                    music.play().then(() => {
                        musicVolumeBeforeMourning = 0.2;
                        music.volume = 0.1;
                    }).catch(e => {
                        console.log('默哀时播放音乐失败:', e);
                    });
                }

                // 3分钟倒计时
                let seconds = 180;
                updateClock(seconds);

                countdown = setInterval(() => {
                    seconds--;
                    updateClock(seconds);

                    if (seconds <= 0) {
                        endMourning();
                    }
                }, 1000);

                // 页面效果变化
                document.getElementById('dynamic-bg').classList.add('grayscale');
            }

            function endMourning() {
                isMourning = false;
                clearInterval(countdown);
                mournButton.innerHTML = '<i class="fa fa-bell-o mr-2"></i>开始默哀';
                mournButton.classList.remove('bg-gray-600', 'hover:bg-gray-700');
                mournButton.classList.add('bg-accent', 'hover:bg-accent/90');

                // 隐藏默哀信息
                mourningMessage.classList.add('hidden');

                // 熄灭蜡烛
                flame.classList.remove('animate-pulse-slow', 'opacity-100');
                flame.classList.add('opacity-0');

                // 恢复背景音乐音量
                if (musicVolumeBeforeMourning !== undefined) {
                    music.volume = musicVolumeBeforeMourning;
                }

                // 恢复页面效果
                document.getElementById('dynamic-bg').classList.remove('grayscale');

                // 重置时钟
                memorialClock.textContent = '00:00';
            }

            function updateClock(seconds) {
                const minutes = Math.floor(seconds / 60);
                const remainingSeconds = seconds % 60;
                memorialClock.textContent = `${minutes.toString().padStart(2, '0')}:${remainingSeconds.toString().padStart(2, '0')}`;
            }
        }

        // 留言功能
        function setupMessageFunctionality() {
            const messageForm = document.getElementById('message-form');
            const messagesContainer = document.getElementById('messages-container');

            messageForm.addEventListener('submit', function(e) {
                e.preventDefault();

                const name = document.getElementById('name').value;
                const message = document.getElementById('message').value;

                // 创建新留言元素
                const messageElement = document.createElement('div');
                messageElement.className = 'bg-glass p-5 rounded-xl shadow-lg border border-white/10 transform transition-all duration-500 hover:shadow-xl hover:border-white/20 opacity-0 animate-fade-in';
                messageElement.innerHTML = `
                    <div class="flex justify-between items-start mb-3">
                        <h4 class="font-bold text-white text-base">${name}</h4>
                        <span class="text-gray-400 text-xs">刚刚</span>
                    </div>
                    <p class="text-gray-300 text-sm">${message}</p>
                `;

                // 添加到留言容器顶部
                messagesContainer.insertBefore(messageElement, messagesContainer.firstChild);

                // 重置表单
                messageForm.reset();

                // 显示成功提示
                alert('留言提交成功，感谢您的参与！');
            });
        }
    </script>
</body>
</html>
