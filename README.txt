<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<meta name="theme-color" content="#080f1a">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="Health OS">
<link rel="manifest" href="manifest.json">
<link rel="apple-touch-icon" href="icons/icon-192.png">
<title>Vijay Health OS</title>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html,body{height:100%;overscroll-behavior:none;background:#080f1a;color:#e2e8f0;font-family:Georgia,serif;font-size:14px;-webkit-tap-highlight-color:transparent}
button{cursor:pointer;font-family:inherit;border:none}input{font-family:inherit}
#hdr{background:linear-gradient(160deg,#0a1628,#112240);border-bottom:1px solid #1e2d45;padding:10px 14px 0;position:sticky;top:0;z-index:90}
.hr1{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:6px}
.htag{font-size:9px;letter-spacing:3px;color:#38bdf8;font-family:monospace;text-transform:uppercase}
.htitle{font-size:19px;color:#f1f5f9;font-weight:bold;margin:2px 0 1px}
.hmeta{font-size:11px;color:#475569}
.cbadge{text-align:right;flex-shrink:0}
.cnum{font-size:22px;font-weight:bold;font-family:monospace;color:#4ade80;line-height:1}
.cnum.warn{color:#fbbf24}.cnum.over{color:#f87171}
.cunit{font-size:9px;color:#475569;margin-top:1px}
.wbanner{border-radius:8px;padding:7px 12px;margin-bottom:7px;display:flex;justify-content:space-between;align-items:center}
.wbanner.eve{background:#071828;border:1px solid #38bdf833}
.wbanner.morn{background:#062012;border:1px solid #4ade8033}
.wbmode{font-size:11px;font-weight:bold;font-family:monospace}
.wbanner.eve .wbmode{color:#38bdf8}.wbanner.morn .wbmode{color:#4ade80}
.wbsub{font-size:10px;color:#475569;margin-top:2px}
.wbnxt{font-size:10px;color:#64748b;margin-bottom:3px}
.wbov{background:transparent;border:1px solid #334155;color:#64748b;padding:3px 8px;border-radius:6px;font-size:10px;font-family:monospace}
.ctrack{height:4px;background:#0d1828;border-radius:4px;margin-bottom:8px;overflow:hidden}
.cfill{height:100%;width:0%;border-radius:4px;transition:width .4s;background:linear-gradient(90deg,#1d4ed8,#4ade80)}
.tnav{display:flex;gap:4px;padding-bottom:8px;overflow-x:auto;scrollbar-width:none}
.tnav::-webkit-scrollbar{display:none}
.tb{flex:0 0 auto;padding:6px 10px;border-radius:8px;background:transparent;border:1px solid #1e2d45;color:#475569;font-size:11px;font-family:monospace;white-space:nowrap}
.tb.on{background:#1d4ed8;border-color:#3b82f6;color:#bfdbfe}
#main{padding:12px 14px 60px;max-width:700px;margin:0 auto}
.hint{font-size:10px;color:#334155;font-family:monospace;margin-bottom:10px;letter-spacing:1px}
.si{display:flex;align-items:center;gap:9px;border-radius:10px;padding:10px 9px;margin-bottom:6px}
.si[data-t=routine]{background:#161e2b;border:1px solid #94a3b833;border-left:3px solid #94a3b8}
.si[data-t=activity]{background:#071828;border:1px solid #38bdf833;border-left:3px solid #38bdf8}
.si[data-t=meal]{background:#1a160a;border:1px solid #fbbf2433;border-left:3px solid #fbbf24}
.si[data-t=meds]{background:#1c0909;border:1px solid #f8717133;border-left:3px solid #f87171}
.si[data-t=gym]{background:#062012;border:1px solid #4ade8033;border-left:3px solid #4ade80}
.si[data-t=routine] .sil{color:#94a3b8}.si[data-t=activity] .sil{color:#38bdf8}
.si[data-t=meal] .sil{color:#fbbf24}.si[data-t=meds] .sil{color:#f87171}.si[data-t=gym] .sil{color:#4ade80}
.si.done{opacity:.4}
.sdb{width:22px;height:22px;border-radius:50%;flex-shrink:0;border:2px solid #334155;background:transparent;color:#052e16;font-size:11px;display:flex;align-items:center;justify-content:center}
.sdb.on{background:#4ade80;border-color:#4ade80}
.sico{font-size:17px;flex-shrink:0}
.sinfo{flex:1;min-width:0}
.sr{display:flex;justify-content:space-between;gap:5px;align-items:baseline}
.sil{font-size:13px;font-weight:bold}.sil.done{text-decoration:line-through}
.stm{font-size:11px;color:#475569;font-family:monospace;flex-shrink:0}
.sdt{font-size:11px;color:#475569;margin-top:2px;line-height:1.4}
.fbadge{font-size:9px;color:#f87171;font-family:monospace;margin-top:2px}
.seb{background:transparent;border:1px solid #1e2d45;color:#475569;padding:3px 7px;border-radius:6px;font-size:12px;flex-shrink:0}
.sph{width:32px;flex-shrink:0}
.flbl{font-size:10px;color:#475569;font-family:monospace;letter-spacing:1px;margin-bottom:6px}
.fslots{display:flex;gap:6px;overflow-x:auto;padding-bottom:4px;margin-bottom:10px;scrollbar-width:none;align-items:stretch}
.fslots::-webkit-scrollbar{display:none}
.slb{min-width:80px;flex-shrink:0;padding:8px 6px;border-radius:8px;text-align:center;background:#111d2e;border:1px solid #1e2d45;color:#475569;font-size:11px;font-weight:bold;line-height:1.3;display:flex;flex-direction:column;align-items:center;gap:2px}
.slb span{font-size:9px;font-weight:normal;opacity:.6}
.slb.on{background:#1d4ed8;border-color:#3b82f6;color:#bfdbfe}
.tlog{background:#0d1828;border:1px solid #1e2d45;border-radius:10px;padding:12px;margin-bottom:10px}
.tlhdr{font-size:10px;color:#fbbf24;font-family:monospace;margin-bottom:8px;letter-spacing:1px}
.tlsn{font-size:11px;color:#475569;margin-bottom:4px;display:flex;gap:8px}
.tlsc{color:#fbbf24;font-family:monospace}
.li{display:flex;align-items:center;gap:7px;background:#111d2e;border-radius:7px;padding:7px 9px;margin-bottom:3px}
.linf{flex:1;min-width:0}
.linm{font-size:12px;color:#e2e8f0;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.limt{font-size:10px;color:#475569}.liwx{font-size:10px;color:#fbbf24}
.qc{display:flex;align-items:center;gap:3px;flex-shrink:0}
.qb{width:22px;height:22px;background:#1a2d44;color:#e2e8f0;border-radius:5px;font-size:13px;display:flex;align-items:center;justify-content:center}
.qv{font-size:11px;color:#94a3b8;min-width:26px;text-align:center;font-family:monospace}
.lcal{font-size:12px;color:#fbbf24;font-family:monospace;min-width:48px;text-align:right;flex-shrink:0}
.lrm{background:transparent;color:#f87171;font-size:15px;padding:0 3px;flex-shrink:0}
.tmac{display:grid;grid-template-columns:repeat(3,1fr);gap:6px;margin-top:8px;padding-top:8px;border-top:1px solid #1e2d45}
.tmc{text-align:center}.tmcv{font-size:15px;font-weight:bold;font-family:monospace}.tmcl{font-size:9px;color:#475569}
.catrow{display:flex;gap:4px;overflow-x:auto;padding-bottom:4px;margin-bottom:8px;scrollbar-width:none;align-items:center}
.catrow::-webkit-scrollbar{display:none}
.cb{padding:5px 12px;border-radius:20px;background:#111d2e;color:#475569;font-size:11px;font-family:monospace;white-space:nowrap;flex-shrink:0}
.cb.on{background:#38bdf8;color:#0f172a;font-weight:bold}
.fsrch{width:100%;background:#0d1828;border:1px solid #1e2d45;color:#e2e8f0;padding:10px 14px;border-radius:10px;font-size:13px;margin-bottom:8px;outline:none}
#flist{display:flex;flex-direction:column;gap:5px;max-height:280px;overflow-y:auto}
.fi{display:flex;align-items:center;gap:8px;background:#111d2e;border:1px solid #1e2d45;border-radius:8px;padding:10px 12px}
.finf{flex:1;min-width:0}.finm{font-size:13px;color:#e2e8f0}.fimt{font-size:10px;color:#475569;margin-top:1px}.fiwx{font-size:10px;color:#fbbf24}
.fcal{font-size:13px;color:#fbbf24;font-family:monospace;min-width:52px;text-align:right;flex-shrink:0}
.fadd{width:32px;height:32px;border-radius:8px;background:#1d4ed8;color:#bfdbfe;font-size:20px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.nores{text-align:center;color:#334155;padding:20px;font-size:13px}
.ctwrap{margin-top:10px}
.cttog{width:100%;background:#0d1828;border:1px dashed #1e2d45;color:#475569;padding:10px;border-radius:8px;font-size:12px;font-family:monospace}
.ctf{background:#111d2e;border:1px solid #1e2d45;border-radius:8px;padding:12px;margin-top:7px;flex-direction:column;gap:7px}
.cinp{width:100%;background:#0d1828;border:1px solid #1e2d45;color:#e2e8f0;padding:8px 10px;border-radius:6px;font-size:13px;outline:none}
.cf4{display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:5px}
.cf4 .cinp{font-size:11px;padding:6px 7px}
.cfbtn{background:#1d4ed8;color:#bfdbfe;padding:10px;border-radius:8px;font-size:13px;width:100%}
.bcc{background:#111d2e;border:1px solid #1e2d45;border-radius:12px;padding:16px;text-align:center;margin-bottom:10px}
.bcta{font-size:9px;letter-spacing:3px;color:#475569;font-family:monospace}
.bcn{font-size:46px;font-weight:bold;font-family:monospace;color:#4ade80;margin:5px 0 2px}
.bcn.warn{color:#fbbf24}.bcn.over{color:#f87171}
.bcs{font-size:12px;color:#475569}
.bcbar{margin:10px auto 4px;background:#0d1828;border-radius:8px;height:7px;max-width:260px}
.bcbf{height:100%;width:0%;background:linear-gradient(90deg,#1d4ed8,#4ade80);border-radius:8px;transition:width .5s}
.bcbf.warn{background:#fbbf24}.bcbf.over{background:#f87171}
.bcr{font-size:12px;color:#4ade80;margin-top:4px}.bcr.over{color:#f87171}
#mcards{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:10px}
.mc{background:#111d2e;border-radius:10px;padding:10px;text-align:center}
.mcl{font-size:9px;color:#475569;font-family:monospace;margin-bottom:3px}
.mcv{font-size:19px;font-weight:bold;font-family:monospace}
.mcg{font-size:9px;color:#334155;margin-bottom:4px}
.mcb{background:#0d1828;border-radius:4px;height:4px}
.mcbf{height:100%;border-radius:4px}
.mct{font-size:9px;margin-top:3px;opacity:.7}
.wcard{background:#111d2e;border:1px solid #1e2d45;border-radius:10px;padding:12px;margin-bottom:10px}
.wct{font-size:12px;color:#38bdf8;font-family:monospace;margin-bottom:9px}
.wrow{display:flex;align-items:center;gap:8px}
.winp{flex:1;background:#0d1828;border:1px solid #1e2d45;color:#e2e8f0;padding:9px 12px;border-radius:8px;font-size:16px;outline:none}
.wu{color:#475569;font-size:14px}
.wsv{background:#1d4ed8;color:#bfdbfe;padding:9px 16px;border-radius:8px;font-size:13px}
.wm{font-size:12px;color:#4ade80;margin-top:7px}
.cmp{background:#111d2e;border:1px solid #1e2d45;border-radius:10px;padding:12px}
.cmpt{font-size:10px;color:#475569;font-family:monospace;letter-spacing:1px;margin-bottom:8px}
.cmpr{display:flex;align-items:center;gap:10px;margin-bottom:4px}
.cmpb{flex:1;background:#0d1828;border-radius:6px;height:8px}
.cmpbf{height:100%;background:#4ade80;border-radius:6px;transition:width .4s;width:0%}
.cmpc{font-size:13px;color:#4ade80;font-family:monospace;flex-shrink:0}
.cmpm{font-size:12px;color:#475569}
.hdr2{display:flex;align-items:center;justify-content:space-between;margin-bottom:10px}
.hnav{background:#111d2e;border:1px solid #1e2d45;color:#94a3b8;width:34px;height:34px;border-radius:8px;font-size:14px;display:flex;align-items:center;justify-content:center}
.hmon{font-size:16px;color:#38bdf8;font-family:monospace;font-weight:bold}
.cgrid{display:grid;grid-template-columns:repeat(7,1fr);gap:3px;margin-bottom:10px}
.cdh{text-align:center;font-size:9px;color:#475569;font-family:monospace;padding:3px 0}
.cd{aspect-ratio:1;display:flex;align-items:center;justify-content:center;border-radius:6px;font-size:11px;font-family:monospace;cursor:pointer;background:#111d2e;border:1px solid transparent;color:#475569}
.cd.good{background:#052e16;border-color:#4ade80;color:#4ade80}
.cd.warn2{background:#1a0f00;border-color:#fbbf24;color:#fbbf24}
.cd.over2{background:#1c0a0a;border-color:#f87171;color:#f87171}
.cd.today{border-color:#38bdf8;color:#38bdf8}
.cd.sel{outline:2px solid #bfdbfe}
.cd.empty{background:transparent;border:none;cursor:default}
.sdl{margin-bottom:10px}
.sdlt{font-size:12px;color:#38bdf8;font-family:monospace;margin-bottom:7px;letter-spacing:1px}
.sdli{display:flex;justify-content:space-between;padding:5px 0;border-bottom:1px solid #1e2d45;font-size:12px;color:#94a3b8}
.sdlc{color:#fbbf24;font-family:monospace}
.rcard{background:#111d2e;border:1px solid #1e2d45;border-radius:10px;padding:12px;margin-bottom:10px}
.rct{font-size:10px;color:#475569;font-family:monospace;letter-spacing:1px;margin-bottom:9px}
#msumm{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:10px}
.ms{background:#0d1828;border-radius:8px;padding:9px;text-align:center}
.msv{font-size:17px;font-weight:bold;font-family:monospace;color:#fbbf24}
.msl{font-size:9px;color:#475569;margin-top:2px}
.pdfbtn{width:100%;background:linear-gradient(135deg,#1d4ed8,#4ade80);color:#fff;padding:11px;border-radius:8px;font-size:13px;font-weight:bold;letter-spacing:1px}
.wgcard{background:#111d2e;border:1px solid #1e2d45;border-radius:10px;padding:12px}
#wchart{width:100%}
.hpt{font-size:12px;color:#f87171;font-family:monospace;letter-spacing:1px;margin-bottom:9px}
#bgrid{display:grid;grid-template-columns:1fr 1fr;gap:6px;margin-bottom:12px}
.bg{background:#111d2e;border-radius:8px;padding:9px}
.bgn{font-size:10px;color:#475569;margin-bottom:2px}
.bgv{font-size:15px;font-weight:bold;font-family:monospace}
.bgv.ok{color:#4ade80}.bgv.warn{color:#fbbf24}.bgv.bad{color:#f87171}
.bgr{font-size:9px;color:#334155;margin-top:1px}
.supc{background:#111d2e;border:1px solid #1e2d45;border-radius:10px;padding:12px;margin-bottom:10px}
.supct{font-size:10px;color:#a78bfa;font-family:monospace;letter-spacing:1px;margin-bottom:9px}
.sup{display:flex;align-items:flex-start;gap:10px;padding:8px 0;border-bottom:1px solid #1e2d45}
.sup:last-child{border-bottom:none}
.supi{font-size:20px}
.supn{font-size:13px;color:#e2e8f0}.supd{font-size:11px;color:#a78bfa}.supw{font-size:10px;color:#475569}
.kcard{background:#110800;border:1px solid rgba(251,191,36,.3);border-radius:10px;padding:12px;margin-bottom:10px}
.kct{font-size:11px;color:#fbbf24;font-family:monospace;margin-bottom:6px}
.ktx{font-size:12px;color:#fde68a;line-height:1.6;margin-bottom:9px}
.wtr{background:#1a1200;border-radius:8px;padding:9px}
.wtlbl{font-size:10px;color:#475569;font-family:monospace;margin-bottom:6px}
.wtbs{display:flex;align-items:center;gap:8px;margin-bottom:6px}
.wtb{width:28px;height:28px;background:#1a2d44;color:#e2e8f0;border-radius:6px;font-size:16px;display:flex;align-items:center;justify-content:center}
.wtct{font-size:22px;font-weight:bold;color:#38bdf8;font-family:monospace;min-width:32px;text-align:center}
.wtu{font-size:11px;color:#475569}
.wtbar{background:#0d1828;border-radius:6px;height:6px;margin-bottom:4px}
.wtf{height:100%;background:#38bdf8;border-radius:6px;transition:width .3s}
.wtm{font-size:11px;color:#38bdf8}
.aicard{background:#0a0a1a;border:1px solid rgba(167,139,250,.3);border-radius:10px;padding:12px}
.ait{font-size:11px;color:#a78bfa;font-family:monospace;letter-spacing:1px;margin-bottom:9px}
.air{padding:7px 0;border-bottom:1px solid #1a1a2e;font-size:12px;color:#94a3b8;line-height:1.6}
.air:last-child{border-bottom:none}
.modal{position:fixed;inset:0;z-index:200;display:flex;align-items:flex-end;justify-content:center;background:rgba(0,0,0,.8)}
.mc2{background:#0d1828;border:1px solid #1e2d45;border-top-left-radius:16px;border-top-right-radius:16px;padding:20px 16px 40px;width:100%;max-width:500px}
.mc2ico{font-size:30px;text-align:center;margin-bottom:10px}
.mc2tit{font-size:15px;color:#38bdf8;font-weight:bold;margin-bottom:8px;text-align:center}
.mc2msg{font-size:13px;color:#94a3b8;line-height:1.5;margin-bottom:14px;text-align:center}
.mlbl{display:block;font-size:10px;color:#475569;font-family:monospace;letter-spacing:1px;margin:10px 0 4px}
.minp{width:100%;background:#080f1a;border:1px solid #1e2d45;color:#e2e8f0;padding:9px 12px;border-radius:8px;font-size:13px;outline:none}
.tinp{color:#38bdf8;border-color:#38bdf8;font-family:monospace}
.myes{width:100%;background:#1d4ed8;color:#fff;padding:12px;border-radius:8px;font-size:14px;margin-bottom:8px;margin-top:14px}
.mno{width:100%;background:transparent;border:1px solid #1e2d45;color:#475569;padding:10px;border-radius:8px;font-size:13px}
::-webkit-scrollbar{width:3px;height:3px}::-webkit-scrollbar-thumb{background:#1e2d45;border-radius:3px}
</style>
</head>
<body>
<div id="app">
<header id="hdr">
  <div class="hr1">
    <div>
      <div class="htag">VIJAY &middot; HEALTH OS &middot; AGE 41</div>
      <div class="htitle">Daily Protocol</div>
      <div class="hmeta" id="hdate"></div>
    </div>
    <div class="cbadge"><div class="cnum" id="cnum">0</div><div class="cunit">/ 1750 kcal</div></div>
  </div>
  <div id="wbanner" class="wbanner eve">
    <div>
      <div class="wbmode" id="wbmode">&#127749; EVENING GYM WEEK</div>
      <div class="wbsub" id="wbsub">This week: Gym 7:00 PM &middot; Wake 6:00 AM</div>
    </div>
    <div style="text-align:right">
      <div class="wbnxt" id="wbnxt">Next switch: Monday</div>
      <button class="wbov" data-action="override">Override</button>
    </div>
  </div>
  <div class="ctrack"><div class="cfill" id="cfill"></div></div>
  <div class="tnav">
    <button class="tb" data-action="tab" data-id="sch">&#128197; Schedule</button>
    <button class="tb" data-action="tab" data-id="food">&#129367; Food</button>
    <button class="tb" data-action="tab" data-id="today">&#128202; Today</button>
    <button class="tb" data-action="tab" data-id="hist">&#128198; History</button>
    <button class="tb" data-action="tab" data-id="health">Health</button>
  </div>
</header>
<main id="main">
  <div id="p-sch" style="display:none">
    <p class="hint">&#9999; Pencil to edit &nbsp;&middot;&nbsp; Circle to mark done &nbsp;&middot;&nbsp; &#128274; Fixed medical time</p>
    <div id="slist"></div>
  </div>
  <div id="p-food" style="display:none">
    <div class="flbl">SELECT MEAL SLOT (auto-filters food list)</div>
    <div class="fslots" id="slots"></div>
    <div class="catrow" id="cats"></div>
    <input id="fsrch" class="fsrch" type="text" placeholder="&#128269; Search food...">
    <div id="flist"></div>
    <div id="tlog"></div>
    <div class="ctwrap">
      <button class="cttog" data-action="togcf">+ Add Custom Food</button>
      <div id="cform" class="ctf" style="display:none">
        <input id="cfn" class="cinp" type="text" placeholder="Food name">
        <div class="cf4">
          <input id="cfc" class="cinp" type="number" placeholder="Calories">
          <input id="cfp" class="cinp" type="number" placeholder="Protein g">
          <input id="cfca" class="cinp" type="number" placeholder="Carbs g">
          <input id="cff" class="cinp" type="number" placeholder="Fat g">
        </div>
        <button class="cfbtn" data-action="addcf">Add to Log</button>
      </div>
    </div>
  </div>
  <div id="p-today" style="display:none">
    <div class="bcc">
      <div class="bcta">TODAY'S CALORIES</div>
      <div class="bcn" id="bcn">0</div>
      <div class="bcs">of 1,750 kcal target</div>
      <div class="bcbar"><div class="bcbf" id="bcbf"></div></div>
      <div class="bcr" id="bcr">1,750 kcal remaining</div>
    </div>
    <div id="mcards"></div>
    <div class="wcard">
      <div class="wct">Today's Weight</div>
      <div class="wrow">
        <input id="wi" class="winp" type="number" step="0.1" placeholder="e.g. 94.5">
        <span class="wu">kg</span>
        <button class="wsv" data-action="saveweight">Save</button>
      </div>
      <div class="wm" id="wm"></div>
    </div>
    <div class="cmp">
      <div class="cmpt">SCHEDULE COMPLETION</div>
      <div class="cmpr"><div class="cmpb"><div class="cmpbf" id="cmpbf"></div></div><span class="cmpc" id="cmpc">0/14</span></div>
      <div class="cmpm" id="cmpm">Tap items in Schedule to mark done.</div>
    </div>
  </div>
  <div id="p-hist" style="display:none">
    <div class="hdr2">
      <button class="hnav" data-action="prevm">&#9664;</button>
      <div class="hmon" id="hmon">April 2026</div>
      <button class="hnav" data-action="nextm">&#9654;</button>
    </div>
    <div id="cgrid" class="cgrid"></div>
    <div id="sdlog" class="sdl"></div>
    <div class="rcard">
      <div class="rct">MONTHLY SUMMARY</div>
      <div id="msumm"></div>
      <button class="pdfbtn" data-action="dlrep">&#128196; Download Monthly Report</button>
    </div>
    <div class="wgcard"><div class="rct">WEIGHT TREND</div><canvas id="wchart" height="120"></canvas></div>
  </div>
  <div id="p-health" style="display:none">
    <div class="hpt">BLOOD REPORT &mdash; 24 APR 2026</div>
    <div id="bgrid"></div>
    <div class="supc"><div class="supct">DAILY SUPPLEMENTS</div><div id="suplist"></div></div>
    <div class="kcard">
      <div class="kct">&#128167; KIDNEY STONE ALERT</div>
      <div class="ktx">Urine oxalate <strong>8.80/hpf</strong> (normal 0&ndash;0.99). Drink <strong>4 litres daily</strong> + lemon juice.</div>
      <div class="wtr">
        <div class="wtlbl">TODAY'S WATER</div>
        <div class="wtbs">
          <button class="wtb" data-action="adjwater" data-d="-1">&#8722;</button>
          <span class="wtct" id="wtct">0</span>
          <button class="wtb" data-action="adjwater" data-d="1">+</button>
          <span class="wtu">glasses of 250ml</span>
        </div>
        <div class="wtbar"><div class="wtf" id="wtf"></div></div>
        <div class="wtm" id="wtm">Target: 16 glasses = 4 litres</div>
      </div>
    </div>
    <div class="aicard">
      <div class="ait">AI RECOMMENDATIONS (Based on Blood Report)</div>
      <div id="airecs"></div>
    </div>
  </div>
</main>
</div>
<div id="nmod" class="modal" style="display:none">
  <div class="mc2">
    <div class="mc2ico">&#128276;</div>
    <div class="mc2tit">Enable Daily Reminders</div>
    <div class="mc2msg">Get phone alerts for meals, medication, gym and weekly schedule switches.</div>
    <button class="myes" data-action="enn">Enable Reminders</button>
    <button class="mno" data-action="closenmod">Not now</button>
  </div>
</div>
<div id="emod" class="modal" style="display:none">
  <div class="mc2">
    <div class="mc2ico" id="eico">?</div>
    <div class="mc2tit">Edit Slot</div>
    <label class="mlbl">Time</label><input type="time" id="etm" class="minp tinp">
    <label class="mlbl">Label</label><input type="text" id="elb" class="minp">
    <label class="mlbl">Notes</label><input type="text" id="edt" class="minp">
    <button class="myes" data-action="saveed">&#10003; Save</button>
    <button class="mno"  data-action="closeed">&#10005; Cancel</button>
  </div>
</div>
<script>
var SCHED_EVE=[{id:"wake",t:"06:00",lb:"Wake Up",ic:"🌅",dt:"2 glasses warm water. 5 min sunlight.",tp:"routine",fx:false},{id:"rout",t:"06:15",lb:"Morning Routine",ic:"🧘",dt:"Brush, freshen up. 10 min light stretch.",tp:"routine",fx:false},{id:"walk",t:"06:30",lb:"Morning Walk",ic:"🚶",dt:"30 min brisk walk. 90-100 steps/min.",tp:"activity",fx:false},{id:"bkf",t:"07:15",lb:"Breakfast",ic:"🥗",dt:"Moong dal chilla or idli + low-fat curd. No sugar.",tp:"meal",fx:false},{id:"meds",t:"10:00",lb:"Sugar Tabs",ic:"💊",dt:"Diabetes medication as prescribed. Take with water.",tp:"meds",fx:true},{id:"frt",t:"11:00",lb:"Fruit Time",ic:"🍎",dt:"1 low-GI fruit: guava or apple or pear. No banana or mango.",tp:"meal",fx:true},{id:"lnch",t:"13:00",lb:"Lunch",ic:"🍱",dt:"Brown rice half cup + dal + sabzi + salad. Eat salad first.",tp:"meal",fx:true},{id:"lwlk",t:"13:30",lb:"Post-Lunch Walk",ic:"🚶",dt:"10-15 min slow walk. Reduces post-meal glucose spike.",tp:"activity",fx:true},{id:"prot",t:"16:30",lb:"Protein Intake",ic:"💪",dt:"Whey protein 1 scoop + chaas OR sprouts chaat. 30g protein.",tp:"meal",fx:true},{id:"b12",t:"17:00",lb:"B12 + Omega-3",ic:"💊",dt:"Methylcobalamin 1500mcg + Omega-3 1g. After protein snack.",tp:"meds",fx:true},{id:"gym",t:"19:00",lb:"Gym Session",ic:"🏋️",dt:"Warm up 10 min. 50-55 min. No deep squats. Protect knees.",tp:"gym",fx:false},{id:"din",t:"20:30",lb:"Dinner",ic:"🌙",dt:"2 multigrain rotis + sabzi or dal. Finish before 9 PM.",tp:"meal",fx:false},{id:"ewlk",t:"21:00",lb:"Post-Dinner Walk",ic:"🌳",dt:"15-20 min slow walk. Mandatory every night.",tp:"activity",fx:false},{id:"slp",t:"22:30",lb:"Sleep",ic:"🛌",dt:"7.5 hrs target. No screens 30 min before.",tp:"routine",fx:false}];
var SCHED_MORN=[{id:"wake",t:"05:30",lb:"Wake Up",ic:"🌅",dt:"2 glasses warm water. Early rise for gym. 5 min sunlight.",tp:"routine",fx:false},{id:"rout",t:"05:45",lb:"Morning Routine",ic:"🧘",dt:"Quick brush. Gym kit ready. Light warm-up.",tp:"routine",fx:false},{id:"gym",t:"06:30",lb:"Gym Session",ic:"🏋️",dt:"Fasted training. Warm up 10 min. 50-55 min. No deep squats.",tp:"gym",fx:false},{id:"pgp",t:"07:30",lb:"Post-Gym Protein",ic:"💪",dt:"Whey protein 1 scoop within 30 min of gym. Critical.",tp:"meal",fx:false},{id:"bkf",t:"08:00",lb:"Breakfast",ic:"🥗",dt:"Moong dal chilla or idli + low-fat curd. No sugar.",tp:"meal",fx:false},{id:"meds",t:"10:00",lb:"Sugar Tabs",ic:"💊",dt:"Diabetes medication as prescribed. Take with water.",tp:"meds",fx:true},{id:"frt",t:"11:00",lb:"Fruit Time",ic:"🍎",dt:"1 low-GI fruit: guava or apple or pear. No banana or mango.",tp:"meal",fx:true},{id:"lnch",t:"13:00",lb:"Lunch",ic:"🍱",dt:"Brown rice half cup + dal + sabzi + salad. Eat salad first.",tp:"meal",fx:true},{id:"lwlk",t:"13:30",lb:"Post-Lunch Walk",ic:"🚶",dt:"10-15 min slow walk. Reduces post-meal glucose spike.",tp:"activity",fx:true},{id:"prot",t:"16:30",lb:"Evening Snack",ic:"💪",dt:"Roasted chana or sprouts chaat. 30g protein target.",tp:"meal",fx:true},{id:"b12",t:"17:00",lb:"B12 + Omega-3",ic:"💊",dt:"Methylcobalamin 1500mcg + Omega-3 1g.",tp:"meds",fx:true},{id:"ewlk",t:"17:30",lb:"Evening Walk",ic:"🌳",dt:"30 min outdoor walk. Vitamin D + extra cardio.",tp:"activity",fx:false},{id:"din",t:"20:00",lb:"Dinner",ic:"🌙",dt:"2 multigrain rotis + sabzi or dal. Finish by 8:30 PM.",tp:"meal",fx:false},{id:"pdwlk",t:"20:30",lb:"Post-Dinner Walk",ic:"🌳",dt:"15-20 min slow walk. Mandatory.",tp:"activity",fx:false},{id:"slp",t:"22:00",lb:"Sleep",ic:"🛌",dt:"7.5 hrs target. Earlier sleep on morning gym weeks.",tp:"routine",fx:false}];
var FOODS=[{id:1,nm:"Moong Dal Chilla",un:"1 piece",cal:130,p:8,c:18,f:3,ct:"Breakfast",ox:false},{id:2,nm:"Idli",un:"1 piece",cal:75,p:2,c:15,f:1,ct:"Breakfast",ox:false},{id:3,nm:"Dosa (plain)",un:"1 piece",cal:180,p:4,c:32,f:4,ct:"Breakfast",ox:false},{id:4,nm:"Oats (cooked)",un:"1 bowl",cal:150,p:5,c:27,f:3,ct:"Breakfast",ox:false},{id:5,nm:"Methi Thepla",un:"1 piece",cal:120,p:4,c:20,f:3,ct:"Breakfast",ox:false},{id:6,nm:"Besan Chilla",un:"1 piece",cal:115,p:7,c:14,f:3,ct:"Breakfast",ox:false},{id:7,nm:"Brown Rice",un:"half cup",cal:108,p:2,c:22,f:1,ct:"Main",ox:false},{id:8,nm:"Multigrain Roti",un:"1 piece",cal:110,p:4,c:22,f:2,ct:"Main",ox:false},{id:9,nm:"Wheat Roti",un:"1 piece",cal:120,p:3,c:25,f:1,ct:"Main",ox:false},{id:10,nm:"Masoor Dal",un:"1 bowl",cal:150,p:9,c:25,f:2,ct:"Main",ox:false},{id:11,nm:"Moong Dal",un:"1 bowl",cal:140,p:8,c:24,f:1,ct:"Main",ox:false},{id:12,nm:"Rajma Curry",un:"1 bowl",cal:180,p:11,c:30,f:2,ct:"Main",ox:false},{id:13,nm:"Chana (cooked)",un:"1 bowl",cal:165,p:9,c:28,f:2,ct:"Main",ox:false},{id:14,nm:"Tofu (plain)",un:"100g",cal:80,p:9,c:2,f:4,ct:"Main",ox:false},{id:15,nm:"Paneer (low-fat)",un:"75g",cal:180,p:13,c:3,f:13,ct:"Main",ox:false},{id:16,nm:"Mixed Veg Sabzi",un:"1 bowl",cal:90,p:3,c:12,f:3,ct:"Main",ox:false},{id:17,nm:"Bhindi Sabzi",un:"1 bowl",cal:80,p:2,c:10,f:3,ct:"Main",ox:false},{id:18,nm:"Lauki Sabzi",un:"1 bowl",cal:55,p:2,c:8,f:2,ct:"Main",ox:false},{id:19,nm:"Sambar",un:"1 bowl",cal:100,p:5,c:15,f:2,ct:"Main",ox:false},{id:20,nm:"Cucumber Raita",un:"1 bowl",cal:80,p:4,c:8,f:3,ct:"Main",ox:false},{id:21,nm:"Salad (no dressing)",un:"1 bowl",cal:40,p:2,c:8,f:0,ct:"Main",ox:false},{id:22,nm:"Khichdi",un:"1 bowl",cal:220,p:8,c:38,f:4,ct:"Main",ox:false},{id:23,nm:"Palak Sabzi (limit)",un:"half bowl",cal:60,p:2,c:6,f:3,ct:"Main",ox:true},{id:24,nm:"Curd/Dahi (low-fat)",un:"1 bowl",cal:98,p:6,c:8,f:4,ct:"Protein",ox:false},{id:25,nm:"Buttermilk/Chaas",un:"1 glass",cal:60,p:3,c:8,f:1,ct:"Protein",ox:false},{id:26,nm:"Whey Protein (plain)",un:"1 scoop 30g",cal:120,p:24,c:3,f:2,ct:"Protein",ox:false},{id:27,nm:"Low-fat Milk",un:"1 glass",cal:120,p:8,c:12,f:3,ct:"Protein",ox:false},{id:28,nm:"Soya Chunks",un:"1 bowl",cal:100,p:15,c:8,f:1,ct:"Protein",ox:false},{id:29,nm:"Sprouts (boiled)",un:"1 bowl",cal:90,p:7,c:15,f:1,ct:"Protein",ox:false},{id:30,nm:"Guava",un:"1 medium",cal:55,p:2,c:12,f:1,ct:"Fruit",ox:false},{id:31,nm:"Apple (half)",un:"half",cal:40,p:0,c:11,f:0,ct:"Fruit",ox:false},{id:32,nm:"Pear (half)",un:"half",cal:38,p:0,c:10,f:0,ct:"Fruit",ox:false},{id:33,nm:"Jamun",un:"small bowl",cal:48,p:1,c:11,f:0,ct:"Fruit",ox:false},{id:34,nm:"Amla/Gooseberry",un:"2 pieces",cal:22,p:0,c:5,f:0,ct:"Fruit",ox:false},{id:35,nm:"Roasted Chana",un:"30g fistful",cal:100,p:7,c:16,f:2,ct:"Snack",ox:false},{id:36,nm:"Walnuts",un:"2-3 halves",cal:65,p:2,c:1,f:6,ct:"Snack",ox:false},{id:37,nm:"Almonds (max 4)",un:"4 only",cal:28,p:1,c:1,f:2,ct:"Snack",ox:true},{id:38,nm:"Makhana (fox nuts)",un:"1 cup 25g",cal:90,p:3,c:19,f:0,ct:"Snack",ox:false},{id:39,nm:"Sprouts Chaat",un:"1 bowl",cal:90,p:7,c:15,f:1,ct:"Snack",ox:false},{id:40,nm:"Flaxseeds (ground)",un:"1 tbsp",cal:37,p:1,c:2,f:3,ct:"Snack",ox:false},{id:41,nm:"Chia Seeds",un:"1 tbsp",cal:49,p:2,c:4,f:3,ct:"Snack",ox:false},{id:42,nm:"Green Tea",un:"1 cup",cal:2,p:0,c:0,f:0,ct:"Drink",ox:false},{id:43,nm:"Black Coffee",un:"1 cup",cal:5,p:0,c:1,f:0,ct:"Drink",ox:false},{id:44,nm:"Coconut Water",un:"1 glass",cal:46,p:1,c:10,f:0,ct:"Drink",ox:false},{id:45,nm:"Fenugreek Water",un:"1 glass",cal:10,p:0,c:2,f:0,ct:"Drink",ox:false},{id:46,nm:"Lemon Water",un:"1 glass",cal:8,p:0,c:2,f:0,ct:"Drink",ox:false}];
var MSLOTS=[["breakfast","Breakfast","7:15 AM"],["fruit","Fruit","11 AM"],["lunch","Lunch","1 PM"],["protein","Protein","4:30 PM"],["dinner","Dinner","8:30 PM"],["other","Other","--"]];
var SLOT_CAT={"breakfast": "Breakfast", "fruit": "Fruit", "lunch": "Main", "protein": "Protein", "dinner": "Main", "other": "All"};
var BLOOD=[{nm:"HbA1c",vl:"6.7%",rf:"<5.6%",st:"bad"},{nm:"Fasting Glucose",vl:"133 mg/dL",rf:"70-99",st:"bad"},{nm:"Triglycerides",vl:"367 mg/dL",rf:"<150",st:"bad"},{nm:"HDL Cholesterol",vl:"22 mg/dL",rf:">40",st:"bad"},{nm:"Vitamin B12",vl:"<148 pg/mL",rf:"187-833",st:"bad"},{nm:"Vitamin D",vl:"20.8 ng/mL",rf:"30-100",st:"warn"},{nm:"VLDL Cholesterol",vl:"73 mg/dL",rf:"<30",st:"bad"},{nm:"Urine Oxalate",vl:"8.80/hpf",rf:"0-0.99",st:"bad"},{nm:"LDL Cholesterol",vl:"33 mg/dL",rf:"<100",st:"ok"},{nm:"Total Cholesterol",vl:"128 mg/dL",rf:"<200",st:"ok"},{nm:"Liver SGOT",vl:"18 U/L",rf:"11-34",st:"ok"},{nm:"Creatinine",vl:"1.05",rf:"0.6-1.3",st:"ok"}];
var SUPPS=[{ic:"💊",nm:"Methylcobalamin B12",ds:"1500mcg daily after breakfast",wy:"Critically low <148. Normal 187-833"},{ic:"☀",nm:"Vitamin D3",ds:"60,000 IU weekly with lunch",wy:"Insufficient 20.8. Target 30-100"},{ic:"🐟",nm:"Omega-3 (Algae/Flax)",ds:"1g daily with dinner",wy:"Reduces Triglycerides 367 to <150"},{ic:"🌿",nm:"Magnesium Glycinate",ds:"200mg before sleep",wy:"Improves insulin sensitivity"}];
var AIRECS=[{t:"Reduce carbs to 110g/day",d:"Triglycerides 367 are driven by carbohydrates. Most impactful change."},{t:"2 walnuts + 1 tbsp flaxseeds daily",d:"Omega-3 lowers triglycerides and raises HDL over 8-12 weeks."},{t:"2-3 raw garlic cloves with meals",d:"Reduces triglycerides 10-15% and raises HDL. Add to dal."},{t:"Limit spinach and almonds strictly",d:"Oxalate crystals 8.80/hpf (normal 0-0.99). Kidney stone risk is high."},{t:"4 litres water + lemon daily",d:"Citrate in lemon prevents calcium oxalate crystals forming."},{t:"No fruit juice ever",d:"Fasting glucose 133 is diabetic range. Juice causes rapid glucose spike."},{t:"No deep squats or lunges yet",d:"Gym assessment shows weak knees. Use leg press machine only."},{t:"Ask doctor about B12 injection",d:"Oral B12 absorbs poorly below 148. Monthly injection may be needed."},{t:"Fenugreek (methi) daily",d:"Soak 1 tsp overnight, drink water in morning. Lowers fasting glucose."},{t:"Next blood test in 3 months",d:"HbA1c needs 3-monthly monitoring. Target: <6.0 in 6 months."}];
var CAL=1750,PRO=140,CARB=110,FAT=70,H2O=16;
var REF_MON=new Date(2026,3,27);
var MONTHS=['January','February','March','April','May','June','July','August','September','October','November','December'];
var ST={done:{},food:{},wts:{},h2o:{},ov:{},tab:'sch',slot:'lunch',cat:'All',hy:new Date().getFullYear(),hm:new Date().getMonth(),selD:null};
var _editId=null,_cfOpen=false;

function save(){try{localStorage.setItem(‘vh6’,JSON.stringify({d:ST.done,f:ST.food,w:ST.wts,h:ST.h2o,o:ST.ov}));}catch(e){}}
function load(){try{var v=localStorage.getItem(‘vh6’);if(v){var x=JSON.parse(v);ST.done=x.d||{};ST.food=x.f||{};ST.wts=x.w||{};ST.h2o=x.h||{};ST.ov=x.o||{};}}catch(e){}}
function dk(){return new Date().toISOString().split(‘T’)[0];}
function ge(id){return document.getElementById(id);}
function p2(n){return n<10?‘0’+n:’’+n;}
function f12(t){var p=t.split(’:’);var h=parseInt(p[0]);return(h%12||12)+’:’+p[1]+’ ’+(h<12?‘AM’:‘PM’);}
function tlog(){return ST.food[dk()]||[];}
function tdone(){return ST.done[dk()]||[];}
function tots(lg){var L=lg||tlog();return L.reduce(function(a,i){return{cal:a.cal+i.cal*i.qty,p:a.p+i.p*i.qty,c:a.c+i.c*i.qty,f:a.f+i.f*i.qty};},{cal:0,p:0,c:0,f:0});}
function getMon(date){var d=new Date(date);var day=d.getDay();d.setDate(d.getDate()+(day===0?-6:1-day));d.setHours(0,0,0,0);return d;}
function getAutoMode(){var w=Math.round((getMon(new Date())-REF_MON)/(7*24*60*60*1000));return w%2===0?‘eve’:‘morn’;}
function getMode(){var k=getMon(new Date()).toISOString().split(‘T’)[0];return ST.ov[k]||getAutoMode();}
function daysToMon(){var d=new Date().getDay();return d===1?7:(d===0?1:(8-d)%7);}
function manualOverride(){var k=getMon(new Date()).toISOString().split(‘T’)[0];ST.ov[k]=getMode()===‘eve’?‘morn’:‘eve’;save();updateBanner();rSched();}

function updateBanner(){
var mode=getMode();var days=daysToMon();
var nxt=mode===‘eve’?‘morn’:‘eve’;var nxtLbl=nxt===‘morn’?‘Morning’:‘Evening’;
var b=ge(‘wbanner’);
if(mode===‘eve’){b.className=‘wbanner eve’;ge(‘wbmode’).textContent=’\uD83C\uDF05 EVENING GYM WEEK’;ge(‘wbsub’).textContent=‘This week: Gym 7:00 PM \u00B7 Wake 6:00 AM’;}
else{b.className=‘wbanner morn’;ge(‘wbmode’).textContent=’\uD83C\uDF05 MORNING GYM WEEK’;ge(‘wbsub’).textContent=‘This week: Gym 6:30 AM \u00B7 Wake 5:30 AM’;}
ge(‘wbnxt’).textContent=‘Switches to ‘+nxtLbl+’ in ‘+days+(days===1?’ day’:’ days’);
}

function go(tab){
ST.tab=tab;
var all=[‘sch’,‘food’,‘today’,‘hist’,‘health’];
for(var i=0;i<all.length;i++){
var panel=ge(‘p-’+all[i]);
if(panel) panel.style.display=(all[i]===tab)?‘block’:‘none’;
}
var btns=document.querySelectorAll(’[data-action=“tab”]’);
for(var j=0;j<btns.length;j++){
btns[j].className=‘tb’+(btns[j].getAttribute(‘data-id’)===tab?’ on’:’’);
}
if(tab===‘sch’){rSched();}
if(tab===‘food’){rSlots();rCats();rFL();rTlog();}
if(tab===‘today’){rToday();}
if(tab===‘hist’){rHist();}
if(tab===‘health’){rHealth();}
}

var ntm=[];
function enN(){
if(!(‘Notification’in window)){ge(‘nmod’).style.display=‘none’;return;}
Notification.requestPermission().then(function(p){ge(‘nmod’).style.display=‘none’;if(p===‘granted’) schedN();});
}
function schedN(){
ntm.forEach(clearTimeout);ntm=[];
if(!(‘Notification’in window)||Notification.permission!==‘granted’) return;
var now=Date.now();var sched=getMode()===‘eve’?SCHED_EVE:SCHED_MORN;
for(var i=0;i<sched.length;i++){
(function(item){
var parts=item.t.split(’:’);var h=parseInt(parts[0]);var m=parseInt(parts[1]);
var d=new Date();d.setHours(h,m,0,0);var ms=d-now;
if(ms>0&&ms<86400000){
ntm.push(setTimeout(function(){
try{new Notification(’\u23F0 ‘+item.lb,{body:item.dt,icon:’./icons/icon-192.png’,tag:item.id,requireInteraction:item.tp===‘meds’});}catch(e){}
},ms));
}
})(sched[i]);
}
// Sunday 8PM switch reminder
var day=new Date().getDay();var dts=day===0?7:(7-day)%7||7;
var sun=new Date();sun.setDate(sun.getDate()+dts);sun.setHours(20,0,0,0);var msSun=sun-now;
if(msSun>0&&msSun<8*24*60*60*1000){
var nxtMode=getMode()===‘eve’?‘morning’:‘evening’;var wakeT=nxtMode===‘morning’?‘5:30 AM’:‘6:00 AM’;
ntm.push(setTimeout(function(){
try{new Notification(‘Schedule switches tomorrow!’,{body:‘Tomorrow: ‘+nxtMode+’ gym week. Wake at ‘+wakeT,icon:’./icons/icon-192.png’,requireInteraction:true});}catch(e){}
},msSun));
}
}
function showNP(){
if(!(‘Notification’in window)) return;
if(Notification.permission===‘default’) setTimeout(function(){ge(‘nmod’).style.display=‘flex’;},1500);
else if(Notification.permission===‘granted’) schedN();
}

function rSched(){
var sched=getMode()===‘eve’?SCHED_EVE:SCHED_MORN;
var done=tdone();
var sorted=sched.slice().sort(function(a,b){return a.t>b.t?1:-1;});
var h=’’;
for(var i=0;i<sorted.length;i++){
var item=sorted[i];var isDone=done.indexOf(item.id)>=0;
var dc=isDone?’ done’:’’;var oc=isDone?’ on’:’’;
h+=’<div class="si'+dc+'" data-t="'+item.tp+'">’;
h+=’<button class="sdb'+oc+'" data-action="done" data-id="'+item.id+'">’+(isDone?’\u2713’:’’)+’</button>’;
h+=’<span class="sico">’+item.ic+’</span>’;
h+=’<div class="sinfo"><div class="sr"><span class="sil'+dc+'">’+item.lb+’</span><span class="stm">’+f12(item.t)+’</span></div>’;
h+=’<div class="sdt">’+item.dt+’</div>’;
if(item.fx) h+=’<div class="fbadge">\uD83D\uDD12 Fixed medical time</div>’;
h+=’</div>’;
if(!item.fx) h+=’<button class="seb" data-action="edit" data-id="'+item.id+'">\u270F\uFE0F</button>’;
else h+=’<span class="sph"></span>’;
h+=’</div>’;
}
var el=ge(‘slist’);if(el) el.innerHTML=h;
}

function tD(id){
var d=dk();if(!ST.done[d]) ST.done[d]=[];
var arr=ST.done[d];var idx=arr.indexOf(id);
if(idx===-1) arr.push(id); else arr.splice(idx,1);
save();rSched();updCal();if(ST.tab===‘today’) rToday();
}
function openEd(id){
var sched=getMode()===‘eve’?SCHED_EVE:SCHED_MORN;
var item=null;for(var i=0;i<sched.length;i++){if(sched[i].id===id){item=sched[i];break;}}
if(!item) return;
_editId=id;ge(‘eico’).textContent=item.ic;ge(‘etm’).value=item.t;ge(‘elb’).value=item.lb;ge(‘edt’).value=item.dt;
ge(‘emod’).style.display=‘flex’;
}
function saveEd(){
if(!_editId) return;
var sched=getMode()===‘eve’?SCHED_EVE:SCHED_MORN;
for(var i=0;i<sched.length;i++){if(sched[i].id===_editId){sched[i].t=ge(‘etm’).value;sched[i].lb=ge(‘elb’).value;sched[i].dt=ge(‘edt’).value;}}
_editId=null;ge(‘emod’).style.display=‘none’;schedN();rSched();
}
function closeEd(){_editId=null;ge(‘emod’).style.display=‘none’;}

// ── FOOD SLOT — auto-switches category filter ──
function setSlot(id){
ST.slot=id;
// Auto-switch category when slot changes
if(SLOT_CAT&&SLOT_CAT[id]) ST.cat=SLOT_CAT[id];
rSlots();rCats();rFL();
}

function rSlots(){
var h=’’;
for(var i=0;i<MSLOTS.length;i++){
var s=MSLOTS[i];
h+=’<button class="slb'+(ST.slot===s[0]?' on':'')+'" data-action="slot" data-id="'+s[0]+'">’+s[1]+’<span>’+s[2]+’</span></button>’;
}
var el=ge(‘slots’);if(el) el.innerHTML=h;
}

function rCats(){
var cats=[‘All’,‘Breakfast’,‘Main’,‘Protein’,‘Fruit’,‘Snack’,‘Drink’];
var h=’’;
for(var i=0;i<cats.length;i++) h+=’<button class="cb'+(ST.cat===cats[i]?' on':'')+'" data-action="cat" data-id="'+cats[i]+'">’+cats[i]+’</button>’;
var el=ge(‘cats’);if(el) el.innerHTML=h;
}
function setCat(c){ST.cat=c;rCats();rFL();}

function rFL(){
var srch=ge(‘fsrch’);var q=srch?srch.value.toLowerCase():’’;
var fl=[];
for(var i=0;i<FOODS.length;i++){var f=FOODS[i];if(f.nm.toLowerCase().indexOf(q)>=0&&(ST.cat===‘All’||f.ct===ST.cat)) fl.push(f);}
var el=ge(‘flist’);if(!el) return;
if(!fl.length){el.innerHTML=’<div class="nores">No foods found. Try Add Custom Food.</div>’;return;}
var h=’’;
for(var i=0;i<fl.length;i++){
var f=fl[i];
h+=’<div class="fi"><div class="finf"><div class="finm">’+f.nm+’</div><div class="fimt">’+f.un+’ \u00B7 P:’+f.p+‘g C:’+f.c+‘g F:’+f.f+‘g</div>’;
if(f.ox) h+=’<div class="fiwx">\u26A0 High oxalate \u2014 limit!</div>’;
h+=’</div><div class="fcal">’+f.cal+’ kcal</div><button class="fadd" data-action="addf" data-id="'+f.id+'">+</button></div>’;
}
el.innerHTML=h;
}

function addF(fid){
var food=null;for(var i=0;i<FOODS.length;i++){if(FOODS[i].id===fid){food=FOODS[i];break;}}
if(!food) return;
var d=dk();if(!ST.food[d]) ST.food[d]=[];
ST.food[d].push({id:food.id,nm:food.nm,un:food.un,cal:food.cal,p:food.p,c:food.c,f:food.f,ox:food.ox,qty:1,slot:ST.slot,lid:Date.now()});
save();rTlog();updCal();if(ST.tab===‘today’) rToday();
}
function adjQ(lid,delta){
var d=dk();
ST.food[d]=(ST.food[d]||[]).map(function(i){
if(i.lid!==lid) return i;
var q=Math.round((i.qty+delta)*2)/2;
return q>0?{id:i.id,nm:i.nm,un:i.un,cal:i.cal,p:i.p,c:i.c,f:i.f,ox:i.ox,qty:q,slot:i.slot,lid:i.lid}:null;
}).filter(Boolean);
save();rTlog();updCal();if(ST.tab===‘today’) rToday();
}
function rmF(lid){
var d=dk();ST.food[d]=(ST.food[d]||[]).filter(function(i){return i.lid!==lid;});
save();rTlog();updCal();if(ST.tab===‘today’) rToday();
}
function rTlog(){
var log=tlog();var el=ge(‘tlog’);if(!el) return;
if(!log.length){el.innerHTML=’’;return;}
var t=tots(log);var by={};
for(var i=0;i<log.length;i++){if(!by[log[i].slot]) by[log[i].slot]=[];by[log[i].slot].push(log[i]);}
var h=’<div class="tlog"><div class="tlhdr">TODAY \u2014 ‘+Math.round(t.cal)+’ / ‘+CAL+’ kcal</div>’;
for(var si=0;si<MSLOTS.length;si++){
var sl=MSLOTS[si];var items=by[sl[0]];if(!items) continue;
var sc=Math.round(items.reduce(function(s,f){return s+f.cal*f.qty;},0));
h+=’<div style="margin-bottom:8px"><div class="tlsn"><span>’+sl[1]+’</span><span class="tlsc">’+sc+’ kcal</span></div>’;
for(var ii=0;ii<items.length;ii++){
var it=items[ii];
h+=’<div class="li"><div class="linf"><div class="linm">’+it.nm+’</div><div class="limt">’+it.un+’</div>’;
if(it.ox) h+=’<div class="liwx">\u26A0 High oxalate</div>’;
h+=’</div><div class="qc"><button class="qb" data-action="adjq" data-lid="'+it.lid+'" data-d="-0.5">\u2212</button>’;
h+=’<span class="qv">\u00D7’+it.qty+’</span>’;
h+=’<button class="qb" data-action="adjq" data-lid="'+it.lid+'" data-d="0.5">+</button></div>’;
h+=’<div class="lcal">’+Math.round(it.cal*it.qty)+’</div>’;
h+=’<button class="lrm" data-action="rmf" data-id="'+it.lid+'">\u00D7</button></div>’;
}
h+=’</div>’;
}
h+=’<div class="tmac"><div class="tmc"><div class="tmcv" style="color:#38bdf8">’+Math.round(t.p)+‘g</div><div class="tmcl">Protein</div></div>’;
h+=’<div class="tmc"><div class="tmcv" style="color:#fbbf24">’+Math.round(t.c)+‘g</div><div class="tmcl">Carbs</div></div>’;
h+=’<div class="tmc"><div class="tmcv" style="color:#a78bfa">’+Math.round(t.f)+‘g</div><div class="tmcl">Fat</div></div></div></div>’;
el.innerHTML=h;
}
function togCF(){_cfOpen=!_cfOpen;var f=ge(‘cform’);if(f) f.style.display=_cfOpen?‘flex’:‘none’;}
function addCF(){
var nm=ge(‘cfn’).value.trim();var cal=parseFloat(ge(‘cfc’).value)||0;
if(!nm||!cal) return;
var d=dk();if(!ST.food[d]) ST.food[d]=[];
ST.food[d].push({id:Date.now(),nm:nm,un:‘1 serving’,cal:cal,p:parseFloat(ge(‘cfp’).value)||0,c:parseFloat(ge(‘cfca’).value)||0,f:parseFloat(ge(‘cff’).value)||0,ox:false,qty:1,slot:ST.slot,lid:Date.now()+1});
[‘cfn’,‘cfc’,‘cfp’,‘cfca’,‘cff’].forEach(function(id){ge(id).value=’’;});
_cfOpen=false;var f=ge(‘cform’);if(f) f.style.display=‘none’;
save();rTlog();updCal();
}

function updCal(){
var t=tots();var pct=Math.min(100,(t.cal/CAL)*100);
var cls=pct>95?‘over’:pct>75?‘warn’:’’;
var cn=ge(‘cnum’);if(cn){cn.textContent=Math.round(t.cal);cn.className=‘cnum’+(cls?’ ‘+cls:’’);}
var cf=ge(‘cfill’);if(cf){cf.style.width=pct+’%’;cf.style.background=pct>95?’#f87171’:pct>75?’#fbbf24’:‘linear-gradient(90deg,#1d4ed8,#4ade80)’;}
}

function rToday(){
var t=tots();var pct=Math.min(100,(t.cal/CAL)*100);
var cls=pct>95?’ over’:pct>80?’ warn’:’’;
var bn=ge(‘bcn’);if(bn){bn.textContent=Math.round(t.cal);bn.className=‘bcn’+cls;}
var bf=ge(‘bcbf’);if(bf){bf.style.width=Math.min(100,pct)+’%’;bf.className=‘bcbf’+(pct>95?’ over’:pct>80?’ warn’:’’);}
var rem=Math.round(CAL-t.cal);var re=ge(‘bcr’);
if(re){if(rem<0){re.textContent=’\u26A0 ‘+Math.abs(rem)+’ kcal over’;re.className=‘bcr over’;}else{re.textContent=rem+’ kcal remaining’;re.className=‘bcr’;}}
var mac=[{l:‘PROTEIN’,v:Math.round(t.p),g:PRO,c:’#38bdf8’,tip:‘Target 140g’},{l:‘CARBS’,v:Math.round(t.c),g:CARB,c:’#fbbf24’,tip:‘Target 110g’},{l:‘FAT’,v:Math.round(t.f),g:FAT,c:’#a78bfa’,tip:‘Target 70g’}];
var mh=’’;for(var i=0;i<mac.length;i++){var m=mac[i];var pm=Math.min(100,Math.round((m.v/m.g)*100));mh+=’<div class="mc" style="border:1px solid '+m.c+'33"><div class="mcl">’+m.l+’</div><div class="mcv" style="color:'+m.c+'">’+m.v+‘g</div><div class="mcg">/’+m.g+‘g</div><div class="mcb"><div class="mcbf" style="width:'+pm+'%;background:'+m.c+'"></div></div><div class="mct" style="color:'+m.c+'">’+m.tip+’</div></div>’;}
var mc=ge(‘mcards’);if(mc) mc.innerHTML=mh;
var tw=ST.wts[dk()];if(tw){var wi=ge(‘wi’);if(wi) wi.value=tw;}
var done=tdone();var sched=getMode()===‘eve’?SCHED_EVE:SCHED_MORN;
var cpct=sched.length?(done.length/sched.length)*100:0;
var cbf=ge(‘cmpbf’);if(cbf) cbf.style.width=cpct+’%’;
var cpc=ge(‘cmpc’);if(cpc) cpc.textContent=done.length+’/’+sched.length;
var cpm=ge(‘cmpm’);if(cpm) cpm.textContent=done.length===0?‘Tap items in Schedule to mark done.’:done.length===sched.length?’\uD83C\uDF89 Full day completed!’:‘Keep going \u2014 ‘+(sched.length-done.length)+’ items remaining.’;
}
function saveW(){
var v=parseFloat(ge(‘wi’).value);if(!v||v<30||v>200) return;
ST.wts[dk()]=v;save();
var diff=(v-94.9).toFixed(1);
var wm=ge(‘wm’);if(wm) wm.textContent=‘Saved: ‘+v+’ kg’+(parseFloat(diff)<0?’ \u00B7 Lost ‘+Math.abs(diff)+‘kg’:’’)+’ \u00B7 Target: 80-85 kg’;
}

function rHist(){var hm=ge(‘hmon’);if(hm) hm.textContent=MONTHS[ST.hm]+’ ‘+ST.hy;rCGrid();rMSum();drawWC();if(ST.selD) rSD(ST.selD);}
function prevM(){ST.hm–;if(ST.hm<0){ST.hm=11;ST.hy–;}ST.selD=null;rHist();}
function nextM(){ST.hm++;if(ST.hm>11){ST.hm=0;ST.hy++;}ST.selD=null;rHist();}
function rCGrid(){
var dh=[‘Su’,‘Mo’,‘Tu’,‘We’,‘Th’,‘Fr’,‘Sa’];
var first=new Date(ST.hy,ST.hm,1).getDay();var total=new Date(ST.hy,ST.hm+1,0).getDate();var today=dk();
var h=dh.map(function(d){return’<div class="cdh">’+d+’</div>’;}).join(’’);
for(var i=0;i<first;i++) h+=’<div class="cd empty"></div>’;
for(var d=1;d<=total;d++){
var key=ST.hy+’-’+p2(ST.hm+1)+’-’+p2(d);var log=ST.food[key]||[];var t=tots(log);
var isT=key===today;var isSel=key===ST.selD;var cls=‘cd’;
if(log.length){var pc=(t.cal/CAL)*100;cls+=pc>100?’ over2’:pc>50?’ good’:’ warn2’;}
if(isT) cls+=’ today’;if(isSel) cls+=’ sel’;
h+=’<div class="'+cls+'" data-action="selday" data-id="'+key+'">’+d+’</div>’;
}
var cg=ge(‘cgrid’);if(cg) cg.innerHTML=h;
}
function selD(key){ST.selD=key;rCGrid();rSD(key);}
function rSD(key){
var log=ST.food[key]||[];var w=ST.wts[key];var el=ge(‘sdlog’);if(!el) return;
if(!log.length&&!w){el.innerHTML=’<div class="sdlt">’+key+’ \u2014 No data logged</div>’;return;}
var t=tots(log);var h=’<div class="sdlt">’+key+(w?’ \u00B7 Wt:’+w+‘kg’:’’)+’</div>’;
for(var i=0;i<log.length;i++){var it=log[i];h+=’<div class="sdli"><span>’+it.nm+’ x’+it.qty+’</span><span class="sdlc">’+Math.round(it.cal*it.qty)+’ kcal</span></div>’;}
if(log.length) h+=’<div class="sdli"><strong>Total</strong><strong class="sdlc">’+Math.round(t.cal)+’ kcal</strong></div>’;
el.innerHTML=h;
}
function rMSum(){
var days=new Date(ST.hy,ST.hm+1,0).getDate();var tc=0,tp=0,dl=0,ot=0;
for(var d=1;d<=days;d++){var key=ST.hy+’-’+p2(ST.hm+1)+’-’+p2(d);var log=ST.food[key];if(log&&log.length){var t=tots(log);tc+=t.cal;tp+=t.p;dl++;if(t.cal<=CAL) ot++;}}
var n=dl||1;var data=[{v:Math.round(tc/n),l:‘Avg Calories’},{v:Math.round(tp/n)+‘g’,l:‘Avg Protein’},{v:dl,l:‘Days Logged’},{v:ot,l:‘On Target’}];
var h=’’;for(var i=0;i<data.length;i++) h+=’<div class="ms"><div class="msv">’+data[i].v+’</div><div class="msl">’+data[i].l+’</div></div>’;
var ms=ge(‘msumm’);if(ms) ms.innerHTML=h;
}
function drawWC(){
var c=ge(‘wchart’);if(!c) return;var ctx=c.getContext(‘2d’);c.width=c.offsetWidth||300;c.height=120;ctx.clearRect(0,0,c.width,c.height);
var entries=Object.entries(ST.wts).sort(function(a,b){return a[0]>b[0]?1:-1;}).slice(-20);
if(entries.length<2){ctx.fillStyle=’#475569’;ctx.font=‘12px monospace’;ctx.fillText(‘Log weight daily to see trend’,10,60);return;}
var vals=entries.map(function(e){return e[1];});var mn=Math.min.apply(null,vals)-2,mx=Math.max.apply(null,vals)+2;
var W=c.width,H=c.height,pad=22,xS=(W-pad*2)/(entries.length-1),yS=(H-pad*2)/(mx-mn);
var y85=H-pad-(85-mn)*yS;
ctx.strokeStyle=’#1a3a26’;ctx.lineWidth=1;ctx.setLineDash([4,4]);ctx.beginPath();ctx.moveTo(pad,y85);ctx.lineTo(W-pad,y85);ctx.stroke();ctx.setLineDash([]);
ctx.fillStyle=’#4ade80’;ctx.font=‘9px monospace’;ctx.fillText(‘85kg’,pad+2,y85-3);
ctx.beginPath();ctx.strokeStyle=’#38bdf8’;ctx.lineWidth=2;
entries.forEach(function(e,i){var x=pad+i*xS,y=H-pad-(e[1]-mn)*yS;i===0?ctx.moveTo(x,y):ctx.lineTo(x,y);});ctx.stroke();
entries.forEach(function(e,i){var x=pad+i*xS,y=H-pad-(e[1]-mn)*yS;ctx.beginPath();ctx.arc(x,y,3,0,Math.PI*2);ctx.fillStyle=’#38bdf8’;ctx.fill();});
ctx.fillStyle=’#475569’;ctx.font=‘9px monospace’;
ctx.fillText(entries[0][0].slice(5),pad,H-2);ctx.fillText(entries[entries.length-1][0].slice(5),W-pad-24,H-2);
}
function dlRep(){
var lines=[‘VIJAY HEALTH OS - MONTHLY REPORT’,‘Period: ‘+MONTHS[ST.hm]+’ ‘+ST.hy,‘Generated: ‘+new Date().toLocaleDateString(‘en-IN’),‘Gym Mode: ‘+(getMode()===‘eve’?‘Evening’:‘Morning’),’—’,‘HEALTH BASELINE (24 Apr 2026)’,‘HbA1c:6.7% | Glucose:133 | TG:367 | HDL:22 | B12:<148’,’—’];
var days=new Date(ST.hy,ST.hm+1,0).getDate();
for(var d=1;d<=days;d++){var key=ST.hy+’-’+p2(ST.hm+1)+’-’+p2(d);var log=ST.food[key];var w=ST.wts[key];var t=log&&log.length?tots(log):null;if(t||w) lines.push(d+’ ‘+MONTHS[ST.hm].slice(0,3)+’: ‘+(t?Math.round(t.cal)+’ kcal P:’+Math.round(t.p)+‘g’:’-’)+(w?’ Wt:’+w+‘kg’:’’));}
lines.push(’—’,‘Targets: 1750kcal P:140g C:110g F:70g | Weight: 80-85kg’);
var blob=new Blob([lines.join(’\n’)],{type:‘text/plain’});var a=document.createElement(‘a’);a.href=URL.createObjectURL(blob);a.download=‘Health_’+MONTHS[ST.hm]+’_’+ST.hy+’.txt’;a.click();
}

function rHealth(){
var h=’’;for(var i=0;i<BLOOD.length;i++){var b=BLOOD[i];h+=’<div class="bg"><div class="bgn">’+b.nm+’</div><div class="bgv '+b.st+'">’+b.vl+’</div><div class="bgr">Normal: ‘+b.rf+’</div></div>’;}
var bg=ge(‘bgrid’);if(bg) bg.innerHTML=h;
var sh=’’;for(var i=0;i<SUPPS.length;i++){var s=SUPPS[i];sh+=’<div class="sup"><span class="supi">’+s.ic+’</span><div><div class="supn">’+s.nm+’</div><div class="supd">’+s.ds+’</div><div class="supw">’+s.wy+’</div></div></div>’;}
var sl=ge(‘suplist’);if(sl) sl.innerHTML=sh;
var w=ST.h2o[dk()]||0;
var wc=ge(‘wtct’);if(wc) wc.textContent=w;
var wf=ge(‘wtf’);if(wf) wf.style.width=Math.min(100,(w/H2O)*100)+’%’;
var wm=ge(‘wtm’);if(wm) wm.textContent=w>=H2O?‘Target reached! Kidneys protected.’:‘Target: ‘+H2O+’ glasses. ‘+(H2O-w)+’ more to go.’;
var ah=’’;for(var i=0;i<AIRECS.length;i++){var r=AIRECS[i];ah+=’<div class="air"><strong>\u2705 ‘+r.t+’</strong><br>’+r.d+’</div>’;}
var ar=ge(‘airecs’);if(ar) ar.innerHTML=ah;
}
function adjW(d){var k=dk();ST.h2o[k]=Math.max(0,(ST.h2o[k]||0)+d);save();rHealth();}

document.addEventListener(‘click’,function(e){
var b=e.target;var limit=8;
while(b&&b!==document.body&&limit–>0){if(b.dataset&&b.dataset.action) break;b=b.parentNode;}
if(!b||!b.dataset||!b.dataset.action) return;
var act=b.dataset.action;var id=b.dataset.id||’’;
switch(act){
case ‘tab’:        go(id);break;
case ‘done’:       tD(id);break;
case ‘edit’:       openEd(id);break;
case ‘slot’:       setSlot(id);break;
case ‘cat’:        setCat(id);break;
case ‘addf’:       addF(parseInt(id,10));break;
case ‘adjq’:       adjQ(parseInt(b.dataset.lid,10),parseFloat(b.dataset.d));break;
case ‘rmf’:        rmF(parseInt(id,10));break;
case ‘selday’:     selD(id);break;
case ‘prevm’:      prevM();break;
case ‘nextm’:      nextM();break;
case ‘saveweight’: saveW();break;
case ‘adjwater’:   adjW(parseInt(b.dataset.d,10));break;
case ‘togcf’:      togCF();break;
case ‘addcf’:      addCF();break;
case ‘dlrep’:      dlRep();break;
case ‘override’:   manualOverride();break;
case ‘enn’:        enN();break;
case ‘closenmod’:  ge(‘nmod’).style.display=‘none’;break;
case ‘saveed’:     saveEd();break;
case ‘closeed’:    closeEd();break;
}
});

function setDate(){
var d=new Date();var days=[‘Sun’,‘Mon’,‘Tue’,‘Wed’,‘Thu’,‘Fri’,‘Sat’];var ms=[‘Jan’,‘Feb’,‘Mar’,‘Apr’,‘May’,‘Jun’,‘Jul’,‘Aug’,‘Sep’,‘Oct’,‘Nov’,‘Dec’];
var el=ge(‘hdate’);if(el) el.textContent=days[d.getDay()]+’, ‘+d.getDate()+’ ‘+ms[d.getMonth()]+’ ’+d.getFullYear();
}

if(‘serviceWorker’in navigator) window.addEventListener(‘load’,function(){navigator.serviceWorker.register(’./sw.js’).catch(function(){});});

window.addEventListener(‘DOMContentLoaded’,function(){
load();setDate();updateBanner();updCal();
var fs=ge(‘fsrch’);if(fs) fs.addEventListener(‘input’,function(){rFL();});
go(‘sch’);
showNP();
});

</script>
</body>
</html>
