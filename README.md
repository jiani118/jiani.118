<!DOCTYPE html><html lang="zh"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover"><title>WebOS 妗岄潰</title>
<style>
:root{--surf:rgba(243,243,243,.92);--s2:#fff;--tx:#1b1b1b;--mut:#666;--bd:rgba(0,0,0,.13);--acc:#0067c0;--sel:rgba(0,103,192,.16);--tbk:rgba(235,240,248,.88)}
@media (prefers-color-scheme:dark){:root:not([data-theme=light]){--surf:rgba(36,36,36,.94);--s2:#2d2d2d;--tx:#f2f2f2;--mut:#aaa;--bd:rgba(255,255,255,.15);--acc:#4cc2ff;--sel:rgba(76,194,255,.22);--tbk:rgba(24,26,32,.88)}}
:root[data-theme=dark]{--surf:rgba(36,36,36,.94);--s2:#2d2d2d;--tx:#f2f2f2;--mut:#aaa;--bd:rgba(255,255,255,.15);--acc:#4cc2ff;--sel:rgba(76,194,255,.22);--tbk:rgba(24,26,32,.88)}
*{box-sizing:border-box}html,body{height:100%;margin:0;overflow:hidden;font:14px "Segoe UI","PingFang SC","Microsoft YaHei",sans-serif;color:var(--tx);background:#0b3f8f;user-select:none;-webkit-user-select:none}
button,input,select,textarea{font:inherit;color:inherit}
button{background:var(--s2);border:1px solid var(--bd);border-radius:5px;padding:4px 10px;cursor:pointer}button:hover{background:var(--sel)}
#desk{position:fixed;left:0;right:0;top:env(safe-area-inset-top,0px);bottom:calc(48px + env(safe-area-inset-bottom,0px));background:radial-gradient(ellipse at 20% 15%,#7fd0ff 0,transparent 45%),radial-gradient(ellipse at 85% 80%,#6a5cff 0,transparent 50%),linear-gradient(135deg,#0a3d91,#1a8fe3 60%,#35c7ff);overflow:hidden}
#icons{position:absolute;inset:6px;display:flex;flex-direction:column;flex-wrap:wrap;align-content:flex-start;gap:4px;pointer-events:none}
.ic{pointer-events:auto;width:84px;padding:8px 2px;text-align:center;color:#fff;text-shadow:0 1px 3px #000;border-radius:6px;cursor:default}.ic:hover{background:rgba(255,255,255,.18)}.ic b{display:block;font-size:34px;font-weight:400}.ic span{font-size:12px}
#bar{position:fixed;left:0;right:0;bottom:0;height:calc(48px + env(safe-area-inset-bottom,0px));padding-bottom:env(safe-area-inset-bottom,0px);display:flex;align-items:center;gap:4px;padding-left:4px;padding-right:8px;background:var(--tbk);backdrop-filter:blur(18px);border-top:1px solid var(--bd);z-index:9999}
#sb{font-size:22px;width:44px;height:38px;padding:0;background:none;border:0}#tasks{flex:1;display:flex;gap:3px;overflow-x:auto}
.tb{display:flex;gap:6px;align-items:center;max-width:150px;min-width:44px;height:38px;background:none;border:0;border-bottom:3px solid transparent;border-radius:5px}.tb span{overflow:hidden;white-space:nowrap;text-overflow:ellipsis}.tb.act{background:var(--sel);border-bottom-color:var(--acc)}
#tray{text-align:right;font-size:12px;line-height:1.25;white-space:nowrap;padding:0 4px}
.win{position:absolute;background:var(--surf);backdrop-filter:blur(20px);border:1px solid var(--bd);border-radius:9px;box-shadow:0 6px 24px rgba(0,0,0,.3);display:flex;flex-direction:column;overflow:hidden;min-width:260px}.win.act{box-shadow:0 12px 40px rgba(0,0,0,.5)}
.win.max{left:0!important;top:0!important;width:100%!important;height:100%!important;border-radius:0}
.tt{display:flex;justify-content:space-between;align-items:center;padding:0 0 0 12px;height:34px;touch-action:none;cursor:default;flex:none}.tt i{display:flex;font-style:normal}.tt b{width:44px;height:34px;display:grid;place-items:center;font-weight:400}.tt b:hover{background:var(--sel)}.tt .cl:hover{background:#e81123;color:#fff}
.bd{flex:1;min-height:0;overflow:auto;background:var(--s2);display:flex;flex-direction:column;user-select:text;-webkit-user-select:text}
.bar{display:flex;gap:6px;align-items:center;padding:6px;border-bottom:1px solid var(--bd);flex-wrap:wrap}.path{color:var(--mut);margin-left:6px}
.ex{display:flex;flex:1;min-height:0}.side{width:120px;border-right:1px solid var(--bd);padding:6px;display:flex;flex-direction:column;gap:2px;flex:none}.side button{text-align:left;border:0;background:none}
.files{flex:1;padding:8px;display:flex;flex-wrap:wrap;align-content:flex-start;gap:4px;overflow:auto}.fi{width:84px;padding:6px 2px;text-align:center;border-radius:6px;border:1px solid transparent;word-break:break-all;font-size:12px}.fi b{display:block;font-size:32px;font-weight:400}.fi.s{background:var(--sel);border-color:var(--acc)}
.empty{color:var(--mut);padding:30px;width:100%;text-align:center}
.rb{display:flex;align-items:center;gap:8px;padding:8px 12px;border-bottom:1px solid var(--bd)}.rb span{flex:1}
.np{flex:1;width:100%;border:0;padding:10px;resize:none;background:var(--s2);outline:0;font:14px/1.6 Consolas,monospace}
.ctr{text-align:center;padding:8px;color:var(--mut)}
#start{position:fixed;left:6px;bottom:calc(54px + env(safe-area-inset-bottom,0px));width:min(400px,calc(100% - 12px));max-height:calc(100% - 80px);background:var(--surf);backdrop-filter:blur(24px);border:1px solid var(--bd);border-radius:12px;box-shadow:0 10px 40px rgba(0,0,0,.45);padding:14px;z-index:9998;display:none;overflow:auto}
#start.on{display:block}#start input{width:100%;padding:8px 12px;border-radius:20px;border:1px solid var(--bd);background:var(--s2);margin-bottom:12px}
#grid{display:grid;grid-template-columns:repeat(4,1fr);gap:6px}#grid button{border:0;background:none;padding:10px 2px}#grid b{display:block;font-size:30px;font-weight:400}#grid span{font-size:12px}
.sf{display:flex;justify-content:space-between;align-items:center;margin-top:12px;padding-top:10px;border-top:1px solid var(--bd)}
#cm{position:fixed;background:var(--surf);border:1px solid var(--bd);border-radius:8px;padding:4px;z-index:9997;display:none;box-shadow:0 6px 20px rgba(0,0,0,.4)}#cm button{display:block;width:100%;border:0;background:none;text-align:left}
.disc{font-size:90px;text-align:center;padding:14px}.disc.spin{animation:sp 3s linear infinite}@keyframes sp{to{transform:rotate(360deg)}}
.pl{padding:6px 12px}.pl button{display:block;width:100%;text-align:left;border:0;background:none}.pl .on{background:var(--sel)}
.calc{display:grid;grid-template-columns:repeat(4,1fr);gap:4px;padding:8px;flex:1}.calc button{font-size:18px}#cd{font-size:30px;text-align:right;padding:14px;min-height:64px;word-break:break-all}
.tabs{display:flex;gap:4px;padding:6px;border-bottom:1px solid var(--bd)}.tabs .on{background:var(--acc);color:#fff}
.ttt{display:grid;grid-template-columns:repeat(3,90px);gap:6px;justify-content:center}.ttt button{height:90px;font-size:40px}.pad{text-align:center}.pad div{display:flex;gap:6px;justify-content:center}.pad button{width:52px;height:40px;margin:2px}
canvas{max-width:100%;display:block;margin:0 auto}
.win{background:linear-gradient(135deg,color-mix(in srgb,var(--s2) 48%,transparent),color-mix(in srgb,var(--s2) 20%,transparent));backdrop-filter:blur(28px) saturate(190%) brightness(1.06);-webkit-backdrop-filter:blur(28px) saturate(190%) brightness(1.06);border:1px solid rgba(255,255,255,.45);border-radius:24px;box-shadow:0 18px 50px rgba(0,0,0,.28),inset 0 1.5px 0 rgba(255,255,255,.8),inset 0 -1px 0 rgba(255,255,255,.2),inset 0 0 24px rgba(255,255,255,.15)}
.win.act{box-shadow:0 28px 80px rgba(0,0,0,.42),inset 0 1.5px 0 rgba(255,255,255,.9),inset 0 -1px 0 rgba(255,255,255,.25),inset 0 0 28px rgba(255,255,255,.2)}
.win::after{content:"";position:absolute;inset:0;border-radius:inherit;pointer-events:none;background:radial-gradient(120% 55% at 18% -12%,rgba(255,255,255,.4),transparent 55%)}
.win.max{border-radius:0}.tt{height:38px}.tt b{height:38px}
.rz{position:absolute;z-index:5;touch-action:none}.win.max .rz{display:none}
.rz.n{top:0;left:14px;right:14px;height:4px;cursor:ns-resize}.rz.s{bottom:0;left:14px;right:14px;height:6px;cursor:ns-resize}.rz.e{right:0;top:14px;bottom:14px;width:6px;cursor:ew-resize}.rz.w{left:0;top:14px;bottom:14px;width:6px;cursor:ew-resize}
.rz.ne,.rz.nw,.rz.se,.rz.sw{width:16px;height:16px}.rz.ne{top:0;right:0;cursor:nesw-resize}.rz.sw{bottom:0;left:0;cursor:nesw-resize}.rz.nw{top:0;left:0;cursor:nwse-resize}.rz.se{bottom:0;right:0;cursor:nwse-resize}
#qp{position:fixed;right:8px;bottom:calc(68px + env(safe-area-inset-bottom,0px));width:min(320px,calc(100% - 16px));background:var(--surf);backdrop-filter:blur(28px) saturate(190%);border:1px solid rgba(255,255,255,.45);border-radius:24px;box-shadow:inset 0 1.5px 0 rgba(255,255,255,.7),0 16px 50px rgba(0,0,0,.4);padding:14px;z-index:9998;display:none}#qp.on{display:block}.qg{display:grid;grid-template-columns:1fr 1fr;gap:8px}.qg button{padding:12px;border-radius:16px;text-align:left}#qp input[type=range]{width:100%}#dim{position:fixed;inset:0;background:#000;opacity:0;pointer-events:none;z-index:99999}#qs{border:0;background:none;font-size:15px;padding:4px 6px}
#desk{background:none;overflow:visible;bottom:calc(78px + env(safe-area-inset-bottom,0px))}
#bar{left:50%;right:auto;transform:translateX(-50%);width:min(1000px,calc(100% - 20px));bottom:calc(12px + env(safe-area-inset-bottom,0px));height:58px;padding:0 10px;gap:8px;border-radius:29px;background:linear-gradient(180deg,color-mix(in srgb,var(--s2) 80%,transparent),color-mix(in srgb,var(--s2) 60%,transparent));border:1px solid rgba(255,255,255,.6);box-shadow:0 16px 44px rgba(0,0,0,.45),0 2px 8px rgba(0,0,0,.3),inset 0 1.5px 0 rgba(255,255,255,.9),inset 0 -1px 0 rgba(0,0,0,.1);backdrop-filter:blur(32px) saturate(210%)}
#sb{flex:none;width:44px;height:44px;border-radius:50%;font-size:20px;color:#fff;background:linear-gradient(135deg,#2b8cff,#7a5cff);box-shadow:0 4px 14px rgba(60,100,255,.55),inset 0 1px 0 rgba(255,255,255,.5)}#sb:hover{filter:brightness(1.1)}
#tasks{justify-content:center;align-items:center;padding:0 4px}
.tb{position:relative;height:44px;border:0;border-radius:14px;padding:0 12px}.tb.act{background:var(--sel)}.tb.act::after{content:"";position:absolute;left:50%;bottom:3px;width:16px;height:3px;border-radius:2px;background:var(--acc);transform:translateX(-50%)}
#tray{padding:5px 12px;border-radius:18px;background:color-mix(in srgb,var(--s2) 55%,transparent);box-shadow:inset 0 0 0 1px rgba(255,255,255,.4)}
#start,#qp,#np{bottom:calc(86px + env(safe-area-inset-bottom,0px))}
#np{position:fixed;right:8px;width:min(360px,calc(100% - 16px));max-height:calc(100% - 110px);overflow:auto;background:var(--surf);backdrop-filter:blur(28px) saturate(190%);border:1px solid rgba(255,255,255,.45);border-radius:24px;box-shadow:inset 0 1.5px 0 rgba(255,255,255,.7),0 16px 50px rgba(0,0,0,.4);padding:14px;z-index:9998;display:none}#np.on{display:block}
.stw{container-type:inline-size;flex:1;min-height:0;display:flex}.st{display:flex;flex:1;min-height:0;width:100%}
.sn{width:230px;flex:none;padding:12px 8px;overflow:auto}.sm{flex:1;min-width:0;display:flex;flex-direction:column;padding:12px 16px}
.sq{width:100%;padding:9px 14px;border-radius:20px;border:1px solid var(--bd);background:color-mix(in srgb,var(--s2) 70%,transparent);margin-bottom:10px}
.sb2{flex:1;overflow:auto}.sb2 h1{margin:6px 0 14px;font-size:28px}
.ub{display:flex;gap:12px;align-items:center;padding:6px 8px 14px}.av{width:48px;height:48px;border-radius:50%;background:#e8e8ec;display:grid;place-items:center;font-size:26px;color:#333;flex:none}
.ni{display:flex;gap:12px;align-items:center;padding:11px 12px;border-radius:8px;cursor:pointer;margin:2px 0}.ni:hover{background:var(--sel)}.ni.on{background:var(--sel);box-shadow:inset 3px 0 0 var(--acc)}
.sc,.sr{display:flex;align-items:center;gap:14px;padding:14px 16px;border-radius:10px;margin-bottom:6px;background:color-mix(in srgb,var(--s2) 55%,transparent);border:1px solid var(--bd)}
.sc{cursor:pointer}.sc:hover{background:var(--sel)}.si{font-size:24px;width:34px;text-align:center}.sx{flex:1;display:flex;flex-direction:column;min-width:0}.sx small{color:var(--mut)}.ch{font-size:22px;color:var(--mut)}
.dev{display:flex;align-items:center;gap:20px;padding:4px 0 14px}.pv{width:200px;height:124px;border-radius:14px;border:5px solid #111;flex:none;background-size:cover}.lk{color:var(--acc);cursor:pointer}
@container (max-width:620px){.st{flex-direction:column}.sn{width:auto;display:flex;overflow-x:auto;flex:none;padding:6px}.ub{display:none}.ni{flex:none;padding:8px 10px}.pv{width:120px;height:76px}}
@keyframes pop{from{opacity:0;transform:scale(.94) translateY(8px)}to{opacity:1;transform:none}}
.win{animation:pop .16s ease-out}.win.max{animation:none}#start.on,#qp.on,#np.on{animation:pop .15s ease-out}
.tb{transition:background .15s,transform .15s}.tb:hover{transform:translateY(-2px)}.ic:active{background:rgba(255,255,255,.28)}
#tray{position:relative}#tray[data-n="1"]::after{content:"";position:absolute;top:3px;right:3px;width:9px;height:9px;border-radius:50%;background:#e81123}
#icons{display:block}.ic{position:absolute;width:calc(84px*var(--is,1));touch-action:none}.ic b{font-size:calc(34px*var(--is,1))}.ic span{font-size:calc(12px*var(--is,1))}
.sl{position:relative;width:100%;aspect-ratio:16/9;container-type:inline-size;overflow:hidden;border-radius:6px;box-shadow:0 2px 10px rgba(0,0,0,.3)}
.bd{background:color-mix(in srgb,var(--s2) 34%,transparent);margin:0 8px 8px;border-radius:16px;box-shadow:inset 0 0 0 1px rgba(255,255,255,.28)}.win.max .bd{margin:0;border-radius:0}
.np{background:transparent}button{background:color-mix(in srgb,var(--s2) 62%,transparent)}

#start{border-radius:26px;border:1px solid rgba(255,255,255,.45);box-shadow:inset 0 1.5px 0 rgba(255,255,255,.7),0 16px 50px rgba(0,0,0,.4)}

/* 闈㈡澘閿氬畾鍒颁换鍔℃爮 + 寮瑰嚭鍔ㄧ敾 */
#start{left:max(10px,calc(50% - 500px));transform-origin:left bottom}
#qp,#np{right:max(10px,calc(50% - 500px));transform-origin:right bottom}
#start,#qp,#np{display:block!important;visibility:hidden;opacity:0;pointer-events:none;transform:translateY(26px) scale(.94);animation:none!important;transition:opacity .2s ease,transform .32s cubic-bezier(.2,.9,.3,1.25),visibility 0s linear .32s}
#start.on,#qp.on,#np.on{visibility:visible;opacity:1;pointer-events:auto;transform:none;transition:opacity .2s ease,transform .32s cubic-bezier(.2,.9,.3,1.25),visibility 0s}
@keyframes winIn{0%{opacity:0;transform:scale(.82) translateY(34px)}60%{opacity:1;transform:scale(1.015) translateY(-3px)}100%{opacity:1;transform:none}}
@keyframes winOut{to{opacity:0;transform:scale(.9) translateY(40px)}}
@keyframes tbIn{from{opacity:0;transform:scale(.6)}to{opacity:1;transform:none}}
.win{animation:winIn .34s cubic-bezier(.2,.8,.3,1)}.win.max{animation:none}
.win.mn,.win.cl{animation:winOut .17s ease-in forwards}.win.cl{pointer-events:none}
.tb{animation:tbIn .28s cubic-bezier(.2,.9,.3,1.3)}#cm{animation:pop .15s ease-out}

/* 姣斾緥閫傞厤锛氭寜灞忓箷瀹藉害鏁翠綋缂╂斁锛屽苟璁╁簲鐢ㄥ唴瀹归殢绐楀彛澶у皬浼哥缉 */
body{font-size:calc(14px*var(--ui,1))}
#desk{bottom:calc(78px*var(--ui,1) + env(safe-area-inset-bottom,0px))}
#bar{height:calc(58px*var(--ui,1));width:min(calc(1000px*var(--ui,1)),calc(100% - 20px));border-radius:calc(29px*var(--ui,1))}
#sb{width:calc(44px*var(--ui,1));height:calc(44px*var(--ui,1));font-size:calc(20px*var(--ui,1))}
.tb{height:calc(44px*var(--ui,1))}#tray{font-size:calc(12px*var(--ui,1))}#qs{font-size:calc(15px*var(--ui,1))}
.tt{height:calc(38px*var(--ui,1))}.tt b{height:calc(38px*var(--ui,1));width:calc(44px*var(--ui,1))}
#start{width:min(calc(400px*var(--ui,1)),calc(100% - 20px));left:max(10px,calc(50% - 500px*var(--ui,1)));bottom:calc(86px*var(--ui,1) + env(safe-area-inset-bottom,0px))}
#qp,#np{bottom:calc(86px*var(--ui,1) + env(safe-area-inset-bottom,0px));right:max(10px,calc(50% - 500px*var(--ui,1)))}
#qp{width:min(calc(320px*var(--ui,1)),calc(100% - 20px))}#np{width:min(calc(360px*var(--ui,1)),calc(100% - 20px))}
.bd{container-type:inline-size}
.svg-clock,.bd svg[viewBox="-100 -100 200 200"]{width:clamp(200px,58cqw,480px)!important}#dg{font-size:clamp(30px,8cqw,64px)!important}
#cd{font-size:clamp(30px,10cqw,68px)}.calc{grid-auto-rows:1fr}.calc button{font-size:clamp(18px,5cqw,36px)}
.g canvas{width:min(92cqw,60vh,560px);height:auto}.ttt{grid-template-columns:repeat(3,min(24cqw,150px))}.ttt button{height:min(24cqw,150px);font-size:clamp(40px,10cqw,80px)}
#vd{max-height:min(52vh,640px)!important}#cv{max-height:min(55vh,640px)!important}.disc{font-size:clamp(70px,20cqw,150px)}
.pgx{width:min(94%,clamp(640px,72cqw,1000px))!important;font-size:clamp(15px,1.3cqw + 9px,21px)}
.bd table{width:100%}.bd td input{width:100%!important;min-width:56px;font-size:clamp(13px,1vw + 7px,18px)}
.fi{width:clamp(84px,9cqw,132px)}.fi b{font-size:clamp(32px,4.2cqw,52px)}#st{max-width:1000px;margin:0 auto}
#grid b{font-size:calc(30px*var(--ui,1))}#grid span{font-size:calc(12px*var(--ui,1))}#start input{font-size:calc(14px*var(--ui,1))}
@media (max-width:700px){.tb span{display:none}.tb{min-width:44px;padding:0 10px}#dt{display:none}#tray{padding:5px 8px}#bar{gap:4px;padding:0 6px}.win{min-width:0}}
@media (max-height:520px){#start{max-height:calc(100% - 100px)}}

/* 璁＄畻鍣� / 鏃ュ巻 鏂扮増甯冨眬 */
.cw{display:flex;flex:1;min-height:0;position:relative}.cm{flex:1;min-width:0;display:flex;flex-direction:column;justify-content:center;align-items:center;padding:8px;overflow:auto}
.ce{color:var(--mut);min-height:1.4em;text-align:right;width:min(100%,520px)}#cd{width:min(100%,520px);text-align:right;font-size:clamp(34px,8cqw,64px);padding:4px 10px 12px;word-break:break-all;min-height:1.3em}
.kp{display:grid;grid-template-columns:repeat(4,1fr);grid-auto-rows:clamp(48px,8.5vh,80px);gap:6px;width:min(100%,520px)}.kp button{font-size:clamp(18px,3.2cqw,30px);border-radius:12px}.kp .n{background:color-mix(in srgb,var(--s2) 88%,transparent)}.kp .eq{background:var(--acc);color:#fff;border-color:transparent}
.chs{display:none;flex-direction:column;border-left:1px solid var(--bd);width:min(300px,38cqw);flex:none;padding:8px;overflow:auto}.chs.on{display:flex;position:absolute;inset:0;width:auto;background:var(--s2);z-index:2;border:0}
.hi{padding:8px 10px;border-radius:8px;cursor:pointer;text-align:right}.hi:hover{background:var(--sel)}.hi small{display:block;color:var(--mut)}.hi b{font-size:1.25em}.chb{position:absolute;top:6px;left:6px;z-index:1}
@container (min-width:640px){.chs{display:flex;position:static!important;width:min(300px,36cqw)!important;background:none!important;border-left:1px solid var(--bd)!important}.hbtn,.hc{display:none}.cvb{left:6px!important}}
.cal{display:flex;flex-direction:column;gap:10px;padding:10px;flex:1;min-height:0;overflow:auto}.cg{width:min(100%,640px);margin:0 auto}.cwk{display:grid;grid-template-columns:repeat(7,1fr);gap:4px;margin-top:6px;text-align:center}.cwk>b{padding:6px 0;color:var(--mut)}
.dy{aspect-ratio:1/.78;font-size:clamp(14px,1.6cqw + 6px,22px);border-radius:12px;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:0}.dy small{font-size:8px;color:var(--acc);line-height:6px}.dy.we{color:#d33}.dy.td{background:var(--acc);color:#fff;border-color:transparent}.dy.sl2{outline:2px solid var(--acc)}
.cev{width:min(100%,640px);margin:0 auto}
@container (min-width:760px){.cal{flex-direction:row;align-items:flex-start;justify-content:center}.cg{margin:0;flex:1;max-width:560px}.cev{margin:0;width:300px;flex:none}}
#wx{max-width:640px;margin:0 auto;width:100%}

.cvo{display:none;position:absolute;inset:0;background:var(--s2);z-index:3;flex-direction:column;overflow:auto}.cvo.on{display:flex}.cvb{left:96px}
.cvh{display:flex;align-items:center;gap:14px;padding:12px 16px;font-size:1.3em}.cvbk{font-size:1.4em;border:0;background:none}
.cvg{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;padding:12px 16px;width:min(100%,720px);margin:0 auto}
.cvt{aspect-ratio:1.55;border-radius:20px;background:color-mix(in srgb,var(--s2) 70%,#888 12%);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:10px;cursor:pointer;border:1px solid var(--bd)}.cvt span{font-size:2.2em}.cvt:hover{background:var(--sel)}
.cvf{display:flex;flex-direction:column;gap:12px;padding:8px 16px 20px;width:min(100%,560px);margin:0 auto}.cvf label{display:flex;flex-direction:column;gap:4px;color:var(--mut)}.cvf input,.cvf select{padding:10px;font-size:1.1em;border-radius:10px;border:1px solid var(--bd);background:var(--s2);color:var(--tx)}
.cvx{display:flex;gap:8px}.cvx input{flex:
