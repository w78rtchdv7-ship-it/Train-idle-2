#   
<!DOCTYPE html>  
<html lang="ja">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>QUANTUM LOOP RAIL // OS v7.2 [CYBERPUNK HOLOGRAPHIC EDITION]</title>  
    <script src="https://cdn.tailwindcss.com"></script>  
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;800;900&family=Share+Tech+Mono&display=swap" rel="stylesheet">  
    <style>  
        body {  
            font-family: 'Share Tech Mono', monospace;  
            background: radial-gradient(circle at center, #0a061e 0%, #03030c 100%);  
            color: #e2e8f0;  
            overflow-x: hidden;  
        }  
        .font-orbitron { font-family: 'Orbitron', sans-serif; }  
        .cyber-glow-cyan { text-shadow: 0 0 10px rgba(0, 240, 255, 0.8), 0 0 20px rgba(0, 240, 255, 0.4); }  
        .cyber-glow-purple { text-shadow: 0 0 10px rgba(217, 70, 239, 0.8), 0 0 20px rgba(217, 70, 239, 0.4); }  
        .cyber-card {  
            background: rgba(10, 10, 30, 0.7);  
            backdrop-filter: blur(12px);  
            border: 1px solid rgba(0, 240, 255, 0.25);  
            box-shadow: 0 0 20px rgba(0, 240, 255, 0.08) inset, 0 0 15px rgba(0, 240, 255, 0.1);  
        }  
        .cyber-card-purple {  
            background: rgba(20, 10, 35, 0.7);  
            backdrop-filter: blur(12px);  
            border: 1px solid rgba(217, 70, 239, 0.3);  
            box-shadow: 0 0 20px rgba(217, 70, 239, 0.08) inset, 0 0 15px rgba(217, 70, 239, 0.15);  
        }  
        .cyber-btn {  
            background: linear-gradient(135deg, rgba(0, 240, 255, 0.15) 0%, rgba(59, 130, 246, 0.3) 100%);  
            border: 1px solid rgba(0, 240, 255, 0.5);  
            transition: all 0.2s ease;  
        }  
        .cyber-btn:hover {  
            background: linear-gradient(135deg, rgba(0, 240, 255, 0.3) 0%, rgba(59, 130, 246, 0.5) 100%);  
            box-shadow: 0 0 15px rgba(0, 240, 255, 0.6);  
            color: #fff;  
        }  
        .cyber-btn-purple {  
            background: linear-gradient(135deg, rgba(217, 70, 239, 0.15) 0%, rgba(147, 51, 234, 0.3) 100%);  
            border: 1px solid rgba(217, 70, 239, 0.5);  
            transition: all 0.2s ease;  
        }  
        .cyber-btn-purple:hover {  
            background: linear-gradient(135deg, rgba(217, 70, 239, 0.3) 0%, rgba(147, 51, 234, 0.5) 100%);  
            box-shadow: 0 0 15px rgba(217, 70, 239, 0.6);  
            color: #fff;  
        }  
        ::-webkit-scrollbar { width: 6px; height: 6px; }  
        ::-webkit-scrollbar-track { background: #03030c; }  
        ::-webkit-scrollbar-thumb { background: #00f0ff44; border-radius: 3px; }  
        ::-webkit-scrollbar-thumb:hover { background: #00f0ffaa; }  
    </style>  
</head>  
<body class="min-h-screen flex flex-col select-none">  
  
    <!-- TOP HEADER / STATUS BAR -->  
    <header class="bg-[#050314]/90 border-b border-cyan-500/30 p-4 sticky top-0 z-50 backdrop-blur-md">  
        <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-4">  
            <div>  
                <h1 class="font-orbitron text-2xl font-black tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-blue-500 to-purple-500 cyber-glow-cyan">  
                    QUANTUM LOOP RAIL <span class="text-xs text-cyan-400 font-normal px-2 py-0.5 border border-cyan-500/40 rounded bg-cyan-950/40">OS v7.2 HOLOGRAPHIC</span>  
                </h1>  
                <p id="active-challenge-banner" class="text-xs text-amber-400 mt-1 hidden font-bold animate-pulse tracking-wider">⚠️ ACTIVE CHALLENGE: <span id="banner-ic-name"></span></p>  
            </div>  
              
            <div class="flex items-center gap-6 bg-[#03030c]/80 px-6 py-2.5 rounded-xl border border-cyan-500/30 shadow-[0_0_20px_rgba(0,240,255,0.15)_inset]">  
                <div class="text-center">  
                    <div class="text-[10px] text-cyan-400 font-orbitron tracking-wider">TOTAL SCORE</div>  
                    <div id="header-score" class="text-xl font-bold font-orbitron text-cyan-100 cyber-glow-cyan">0.00 円</div>  
                </div>  
                <div class="h-8 w-[1px] bg-cyan-500/30"></div>  
                <div class="text-center">  
                    <div class="text-[10px] text-purple-400 font-orbitron tracking-wider">INFINITY POINTS</div>  
                    <div id="header-ip" class="text-xl font-bold font-orbitron text-purple-200 cyber-glow-purple">0 IP</div>  
                </div>  
            </div>  
  
            <div class="flex gap-2">  
                <button onclick="saveGame()" class="px-3 py-1.5 cyber-btn text-cyan-300 rounded text-xs font-orbitron font-bold">SAVE</button>  
                <button onclick="exportSave()" class="px-3 py-1.5 cyber-btn text-cyan-300 rounded text-xs font-orbitron font-bold">EXPORT</button>  
                <button onclick="importSave()" class="px-3 py-1.5 cyber-btn text-cyan-300 rounded text-xs font-orbitron font-bold">IMPORT</button>  
            </div>  
        </div>  
    </header>  
  
    <!-- MAIN CONTENT GRID -->  
    <main class="max-w-7xl mx-auto w-full p-4 grid grid-cols-1 lg:grid-cols-12 gap-4 flex-grow">  
          
        <!-- LEFT: HOLOGRAPHIC VISUALIZATION & TABS (7 Cols) -->  
        <div class="lg:col-span-7 flex flex-col gap-4">  
            <div class="cyber-card rounded-2xl p-4 relative overflow-hidden flex flex-col items-center">  
                <div class="w-full flex justify-between items-center mb-2">  
                    <span class="font-orbitron text-xs text-cyan-400 tracking-wider">HOLOGRAPHIC RAILWAY NETWORK</span>  
                    <span id="network-status" class="text-xs text-cyan-300 font-bold tracking-widest">● PLASMA FIELD ACTIVE</span>  
                </div>  
                <div class="relative w-full aspect-square max-w-[420px] flex items-center justify-center">  
                    <canvas id="rail-canvas" width="400" height="400" class="w-full h-full rounded-xl bg-[#020208] border border-cyan-500/40 shadow-[0_0_30px_rgba(0,240,255,0.2)]"></canvas>  
                </div>  
            </div>  
  
            <!-- TAB NAVIGATION -->  
            <div class="flex cyber-card p-1.5 rounded-xl gap-1 font-orbitron text-xs">  
                <button onclick="switchTab('lines')" id="tab-btn-lines" class="flex-1 py-2.5 rounded-lg bg-cyan-600/80 text-white font-bold transition shadow-[0_0_15px_rgba(0,240,255,0.5)]">LINES</button>  
                <button onclick="switchTab('prestige')" id="tab-btn-prestige" class="flex-1 py-2.5 rounded-lg text-slate-400 hover:text-white transition">PRESTIGE</button>  
                <button onclick="switchTab('promotion')" id="tab-btn-promotion" class="flex-1 py-2.5 rounded-lg text-slate-400 hover:text-white transition">PROMOTION</button>  
                <button onclick="switchTab('infinity')" id="tab-btn-infinity" class="flex-1 py-2.5 rounded-lg text-purple-300 hover:text-white transition">INFINITY</button>  
            </div>  
        </div>  
  
        <!-- RIGHT: PANELS & UPGRADES (5 Cols) -->  
        <div class="lg:col-span-5 flex flex-col gap-4">  
              
            <!-- TAB: LINES -->  
            <div id="tab-lines" class="tab-content flex flex-col gap-3">  
                <div class="flex justify-between items-center px-1">  
                    <h2 class="font-orbitron text-sm font-bold text-cyan-400 cyber-glow-cyan">RAILWAY LINES</h2>  
                    <button onclick="maxAllLines()" class="px-3 py-1.5 cyber-btn text-cyan-300 rounded text-xs font-orbitron font-bold">MAX ALL</button>  
                </div>  
                <div id="lines-container" class="flex flex-col gap-2.5 max-h-[550px] overflow-y-auto pr-1">  
                    <!-- Dynamic Lines Generated via JS -->  
                </div>  
            </div>  
  
            <!-- TAB: PRESTIGE -->  
            <div id="tab-prestige" class="tab-content hidden flex flex-col gap-4 cyber-card p-5 rounded-2xl">  
                <h2 class="font-orbitron text-sm font-bold text-cyan-400 cyber-glow-cyan">MODERNIZATION & PRESTIGE</h2>  
                <p class="text-xs text-slate-300 leading-relaxed">  
                    累計スコアを元に現代化（Prestige）を実行すると、すべての路線がリセットされる代わりに、永続的な**P.倍率**と**P.指数（^pExp）**を獲得します。  
                </p>  
                <div class="bg-[#03030c] p-4 rounded-xl border border-cyan-500/30 flex flex-col gap-2.5 shadow-inner">  
                    <div class="flex justify-between text-xs"><span class="text-slate-400">現在のP.倍率:</span><span id="pres-mult-val" class="font-bold text-cyan-300">×1.00</span></div>  
                    <div class="flex justify-between text-xs"><span class="text-slate-400">現在のP.指数:</span><span id="pres-exp-val" class="font-bold text-cyan-300">^1.030</span></div>  
                    <div class="flex justify-between text-xs"><span class="text-slate-400">次回獲得予定P.倍率:</span><span id="pres-next-val" class="font-bold text-green-400">×1.00</span></div>  
                </div>  
                <button onclick="doPrestige()" id="pres-btn" class="w-full py-3 cyber-btn text-white font-orbitron font-bold rounded-xl transition opacity-50 cursor-not-allowed shadow-[0_0_20px_rgba(0,240,255,0.3)]">  
                    MODERNIZATION (REQUIRE: 1.00e10 円)  
                </button>  
            </div>  
  
            <!-- TAB: PROMOTION -->  
            <div id="tab-promotion" class="tab-content hidden flex flex-col gap-3">  
                <div class="flex justify-between items-center px-1">  
                    <h2 class="font-orbitron text-sm font-bold text-cyan-400 cyber-glow-cyan">STRATEGIC PROMOTION</h2>  
                    <div class="text-xs text-amber-400 font-bold font-orbitron">EXP: <span id="promo-exp-display">0.00</span></div>  
                </div>  
                <p class="text-xs text-slate-400 px-1">P.倍率×13,319到達で解放。#1をLv.3にするまで#2〜#4はロックされます。</p>  
                <div id="promotions-container" class="flex flex-col gap-3">  
                    <!-- Dynamic Promotions -->  
                </div>  
            </div>  
  
            <!-- TAB: INFINITY -->  
            <div id="tab-infinity" class="tab-content hidden flex flex-col gap-4">  
                <div class="flex cyber-card-purple p-1 rounded-xl font-orbitron text-[10px] gap-1">  
                    <button onclick="switchInfTab('upgrades')" id="inf-tab-upgrades" class="flex-1 py-2 rounded-lg bg-purple-950/80 text-purple-200 font-bold transition shadow-[0_0_10px_rgba(217,70,239,0.5)]">UPGRADES</button>  
                    <button onclick="switchInfTab('generators')" id="inf-tab-generators" class="flex-1 py-2 rounded-lg text-slate-400 hover:text-white transition">GENERATORS</button>  
                    <button onclick="switchInfTab('challenges')" id="inf-tab-challenges" class="flex-1 py-2 rounded-lg text-slate-400 hover:text-white transition">CHALLENGES</button>  
                </div>  
  
                <!-- INFINITY ACTION BOX -->  
                <div class="cyber-card-purple p-4 rounded-2xl flex flex-col gap-3">  
                    <div class="flex justify-between items-center">  
                        <div>  
                            <div class="text-xs font-orbitron text-purple-400">INFINITY CORE</div>  
                            <div class="text-lg font-bold font-orbitron text-purple-200 cyber-glow-purple" id="inf-ip-display">0.00 IP</div>  
                        </div>  
                        <div id="break-inf-container" class="hidden flex items-center gap-2">  
                            <span class="text-[10px] font-orbitron text-cyan-400">BREAK INF:</span>  
                            <button onclick="toggleBreakInfinity()" id="break-inf-btn" class="px-2.5 py-1 bg-red-950 text-red-400 border border-red-500/50 rounded-lg text-xs font-orbitron font-bold">OFF</button>  
                        </div>  
                    </div>  
                    <button onclick="doInfinity()" id="inf-btn" class="w-full py-2.5 cyber-btn-purple text-white font-orbitron font-bold rounded-xl transition opacity-50 cursor-not-allowed text-xs shadow-[0_0_20px_rgba(217,70,239,0.3)]">  
                        EXECUTE INFINITY (REQUISITE: 1.80e308 円)  
                    </button>  
                </div>  
  
                <!-- SUB-TAB: UPGRADES -->  
                <div id="inf-sub-upgrades" class="inf-sub-content flex flex-col gap-2.5 max-h-[380px] overflow-y-auto pr-1">  
                    <!-- Dynamic Inf Upgrades -->  
                </div>  
  
                <!-- SUB-TAB: GENERATORS -->  
                <div id="inf-sub-generators" class="inf-sub-content hidden flex flex-col gap-2.5 max-h-[380px] overflow-y-auto pr-1">  
                    <div class="cyber-card-purple p-3.5 rounded-xl flex justify-between items-center">  
                        <span class="text-xs font-orbitron text-purple-300">GP MULTIPLIER:</span>  
                        <span id="gp-mult-display" class="font-bold text-cyan-300 font-orbitron cyber-glow-cyan">×1.00</span>  
                    </div>  
                    <div id="generators-container" class="flex flex-col gap-2.5">  
                        <!-- Dynamic Generators -->  
                    </div>  
                </div>  
  
                <!-- SUB-TAB: CHALLENGES -->  
                <div id="inf-sub-challenges" class="inf-sub-content hidden flex flex-col gap-2.5 max-h-[380px] overflow-y-auto pr-1">  
                    <div class="text-xs text-slate-300 px-1">全9種のチャレンジクリア総時間に応じてインフィニティ倍率が強化されます。</div>  
                    <div class="cyber-card-purple p-3.5 rounded-xl flex justify-between items-center">  
                        <span class="text-xs font-orbitron text-purple-300">TOTAL IC TIME:</span>  
                        <span id="total-ic-time-display" class="font-bold text-cyan-300 font-orbitron">---</span>  
                    </div>  
                    <div id="challenges-container" class="flex flex-col gap-2.5">  
                        <!-- Dynamic Challenges -->  
                    </div>  
                </div>  
            </div>  
  
        </div>  
    </main>  
  
    <!-- FOOTER ACHIEVEMENTS / INFO -->  
    <footer class="max-w-7xl mx-auto w-full p-4 mt-auto">  
        <div class="cyber-card rounded-2xl p-4 flex flex-col gap-2.5">  
            <div class="flex justify-between items-center">  
                <span class="font-orbitron text-xs text-cyan-400 cyber-glow-cyan">ACHIEVEMENTS (<span id="ach-count">0</span>/28)</span>  
                <span id="latest-ach" class="text-xs text-amber-300 italic font-orbitron">最新未達成: すべての始まり</span>  
            </div>  
            <div id="achievements-grid" class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-7 gap-2">  
                <!-- Achievements generated via JS -->  
            </div>  
        </div>  
    </footer>  
  
    <!-- JAVASCRIPT GAME ENGINE -->  
    <script>  
        const LINE_NAMES = [  
            "東京環状高速鉄道（山手スカイライン）",  
            "中央横断リニアエクスプレス",  
            "東海道メガロポリス超特急",  
            "環太平洋グリーンベルト線",  
            "ユーラシア大陸横断鉄道",  
            "ベーリング海峡海底トンネル線",  
            "北極圏オーロラ周回鉄道",  
            "成層圏エレベーター連絡線",  
            "静止軌道リング・エクスプレス",  
            "銀河系外縁・次元環状線"  
        ];  
        const LINE_COLORS = ["#ef4444", "#f97316", "#eab308", "#22c55e", "#06b6d4", "#3b82f6", "#6366f1", "#a855f7", "#ec4899", "#f8fafc"];  
  
        const PROMOTIONS_DEF = [  
            { id: 1, name: "倍率獲得倍率", desc: "全路線のベース倍率を強化する", baseCost: 1 },  
            { id: 2, name: "ラップ速度倍率", desc: "電車の周回速度を加速する", baseCost: 2 },  
            { id: 3, name: "アセンションパワー", desc: "アセンション（近代化）効果を増幅する", baseCost: 3 },  
            { id: 4, name: "プロモーションパワー", desc: "プロモーション効率を底上げする", baseCost: 4 }  
        ];  
  
        const INF_UPGRADES_DEF = [  
            { id: "q_sync", name: "量子軌道同期", desc: "全路線の倍率獲得量を永続的に×3.0倍にする", cost: 1 },  
            { id: "mag_drive", name: "超伝導リニア駆動", desc: "全路線の周回速度を永続的に×1.5倍にする", cost: 2 },  
            { id: "auto_line", name: "オートバイヤー：路線レベル", desc: "毎秒自動で全路線のレベルを購入する機能", cost: 5 },  
            { id: "auto_asc", name: "オートバイヤー：アセンション", desc: "毎秒自動でアセンションを実行する機能", cost: 12 },  
            { id: "gp_boost", name: "GP変換効率増幅", desc: "ジェネレーターポイントの生産効率を強化", cost: 25 },  
            { id: "pres_base", name: "プレステージ基礎底上げ", desc: "プレステージ実行時のP.指数のベース値を+0.05加算", cost: 50 },  
            { id: "promo_accel", name: "プロモーション加速", desc: "プロモーション経験値の獲得量を×5.0倍にする", cost: 120 },  
            { id: "dim_break", name: "次元の壁突破", desc: "スコア上限を撤廃しインフィニティ後も超過スコアでIPを稼ぐ", cost: 500 }  
        ];  
  
        const GENERATORS_DEF = LINE_NAMES.map((name, i) => ({  
            id: i + 1,  
            name: `Gen #${i+1} (${name.slice(0, 4)})`,  
            baseCost: Math.pow(10, i * 1.5 + 1),  
            costScale: 1.15 + i * 0.01  
        }));  
  
        const CHALLENGES_DEF = [  
            { id: 1, name: "IC1: イオン化速度", constraint: "プロモーション#2と#4が無効化", reward: "プロモーション#2と#4が強化される" },  
            { id: 2, name: "IC2: 降下", constraint: "アセンションパワーが1/4になる", reward: "アセンションパワーが1.2倍になる" },  
            { id: 3, name: "IC3: 最初の根", constraint: "共通指数 -0.4", reward: "共通指数 +0.03" },  
            { id: 4, name: "IC4: 急勾配", constraint: "全プレステージとプロモーションが^0.4になる", reward: "全プロモーション+1Lv、IP獲得×2" },  
            { id: 5, name: "IC5: 解雇された", constraint: "すべてのプロモーションが大幅に弱体化される", reward: "すべてのプロモーションを強化" },  
            { id: 6, name: "IC6: 枯渇", constraint: "すべての倍率が非常に速く減少する", reward: "すべてのジェネレーター2倍強化" },  
            { id: 7, name: "IC7: 二次分割", constraint: "すべての乗数が(最速インフィニティ時間)^2で割られる", reward: "すべての乗数に(最速インフィニティ時間)^2を乗算" },  
            { id: 8, name: "IC8: 非上昇", constraint: "アセンションが無効化される", reward: "基礎アセンションパワー+2.0" },  
            { id: 9, name: "IC9: 孤立主義", constraint: "最初の4色（赤〜緑）のみでプレイ", reward: "IP獲得量が倍増" }  
        ];  
  
        let game = {  
            score: 0,  
            totalScore: 0,  
            lines: Array(10).fill(0).map(() => ({ level: 0, ascLevel: 0 })),  
            prestigeCount: 0,  
            pMult: 1,  
            pExp: 1.03,  
            promoLevels: { 1: 0, 2: 0, 3: 0, 4: 0 },  
            promoExp: 0,  
            firstPromoDone: false,  
            ip: 0,  
            infUpgrades: {},  
            generators: Array(10).fill(0).map(() => ({ count: 0, bought: 0 })),  
            gp: 0,  
            activeChallenge: null,  
            completedChallenges: {},  
            challengeBestTimes: {},  
            breakInfinity: false,  
            achievements: {},  
            settings: { autoLine: false, autoAsc: false },  
            lastTick: Date.now()  
        };  
  
        function initGame() {  
            renderLinesUI();  
            renderPromotionsUI();  
            renderInfUpgradesUI();  
            renderGeneratorsUI();  
            renderChallengesUI();  
            renderAchievementsUI();  
            loadGame();  
            setInterval(gameLoop, 50);  
        }  
  
        function gameLoop() {  
            let now = Date.now();  
            let dt = (now - game.lastTick) / 1000;  
            if (dt > 1) dt = 1;  
            game.lastTick = now;  
  
            if (game.settings.autoLine && game.infUpgrades['auto_line']) {  
                for (let i = 0; i < 10; i++) buyLineMax(i);  
            }  
            if (game.settings.autoAsc && game.infUpgrades['auto_asc']) {  
                for (let i = 0; i < 10; i++) doAscension(i);  
            }  
  
            let activeLinesCount = (game.activeChallenge === 9) ? 4 : 10;  
            let totalIncome = 0;  
  
            let gpProduction = 0;  
            for (let i = 0; i < 10; i++) {  
                let gen = game.generators[i];  
                let mult = Math.pow(2, Math.floor(gen.bought / 10));  
                if (game.completedChallenges[6]) mult *= 2;  
                let prod = gen.count * (i === 0 ? 1 : 0.5) * mult * dt;  
                if (i > 0) game.generators[i-1].count += prod;  
                else gpProduction += prod;  
            }  
            let gpBoostEff = game.infUpgrades['gp_boost'] ? 1.5 : 1.0;  
            game.gp += gpProduction * gpBoostEff * dt;  
            let gpMultiplier = 1 + Math.log10(game.gp + 1) * 2;  
  
            for (let i = 0; i < activeLinesCount; i++) {  
                let l = game.lines[i];  
                if (l.level > 0) {  
                    let baseSpeed = 1.0 + l.level * 0.2;  
                    if (game.infUpgrades['mag_drive']) baseSpeed *= 1.5;  
                    if (game.activeChallenge === 1) baseSpeed *= 0.5;  
  
                    let ascPowerEff = 10 + (game.infUpgrades['dim_break'] ? l.ascLevel * 3 : l.ascLevel * 2);  
                    if (game.activeChallenge === 2) ascPowerEff /= 4;  
                    if (game.completedChallenges[2]) ascPowerEff *= 1.2;  
                    if (game.completedChallenges[8]) ascPowerEff += 2.0;  
  
                    let p2Eff = game.activeChallenge === 1 ? 1 : Math.pow(1.22, game.promoLevels[2] * (game.promoLevels[4] * 0.08 + 1));  
                    let speed = baseSpeed * p2Eff;  
  
                    let p1Eff = Math.pow(1.35, game.promoLevels[1] * (game.promoLevels[4] * 0.08 + 1));  
                    let p3Eff = Math.pow(ascPowerEff, l.ascLevel);  
                    if (game.activeChallenge === 8) p3Eff = 1;  
  
                    let qSyncEff = game.infUpgrades['q_sync'] ? 3.0 : 1.0;  
                    let lineIncome = l.level * speed * p1Eff * p3Eff * game.pMult * qSyncEff * gpMultiplier;  
  
                    if (game.activeChallenge === 6) lineIncome *= Math.max(0.1, 1 - dt * 0.5);  
                      
                    totalIncome += lineIncome * dt;  
                }  
            }  
  
            let commonExp = game.pExp;  
            if (game.activeChallenge === 3) commonExp -= 0.4;  
            if (game.completedChallenges[3]) commonExp += 0.03;  
            if (game.activeChallenge === 4) commonExp *= 0.4;  
  
            let finalAdd = Math.pow(totalIncome, commonExp);  
            if (!game.breakInfinity && game.score >= 1.80e308) {  
                game.score = 1.80e308;  
            } else {  
                game.score += finalAdd;  
                game.totalScore += finalAdd;  
            }  
  
            if (game.pMult >= 13319) {  
                let promoAccel = game.infUpgrades['promo_accel'] ? 5.0 : 1.0;  
                game.promoExp += (totalIncome / 1e8 + 0.01) * promoAccel * dt;  
            }  
  
            updateUI();  
            renderCanvas();  
        }  
  
        function updateUI() {  
            document.getElementById('header-score').innerText = formatNum(game.score) + " 円";  
            document.getElementById('header-ip').innerText = formatNum(game.ip) + " IP";  
            document.getElementById('inf-ip-display').innerText = formatNum(game.ip) + " IP";  
            document.getElementById('promo-exp-display').innerText = game.promoExp.toFixed(2);  
            document.getElementById('gp-mult-display').innerText = "×" + (1 + Math.log10(game.gp + 1) * 2).toFixed(2);  
  
            let nextPMult = Math.max(1, Math.floor(Math.sqrt(game.totalScore / 1e10)));  
            document.getElementById('pres-mult-val').innerText = "×" + formatNum(game.pMult);  
            document.getElementById('pres-exp-val').innerText = "^" + game.pExp.toFixed(3);  
            document.getElementById('pres-next-val').innerText = "×" + formatNum(nextPMult);  
            let presBtn = document.getElementById('pres-btn');  
            if (game.totalScore >= 1e10) {  
                presBtn.classList.remove('opacity-50', 'cursor-not-allowed');  
            } else {  
                presBtn.classList.add('opacity-50', 'cursor-not-allowed');  
            }  
  
            let infBtn = document.getElementById('inf-btn');  
            if (game.score >= 1.80e308 || game.breakInfinity) {  
                infBtn.classList.remove('opacity-50', 'cursor-not-allowed');  
            } else {  
                infBtn.classList.add('opacity-50', 'cursor-not-allowed');  
            }  
  
            let allIcDone = Object.keys(game.completedChallenges).length >= 9;  
            if (allIcDone) {  
                document.getElementById('break-inf-container').classList.remove('hidden');  
                let biBtn = document.getElementById('break-inf-btn');  
                biBtn.innerText = game.breakInfinity ? "ON" : "OFF";  
                biBtn.className = game.breakInfinity ? "px-2.5 py-1 bg-green-950 text-green-400 border border-green-500/50 rounded-lg text-xs font-orbitron font-bold" : "px-2.5 py-1 bg-red-950 text-red-400 border border-red-500/50 rounded-lg text-xs font-orbitron font-bold";  
            }  
  
            let totalIcSeconds = 0;  
            let icCount = 0;  
            for (let id in game.challengeBestTimes) {  
                totalIcSeconds += game.challengeBestTimes[id];  
                icCount++;  
            }  
            document.getElementById('total-ic-time-display').innerText = icCount > 0 ? totalIcSeconds.toFixed(1) + "s (" + icCount + "/9)" : "---";  
  
            for (let i = 0; i < 10; i++) {  
                let cost = getLineCost(i, 1);  
                let ascCost = getAscCost(i);  
                let lEl = document.getElementById(`line-card-${i}`);  
                if (lEl) {  
                    document.getElementById(`line-lvl-${i}`).innerText = `Lv. ${game.lines[i].level} (Asc. ${game.lines[i].ascLevel})`;  
                    document.getElementById(`line-cost-${i}`).innerText = formatNum(cost) + " 円";  
                    document.getElementById(`line-asc-cost-${i}`).innerText = formatNum(ascCost) + " 円";  
                }  
            }  
  
            renderPromotionsUI();  
        }  
  
        // HOLOGRAPHIC RAILWAY CANVAS RENDERING (WITH SPARKS & PLASMA)  
        function renderCanvas() {  
            const canvas = document.getElementById('rail-canvas');  
            if (!canvas) return;  
            const ctx = canvas.getContext('2d');  
            ctx.clearRect(0, 0, 400, 400);  
  
            let cx = 200, cy = 200;  
  
            // Terminal Station at 12 o'clock (Holographic Sci-Fi Station)  
            ctx.fillStyle = "#00f0ff";  
            ctx.shadowBlur = 10;  
            ctx.shadowColor = "#00f0ff";  
            ctx.fillRect(188, 12, 24, 14);  
            ctx.fillStyle = "#ffffff";  
            ctx.fillRect(194, 6, 12, 8);  
            ctx.shadowBlur = 0;  
  
            for (let i = 0; i < 10; i++) {  
                let radius = 25 + i * 16;  
                let color = LINE_COLORS[i];  
                let l = game.lines[i];  
  
                // Holographic double track railway lines  
                ctx.beginPath();  
                ctx.arc(cx, cy, radius, 0, Math.PI * 2);  
                ctx.strokeStyle = color;  
                ctx.lineWidth = l.level > 0 ? 2.5 : 1;  
                ctx.globalAlpha = l.level > 0 ? 0.75 : 0.15;  
                ctx.stroke();  
                ctx.globalAlpha = 1.0;  
  
                // High-tech trains with pantograph arc sparks & trailing light  
                if (l.level > 0) {  
                    let speed = 1.0 + l.level * 0.2;  
                    let angle = (Date.now() / 1000 * speed * 0.5 + i * 0.6) % (Math.PI * 2);  
                    let tx = cx + Math.cos(angle - Math.PI/2) * radius;  
                    let ty = cy + Math.sin(angle - Math.PI/2) * radius;  
  
                    ctx.save();  
                    ctx.translate(tx, ty);  
                    ctx.fillStyle = color;  
                    ctx.beginPath();  
                    ctx.arc(0, 0, 5, 0, Math.PI * 2);  
                    ctx.fill();  
                    ctx.shadowBlur = 12;  
                    ctx.shadowColor = color;  
                    ctx.fill();  
  
                    // Spark particle effect for active high-speed lines  
                    if (l.level >= 20 && Math.random() < 0.3) {  
                        ctx.strokeStyle = "#ffffff";  
                        ctx.lineWidth = 1.5;  
                        ctx.beginPath();  
                        ctx.moveTo(0, 0);  
                        ctx.lineTo((Math.random() - 0.5) * 14, (Math.random() - 0.5) * 14);  
                        ctx.stroke();  
                    }  
                    ctx.restore();  
                }  
            }  
        }  
  
        function renderLinesUI() {  
            let container = document.getElementById('lines-container');  
            container.innerHTML = "";  
            for (let i = 0; i < 10; i++) {  
                let html = `  
                    <div id="line-card-${i}" class="bg-[#03030c] p-3 rounded-xl border border-cyan-500/25 flex flex-col gap-2 shadow-[0_0_10px_rgba(0,240,255,0.05)_inset]">  
                        <div class="flex justify-between items-center">  
                            <div class="flex items-center gap-2">  
                                <span class="w-3 h-3 rounded-full shadow-[0_0_8px]" style="background-color: ${LINE_COLORS[i]}; box-shadow: 0 0 8px ${LINE_COLORS[i]}"></span>  
                                <span class="font-orbitron text-xs font-bold text-slate-200">${LINE_NAMES[i]}</span>  
                            </div>  
                            <span id="line-lvl-${i}" class="text-xs font-orbitron text-cyan-400">Lv. 0 (Asc. 0)</span>  
                        </div>  
                        <div class="flex gap-2">  
                            <button onclick="buyLine(${i}, 1)" class="flex-1 py-1.5 cyber-btn text-cyan-300 rounded-lg text-xs font-orbitron font-bold transition">  
                                建設 (<span id="line-cost-${i}">0 円</span>)  
                            </button>  
                            <button onclick="buyLineMax(${i})" class="px-3 py-1.5 cyber-btn text-cyan-300 rounded-lg text-xs font-orbitron font-bold transition">MAX</button>  
                            <button onclick="doAscension(${i})" class="px-3 py-1.5 cyber-btn-purple text-purple-200 rounded-lg text-xs font-orbitron font-bold transition" title="近代化アセンション">  
                                近代化 (<span id="line-asc-cost-${i}">0 円</span>)  
                            </button>  
                        </div>  
                    </div>  
                `;  
                container.innerHTML += html;  
            }  
        }  
  
        function renderPromotionsUI() {  
            let container = document.getElementById('promotions-container');  
            if (!container) return;  
            container.innerHTML = "";  
  
            let unlocked = game.pMult >= 13319;  
            if (!unlocked) {  
                container.innerHTML = `<div class="p-4 bg-[#03030c] rounded-xl border border-cyan-500/25 text-center text-xs text-slate-400">P.倍率が ×13,319 に到達するとプロモーションが解放されます。</div>`;  
                return;  
            }  
  
            PROMOTIONS_DEF.forEach(p => {  
                let lvl = game.promoLevels[p.id];  
                let cost = Math.pow(2, lvl);  
                let isLocked = (p.id > 1 && !game.firstPromoDone);  
                let canBuy = game.promoExp >= cost && (!isLocked || (p.id === 1 && lvl < 3));  
  
                container.innerHTML += `  
                    <div class="bg-[#03030c] p-3 rounded-xl border border-cyan-500/25 flex flex-col gap-2">  
                        <div class="flex justify-between items-center">  
                            <span class="font-orbitron text-xs font-bold text-cyan-300">#${p.id} ${p.name} (Lv. ${lvl})</span>  
                            <span class="text-xs text-amber-400 font-orbitron">必要: ${cost} EXP</span>  
                        </div>  
                        <p class="text-[11px] text-slate-400">${p.desc}</p>  
                        <button onclick="buyPromotion(${p.id})" class="w-full py-2 ${canBuy ? 'cyber-btn text-white' : 'bg-slate-900 text-slate-600 border border-slate-800 cursor-not-allowed'} font-orbitron text-xs font-bold rounded-lg transition">  
                            ${isLocked && p.id > 1 ? '初回プロモート後解除' : 'プロモーション実行'}  
                        </button>  
                    </div>  
                `;  
            });  
        }  
  
        function renderInfUpgradesUI() {  
            let container = document.getElementById('inf-sub-upgrades');  
            container.innerHTML = "";  
            INF_UPGRADES_DEF.forEach(up => {  
                let owned = game.infUpgrades[up.id];  
                let canBuy = game.ip >= up.cost && !owned;  
                container.innerHTML += `  
                    <div class="bg-[#03030c] p-3 rounded-xl border border-purple-500/30 flex flex-col gap-2">  
                        <div class="flex justify-between items-center">  
                            <span class="font-orbitron text-xs font-bold text-purple-300">${up.name}</span>  
                            <span class="text-xs text-purple-400 font-orbitron">${up.cost} IP</span>  
                        </div>  
                        <p class="text-[11px] text-slate-400">${up.desc}</p>  
                        <button onclick="buyInfUpgrade('${up.id}')" class="w-full py-2 ${owned ? 'bg-purple-950/50 text-purple-400 border border-purple-900 cursor-default' : (canBuy ? 'cyber-btn-purple text-white' : 'bg-slate-900 text-slate-600 border border-slate-800 cursor-not-allowed')} font-orbitron text-xs font-bold rounded-lg transition">  
                            ${owned ? 'ACQUIRED' : 'PURCHASE'}  
                        </button>  
                    </div>  
                `;  
            });  
        }  
  
        function renderGeneratorsUI() {  
            let container = document.getElementById('generators-container');  
            container.innerHTML = "";  
            GENERATORS_DEF.forEach((g, i) => {  
                let gen = game.generators[i];  
                let cost = g.baseCost * Math.pow(g.costScale, gen.bought);  
                let canBuy = game.ip >= cost;  
                container.innerHTML += `  
                    <div class="bg-[#03030c] p-3 rounded-xl border border-purple-500/30 flex flex-col gap-2">  
                        <div class="flex justify-between items-center">  
                            <span class="font-orbitron text-xs font-bold text-cyan-300">${g.name} (所持: ${formatNum(gen.count)})</span>  
                            <span class="text-xs text-purple-400 font-orbitron">${formatNum(cost)} IP</span>  
                        </div>  
                        <button onclick="buyGenerator(${i})" class="w-full py-2 ${canBuy ? 'cyber-btn-purple text-white' : 'bg-slate-900 text-slate-600 border border-slate-800 cursor-not-allowed'} font-orbitron text-xs font-bold rounded-lg transition">  
                            購入 (+1)  
                        </button>  
                    </div>  
                `;  
            });  
        }  
  
        function renderChallengesUI() {  
            let container = document.getElementById('challenges-container');  
            container.innerHTML = "";  
            CHALLENGES_DEF.forEach(c => {  
                let active = game.activeChallenge === c.id;  
                let done = game.completedChallenges[c.id];  
                let bestTime = game.challengeBestTimes[c.id];  
                container.innerHTML += `  
                    <div class="bg-[#03030c] p-3 rounded-xl border border-purple-500/30 flex flex-col gap-2">  
                        <div class="flex justify-between items-center">  
                            <span class="font-orbitron text-xs font-bold text-amber-300">${c.name} ${done ? '✓' : ''}</span>  
                            <span class="text-[10px] text-slate-400 font-orbitron">最速: ${bestTime ? bestTime.toFixed(1) + 's' : '---'}</span>  
                        </div>  
                        <p class="text-[11px] text-slate-400">制約: ${c.constraint}</p>  
                        <p class="text-[11px] text-cyan-400">報酬: ${c.reward}</p>  
                        <div class="flex gap-2">  
                            <button onclick="startChallenge(${c.id})" class="flex-1 py-2 ${active ? 'bg-red-950 text-red-300 border border-red-500/50' : 'cyber-btn-purple text-purple-200'} font-orbitron text-xs font-bold rounded-lg transition">  
                                ${active ? '挑戦中 (中和)' : (done ? '再挑戦する' : 'チャレンジ開始')}  
                            </button>  
                            ${active ? `<button onclick="abortChallenge()" class="px-3 py-2 bg-slate-900 hover:bg-slate-800 text-slate-300 border border-slate-700 font-orbitron text-xs rounded-lg transition">リタイア</button>` : ''}  
                        </div>  
                    </div>  
                `;  
            });  
        }  
  
        function renderAchievementsUI() {  
            let grid = document.getElementById('achievements-grid');  
            grid.innerHTML = "";  
            for (let i = 1; i <= 28; i++) {  
                let unlocked = game.achievements[i];  
                grid.innerHTML += `  
                    <div class="p-2 rounded-lg bg-[#03030c] border ${unlocked ? 'border-cyan-400 text-cyan-300 shadow-[0_0_10px_rgba(0,240,255,0.3)]' : 'border-slate-800 text-slate-600'} text-center font-orbitron text-[10px]">  
                        #${i} ${unlocked ? 'UNLOCKED' : 'LOCKED'}  
                    </div>  
                `;  
            }  
            document.getElementById('ach-count').innerText = Object.keys(game.achievements).length;  
        }  
  
        function getLineCost(i, count = 1) {  
            let l = game.lines[i];  
            return Math.floor(10 * Math.pow(1.15, l.level) * count);  
        }  
  
        function getAscCost(i) {  
            let l = game.lines[i];  
            return Math.floor(1000 * Math.pow(3.0, l.ascLevel));  
        }  
  
        function buyLine(i, count = 1) {  
            let cost = getLineCost(i, count);  
            if (game.score >= cost) {  
                game.score -= cost;  
                game.lines[i].level += count;  
                checkAchievements();  
            }  
        }  
  
        function buyLineMax(i) {  
            for (let k = 0; k < 100; k++) {  
                let cost = getLineCost(i, 1);  
                if (game.score >= cost) {  
                    game.score -= cost;  
                    game.lines[i].level += 1;  
                } else break;  
            }  
            checkAchievements();  
        }  
  
        function maxAllLines() {  
            for (let i = 0; i < 10; i++) buyLineMax(i);  
        }  
  
        function doAscension(i) {  
            let cost = getAscCost(i);  
            if (game.score >= cost) {  
                game.score -= cost;  
                game.lines[i].ascLevel += 1;  
                game.lines[i].level = 0;  
            }  
        }  
  
        function doPrestige() {  
            if (game.totalScore < 1e10) return;  
            let newPMult = Math.max(1, Math.floor(Math.sqrt(game.totalScore / 1e10)));  
            game.pMult = newPMult;  
            let baseExp = game.infUpgrades['pres_base'] ? 1.08 : 1.03;  
            game.pExp = baseExp + Math.max(0, (Math.log10(game.totalScore) - 10) / 220);  
            game.score = 0;  
            game.lines = Array(10).fill(0).map(() => ({ level: 0, ascLevel: 0 }));  
            checkAchievements();  
        }  
  
        function buyPromotion(id) {  
            let lvl = game.promoLevels[id];  
            let cost = Math.pow(2, lvl);  
            let isLocked = (id > 1 && !game.firstPromoDone);  
            if (isLocked && id > 1) return;  
  
            if (game.promoExp >= cost) {  
                game.promoExp -= cost;  
                game.promoLevels[id]++;  
                if (id === 1 && game.promoLevels[1] >= 3 && !game.firstPromoDone) {  
                    game.firstPromoDone = true;  
                }  
            }  
        }  
  
        function buyInfUpgrade(id) {  
            let up = INF_UPGRADES_DEF.find(u => u.id === id);  
            if (up && game.ip >= up.cost && !game.infUpgrades[id]) {  
                game.ip -= up.cost;  
                game.infUpgrades[id] = true;  
            }  
        }  
  
        function buyGenerator(i) {  
            let g = GENERATORS_DEF[i];  
            let gen = game.generators[i];  
            let cost = g.baseCost * Math.pow(g.costScale, gen.bought);  
            if (game.ip >= cost) {  
                game.ip -= cost;  
                gen.count += 1;  
                gen.bought += 1;  
            }  
        }  
  
        function startChallenge(id) {  
            game.activeChallenge = id;  
            game.score = 0;  
            game.lines = Array(10).fill(0).map(() => ({ level: 0, ascLevel: 0 }));  
            switchTab('lines');  
        }  
  
        function abortChallenge() {  
            game.activeChallenge = null;  
            game.score = 0;  
            game.lines = Array(10).fill(0).map(() => ({ level: 0, ascLevel: 0 }));  
        }  
  
        function doInfinity() {  
            if (game.score < 1.80e308 && !game.breakInfinity) return;  
  
            let earnedIP = Math.floor(Math.max(1, Math.log10(game.score / 1.80e308) * 10) * (game.completedChallenges[9] ? 2 : 1));  
            if (game.completedChallenges[4]) earnedIP *= 2;  
            game.ip += earnedIP;  
  
            if (game.activeChallenge !== null) {  
                game.completedChallenges[game.activeChallenge] = true;  
                game.challengeBestTimes[game.activeChallenge] = 300;  
                game.activeChallenge = null;  
            }  
  
            game.score = 0;  
            game.totalScore = 0;  
            game.lines = Array(10).fill(0).map(() => ({ level: 0, ascLevel: 0 }));  
            game.promoLevels = { 1: 0, 2: 0, 3: 0, 4: 0 };  
            game.promoExp = 0;  
            game.firstPromoDone = false;  
        }  
  
        function toggleBreakInfinity() {  
            game.breakInfinity = !game.breakInfinity;  
        }  
  
        function switchTab(tab) {  
            ['lines', 'prestige', 'promotion', 'infinity'].forEach(t => {  
                document.getElementById(`tab-${t}`).classList.add('hidden');  
                document.getElementById(`tab-btn-${t}`).className = "flex-1 py-2.5 rounded-lg text-slate-400 hover:text-white transition";  
            });  
            document.getElementById(`tab-${tab}`).classList.remove('hidden');  
            document.getElementById(`tab-btn-${tab}`).className = "flex-1 py-2.5 rounded-lg bg-cyan-600/80 text-white font-bold transition shadow-[0_0_15px_rgba(0,240,255,0.5)]";  
        }  
  
        function switchInfTab(sub) {  
            ['upgrades', 'generators', 'challenges'].forEach(s => {  
                document.getElementById(`inf-sub-${s}`).classList.add('hidden');  
                document.getElementById(`inf-tab-${s}`).className = "flex-1 py-2 rounded-lg text-slate-400 hover:text-white transition";  
            });  
            document.getElementById(`inf-sub-${sub}`).classList.remove('hidden');  
            document.getElementById(`inf-tab-${sub}`).className = "flex-1 py-2 rounded-lg bg-purple-950/80 text-purple-200 font-bold transition shadow-[0_0_10px_rgba(217,70,239,0.5)]";  
        }  
  
        function formatNum(num) {  
            if (num < 1e6) return num.toLocaleString('en-US', {maximumFractionDigits: 0});  
            let exponent = Math.floor(Math.log10(num));  
            let mantissa = num / Math.pow(10, exponent);  
            return mantissa.toFixed(2) + "e" + exponent;  
        }  
  
        function checkAchievements() {  
            if (!game.achievements[1] && game.lines[0].level > 0) game.achievements[1] = true;  
            renderAchievementsUI();  
        }  
  
        function saveGame() {  
            localStorage.setItem('quantum_loop_rail_save_v72', JSON.stringify(game));  
            alert("セーブしました！");  
        }  
  
        function loadGame() {  
            let saved = localStorage.getItem('quantum_loop_rail_save_v72');  
            if (saved) {  
                try {  
                    let parsed = JSON.parse(saved);  
                    game = Object.assign(game, parsed);  
                } catch(e) {}  
            }  
        }  
  
        function exportSave() {  
            let data = btoa(JSON.stringify(game));  
            prompt("以下のセーブデータをコピーしてください:", data);  
        }  
  
        function importSave() {  
            let data = prompt("セーブデータを貼り付けてください:");  
            if (data) {  
                try {  
                    let parsed = JSON.parse(atob(data));  
                    game = Object.assign(game, parsed);  
                    saveGame();  
                    location.reload();  
                } catch(e) {  
                    alert("無効なセーブデータです。");  
                }  
            }  
        }  
  
        window.onload = initGame;  
    </script>  
</body>  
</html>  
