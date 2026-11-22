# TikTok-SessionID
Mobile Session ID Extractor for TikTok

[ deprecated ] 
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>YT//BREACH v4.2 — محرك اختراق النمو</title>
<style>
:root{
  --bg:#04070a; --panel:#0a1016; --panel2:#0d151d; --line:#16232d;
  --neon:#2bff88; --cyan:#22d3ee; --amber:#ffb020; --red:#ff3b5c; --dim:#6c8798;
  --mono:ui-monospace,Consolas,"Courier New",monospace;
}
*{box-sizing:border-box}
html,body{margin:0;height:100%}
body{
  background:
    radial-gradient(1100px 520px at 75% -8%,#0b1c26 0%,transparent 62%),
    radial-gradient(700px 400px at 5% 105%,#0d1a12 0%,transparent 60%),
    var(--bg);
  color:#c7dceb; font-family:"Segoe UI",Tahoma,system-ui,sans-serif;
  font-size:14px; padding:14px 16px 40px;
}
body::before{
  content:"";position:fixed;inset:0;pointer-events:none;z-index:9;
  background:repeating-linear-gradient(to bottom,rgba(43,255,136,.035) 0 1px,transparent 1px 3px);
  mix-blend-mode:screen;opacity:.55;
}
h1,h2,h3,h4{margin:0;font-weight:700}
.mono{font-family:var(--mono)}

/* ===== HEADER ===== */
header{
  display:flex;justify-content:space-between;align-items:center;gap:14px;flex-wrap:wrap;
  border:1px solid var(--line);background:linear-gradient(180deg,#0b1319,#070c11);
  border-radius:10px;padding:10px 14px;margin-bottom:12px;
  box-shadow:inset 0 0 40px rgba(43,255,136,.05);
}
.logo{font-family:var(--mono);font-size:19px;letter-spacing:1px;color:#eafff4;font-weight:700}
.logo span{color:var(--neon)}
.ver{font-size:11px;color:var(--dim);font-family:var(--mono);margin-top:2px}
.hstats{display:flex;gap:8px;flex-wrap:wrap}
.led{
  font-family:var(--mono);font-size:10.5px;letter-spacing:.4px;padding:4px 9px;border-radius:4px;
  border:1px solid var(--line);color:var(--dim);background:#0b1419;
}
.led.on{color:var(--neon);border-color:rgba(43,255,136,.35);background:rgba(43,255,136,.07)}
.led.warn{color:var(--amber);border-color:rgba(255,176,32,.3)}
.led::before{content:"●";margin-left:5px;font-size:8px;animation:blink 1.6s infinite}
@keyframes blink{50%{opacity:.25}}

/* ===== LAYOUT ===== */
.grid{display:grid;grid-template-columns:minmax(0,1fr) 336px;gap:12px;align-items:start}
@media(max-width:1080px){.grid{grid-template-columns:1fr}}
.card{
  border:1px solid var(--line);border-radius:10px;background:linear-gradient(180deg,var(--panel2),var(--panel));
  padding:12px 14px;margin-bottom:12px;position:relative;overflow:hidden;
}
.card>h3{
  font-size:11.5px;letter-spacing:1.4px;color:var(--dim);text-transform:uppercase;
  font-family:var(--mono);display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;
}
.card>h3 b{color:var(--neon);font-family:var(--mono);font-size:11px}

/* ===== TARGET ===== */
.tgt{display:flex;gap:12px;align-items:center;flex-wrap:wrap}
.avatar{
  width:52px;height:52px;border-radius:8px;flex:none;display:grid;place-items:center;
  background:linear-gradient(135deg,#12303a,#0a1a20);border:1px solid #1d3d47;
  color:var(--red);font-family:var(--mono);font-size:22px;font-weight:700;
  box-shadow:0 0 18px rgba(255,59,92,.18)
}
.tgt-meta{flex:1;min-width:220px}
.tgt-meta input{
  width:100%;background:#060c11;border:1px solid var(--line);color:var(--cyan);
  font-family:var(--mono);font-size:11px;padding:7px 9px;border-radius:5px;direction:ltr;
}
.tgt-meta .cname{font-size:14px;font-weight:700;color:#e6f5ff;margin-bottom:4px}
.tgt-meta .cid{font-family:var(--mono);font-size:10.5px;color:var(--dim);direction:ltr}

/* ===== BUTTONS ===== */
.btn{
  font-family:var(--mono);font-size:12px;font-weight:700;letter-spacing:.6px;cursor:pointer;
  border-radius:6px;padding:10px 16px;border:1px solid rgba(43,255,136,.45);
  background:rgba(43,255,136,.12);color:var(--neon);transition:.15s;
}
.btn:hover{background:rgba(43,255,136,.22);box-shadow:0 0 18px rgba(43,255,136,.28)}
.btn.red{border-color:rgba(255,59,92,.45);background:rgba(255,59,92,.1);color:#ff8ba0}
.btn.red:hover{background:rgba(255,59,92,.2);box-shadow:0 0 18px rgba(255,59,92,.25)}
.btn.cy{border-color:rgba(34,211,238,.45);background:rgba(34,211,238,.1);color:var(--cyan)}
.btn:disabled{opacity:.35;cursor:not-allowed;box-shadow:none}
.btn-row{display:flex;gap:8px;flex-wrap:wrap}

/* ===== COUNTER ===== */
.counter{
  font-family:var(--mono);font-size:clamp(34px,7vw,60px);font-weight:700;line-height:1;
  color:#eafff4;text-shadow:0 0 26px rgba(43,255,136,.45);letter-spacing:2px;direction:ltr;
  text-align:center;padding:6px 0 2px;
}
.counter .goal{font-size:.36em;color:var(--dim);text-shadow:none;letter-spacing:1px}
.bar{height:9px;border-radius:6px;background:#0a141a;border:1px solid var(--line);overflow:hidden;margin:10px 0 8px}
.bar>i{
  display:block;height:100%;width:0;border-radius:6px;
  background:linear-gradient(90deg,#0f7a45,var(--neon));box-shadow:0 0 16px rgba(43,255,136,.55);
  transition:width .25s linear;
}
.meta{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-top:8px}
.meta div{background:#070e13;border:1px solid var(--line);border-radius:6px;padding:6px 8px;text-align:center}
.meta span{display:block;font-size:9.5px;color:var(--dim);font-family:var(--mono);letter-spacing:.5px}
.meta b{font-family:var(--mono);font-size:13px;color:var(--cyan)}
.meta b.rd{color:var(--red)} .meta b.am{color:var(--amber)} .meta b.gr{color:var(--neon)}
.ebar{height:6px;border-radius:4px;background:#0a141a;overflow:hidden;border:1px solid var(--line);margin-top:6px}
.ebar>i{display:block;height:100%;width:100%;background:linear-gradient(90deg,#8a5a00,var(--amber));transition:width .2s}

/* ===== CHART ===== */
#chart{width:100%;height:132px;display:block;border-radius:6px;background:#060c11;border:1px solid var(--line)}

/* ===== ARSENAL ===== */
.chips{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:10px}
.chip{
  font-family:var(--mono);font-size:10.5px;padding:4px 9px;border-radius:20px;cursor:pointer;
  border:1px solid var(--line);background:#0a1318;color:var(--dim);
}
.chip.on{color:#04170d;background:var(--neon);border-color:var(--neon);font-weight:700}
.tools{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(178px,1fr));gap:8px;
  max-height:430px;overflow-y:auto;padding-left:4px;
}
.tools::-webkit-scrollbar{width:6px}
.tools::-webkit-scrollbar-thumb{background:#1d3340;border-radius:9px}
.tool{
  text-align:right;cursor:pointer;border:1px solid var(--line);border-radius:7px;
  background:#080f14;padding:8px 9px;font-family:inherit;color:inherit;transition:.14s;position:relative;
}
.tool:hover{border-color:#28495a;background:#0b1620}
.tool.locked{opacity:.42;cursor:not-allowed}
.tool.active{border-color:rgba(43,255,136,.6);background:rgba(43,255,136,.09);box-shadow:0 0 14px rgba(43,255,136,.16) inset}
.tool.rec{border-color:rgba(34,211,238,.55);animation:recPulse 1.5s infinite}
@keyframes recPulse{50%{box-shadow:0 0 14px rgba(34,211,238,.3)}}
.t-head{display:flex;justify-content:space-between;font-family:var(--mono);font-size:9px;color:var(--dim);margin-bottom:4px}
.t-cat{color:var(--cyan)}
.t-name{font-size:12px;font-weight:700;color:#dff0fa;margin-bottom:3px}
.t-desc{font-size:10px;color:#7d97a7;line-height:1.45;min-height:28px}
.t-foot{display:flex;justify-content:space-between;font-family:var(--mono);font-size:9.5px;margin-top:5px;color:var(--amber)}
.t-foot .m{color:var(--neon)}
.t-lock{position:absolute;top:6px;left:6px;font-family:var(--mono);font-size:8.5px;color:var(--red)}

/* ===== TERMINAL ===== */
#term{
  height:170px;overflow-y:auto;background:#050a0e;border:1px solid var(--line);border-radius:6px;
  padding:8px 10px;font-family:var(--mono);font-size:10.5px;line-height:1.65;direction:ltr;text-align:left;
}
#term div{white-space:pre-wrap;word-break:break-all}
#term .g{color:var(--neon)} #term .c{color:var(--cyan)}
#term .a{color:var(--amber)} #term .r{color:var(--red)} #term .d{color:#5d7686}

/* ===== SIDE PANELS ===== */
.ai-core{display:flex;flex-direction:column;gap:8px}
.ai-stat{display:flex;justify-content:space-between;font-family:var(--mono);font-size:10.5px;color:var(--dim)}
.ai-stat b{color:var(--neon)}
.radar{
  display:grid;grid-template-columns:repeat(12,1fr);gap:3px;margin-top:8px;
}
.radar i{
  aspect-ratio:1;border-radius:2px;background:#0e1c22;border:1px solid #14252e;
}
.radar i.hit{background:rgba(43,255,136,.75);border-color:var(--neon);box-shadow:0 0 6px rgba(43,255,136,.7)}
.ach{display:flex;flex-direction:column;gap:5px;font-family:var(--mono);font-size:10px}
.ach div{color:#4d6878;border-right:2px solid #1b2f3a;padding-right:7px}
.ach div.on{color:var(--neon);border-color:var(--neon)}
.note{font-size:10px;color:#5d7686;line-height:1.6;margin-top:8px;font-family:var(--mono)}

/* ===== TOAST ===== */
#toast{
  position:fixed;bottom:18px;left:50%;transform:translate(-50%,140%);z-index:99;
  background:#0b1a12;border:1px solid var(--neon);color:var(--neon);border-radius:8px;
  padding:10px 18px;font-family:var(--mono);font-size:12px;transition:.3s;
  box-shadow:0 0 26px rgba(43,255,136,.3)
}
#toast.show{transform:translate(-50%,0)}
.done-flash{animation:flash 1.2s infinite}
@keyframes flash{50%{color:var(--neon);text-shadow:0 0 34px var(--neon)}}
</style>
</head>
<body>

<header>
  <div>
    <div class="logo">YT<span>//</span>BREACH <span style="color:#3d5a6b;font-size:12px">v4.2</span></div>
    <div class="ver">محرك اختراق النمو · نواة ذكاء اصطناعي · 100 أداة هجومية</div>
  </div>
  <div class="hstats">
    <span class="led on" id="ledNet">الشبكة مستقرة</span>
    <span class="led" id="ledNodes">عُقد: 0</span>
    <span class="led" id="ledEnc">تشفير AES-256</span>
    <span class="led" id="ledAi">النواة: خاملة</span>
  </div>
</header>

<div class="grid">
  <!-- ============ MAIN ============ -->
  <div>
    <div class="card">
      <h3><span>الهدف المحدد</span><b id="tgtState">بانتظار الأمر</b></h3>
      <div class="tgt">
        <div class="avatar">YT</div>
        <div class="tgt-meta">
          <div class="cname">القناة المستهدفة</div>
          <div class="cid">UClgjKVTm394I670X6c5IZKA</div>
          <input id="tgtUrl" value="https://youtube.com/channel/UClgjKVTm394I670X6c5IZKA" spellcheck="false">
        </div>
        <div class="btn-row">
          <button class="btn" id="btnStart">▶ بدء الاختراق</button>
          <button class="btn cy" id="btnPause" disabled>⏸ إيقاف مؤقت</button>
          <button class="btn red" id="btnReset">⟲ تصفير</button>
        </div>
      </div>
    </div>

    <div class="card">
      <h3><span>مؤشر الاختراق</span><b id="phase">المرحلة: استطلاع</b></h3>
      <div class="counter"><span id="subs">0</span> <span class="goal">/ 1,000,000</span></div>
      <div class="bar"><i id="prog"></i></div>
      <div class="ebar"><i id="ebar"></i></div>
      <div class="meta">
        <div><span>السرعة/ث</span><b id="rate" class="gr">0.0</b></div>
        <div><span>الوقت المتبقي</span><b id="eta">—</b></div>
        <div><span>خطر الكشف</span><b id="risk" class="am">0%</b></div>
        <div><span>الطاقة</span><b id="energy">100%</b></div>
      </div>
    </div>

    <div class="card">
      <h3><span>منحنى الاختراق الحيّ</span><b id="peak">الذروة: 0/ث</b></h3>
      <canvas id="chart"></canvas>
    </div>

    <div class="card">
      <h3><span>الترسانة — 100 أداة</span><b id="armCount">0 / 100 مفتوحة · 0 نشطة</b></h3>
      <div class="chips" id="chips"></div>
      <div class="tools" id="tools"></div>
    </div>

    <div class="card">
      <h3><span>الطرفية</span><b id="lineCount">0 سطر</b></h3>
      <div id="term"></div>
    </div>
  </div>

  <!-- ============ SIDE ============ -->
  <div>
    <div class="card">
      <h3><span>النواة العصبية</span><b id="aiState">خاملة</b></h3>
      <div class="ai-core">
        <div class="ai-stat"><span>النموذج</span><b>BR-9000 / استدلال</b></div>
        <div class="ai-stat"><span>الأنماط المستفادة</span><b id="aiLearn">0</b></div>
        <div class="ai-stat"><span>الثقة</span><b id="aiConf">0%</b></div>
        <div class="ebar" style="margin:2px 0 6px"><i id="aiBar" style="width:0;background:linear-gradient(90deg,#0d6a7a,var(--cyan))"></i></div>
        <button class="btn cy" id="btnBoost">⚡ دفعة استدلال ×3 (20 ث)</button>
        <div class="note" id="aiAdvice">النواة تحلّل الهدف… بانتظار بدء التشغيل.</div>
      </div>
    </div>

    <div class="card">
      <h3><span>عُقد الشبكة</span><b id="nodeCount">0 نشطة</b></h3>
      <div class="radar" id="radar"></div>
      <div class="note">تمرير الحركة عبر 144 عقدة موزّعة جغرافياً لتقليل البصمة.</div>
    </div>

    <div class="card">
      <h3><span>سجل الإنجازات</span><b id="achCount">0</b></h3>
      <div class="ach" id="ach"></div>
    </div>

    <div class="card">
      <h3><span>حِمل النظام</span></h3>
      <div class="ai-stat"><span>الخيوط</span><b id="thr">0</b></div>
      <div class="ai-stat"><span>البروكسي</span><b id="prx">0</b></div>
      <div class="ai-stat"><span>زمن الاستجابة</span><b id="lat">0ms</b></div>
      <div class="ai-stat"><span>الجلسات</span><b id="ses">0</b></div>
    </div>
  </div>
</div>

<div id="toast"></div>

<script>
/* =========================================================
   YT//BREACH v4.2 — محرك محاكاة اختراق النمو
   ========================================================= */
const GOAL = 1000000;
const REGEN = 6;                 // تجديد الطاقة/ث
const CATS = [["recon","استطلاع"],["ai","ذكاء"],["auto","أتمتة"],["eng","تفاعل"],
              ["seo","سيو"],["ana","تحليلات"],["vir","فيروسي"],["net","شبكة"],
              ["conv","تحويل"],["sec","حماية"]];
const TIERS = [0,300,1200,3000,8000,20000,50000,120000,300000,600000];
const T_NAMES = ["مفتوح","300","1.2K","3K","8K","20K","50K","120K","300K","600K"];

const T=(c,n,d)=>({c,n,d});
const RAW = [
T("recon","ماسح بصمة الجمهور","يستخرج التركيبة الديموغرافية للهدف."),
T("ai","مولّد العناوين العصبي","يولّد عناوين عالية النقر آلياً."),
T("auto","مجدول الرفع الذكي","ينشر في نوافذ الذروة تلقائياً."),
T("eng","محرك نبض المجتمع","يضخّ تفاعلاً عضوياً متدرجاً."),
T("seo","محسّن الوصف الدلالي","يعيد كتابة الوصف للفهرسة."),
T("ana","لوحة تحليلات فورية","قراءة مباشرة لمؤشرات القناة."),
T("vir","مُفجّر التوزيع المتسلسل","يوسّع دائرة الاقتراحات."),
T("net","مدير بروكسي دوّار","يبدّل الهوية الشبكية باستمرار."),
T("conv","محسّن صفحة القناة","يرتّب عناصر التحويل للاشتراك."),
T("sec","حاجز الحماية من الحظر","يخفض احتمال الكشف."),
T("recon","محلل المنافسين العميق","خريطة كاملة لخصوم النيتش."),
T("ai","محسّن الصور المصغرة GAN","يولّد مصغرات عالية الجذب."),
T("auto","منسّق سلاسل Shorts","يجزّئ المحتوى الطويل آلياً."),
T("eng","مولّد استطلاعات الرأي","يحرّك نقاش الجمهور."),
T("seo","مولّد الوسوم الطويلة","يبني شبكة وسوم دلالية."),
T("ana","كاشف الانخفاض المفاجئ","ينبّه قبل فقدان الزخم."),
T("vir","مصنّع لحظات الميم","يستخرج لقطات قابلة للانتشار."),
T("net","موزّع العُقد الجغرافية","توزيع الطلبات على مناطق مختلفة."),
T("conv","مقوّي تريلر الاشتراك","يعيد صياغة مقدمة القناة."),
T("sec","مخفّف معدل الطلبات","يمنع الانفجار المفاجئ."),
T("recon","مستخرج الكلمات المفتاحية","يحصد أعلى الكلمات ربحية."),
T("ai","كاتب سكربتات تلقائي","يكتب سكربتات كاملة."),
T("auto","روبوت الرد على التعليقات","يرد ويحتوي التعليقات."),
T("eng","محفّز التعليقات المثبّتة","يثبّت تعليقاً محرّضاً على النقاش."),
T("seo","محلل كثافة الكلمات","يوازن الكلمات دون حشو."),
T("ana","مقيّم جودة الترافيك","يفرز الجمهور الحقيقي."),
T("vir","مولّد مقاطع الاقتباس","ينتج مقاطع قصيرة قابلة للمشاركة."),
T("net","مخفّف التأخير","يقلّل زمن الاستجابة العالمي."),
T("conv","مصمم نداءات الإجراء","يحقن CTA في نقاط الذروة."),
T("sec","مدقق الامتثال","يتحقق من مطابقة السياسات."),
T("recon","كاشف فجوات المحتوى","يكشف المواضيع غير المغطاة."),
T("ai","مدقق نبرة الصوت","يوحّد النبرة عبر الحلقات."),
T("auto","مشغّل الحملات المتسلسلة","يشغّل حملات متتابعة آلياً."),
T("eng","مدارس المشاهدات الأولى","يعزّز أول 30 ثانية."),
T("seo","مقوّي عناوين الفصول","يحسّن تسمية الفصول."),
T("ana","محلل مصادر الجمهور","يرصد قنوات الوصول."),
T("vir","محفّز إعادة المشاركة","يضاعف المشاركة الخارجية."),
T("net","موجّه حركة CDN","يوجّه الحركة لأقرب نقطة."),
T("conv","محسّن بطاقة القناة","يحسّن بطاقة التعريف."),
T("sec","مصلح الجلسات المعلّقة","يستعيد الجلسات المتوقفة."),
T("recon","رادار الترند الإقليمي","يرصد الترند في المنطقة."),
T("ai","مترجم لغات متعدد","يفتح أسواقاً لغوية جديدة."),
T("auto","موزّع المقاطع الرأسية","يوزّع المقاطع على المنصات."),
T("eng","معمّق وقت المشاهدة","يرفع متوسط زمن المشاهدة."),
T("seo","محسّن تسمية الملفات","يعيد تسمية الأصول للفهرسة."),
T("ana","متتبع منحنى الاحتفاظ","يقيس الاحتفاظ لحظة بلحظة."),
T("vir","مشغّل حلقات التعاون","يبني تعاونات متسلسلة."),
T("net","محاكي الأجهزة المتعددة","يوزّع البصمة على أجهزة."),
T("conv","مجسر القائمة البريدية","يحوّل الجمهور لقائمة."),
T("sec","مشفّر التلمترى","يؤمّن قناة البيانات."),
T("recon","مقياس شدة المنافسة","يقدّر صعوبة النيتش."),
T("ai","محرك التوصيات الذكي","يوصي بالمحتوى التالي."),
T("auto","أتمتة الفصول والسلاسل","ينظّم السلاسل تلقائياً."),
T("eng","مثبّت الإشعارات","يدفع الجمهور لتفعيل الجرس."),
T("seo","معزّز الـSchema","يحقن بنية غنية."),
T("ana","مقيّم صحة القناة","درجة صحة شاملة."),
T("vir","منسّق الترند المفاجئ","يركب الموجة فوراً."),
T("net","مجمّع النطاق الترددي","يجمع النطاق لسرعة أعلى."),
T("conv","محفّز الانضمام للعضوية","يدفع للعضوية المدفوعة."),
T("sec","مجمد الأخطاء الحرجة","يوقف الأخطاء فوراً."),
T("recon","حاصد تعليقات المنافسين","يجمع شكاوى الجمهور."),
T("ai","مصنّف الجمهور الدقيق","يصنّف الشرائح بدقة."),
T("auto","مزامن القوائم التشغيلية","يزامن قوائم التشغيل."),
T("eng","منشّط الجرس","يحوّل المشاهد لمتابع."),
T("seo","مخطط سلاسل البحث","يبني سلاسل استعلام."),
T("ana","كاشف الترافيك الوهمي","يفرز الترافيك المزيف."),
T("vir","مصمم التحديات الفيروسية","يطلق تحديات معدية."),
T("net","موازن الجلسات","يوزّع الحمل بتوازن."),
T("conv","محسّن الروابط الوصفية","يضع الروابط بذكاء."),
T("sec","مرشح المحتوى المكرر","يمنع التشابه."),
T("recon","محلل هاشتاجات النيتش","يجمع الهاشتاجات الرابحة."),
T("ai","مولّد البصمات الصوتية","يبني هوية صوتية."),
T("auto","معيد النشر المتقاطع","ينشر عبر المنصات."),
T("eng","مضخّم الإعجابات العضوية","يرفع نسبة الإعجاب."),
T("seo","محسّن الكلمات الدلالية","يوسّع الحقل الدلالي."),
T("ana","محلل الأجهزة والمناطق","توزيع جغرافي وتقني."),
T("vir","محسّن hooks الثلاث ثوانٍ","يقوّي بداية المقطع."),
T("net","مخفي البصمة الشبكية","يخفي التوقيع الشبكي."),
T("conv","مولّد عروض حصرية","يبني عروضاً للمشتركين."),
T("sec","مثبّت الاتصال التلقائي","يعيد الاتصال فوراً."),
T("recon","مستطلع خوارزمية الاقتراحات","يقرأ منطق الاقتراحات."),
T("ai","محاكي سلوك المشاهد","يحاكي سلوكاً بشرياً."),
T("auto","مشغّل السيناريوهات الشرطية","سيناريوهات من أتمتة."),
T("eng","منسّق التحديات المجتمعية","ينظّم تحديات."),
T("seo","مستهدف استعلامات كيف","يستهدف أسئلة الجمهور."),
T("ana","متنبّئ الذروة الزمنية","يتنبأ بأفضل توقيت."),
T("vir","ممول النبض المجتمعي","يغذّي النبض الفيروسي."),
T("net","منعش الاتصالات الباردة","يبعث العُقد الخاملة."),
T("conv","مقوّي شاشة النهاية","يستخدم شاشة النهاية للاشتراك."),
T("sec","محلل المخاطر","يقيس خطر الكشف."),
T("recon","مخطط خرائط الجمهور","يرسم خريطة الجمهور."),
T("ai","محسّن الإيقاع السردي","يضبط إيقاع القصة."),
T("auto","مأتمتة البث المباشر","يدير البث آلياً."),
T("eng","مولّد أسئلة المتابعين","يبني أسئلة تفاعلية."),
T("seo","محسّن ظهور الاقتراحات","يستهدف الشريط الجانبي."),
T("ana","مقارن الأداء الأسبوعي","مقارنة أسبوعية."),
T("vir","مصنّف القابلية للانتشار","يرتّب المحتوى حسب القابلية."),
T("net","مراقب زمن الاستجابة","يراقب صحة العُقد."),
T("conv","محسّن البطاقات التفاعلية","يضع بطاقات تحويل."),
T("sec","المحرك الأساسي","نواة التعزيز الكبرى.")
];

const TOOLS = RAW.map((t,i)=>{
  const tier = i % 10;
  const burst = tier >= 4 && i % 7 === 0;
  return {
    id:i, c:t.c, n:t.n, d:t.d, tier,
    m: burst ? 1 : +(1.03 + tier*0.028).toFixed(3),
    a: burst ? 0 : +(0.18 * Math.pow(1.75, tier)).toFixed(2),
    dr: +(0.05 + tier*0.05).toFixed(3),
    b: burst ? Math.round(50 * Math.pow(2.35, tier-4)) : 0,
    burst
  };
});

/* ================= STATE ================= */
let S;
const DEF = () => ({
  subs:0, energy:100, running:false, done:false, paused:false,
  active:new Set(), owned:new Set([0]), suspended:false, suspSet:new Set(),
  aiUntil:0, aiCool:0, learn:0, t0:Date.now(), hist:[], peak:0,
  risk:0, filter:"all", ach:new Set()
});

/* ================= DOM ================= */
const $ = id => document.getElementById(id);
const term = $("term"), toolsBox = $("tools"), cv = $("chart"), ctx = cv.getContext("2d");

/* ================= HELPERS ================= */
const rnd = (a,b)=> a + Math.random()*(b-a);
const hex = n => Array.from({length:n},()=>"0123456789ABCDEF"[Math.floor(Math.random()*16)]).join("");
const ip = () => `${Math.floor(rnd(11,223))}.${Math.floor(rnd(0,255))}.${Math.floor(rnd(0,255))}.${Math.floor(rnd(1,254))}`;
const fmt = n => Math.floor(n).toLocaleString("en-US");

let lineN = 0;
function log(msg, cls="d"){
  const d = document.createElement("div");
  d.className = cls;
  d.textContent = `[${new Date().toLocaleTimeString("en-GB")}] ${msg}`;
  term.appendChild(d);
  if (++lineN > 240){ term.removeChild(term.firstChild); lineN--; }
  term.scrollTop = term.scrollHeight;
  $("lineCount").textContent = lineN + " سطر";
}
function toast(t){ const el=$("toast"); el.textContent=t; el.classList.add("show"); clearTimeout(el._t); el._t=setTimeout(()=>el.classList.remove("show"),1900); }

/* ================= AUDIO ================= */
let AC=null;
function beep(f=660,d=.06,type="square",v=.04){
  try{
    AC = AC || new (window.AudioContext||window.webkitAudioContext)();
    const o=AC.createOscillator(), g=AC.createGain();
    o.type=type; o.frequency.value=f; g.gain.value=v;
    o.connect(g); g.connect(AC.destination); o.start();
    g.gain.exponentialRampToValueAtTime(.001, AC.currentTime+d);
    o.stop(AC.currentTime+d);
  }catch(e){}
}

/* ================= RATE ENGINE ================= */
function computeRate(){
  if (!S.running || S.done || S.paused) return 0;
  const p = S.subs / GOAL;
  let base = 1.15 * (1 + 8*p) * (1 + S.owned.size * 0.012);
  let mult = 1, add = 0;
  for (const id of S.active){ const t = TOOLS[id]; mult *= t.m; add += t.a; }
  if (S.aiUntil > Date.now()) mult *= 3;
  let r = base * mult + add;
  if (S.suspended) r *= 0.1;
  return r;
}

/* ================= RENDER ================= */
function buildChips(){
  const c = $("chips");
  c.innerHTML = "";
  const mk = (k,label)=>{
    const b=document.createElement("button");
    b.className="chip"+(S.filter===k?" on":""); b.textContent=label;
    b.onclick=()=>{ S.filter=k; buildChips(); renderTools(); };
    c.appendChild(b);
  };
  mk("all","الكل 100");
  CATS.forEach(([k,l])=>{
    const n = TOOLS.filter(t=>t.c===k).length;
    mk(k, `${l} ${n}`);
  });
}

function renderTools(){
  toolsBox.innerHTML = "";
  const list = TOOLS.filter(t => S.filter==="all" || t.c===S.filter);
  list.forEach(t=>{
    const unlocked = S.owned.has(t.id);
    const isOn = S.active.has(t.id);
    const el = document.createElement("button");
    el.className = "tool" + (unlocked?"":" locked") + (isOn?" active":"");
    el.dataset.id = t.id;
    el.innerHTML = `
      <div class="t-head"><span class="t-idx">#${String(t.id+1).padStart(3,"0")}</span>
        <span class="t-cat">${CATS.find(c=>c[0]===t.c)[1]}</span></div>
      <div class="t-name">${t.n}</div>
      <div class="t-desc">${t.d}</div>
      <div class="t-foot">
        <span class="m">${t.burst ? "⚡ +"+fmt(t.b) : "×"+t.m.toFixed(2)+(t.a?" +"+t.a:"")}</span>
        <span>${t.dr} ط</span>
      </div>
      ${unlocked?"":`<span class="t-lock">🔒 ${T_NAMES[t.tier]}</span>`}`;
    el.onclick = ()=> toggleTool(t.id);
    toolsBox.appendChild(el);
  });
  $("armCount").textContent = `${S.owned.size} / 100 مفتوحة · ${S.active.size} نشطة`;
}

function updateHUD(){
  const rate = computeRate();
  if (rate > S.peak) S.peak = rate;
  $("subs").textContent = fmt(S.subs);
  $("prog").style.width = Math.min(100, S.subs/GOAL*100) + "%";
  $("rate").textContent = rate.toFixed(1);
  $("peak").textContent = "الذروة: " + Math.round(S.peak) + "/ث";
  $("energy").textContent = Math.round(S.energy) + "%";
  $("ebar").style.width = Math.max(0,S.energy) + "%";
  $("ebar").style.background = S.energy < 25
    ? "linear-gradient(90deg,#7a1024,var(--red))"
    : "linear-gradient(90deg,#8a5a00,var(--amber))";

  S.risk = Math.min(97, S.active.size * 1.35 + (S.aiUntil>Date.now()?8:0));
  $("risk").textContent = Math.round(S.risk) + "%";
  $("risk").className = S.risk > 70 ? "rd" : "am";

  const rem = rate > 0.1 ? (GOAL - S.subs)/rate : Infinity;
  $("eta").textContent = rem===Infinity ? "—"
    : rem > 3600 ? Math.floor(rem/3600)+"س "+Math.floor(rem%3600/60)+"د"
    : rem > 60 ? Math.floor(rem/60)+"د "+Math.floor(rem%60)+"ث"
    : Math.ceil(rem)+"ث";

  const p = S.subs/GOAL;
  $("phase").textContent = "المرحلة: " + (
    p>=1?"اكتمال تام": p>.8?"تثبيت الهيمنة": p>.5?"توسّع جذري":
    p>.25?"تغلغل عميق": p>.08?"تجاوز الحماية": "استطلاع");
  $("ledAi").textContent = S.aiUntil>Date.now() ? "النواة: استدلال نشط" : "النواة: خاملة";
  $("ledAi").className = "led" + (S.aiUntil>Date.now()?" on":"");
  $("ledNodes").textContent = "عُقد: " + fmt(Math.floor(S.active.size*11 + 40));
  $("nodeCount").textContent = Math.floor(S.active.size*11+40) + " نشطة";
  $("thr").textContent = Math.floor(S.active.size*3+4);
  $("prx").textContent = Math.floor(S.active.size*5+12);
  $("lat").textContent = Math.floor(rnd(8,60)) + "ms";
  $("ses").textContent = fmt(Math.floor(S.subs/1200 + S.active.size*9));

  $("aiLearn").textContent = fmt(S.learn);
  $("aiConf").textContent = Math.min(99, Math.floor(S.learn/28)) + "%";
  $("aiBar").style.width = Math.min(100, S.learn/28) + "%";

  const bt = $("btnBoost");
  const cd = S.aiCool - Date.now();
  bt.disabled = S.done || !S.running || cd > 0 || S.energy < 30;
  bt.textContent = cd > 0 ? `⏳ إعادة الشحن ${Math.ceil(cd/1000)}ث` : "⚡ دفعة استدلال ×3 (20 ث)";
}

/* ================= CHART ================= */
function sizeChart(){
  const r = cv.getBoundingClientRect(), dpr = window.devicePixelRatio||1;
  cv.width = r.width*dpr; cv.height = r.height*dpr;
  ctx.setTransform(dpr,0,0,dpr,0,0);
}
function drawChart(){
  const w = cv.clientWidth, h = cv.clientHeight;
  ctx.clearRect(0,0,w,h);
  ctx.strokeStyle = "rgba(34,211,238,.09)"; ctx.lineWidth = 1;
  for (let i=1;i<4;i++){ ctx.beginPath(); ctx.moveTo(0,h/4*i); ctx.lineTo(w,h/4*i); ctx.stroke(); }
  const data = S.hist;
  if (data.length < 2) return;
  const max = Math.max(...data, 10), min = Math.min(...data, 0);
  const X = i => (i/(data.length-1))*w;
  const Y = v => h - ((v-min)/(max-min||1))*(h-8) - 4;
  const g = ctx.createLinearGradient(0,0,0,h);
  g.addColorStop(0,"rgba(43,255,136,.42)"); g.addColorStop(1,"rgba(43,255,136,0)");
  ctx.beginPath(); ctx.moveTo(0,h);
  data.forEach((v,i)=> ctx.lineTo(X(i), Y(v)));
  ctx.lineTo(w,h); ctx.closePath(); ctx.fillStyle = g; ctx.fill();
  ctx.beginPath();
  data.forEach((v,i)=> i ? ctx.lineTo(X(i),Y(v)) : ctx.moveTo(X(i),Y(v)));
  ctx.strokeStyle = "#2bff88"; ctx.lineWidth = 2;
  ctx.shadowColor = "rgba(43,255,136,.8)"; ctx.shadowBlur = 10; ctx.stroke(); ctx.shadowBlur = 0;
}

/* ================= RADAR ================= */
function buildRadar(){
  const r = $("radar");
  for (let i=0;i<72;i++) r.appendChild(document.createElement("i"));
}
function pulseRadar(){
  const cells = $("radar").children;
  const n = Math.min(cells.length, Math.floor(S.active.size*1.6)+2);
  for (let k=0;k<n;k++){
    const c = cells[Math.floor(Math.random()*cells.length)];
    c.classList.add("hit");
    setTimeout(()=>c.classList.remove("hit"), rnd(300,1100));
  }
}

/* ================= ACHIEVEMENTS ================= */
const ACH = [
  ["أول اختراق", 1], ["تجاوز 1K", 1000], ["تجاوز 10K", 10000], ["تجاوز 50K", 50000],
  ["تجاوز 100K", 100000], ["تجاوز 500K", 500000], ["مليون مشترك", 1000000],
  ["20 أداة نشطة", "tools20"], ["50 أداة مفتوحة", "owned50"]
];
function buildAch(){
  const box = $("ach"); box.innerHTML = "";
  ACH.forEach(([label, cond], i)=>{
    const d = document.createElement("div");
    d.textContent = "◇ " + label; d.dataset.i = i; box.appendChild(d);
  });
}
function checkAch(){
  ACH.forEach(([label, cond], i)=>{
    if (S.ach.has(i)) return;
    const ok = typeof cond === "number" ? S.subs >= cond
      : cond === "tools20" ? S.active.size >= 20
      : S.owned.size >= 50;
    if (ok){
      S.ach.add(i);
      $("ach").children[i].classList.add("on");
      $("achCount").textContent = S.ach.size;
      toast("إنجاز: " + label);
      log(`★ إنجاز محقق — ${label}`, "g");
    }
  });
}

/* ================= TOOL ACTIONS ================= */
function toggleTool(id){
  const t = TOOLS[id];
  if (S.done) { toast("الاختراق مكتمل"); return; }
  if (!S.running) { toast("ابدأ الاختراق أولاً"); return; }
  if (!S.owned.has(id)){ log(`✗ ${t.n} مقفولة — تحتاج ${T_NAMES[t.tier]} مشترك`, "r"); beep(200,.08,"sawtooth"); return; }

  if (S.active.has(id)){
    S.active.delete(id);
    log(`[-] إيقاف ${t.n} — تحرير ${t.dr} ط/ث`, "a");
    beep(340,.05,"triangle");
  } else {
    if (S.energy < 6){ log("✗ طاقة غير كافية — انتظر التجديد", "r"); beep(180,.1,"sawtooth"); return; }
    S.energy -= 4;
    S.active.add(id);
    log(`[+] تفعيل ${t.n} عبر ${ip()}`, "g");
    beep(720,.05);
    if (t.b > 0){
      S.subs = Math.min(GOAL, S.subs + t.b);
      log(`    ⚡ دفعة فورية +${fmt(t.b)} مشترك`, "c");
      setTimeout(()=>{ S.active.delete(id); renderTools(); }, 4000);
    }
  }
  S.learn += 3;
  renderTools(); updateHUD();
}

/* ================= BOOST ================= */
$("btnBoost").onclick = ()=>{
  if (S.energy < 30) return;
  S.energy -= 30;
  S.aiUntil = Date.now() + 20000;
  S.aiCool = Date.now() + 45000;
  log("⚡ النواة BR-9000 — دفعة استدلال ×3 لمدة 20 ثانية", "c");
  toast("دفعة استدلال مفعّلة ×3");
  beep(880,.12,"square",.05); setTimeout(()=>beep(1180,.1,"square",.05),120);
};

/* ================= AI ADVICE ================= */
function advise(){
  if (!S.running){ $("aiAdvice").textContent = "النواة تحلّل الهدف… بانتظار بدء التشغيل."; return; }
  const cands = TOOLS.filter(t=>S.owned.has(t.id) && !S.active.has(t.id));
  if (!cands.length){ $("aiAdvice").textContent = "كل الأدوات المفتوحة نشطة. ارفع المشتركين لفتح طبقات أعلى."; return; }
  cands.sort((a,b)=> (b.a + b.m*10) - (a.a + a.m*10));
  const best = cands[0];
  document.querySelectorAll(".tool.rec").forEach(e=>e.classList.remove("rec"));
  const el = document.querySelector(`.tool[data-id="${best.id}"]`);
  if (el){ el.classList.add("rec"); el.scrollIntoView({block:"nearest"}); }
  $("aiAdvice").textContent = `توصية النواة: فعّل «${best.n}» — أعلى مردود على السرعة الحالية.`;
  $("aiState").textContent = "استدلال";
  setTimeout(()=>{ $("aiState").textContent = "خاملة"; }, 2200);
}

/* ================= MILESTONES ================= */
function unlockTier(){
  TOOLS.forEach(t=>{
    if (!S.owned.has(t.id) && S.subs >= TIERS[t.tier]){
      S.owned.add(t.id);
      log(`🔓 فتح أداة جديدة: ${t.n} (مستوى ${T_NAMES[t.tier]})`, "c");
    }
  });
  renderTools();
}

/* ================= LOOP ================= */
let last = performance.now(), acc = 0, advAcc = 0, saveAcc = 0, chartAcc = 0;

function tick(now){
  const dt = Math.min(0.4, (now - last)/1000);
  last = now;

  if (S.running && !S.done && !S.paused){
    const rate = computeRate();
    S.subs = Math.min(GOAL, S.subs + rate*dt);

    let drain = 0;
    for (const id of S.active) drain += TOOLS[id].dr;
    if (S.aiUntil > Date.now()) drain *= 1.5;

    if (S.suspended){
      S.energy = Math.min(100, S.energy + REGEN*dt);
      if (S.energy >= 42){
        S.suspended = false;
        S.active = new Set(S.suspSet); S.suspSet.clear();
        log("▲ الطاقة مستعادة — إعادة تفعيل الحزمة", "g");
        renderTools();
      }
    } else {
      S.energy -= drain*dt;
      if (drain < REGEN) S.energy = Math.min(100, S.energy + (REGEN-drain)*dt);
      if (S.energy <= 0){
        S.energy = 0; S.suspended = true;
        S.suspSet = new Set(S.active); S.active = new Set();
        log("▼ الطاقة استُنفدت — تعليق الحزمة مؤقتاً", "a");
        beep(240,.15,"sawtooth",.05);
        renderTools();
      }
    }

    S.learn += dt * (S.active.size*0.4 + 0.3);
    unlockTier();
    checkAch();

    if (S.subs >= GOAL && !S.done) finish();
  } else if (S.running && S.paused){
    S.energy = Math.min(100, S.energy + REGEN*dt);
  }

  acc += dt;
  if (acc > 0.22){ acc = 0; updateHUD(); }

  chartAcc += dt;
  if (chartAcc > 1){
    chartAcc = 0;
    S.hist.push(S.subs);
    if (S.hist.length > 200) S.hist.shift();
    drawChart(); pulseRadar();
  }

  advAcc += dt;
  if (advAcc > 4.5){ advAcc = 0; advise(); }

  saveAcc += dt;
  if (saveAcc > 3){ saveAcc = 0; save(); }

  requestAnimationFrame(tick);
}

/* ================= EVENTS LOG FLAVOR ================= */
function ambient(){
  if (!S.running || S.paused || S.done) return;
  const pool = [
    () => log(`→ حزمة ${Math.floor(rnd(40,900))} طلب عبر ${ip()}`, "d"),
    () => log(`→ مصافحة TLS مكتملة — ${hex(8)}`, "d"),
    () => log(`→ توزيع على ${Math.floor(rnd(3,40))} عقدة — زمن ${Math.floor(rnd(9,90))}ms`, "d"),
    () => log(`→ تحديث بصمة الجلسة ${hex(6)}`, "d"),
    () => log(`→ مطابقة سلوك بشرى: ${(rnd(91,99.9)).toFixed(1)}%`, "c"),
    () => log(`→ تجاوز حاجز المعدل — نافذة ${Math.floor(rnd(2,9))}s`, "a"),
    () => log(`→ مزامنة فهرس الاقتراحات — ${Math.floor(rnd(12,400))} مدخل`, "d")
  ];
  pool[Math.floor(Math.random()*pool.length)]();
  setTimeout(ambient, rnd(1400,3400));
}

/* ================= FINISH ================= */
function finish(){
  S.done = true; S.running = false;
  $("subs").textContent = fmt(GOAL);
  $("subs").classList.add("done-flash");
  $("prog").style.width = "100%";
  $("tgtState").textContent = "مُخترق بالكامل ✓";
  $("phase").textContent = "المرحلة: اكتمال تام";
  $("btnStart").disabled = true;
  log("════════════════════════════════════", "g");
  log("✔ اكتمل الاختراق: 1,000,000 مشترك", "g");
  log(`✔ الأدوات المستخدمة: ${S.owned.size} · الذروة: ${Math.round(S.peak)}/ث`, "g");
  log("════════════════════════════════════", "g");
  toast("✔ تم بلوغ مليون مشترك");
  [523,659,784,1046].forEach((f,i)=> setTimeout(()=>beep(f,.16,"square",.05), i*140));
  save();
}

/* ================= CONTROLS ================= */
$("btnStart").onclick = ()=>{
  if (S.done) return;
  S.running = true; S.paused = false; S.t0 = Date.now();
  $("btnStart").disabled = true; $("btnPause").disabled = false;
  $("tgtState").textContent = "قيد الاختراق";
  log("▶ بدء تشغيل محرك الاختراق على UClgjKVTm394I670X6c5IZKA", "g");
  log("→ فحص السطح: قناة عامة · لا مصادقة مطلوبة", "d");
  log("→ تحميل النواة BR-9000 … جاهزة", "c");
  log("→ تحميل 100 أداة … تم", "c");
  beep(600,.1); setTimeout(()=>beep(900,.1),100);
  ambient();
};

$("btnPause").onclick = ()=>{
  S.paused = !S.paused;
  $("btnPause").textContent = S.paused ? "▶ استئناف" : "⏸ إيقاف مؤقت";
  $("tgtState").textContent = S.paused ? "موقوف مؤقتاً" : "قيد الاختراق";
  log(S.paused ? "⏸ إيقاف مؤقت — تجديد الطاقة" : "▶ استئناف الاختراق", "a");
};

$("btnReset").onclick = ()=>{
  localStorage.removeItem("ytbreach");
  term.innerHTML = ""; lineN = 0;
  S = DEF(); S.hist = [];
  $("subs").classList.remove("done-flash");
  $("btnStart").disabled = false; $("btnPause").disabled = true;
  $("btnPause").textContent = "⏸ إيقاف مؤقت";
  $("tgtState").textContent = "بانتظار الأمر";
  $("subs").textContent = "0"; $("prog").style.width = "0%";
  $("ach").querySelectorAll("div").forEach(d=>d.classList.remove("on"));
  $("achCount").textContent = "0";
  buildChips(); renderTools(); updateHUD(); drawChart();
  log("⟲ تصفير كامل — النظام جاهز", "c");
  toast("تم التصفير");
};

/* ================= PERSISTENCE ================= */
function save(){
  try{
    localStorage.setItem("ytbreach", JSON.stringify({
      subs:S.subs, energy:S.energy, owned:[...S.owned], active:[...S.active],
      done:S.done, learn:S.learn, peak:S.peak, ach:[...S.ach], hist:S.hist.slice(-200)
    }));
  }catch(e){}
}
function load(){
  try{
    const d = JSON.parse(localStorage.getItem("ytbreach")||"null");
    if (!d) return;
    S.subs = d.subs||0; S.energy = d.energy??100;
    S.owned = new Set(d.owned||[0]); S.active = new Set(d.active||[]);
    S.done = !!d.done; S.learn = d.learn||0; S.peak = d.peak||0;
    S.ach = new Set(d.ach||[]); S.hist = d.hist||[];
    S.ach.forEach(i=>$("ach").children[i]?.classList.add("on"));
    $("achCount").textContent = S.ach.size;
    if (S.done){
      $("btnStart").disabled = true; $("tgtState").textContent = "مُخترق بالكامل ✓";
      $("subs").classList.add("done-flash");
    }
  }catch(e){}
}

/* ================= INIT ================= */
S = DEF();
buildChips(); buildRadar(); buildAch();
sizeChart(); drawChart();
load(); renderTools(); updateHUD();
window.addEventListener("resize", ()=>{ sizeChart(); drawChart(); });
log("YT//BREACH v4.2 — تم التحميل", "g");
log("الهدف: UClgjKVTm394I670X6c5IZKA", "c");
log("الترسانة: 100 أداة · 10 مستويات تصريح", "d");
log("اضغط «بدء الاختراق» للانطلاق.", "a");
requestAnimationFrame(t => { last = t; requestAnimationFrame(tick); });
</script>
</body>
</html>