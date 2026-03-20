<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>수행평가 : 데이터 기반 사회변화 논증하기</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+KR:wght@400;600;700;900&family=Noto+Sans+KR:wght@300;400;500;700&family=IBM+Plex+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#0b0f18;--surf:#111827;--surf2:#1a2236;--surf3:#1f2a3d;
  --bdr:#2a3650;--bdr2:#1e2d45;
  --tx:#e2e8f4;--tx2:#8899b8;--tx3:#566080;
  --acc:#4f9eff;--acc2:#7db8ff;
  --grn:#34c06a;--org:#f5883a;--red:#f06060;--pur:#a78bfa;--yel:#eab308;--teal:#22d3ae;
  --gold:#f0b429;
}
*{box-sizing:border-box;margin:0;padding:0;}
html{scroll-behavior:smooth;}
body{font-family:'Noto Sans KR',sans-serif;background:var(--bg);color:var(--tx);min-height:100vh;line-height:1.6;}

/* ── HEADER ── */
.hdr{background:linear-gradient(90deg,#0d1525 0%,#111e35 100%);border-bottom:2px solid var(--acc);position:sticky;top:0;z-index:300;box-shadow:0 2px 20px rgba(0,0,0,.5);}
.hdr-in{max-width:1120px;margin:0 auto;padding:12px 24px;display:flex;align-items:center;justify-content:space-between;gap:12px;}
.hdr-left{display:flex;align-items:center;gap:14px;min-width:0;}
.exam-badge{background:var(--acc);color:#0b0f18;font-family:'IBM Plex Mono',monospace;font-size:9px;font-weight:700;padding:3px 8px;border-radius:3px;letter-spacing:1.5px;white-space:nowrap;flex-shrink:0;}
.exam-badge.locked{background:var(--red);}
.hdr-title{font-family:'Noto Serif KR',serif;font-size:15px;font-weight:700;line-height:1.3;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
.hdr-right{display:flex;align-items:center;gap:20px;font-size:11px;color:var(--tx2);font-family:'IBM Plex Mono',monospace;white-space:nowrap;flex-shrink:0;}
.hdr-right .pt{color:var(--gold);font-weight:600;}

/* ── TABS (student sees 2, teacher sees more) ── */
.tabs{background:var(--surf);border-bottom:1px solid var(--bdr);overflow-x:auto;}
.tabs-in{max-width:1120px;margin:0 auto;padding:0 24px;display:flex;}
.tab{background:transparent;border:none;border-bottom:2px solid transparent;color:var(--tx3);font-family:'Noto Sans KR',sans-serif;font-size:13px;font-weight:500;padding:11px 18px;cursor:pointer;transition:all .2s;white-space:nowrap;}
.tab:hover{color:var(--tx2);}
.tab.on{color:var(--acc);border-bottom-color:var(--acc);font-weight:700;}
.tab.teacher-only{display:none;}
.tab.teacher-only.visible{display:flex;align-items:center;gap:6px;}
.tab.ton.on{color:var(--red);border-bottom-color:var(--red);}
.tbadge{background:var(--surf2);color:var(--tx3);font-size:10px;font-family:'IBM Plex Mono',monospace;padding:1px 5px;border-radius:10px;}
.tab.on .tbadge{background:rgba(79,158,255,.15);color:var(--acc);}

/* ── MAIN ── */
.main{max-width:1120px;margin:0 auto;padding:28px 24px;}
.panel{display:none;}.panel.on{display:block;}

/* ── QUESTION BOX ── */
.qbox{background:linear-gradient(135deg,#131f36 0%,#0f1a2e 100%);border:1px solid var(--bdr);border-left:4px solid var(--acc);border-radius:8px;padding:22px 26px;margin-bottom:24px;}
.qbox-meta{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:12px;}
.qtag{font-size:11px;font-family:'IBM Plex Mono',monospace;padding:2px 9px;border-radius:3px;border:1px solid;}
.qtag.s{border-color:var(--gold);color:var(--gold);}
.qtag.t{border-color:var(--org);color:var(--org);}
.qtag.l{border-color:var(--pur);color:var(--pur);}
.qtag.c{border-color:var(--teal);color:var(--teal);}
.qbox-title{font-family:'Noto Serif KR',serif;font-size:17px;font-weight:900;line-height:1.7;margin-bottom:14px;color:var(--tx);}
.qbox-conds{background:rgba(79,158,255,.06);border:1px solid rgba(79,158,255,.15);border-radius:6px;padding:14px 18px;margin-bottom:14px;}
.qbox-conds h4{font-size:12px;font-weight:700;color:var(--acc);margin-bottom:10px;font-family:'IBM Plex Mono',monospace;letter-spacing:.8px;}
.cond-list{display:flex;flex-direction:column;gap:7px;}
.cond{display:flex;align-items:flex-start;gap:10px;font-size:13px;color:var(--tx2);line-height:1.6;}
.cond-n{background:var(--acc);color:#0b0f18;font-family:'IBM Plex Mono',monospace;font-size:10px;font-weight:700;min-width:18px;height:18px;border-radius:50%;display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:2px;}
.cond strong{color:var(--tx);}
.qbox-struct{margin-top:12px;display:flex;align-items:center;gap:8px;flex-wrap:wrap;}
.struct-step{background:var(--surf2);border:1px solid var(--bdr);padding:5px 12px;border-radius:20px;font-size:12px;color:var(--tx2);display:flex;align-items:center;gap:6px;}
.struct-step .snum{color:var(--acc);font-weight:700;font-family:'IBM Plex Mono',monospace;font-size:11px;}
.struct-arrow{color:var(--tx3);font-size:14px;}

/* ── SECTION HEADER ── */
.sec-hdr{display:flex;align-items:center;gap:12px;margin-bottom:18px;}
.sec-hdr h3{font-family:'Noto Serif KR',serif;font-size:15px;font-weight:700;}
.sec-line{flex:1;height:1px;background:var(--bdr);}
.sec-chip{font-size:10px;font-family:'IBM Plex Mono',monospace;color:var(--tx3);letter-spacing:1px;}

/* ── DATA GRID ── */
.data-grid{display:grid;grid-template-columns:1fr 1fr;gap:18px;margin-bottom:28px;}
.dc{background:var(--surf);border:1px solid var(--bdr);border-radius:8px;overflow:hidden;animation:fadeUp .4s ease both;}
.dc:hover{border-color:rgba(79,158,255,.4);transition:border-color .2s;}
.dc.wide{grid-column:1/-1;}
.dc.triple{grid-column:1/-1;}
.dc-hdr{padding:12px 16px;border-bottom:1px solid var(--bdr2);display:flex;align-items:center;justify-content:space-between;}
.dc-title{display:flex;align-items:center;gap:10px;}
.dicon{width:28px;height:28px;border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:14px;flex-shrink:0;}
.dc-title h4{font-size:13px;font-weight:700;color:var(--tx);line-height:1.3;}
.dc-title small{font-size:10px;color:var(--tx3);font-family:'IBM Plex Mono',monospace;display:block;}
.dsrc{font-size:10px;font-family:'IBM Plex Mono',monospace;color:var(--tx3);background:var(--surf2);padding:2px 8px;border-radius:3px;flex-shrink:0;}
.dc-body{padding:14px 16px;}

/* ── TABLE ── */
.dtbl{width:100%;border-collapse:collapse;font-size:12px;margin-top:8px;}
.dtbl th{background:var(--surf3);color:var(--tx2);font-weight:600;font-family:'IBM Plex Mono',monospace;font-size:11px;padding:7px 10px;text-align:center;border:1px solid var(--bdr2);}
.dtbl td{padding:7px 10px;text-align:center;border:1px solid var(--bdr2);font-family:'IBM Plex Mono',monospace;color:var(--tx2);font-size:11px;}
.dtbl tr:hover td{background:rgba(79,158,255,.04);color:var(--tx);}
.dtbl td:first-child{text-align:left;font-family:'Noto Sans KR',sans-serif;color:var(--tx);font-size:11px;}
.hl{color:var(--acc);font-weight:700;}
.hl2{color:var(--gold);font-weight:700;}
.up{color:var(--red);}
.dn{color:var(--grn);}
.warn{color:var(--org);}
.tag-pill{display:inline-block;padding:1px 6px;border-radius:3px;font-size:10px;font-weight:600;}
.insight{margin-top:10px;padding:9px 13px;background:rgba(79,158,255,.06);border-left:3px solid var(--acc);border-radius:0 4px 4px 0;font-size:12px;color:var(--tx2);line-height:1.75;}
.insight strong{color:var(--acc2);}
.insight.warn-box{background:rgba(240,136,62,.06);border-left-color:var(--org);}
.insight.warn-box strong{color:var(--org);}

/* ── DB SCHEMA CARD ── */
.schema-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-bottom:12px;}
.schema-tbl{background:var(--surf3);border:1px solid var(--bdr);border-radius:6px;overflow:hidden;}
.schema-tbl-hdr{background:var(--surf2);padding:8px 12px;border-bottom:1px solid var(--bdr2);display:flex;align-items:center;gap:8px;}
.schema-tbl-name{font-family:'IBM Plex Mono',monospace;font-size:12px;font-weight:700;color:var(--acc);}
.schema-tbl-type{font-size:10px;color:var(--tx3);font-family:'IBM Plex Mono',monospace;}
.schema-field{display:flex;align-items:center;gap:8px;padding:5px 12px;border-bottom:1px solid var(--bdr2);font-size:11px;}
.schema-field:last-child{border-bottom:none;}
.field-key{font-family:'IBM Plex Mono',monospace;font-size:10px;font-weight:700;padding:1px 5px;border-radius:3px;flex-shrink:0;}
.field-key.pk{background:rgba(240,176,41,.15);color:var(--gold);border:1px solid rgba(240,176,41,.3);}
.field-key.fk{background:rgba(167,139,250,.15);color:var(--pur);border:1px solid rgba(167,139,250,.3);}
.field-key.idx{background:rgba(79,158,255,.1);color:var(--acc);border:1px solid rgba(79,158,255,.2);}
.field-name{font-family:'IBM Plex Mono',monospace;color:var(--tx);font-size:11px;flex:1;}
.field-type{font-size:10px;color:var(--tx3);font-family:'IBM Plex Mono',monospace;}
.field-card{font-size:10px;color:var(--teal);font-family:'IBM Plex Mono',monospace;margin-left:auto;}
.rel-arrows{display:flex;flex-direction:column;gap:6px;padding:10px 12px;background:var(--surf3);border:1px solid var(--bdr);border-radius:6px;margin-top:10px;}
.rel-row{display:flex;align-items:center;gap:8px;font-size:11px;font-family:'IBM Plex Mono',monospace;color:var(--tx2);}
.rel-type{background:rgba(34,211,174,.12);color:var(--teal);border:1px solid rgba(34,211,174,.25);padding:1px 7px;border-radius:3px;font-size:10px;font-weight:700;flex-shrink:0;}

/* ── CANVAS ── */
.chart-wrap{position:relative;width:100%;}
canvas{display:block;width:100%!important;}

/* ── NOTE ── */
.note{padding:11px 15px;border-radius:6px;font-size:13px;color:var(--tx2);line-height:1.75;margin-bottom:16px;}
.note.blue{background:rgba(79,158,255,.07);border-left:3px solid var(--acc);}
.note.red{background:rgba(240,96,96,.08);border-left:3px solid var(--red);}
.note.grn{background:rgba(52,192,106,.07);border-left:3px solid var(--grn);}
.note.org{background:rgba(245,136,58,.07);border-left:3px solid var(--org);}
.note.gold{background:rgba(234,179,8,.07);border-left:3px solid var(--gold);}
.note strong{color:var(--tx);}

/* ── ANSWER FIELDS ── */
.name-row{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:18px;}
.name-field{background:var(--surf2);border:1px solid var(--bdr);border-radius:6px;overflow:hidden;transition:border-color .2s;}
.name-field:focus-within{border-color:var(--acc);}
.name-field label{display:block;padding:7px 13px 0;font-size:11px;font-weight:700;color:var(--tx3);letter-spacing:.8px;text-transform:uppercase;font-family:'IBM Plex Mono',monospace;}
.name-field input{width:100%;background:transparent;border:none;outline:none;color:var(--tx);font-family:'Noto Sans KR',sans-serif;font-size:14px;padding:4px 13px 10px;}
.name-field input::placeholder{color:var(--tx3);}
.afield{background:var(--surf2);border:1px solid var(--bdr2);border-radius:6px;overflow:hidden;margin-bottom:12px;transition:border-color .2s;}
.afield:focus-within{border-color:var(--acc);box-shadow:0 0 0 3px rgba(79,158,255,.1);}
.afield-lbl{padding:9px 13px;background:rgba(79,158,255,.04);border-bottom:1px solid var(--bdr2);display:flex;align-items:center;justify-content:space-between;}
.afield-lbl-l{display:flex;align-items:center;gap:9px;}
.fnum{background:var(--acc);color:#0b0f18;font-family:'IBM Plex Mono',monospace;font-size:10px;font-weight:700;width:18px;height:18px;border-radius:50%;display:flex;align-items:center;justify-content:center;flex-shrink:0;}
.ftitle{font-size:12px;font-weight:700;}
.fsub{font-size:11px;color:var(--tx3);}
.fcount{font-size:11px;font-family:'IBM Plex Mono',monospace;color:var(--tx3);}
.afield textarea{width:100%;background:transparent;border:none;outline:none;color:var(--tx);font-family:'Noto Sans KR',sans-serif;font-size:13px;line-height:1.85;padding:12px 13px;resize:none;min-height:90px;}
.afield textarea.lg{min-height:140px;}
.afield textarea:disabled{opacity:.4;cursor:not-allowed;}
.afield textarea::placeholder{color:var(--tx3);font-size:12px;}
.char-bar{display:flex;align-items:center;justify-content:space-between;padding:10px 14px;background:var(--surf3);border-radius:6px;margin-bottom:12px;font-size:12px;color:var(--tx2);font-family:'IBM Plex Mono',monospace;}
.sbtn{width:100%;background:var(--acc);color:#0b0f18;border:none;padding:14px;font-family:'Noto Serif KR',serif;font-size:16px;font-weight:700;cursor:pointer;border-radius:6px;transition:all .2s;letter-spacing:.3px;}
.sbtn:hover:not(:disabled){background:var(--acc2);transform:translateY(-1px);}
.sbtn:disabled{background:var(--surf3);color:var(--tx3);cursor:not-allowed;transform:none;}
.sub-ok{text-align:center;padding:40px 20px;background:var(--surf2);border:1px solid var(--bdr);border-radius:8px;}
.sub-ok .icon{font-size:44px;margin-bottom:12px;}
.sub-ok h3{font-family:'Noto Serif KR',serif;font-size:20px;font-weight:700;color:var(--grn);margin-bottom:8px;}
.sub-ok p{font-size:13px;color:var(--tx2);line-height:1.8;}

/* ── TEACHER LOGIN ── */
.login-wrap{max-width:420px;margin:70px auto;text-align:center;}
.login-wrap h2{font-family:'Noto Serif KR',serif;font-size:22px;font-weight:700;margin-bottom:8px;}
.login-wrap p{font-size:13px;color:var(--tx2);margin-bottom:26px;}
.pw-row{display:flex;gap:8px;margin-bottom:8px;}
.pw-in{flex:1;background:var(--surf2);border:1px solid var(--bdr);border-radius:6px;padding:10px 14px;color:var(--tx);font-family:'IBM Plex Mono',monospace;font-size:14px;outline:none;}
.pw-in:focus{border-color:var(--acc);}
.pw-btn{background:var(--acc);color:#0b0f18;border:none;padding:10px 20px;font-weight:700;font-size:13px;border-radius:6px;cursor:pointer;font-family:'Noto Sans KR',sans-serif;}
.pw-btn:hover{background:var(--acc2);}
.pw-err{color:var(--red);font-size:12px;font-family:'IBM Plex Mono',monospace;min-height:18px;}

/* ── TEACHER DASHBOARD ── */
.t-top{display:flex;align-items:center;justify-content:space-between;margin-bottom:18px;flex-wrap:wrap;gap:12px;}
.t-top h2{font-family:'Noto Serif KR',serif;font-size:17px;font-weight:700;}
.stats{display:flex;gap:8px;flex-wrap:wrap;}
.sbox{background:var(--surf);border:1px solid var(--bdr);border-radius:6px;padding:9px 14px;text-align:center;min-width:72px;}
.snum{font-family:'IBM Plex Mono',monospace;font-size:18px;font-weight:700;color:var(--acc);}
.slbl{font-size:10px;color:var(--tx3);margin-top:1px;}
.t-actions{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:18px;align-items:center;}
.tbtn{padding:8px 14px;font-size:12px;font-weight:700;border-radius:5px;border:none;cursor:pointer;transition:all .2s;font-family:'Noto Sans KR',sans-serif;white-space:nowrap;}
.tbtn.pri{background:var(--acc);color:#0b0f18;}
.tbtn.pri:hover:not(:disabled){background:var(--acc2);}
.tbtn.pri:disabled{background:var(--surf3);color:var(--tx3);cursor:not-allowed;}
.tbtn.sec{background:transparent;border:1px solid var(--bdr);color:var(--tx2);}
.tbtn.sec:hover{border-color:var(--tx2);color:var(--tx);}
.tbtn.danger{background:transparent;border:1px solid var(--red);color:var(--red);}
.tbtn.danger:hover{background:rgba(240,96,96,.08);}
.sort-row{display:flex;align-items:center;gap:10px;margin-bottom:14px;flex-wrap:wrap;}
.sort-lbl{font-size:12px;color:var(--tx3);font-family:'IBM Plex Mono',monospace;}
.sort-btn{background:var(--surf2);border:1px solid var(--bdr);color:var(--tx2);padding:5px 12px;font-size:11px;border-radius:4px;cursor:pointer;transition:all .2s;font-family:'IBM Plex Mono',monospace;}
.sort-btn:hover,.sort-btn.on{border-color:var(--acc);color:var(--acc);background:rgba(79,158,255,.08);}
.filter-input{background:var(--surf2);border:1px solid var(--bdr);color:var(--tx);padding:6px 12px;font-size:12px;border-radius:5px;outline:none;font-family:'Noto Sans KR',sans-serif;width:160px;}
.filter-input:focus{border-color:var(--acc);}

/* ── SCORE SUMMARY TABLE ── */
.score-tbl-wrap{background:var(--surf);border:1px solid var(--bdr);border-radius:8px;overflow:hidden;margin-bottom:20px;}
.score-tbl{width:100%;border-collapse:collapse;font-size:12px;}
.score-tbl th{background:var(--surf2);color:var(--tx2);font-weight:700;font-family:'IBM Plex Mono',monospace;font-size:11px;padding:9px 12px;text-align:center;border-bottom:1px solid var(--bdr);position:sticky;top:0;}
.score-tbl th:first-child,.score-tbl td:first-child{text-align:left;}
.score-tbl td{padding:8px 12px;border-bottom:1px solid var(--bdr2);text-align:center;font-family:'IBM Plex Mono',monospace;font-size:12px;color:var(--tx2);}
.score-tbl tr:hover td{background:rgba(79,158,255,.04);}
.score-tbl td.name-col{font-family:'Noto Sans KR',sans-serif;color:var(--tx);font-size:12px;}
.score-pill{display:inline-block;padding:2px 8px;border-radius:3px;font-weight:700;font-size:11px;}
.sp-a{background:rgba(52,192,106,.12);color:var(--grn);border:1px solid rgba(52,192,106,.3);}
.sp-b{background:rgba(79,158,255,.12);color:var(--acc);border:1px solid rgba(79,158,255,.3);}
.sp-c{background:rgba(245,136,58,.12);color:var(--org);border:1px solid rgba(245,136,58,.3);}
.sp-d{background:rgba(240,96,96,.12);color:var(--red);border:1px solid rgba(240,96,96,.3);}
.sp-none{background:var(--surf3);color:var(--tx3);border:1px solid var(--bdr);}
.time-col{font-size:10px;color:var(--tx3);}

/* ── SUBMISSION DETAIL CARD ── */
.sub-list{display:flex;flex-direction:column;gap:10px;}
.scard{background:var(--surf);border:1px solid var(--bdr);border-radius:8px;overflow:hidden;transition:border-color .2s;}
.scard:hover{border-color:rgba(79,158,255,.3);}
.scard-hdr{padding:12px 18px;display:flex;align-items:center;justify-content:space-between;cursor:pointer;user-select:none;}
.scard-hdr:hover{background:rgba(255,255,255,.015);}
.shdr-l{display:flex;align-items:center;gap:10px;}
.sno{font-family:'IBM Plex Mono',monospace;font-size:10px;color:var(--tx3);background:var(--surf2);border:1px solid var(--bdr2);padding:2px 6px;border-radius:3px;}
.sname{font-weight:700;font-size:14px;}
.sid{font-size:11px;color:var(--tx3);font-family:'IBM Plex Mono',monospace;}
.stime{font-size:10px;color:var(--tx3);font-family:'IBM Plex Mono',monospace;}
.shdr-r{display:flex;align-items:center;gap:8px;}
.sbadge{font-family:'IBM Plex Mono',monospace;font-size:12px;font-weight:700;padding:3px 10px;border-radius:3px;border:1.5px solid;}
.sbadge.a{color:var(--grn);border-color:var(--grn);background:rgba(52,192,106,.08);}
.sbadge.b{color:var(--acc);border-color:var(--acc);background:rgba(79,158,255,.08);}
.sbadge.c{color:var(--org);border-color:var(--org);background:rgba(245,136,58,.08);}
.sbadge.d{color:var(--red);border-color:var(--red);background:rgba(240,96,96,.08);}
.sbadge.none{color:var(--tx3);border-color:var(--bdr);}
.scard-body{border-top:1px solid var(--bdr2);padding:16px 18px;display:none;}
.scard-body.open{display:block;}
.sans-item{margin-bottom:12px;padding:12px 14px;background:var(--surf2);border-radius:5px;border-left:3px solid var(--bdr);}
.sans-item.has{border-left-color:var(--acc);}
.sans-title{font-size:11px;font-family:'IBM Plex Mono',monospace;color:var(--tx3);margin-bottom:6px;text-transform:uppercase;letter-spacing:.8px;}
.sans-text{font-size:13px;line-height:1.85;color:var(--tx2);white-space:pre-wrap;}
.divider{height:1px;background:var(--bdr2);margin:14px 0;}

/* ── GRADE BOX ── */
.grade-box{background:rgba(79,158,255,.04);border:1px solid rgba(79,158,255,.18);border-radius:8px;padding:16px;margin-top:12px;}
.grade-box-title{font-size:11px;font-family:'IBM Plex Mono',monospace;color:var(--acc);margin-bottom:12px;letter-spacing:.8px;}
.total-score-row{display:flex;align-items:center;justify-content:space-between;padding:10px 13px;background:var(--surf3);border-radius:5px;margin-bottom:12px;}
.tsl{font-weight:700;font-size:13px;}
.tsr{font-family:'IBM Plex Mono',monospace;font-size:24px;font-weight:700;color:var(--acc);}
.tsr small{font-size:13px;color:var(--tx3);font-weight:400;}
.gitems{display:grid;grid-template-columns:repeat(2,1fr);gap:8px;margin-bottom:12px;}
.gitem{background:var(--surf3);border-radius:5px;padding:10px 11px;}
.gi-name{font-size:11px;color:var(--tx3);margin-bottom:4px;}
.gi-sc{font-family:'IBM Plex Mono',monospace;font-weight:700;font-size:15px;}
.gi-sc small{font-size:11px;font-weight:400;color:var(--tx3);}
.pbar-w{height:4px;background:var(--bdr);border-radius:2px;margin-top:4px;}
.pbar{height:100%;border-radius:2px;transition:width .6s ease;}
.gi-deduct{font-size:11px;color:var(--red);margin-top:5px;line-height:1.6;padding:5px 8px;background:rgba(240,96,96,.06);border-radius:3px;border-left:2px solid var(--red);}
.gi-deduct.none{color:var(--grn);background:rgba(52,192,106,.06);border-left-color:var(--grn);}
.gfeedback{font-size:13px;color:var(--tx2);line-height:1.85;padding:11px 13px;background:var(--surf2);border-radius:5px;margin-bottom:8px;}
.gfeedback strong{color:var(--tx);}
.grade-actions{display:flex;gap:8px;margin-top:12px;}
.gbtn{flex:1;padding:9px;font-size:12px;font-weight:700;border-radius:5px;border:none;cursor:pointer;font-family:'Noto Sans KR',sans-serif;transition:all .2s;}
.gbtn.pri{background:var(--acc);color:#0b0f18;}
.gbtn.pri:hover:not(:disabled){background:var(--acc2);}
.gbtn.pri:disabled{background:var(--surf3);color:var(--tx3);cursor:not-allowed;}
.gbtn.sec{background:transparent;border:1px solid var(--bdr);color:var(--tx2);}
.gbtn.sec:hover{border-color:var(--tx2);color:var(--tx);}

/* ── STUDENT FEEDBACK CARD ── */
.feedback-card{background:var(--surf);border:1px solid rgba(79,158,255,.25);border-radius:8px;padding:18px;margin-top:16px;}
.fc-header{display:flex;align-items:center;gap:10px;margin-bottom:14px;}
.fc-header h4{font-family:'Noto Serif KR',serif;font-size:14px;font-weight:700;}
.fc-score{font-family:'IBM Plex Mono',monospace;font-size:20px;font-weight:700;color:var(--acc);margin-left:auto;}
.fc-items{display:flex;flex-direction:column;gap:8px;}
.fc-item{padding:10px 13px;border-radius:5px;border:1px solid var(--bdr2);}
.fc-item.ok{background:rgba(52,192,106,.05);border-color:rgba(52,192,106,.2);}
.fc-item.deduct{background:rgba(240,96,96,.05);border-color:rgba(240,96,96,.2);}
.fc-item-top{display:flex;align-items:center;gap:8px;margin-bottom:4px;}
.fc-item-name{font-size:12px;font-weight:700;}
.fc-item-score{font-family:'IBM Plex Mono',monospace;font-size:12px;font-weight:700;margin-left:auto;}
.fc-item.ok .fc-item-score{color:var(--grn);}
.fc-item.deduct .fc-item-score{color:var(--red);}
.fc-item-comment{font-size:12px;color:var(--tx2);line-height:1.65;}

/* ── SPINNER ── */
.spin{display:inline-block;width:12px;height:12px;border:2px solid rgba(255,255,255,.2);border-top-color:#0b0f18;border-radius:50%;animation:rot .65s linear infinite;margin-right:5px;vertical-align:middle;}
.spin.lt{border-top-color:var(--tx);}
@keyframes rot{to{transform:rotate(360deg);}}
@keyframes fadeUp{from{opacity:0;transform:translateY(12px);}to{opacity:1;transform:translateY(0);}}
.dc:nth-child(1){animation-delay:.04s}
.dc:nth-child(2){animation-delay:.08s}
.dc:nth-child(3){animation-delay:.12s}
.dc:nth-child(4){animation-delay:.16s}
.dc:nth-child(5){animation-delay:.20s}

/* ── TEACHER HINT (독해포인트) ── */
.teacher-hint { display: none; }
body.teacher-mode .teacher-hint { display: block; }

/* ── EMPTY ── */
.empty{text-align:center;padding:56px 20px;color:var(--tx3);}
.empty .eicon{font-size:38px;margin-bottom:10px;}

/* ── MODAL (feedback print) ── */
.modal-bg{display:none;position:fixed;inset:0;background:rgba(0,0,0,.7);z-index:500;align-items:center;justify-content:center;}
.modal-bg.open{display:flex;}
.modal{background:var(--surf);border:1px solid var(--bdr);border-radius:10px;max-width:560px;width:90%;max-height:85vh;overflow-y:auto;padding:24px;}
.modal-hdr{display:flex;align-items:center;justify-content:space-between;margin-bottom:18px;}
.modal-hdr h3{font-family:'Noto Serif KR',serif;font-size:16px;font-weight:700;}
.modal-close{background:transparent;border:none;color:var(--tx3);font-size:20px;cursor:pointer;line-height:1;}
.modal-close:hover{color:var(--tx);}

@media print{.hdr,.tabs,.t-actions,.t-top,.sort-row,.grade-actions{display:none!important;}.panel{display:block!important;}}
@media(max-width:700px){
  .data-grid{grid-template-columns:1fr;}
  .dc.wide,.dc.triple{grid-column:1;}
  .schema-grid{grid-template-columns:1fr;}
  .gitems{grid-template-columns:1fr;}
  .name-row{grid-template-columns:1fr;}
  .hdr-right{display:none;}
}
</style>
</head>
<body>
<!-- HEADER -->
<header class="hdr">
  <div class="hdr-in">
    <div class="hdr-left">
      <span class="exam-badge" id="mode-chip">수행평가</span>
      <span class="hdr-title">수행평가 : 데이터 기반 사회변화 논증하기 (20%)</span>
    </div>
    <div class="hdr-right">
      <span>광문고 데이터과학</span>
      <span>by 김채연T</span>
      <span class="pt">만점 20점</span>
    </div>
  </div>
</header>

<!-- TABS -->
<nav class="tabs">
  <div class="tabs-in">
    <button class="tab on" id="tab-data" onclick="switchTab('data',this)">📊 문제 &amp; 데이터</button>
    <button class="tab" id="tab-answer" onclick="switchTab('answer',this)">✍️ 답안 작성</button>
    <button class="tab teacher-only" id="tab-example" onclick="switchTab('example',this)">💡 예시 답안<span class="tbadge">교사</span></button>
    <button class="tab teacher-only" id="tab-rubric" onclick="switchTab('rubric',this)">📋 채점 기준<span class="tbadge">교사</span></button>
    <button class="tab teacher-only ton" id="tab-teacher" onclick="switchTab('teacher',this)">🔐 교사 채점<span class="tbadge">교사</span></button>
  </div>
</nav>

<main class="main">

<!-- ════════════════ PANEL: 문제 & 데이터 ════════════════ -->
<div id="panel-data" class="panel on">

  <div class="qbox">
    <div class="qbox-meta">
      <span class="qtag s">만점 20점</span>
      <span class="qtag t">50분</span>
      <span class="qtag l">논술형 · 상급</span>
      <span class="qtag c">차수 · 카디널리티 · 관계유형</span>
    </div>
    <div class="qbox-title">
      아래 제시된 4개의 자료(데이터베이스 구조 분석표, 집계 데이터, 시각화 차트, 통계 보고서)를 종합 분석하여,<br>
      <strong>「온라인 플랫폼 경제의 성장이 한국 청년 노동시장 구조를 어떻게 변화시키고 있는가」</strong>에 대해<br>
      데이터를 근거로 논증하는 글을 작성하시오.
    </div>

    <div class="qbox-conds">
      <h4>✦ 작성 조건 (모두 충족해야 만점)</h4>
      <div class="cond-list">
        <div class="cond"><span class="cond-n">1</span><span><strong>[자료 번호] 명시 필수:</strong> 인용 시 반드시 [자료1]~[자료4] 형태로 출처를 표기하고, 구체적인 수치·컬럼명·관계 구조를 근거로 활용할 것</span></div>
        <div class="cond"><span class="cond-n">2</span><span><strong>DB 개념 활용:</strong> [자료1]에서 <strong>차수(Degree), 카디널리티(Cardinality), 관계 유형(1:N·M:N)</strong> 중 최소 2개 이상의 개념을 본문에 직접 서술하며 논거로 사용할 것 (개념 정의 + 수치 근거 모두 포함)</span></div>
        <div class="cond"><span class="cond-n">3</span><span><strong>자료 최소 3개 이상 인용:</strong> 4개 자료 중 3개 이상을 논증에 통합할 것 (단순 언급은 인용으로 불인정 — 수치와 함께 해석해야 함)</span></div>
        <div class="cond"><span class="cond-n">4</span><span><strong>반론 인식 후 재반박:</strong> 플랫폼 경제의 부정적 측면(불안정 고용, 수입 변동성 등)을 인정하되, 데이터를 근거로 재반박할 것</span></div>
        <div class="cond"><span class="cond-n">5</span><span><strong>분량 기준:</strong> 각 항목(주장·근거1·근거2·반론재반박·결론) 최소 50자 이상 / 전체 최소 500자. <strong>결론에 정책·사회적 제언을 구체적으로 포함</strong>할 것</span></div>
      </div>
    </div>

    <div class="qbox-struct">
      <div class="struct-step"><span class="snum">①</span>주장</div>
      <span class="struct-arrow">→</span>
      <div class="struct-step"><span class="snum">②</span>근거1 (DB 개념 활용)</div>
      <span class="struct-arrow">→</span>
      <div class="struct-step"><span class="snum">③</span>근거2 (통계·차트 분석)</div>
      <span class="struct-arrow">→</span>
      <div class="struct-step"><span class="snum">④</span>반론 인식 + 재반박</div>
      <span class="struct-arrow">→</span>
      <div class="struct-step"><span class="snum">⑤</span>결론 + 사회적 제언</div>
    </div>
  </div>

  <div class="sec-hdr"><h3>제시 자료 (4종)</h3><div class="sec-line"></div><span class="sec-chip">DATA SOURCES</span></div>

  <div class="data-grid">

    <!-- 자료 1: 플랫폼 노동 DB 구조 분석 (차수·카디널리티) -->
    <div class="dc wide">
      <div class="dc-hdr">
        <div class="dc-title">
          <div class="dicon" style="background:rgba(240,176,41,.12)">🗄️</div>
          <div>
            <h4>[자료 1] 플랫폼 노동 데이터베이스 구조 분석표</h4>
            <small>5개 테이블 · 각 테이블의 차수(Degree)와 카디널리티(Cardinality) 정보</small>
          </div>
        </div>
        <span class="dsrc">플랫폼 노동 실태조사 DB</span>
      </div>
      <div class="dc-body">

        <!-- 테이블 구조 분석표 -->
        <table class="dtbl">
          <thead>
            <tr>
              <th style="text-align:left">테이블명</th>
              <th>역할 (담고 있는 정보)</th>
              <th>차수</th>
              <th>카디널리티</th>
              <th>주요 속성</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><strong>WORKER</strong> (참여자)</td>
              <td style="text-align:left;font-family:'Noto Sans KR',sans-serif;">플랫폼 노동 참여자 기본 정보</td>
              <td class="hl">7</td>
              <td class="hl">28,419</td>
              <td style="text-align:left;font-size:11px;color:var(--tx3);">나이·학력·지역·성별·가입연도·주업여부</td>
            </tr>
            <tr>
              <td><strong>PLATFORM</strong> (플랫폼)</td>
              <td style="text-align:left;font-family:'Noto Sans KR',sans-serif;">등록된 플랫폼 기본 정보</td>
              <td>5</td>
              <td>12</td>
              <td style="text-align:left;font-size:11px;color:var(--tx3);">플랫폼명·카테고리·출시연도·시장점유율</td>
            </tr>
            <tr>
              <td><strong>CONTRACT</strong> (계약)</td>
              <td style="text-align:left;font-family:'Noto Sans KR',sans-serif;">참여자-플랫폼-클라이언트 간 계약 이력</td>
              <td class="hl">8</td>
              <td class="hl2">1,847,302</td>
              <td style="text-align:left;font-size:11px;color:var(--tx3);">계약유형·금액·기간·완료일시 + 참조키 3개</td>
            </tr>
            <tr>
              <td><strong>CLIENT</strong> (의뢰인)</td>
              <td style="text-align:left;font-family:'Noto Sans KR',sans-serif;">업무를 의뢰한 기업·개인 정보</td>
              <td>5</td>
              <td>94,203</td>
              <td style="text-align:left;font-size:11px;color:var(--tx3);">기업규모·업종·재의뢰여부·평균평점</td>
            </tr>
            <tr>
              <td><strong>INCOME_LOG</strong> (수입기록)</td>
              <td style="text-align:left;font-family:'Noto Sans KR',sans-serif;">참여자별 월별 수입 상세 기록</td>
              <td>6</td>
              <td class="hl2">5,291,044</td>
              <td style="text-align:left;font-size:11px;color:var(--tx3);">연월·총수입·플랫폼 수수료</td>
            </tr>
          </tbody>
        </table>

        <!-- 테이블 간 관계 -->
        <div style="margin-top:14px;background:var(--surf3);border:1px solid var(--bdr);border-radius:6px;padding:12px 16px;">
          <div style="font-size:11px;font-family:'IBM Plex Mono',monospace;color:var(--tx2);font-weight:700;margin-bottom:10px;">테이블 간 관계 (Relationship)</div>
          <div style="display:flex;flex-direction:column;gap:7px;font-size:12px;font-family:'IBM Plex Mono',monospace;color:var(--tx2);">
            <div style="display:flex;align-items:center;gap:10px;"><span style="background:rgba(34,211,174,.12);color:var(--teal);border:1px solid rgba(34,211,174,.25);padding:1px 8px;border-radius:3px;font-size:10px;font-weight:700;flex-shrink:0;">1 : N</span><span>WORKER → CONTRACT (한 참여자가 여러 계약 체결 가능)</span></div>
            <div style="display:flex;align-items:center;gap:10px;"><span style="background:rgba(34,211,174,.12);color:var(--teal);border:1px solid rgba(34,211,174,.25);padding:1px 8px;border-radius:3px;font-size:10px;font-weight:700;flex-shrink:0;">1 : N</span><span>PLATFORM → CONTRACT (한 플랫폼에 여러 계약 등록)</span></div>
            <div style="display:flex;align-items:center;gap:10px;"><span style="background:rgba(167,139,250,.12);color:var(--pur);border:1px solid rgba(167,139,250,.25);padding:1px 8px;border-radius:3px;font-size:10px;font-weight:700;flex-shrink:0;">M : N</span><span>WORKER ↔ PLATFORM (한 참여자가 여러 플랫폼에서 동시 활동 가능)</span></div>
            <div style="display:flex;align-items:center;gap:10px;"><span style="background:rgba(34,211,174,.12);color:var(--teal);border:1px solid rgba(34,211,174,.25);padding:1px 8px;border-radius:3px;font-size:10px;font-weight:700;flex-shrink:0;">1 : N</span><span>CONTRACT → INCOME_LOG (하나의 계약에서 여러 달의 수입 기록 생성)</span></div>
          </div>
        </div>

        <div class="insight teacher-hint" style="margin-top:12px;">
          <strong>독해 포인트:</strong>
          CONTRACT 테이블의 <strong>카디널리티(1,847,302)</strong>는 WORKER(28,419)의 약 <strong>65배</strong> →
          참여자 1인당 평균 65건의 계약 이력 보유.
          INCOME_LOG의 카디널리티(5,291,044)는 CONTRACT의 약 2.9배 →
          계약 1건당 평균 <strong>2.9개월</strong>치 수입 기록 생성.
          CONTRACT 테이블의 <strong>차수(8)</strong>가 가장 높아, 계약 정보가 이 데이터베이스에서 가장 복합적인 정보를 담고 있음을 의미.
        </div>
      </div>
    </div>

    <!-- 자료 2: 연도별 플랫폼 노동 집계 -->
    <div class="dc">
      <div class="dc-hdr">
        <div class="dc-title">
          <div class="dicon" style="background:rgba(79,158,255,.12)">📈</div>
          <div>
            <h4>[자료 2] 플랫폼 노동 참여 규모 연도별 집계</h4>
            <small>2016–2024 · 고용노동부 플랫폼 노동 실태조사 연도별 집계</small>
          </div>
        </div>
        <span class="dsrc">플랫폼 노동 DB 집계</span>
      </div>
      <div class="dc-body">
        <div class="chart-wrap" style="height:200px"><canvas id="c2"></canvas></div>
        <table class="dtbl" style="margin-top:10px">
          <thead><tr><th>연도</th><th>신규워커(명)</th><th>20대비율(%)</th><th>주업비율(%)</th><th>평균월수입(만원)</th></tr></thead>
          <tbody>
            <tr><td>2016</td><td>1,204</td><td>31.2</td><td>18.4</td><td>87</td></tr>
            <tr><td>2018</td><td>3,871</td><td>38.6</td><td>24.1</td><td>104</td></tr>
            <tr><td>2020</td><td>8,940</td><td>44.8</td><td>31.7</td><td>121</td></tr>
            <tr><td>2022</td><td>7,213</td><td>51.3</td><td>38.9</td><td>148</td></tr>
            <tr><td>2024</td><td class="hl">5,187</td><td class="hl">57.4</td><td class="hl">47.2</td><td class="hl">172</td></tr>
          </tbody>
        </table>
        <div class="insight teacher-hint"><strong>독해 포인트:</strong> 신규 워커 수는 2020년 정점 후 감소하나, 20대 비율(31%→57%)과 <strong>주업 비율(18%→47%)</strong>은 지속 상승 → 플랫폼 노동의 '부업→주업 전환' 구조 변화.</div>
      </div>
    </div>

    <!-- 자료 3: 직종별 수입 분포 -->
    <div class="dc">
      <div class="dc-hdr">
        <div class="dc-title">
          <div class="dicon" style="background:rgba(52,192,106,.12)">💰</div>
          <div>
            <h4>[자료 3] 플랫폼 카테고리별 수입 분포 (2024)</h4>
            <small>플랫폼 노동 실태조사 직종별 분석 · 단위: 만원/월</small>
          </div>
        </div>
        <span class="dsrc">플랫폼 DB 분석 결과</span>
      </div>
      <div class="dc-body">
        <div class="chart-wrap" style="height:200px"><canvas id="c3"></canvas></div>
        <table class="dtbl" style="margin-top:10px">
          <thead><tr><th>플랫폼 카테고리</th><th>중위수입</th><th>상위10%</th><th>하위10%</th><th>변동계수</th></tr></thead>
          <tbody>
            <tr><td>IT·개발</td><td class="hl">287</td><td>512</td><td>143</td><td class="dn">0.41</td></tr>
            <tr><td>디자인·창작</td><td>198</td><td>381</td><td>72</td><td>0.58</td></tr>
            <tr><td>번역·글쓰기</td><td>134</td><td>248</td><td>41</td><td>0.63</td></tr>
            <tr><td>배달·운송</td><td>163</td><td>221</td><td>88</td><td class="warn">0.38</td></tr>
            <tr><td>가사·청소</td><td>121</td><td>178</td><td>64</td><td>0.39</td></tr>
            <tr><td>전문직(법·회계)</td><td class="hl2">342</td><td>680</td><td>112</td><td class="up">0.72</td></tr>
          </tbody>
        </table>
        <div class="insight warn-box teacher-hint"><strong>독해 포인트:</strong> 전문직의 변동계수(0.72)가 가장 높아 수입 불안정성 극심. 반면 배달·운송(0.38)은 안정적이나 수입 상한이 낮음. IT직종은 중위수입과 안정성 모두 우수.</div>
      </div>
    </div>

    <!-- 자료 4: 청년층 고용 구조 변화 통계 -->
    <div class="dc wide">
      <div class="dc-hdr">
        <div class="dc-title">
          <div class="dicon" style="background:rgba(167,139,250,.12)">📊</div>
          <div>
            <h4>[자료 4] 청년층(20~34세) 고용 형태 변화 통계 (2015→2024)</h4>
            <small>통계청 경제활동인구조사 + 고용노동부 실태조사 연계 분석</small>
          </div>
        </div>
        <span class="dsrc">통계청·플랫폼 DB</span>
      </div>
      <div class="dc-body">
        <div style="display:grid;grid-template-columns:1.2fr 1fr;gap:18px;align-items:start;">
          <div>
            <div class="chart-wrap" style="height:210px"><canvas id="c4"></canvas></div>
          </div>
          <div>
            <table class="dtbl">
              <thead>
                <tr><th>고용형태</th><th>2015(%)</th><th>2024(%)</th><th>변화</th></tr>
              </thead>
              <tbody>
                <tr><td>정규직 취업</td><td>48.3</td><td class="up">35.1</td><td class="up">▼13.2p</td></tr>
                <tr><td>비정규직</td><td>22.4</td><td>19.8</td><td class="up">▼2.6p</td></tr>
                <tr><td>플랫폼 주업</td><td>1.2</td><td class="hl">12.7</td><td class="dn">▲11.5p</td></tr>
                <tr><td>플랫폼 부업</td><td>3.1</td><td class="hl">18.4</td><td class="dn">▲15.3p</td></tr>
                <tr><td>자영업</td><td>11.7</td><td>8.3</td><td class="up">▼3.4p</td></tr>
                <tr><td>구직 중/무직</td><td>13.3</td><td>5.7</td><td class="dn">▼7.6p</td></tr>
              </tbody>
            </table>
            <div class="insight teacher-hint" style="margin-top:10px"><strong>독해 포인트:</strong> 청년 정규직 비율이 9년간 <strong>13.2%p 감소</strong>한 반면, 플랫폼 노동(주업+부업) 합산 비율은 4.3%→31.1%로 <strong>26.8%p 급증</strong>. 청년 고용의 핵심 변수로 부상.</div>
          </div>
        </div>
      </div>
    </div>

  </div><!-- /data-grid -->
</div><!-- /panel-data -->
<!-- ════════════════ PANEL: 답안 작성 ════════════════ -->
<div id="panel-answer" class="panel">
  <div id="answer-form">
    <div class="note red"><strong>⚠ 제출 규칙:</strong> 학번은 고유 식별자로 사용됩니다. <strong>한 학번으로 1회만 제출</strong> 가능하며, 제출 후 수정이 불가합니다. 학번·이름을 정확히 입력하세요.</div>

    <div class="name-row">
      <div class="name-field">
        <label>학번</label>
        <input id="inp-sid" placeholder="예: 20312" maxlength="10" type="text">
      </div>
      <div class="name-field">
        <label>이름</label>
        <input id="inp-name" placeholder="본인 이름" maxlength="10">
      </div>
    </div>

    <div class="afield">
      <div class="afield-lbl">
        <div class="afield-lbl-l"><span class="fnum">1</span><div><div class="ftitle">주장 (Thesis)</div><div class="fsub">플랫폼 경제가 청년 노동시장에 미치는 영향에 대한 핵심 주장</div></div></div>
        <span class="fcount" id="fc1">0자</span>
      </div>
      <textarea id="ans1" oninput="cnt(1)" placeholder=""></textarea>
    </div>
    <div class="afield">
      <div class="afield-lbl">
        <div class="afield-lbl-l"><span class="fnum">2</span><div><div class="ftitle">근거 1 — DB 구조 기반 분석</div><div class="fsub">[자료1] 활용 · 차수·카디널리티·관계유형 개념 반드시 포함</div></div></div>
        <span class="fcount" id="fc2">0자</span>
      </div>
      <textarea id="ans2" oninput="cnt(2)" placeholder=""></textarea>
    </div>
    <div class="afield">
      <div class="afield-lbl">
        <div class="afield-lbl-l"><span class="fnum">3</span><div><div class="ftitle">근거 2 — 통계·차트 데이터 분석</div><div class="fsub">[자료2][자료3][자료4] 중 2개 이상 활용 · 구체 수치 필수</div></div></div>
        <span class="fcount" id="fc3">0자</span>
      </div>
      <textarea id="ans3" oninput="cnt(3)" placeholder=""></textarea>
    </div>
    <div class="afield">
      <div class="afield-lbl">
        <div class="afield-lbl-l"><span class="fnum">4</span><div><div class="ftitle">반론 인식 및 재반박</div><div class="fsub">불안정 고용·수입 변동성 인정 → 데이터로 재반박</div></div></div>
        <span class="fcount" id="fc4">0자</span>
      </div>
      <textarea id="ans4" oninput="cnt(4)" placeholder=""></textarea>
    </div>
    <div class="afield">
      <div class="afield-lbl">
        <div class="afield-lbl-l"><span class="fnum">5</span><div><div class="ftitle">결론 및 사회적 제언</div><div class="fsub">논증 종합 + 구체적 정책·제도 제언 포함 필수</div></div></div>
        <span class="fcount" id="fc5">0자</span>
      </div>
      <textarea id="ans5" class="lg" oninput="cnt(5)" placeholder=""></textarea>
    </div>

    <div class="char-bar">
      <span>총 작성: <strong id="total-c" style="font-family:'IBM Plex Mono',monospace">0</strong>자</span>
      <span style="color:var(--tx3)">권장: 500자 이상</span>
    </div>
    <button class="sbtn" onclick="submitAnswer()">📤 최종 제출 (학번당 1회)</button>
  </div>
  <div id="answer-done" style="display:none">
    <div class="sub-ok">
      <div class="icon">✅</div>
      <h3>제출 완료!</h3>
      <p id="done-msg"></p>
      <p style="margin-top:12px;font-size:12px;color:var(--tx3)">채점 결과는 교사에게 문의하거나 교사가 개별 피드백 카드를 제공합니다.</p>
    </div>
  </div>
</div>

<!-- ════════════════ PANEL: 예시 답안 (교사전용) ════════════════ -->
<div id="panel-example" class="panel">
  <div class="note org"><strong>📌 교사 전용:</strong> 아래 예시 답안은 배포 전 반드시 검토하세요.</div>

  <div style="background:var(--surf);border:1px solid var(--bdr);border-radius:8px;overflow:hidden;margin-bottom:16px;">
    <div style="padding:14px 20px;border-bottom:1px solid var(--bdr2);display:flex;align-items:center;justify-content:space-between;">
      <span style="font-family:'Noto Serif KR',serif;font-size:14px;font-weight:700;">
        💡 A등급 모범 예시 답안
        <span style="font-size:11px;font-family:'IBM Plex Mono',monospace;background:rgba(52,192,106,.12);color:var(--grn);border:1px solid rgba(52,192,106,.3);padding:2px 8px;border-radius:3px;margin-left:8px;">20점</span>
      </span>
      <button id="ex-toggle-a" onclick="toggleEx('ex-body-a','ex-toggle-a')" style="background:transparent;border:1px solid var(--bdr);color:var(--tx2);padding:5px 12px;border-radius:4px;cursor:pointer;font-size:12px;font-family:'Noto Sans KR',sans-serif;">▼ 보기</button>
    </div>
    <div id="ex-body-a" style="display:none;padding:20px;">

      <div style="margin-bottom:14px;padding:13px 15px;background:var(--surf2);border-radius:6px;border-left:3px solid var(--acc);">
        <div style="font-size:11px;font-family:'IBM Plex Mono',monospace;color:var(--acc);margin-bottom:8px;letter-spacing:.8px;">① 주장</div>
        <p style="font-size:13px;line-height:1.9;color:var(--tx2);">온라인 플랫폼 경제의 성장은 한국 청년 노동시장을 단순히 불안정화하는 것이 아니라, 전통적 고용 구조에서 탈피한 <strong style="color:var(--tx)">자율적 유연 노동으로의 구조적 전환</strong>을 주도하고 있다. 이 변화는 기회와 리스크를 동시에 내포하며, 데이터는 청년층이 이를 능동적으로 수용하고 있음을 보여준다.</p>
      </div>

      <div style="margin-bottom:14px;padding:13px 15px;background:var(--surf2);border-radius:6px;border-left:3px solid var(--grn);">
        <div style="font-size:11px;font-family:'IBM Plex Mono',monospace;color:var(--grn);margin-bottom:8px;letter-spacing:.8px;">② 근거 1 — DB 개념 활용 (차수·카디널리티)</div>
        <p style="font-size:13px;line-height:1.9;color:var(--tx2);">[자료1]에서 CONTRACT 테이블은 <strong style="color:var(--tx)">차수(Degree)가 8</strong>로 5개 테이블 중 가장 높아, 계약 정보가 가장 복합적인 데이터를 담고 있음을 의미한다. 또한 CONTRACT의 <strong style="color:var(--tx)">카디널리티(1,847,302)</strong>는 WORKER(28,419)의 약 65배에 달하는데, 이는 참여자 1인당 평균 65건의 계약을 체결함을 뜻하며 플랫폼 노동이 단발성이 아닌 지속적·반복적 형태임을 수치로 증명한다. WORKER와 PLATFORM 사이의 <strong style="color:var(--tx)">M:N(다대다) 관계</strong>는 한 참여자가 복수의 플랫폼에서 동시에 활동할 수 있는 구조임을 보여주며, 멀티 플랫폼 노동이 이미 일반화되었음을 알 수 있다.</p>
      </div>

      <div style="margin-bottom:14px;padding:13px 15px;background:var(--surf2);border-radius:6px;border-left:3px solid var(--org);">
        <div style="font-size:11px;font-family:'IBM Plex Mono',monospace;color:var(--org);margin-bottom:8px;letter-spacing:.8px;">③ 근거 2 — 통계·차트 데이터 분석</div>
        <p style="font-size:13px;line-height:1.9;color:var(--tx2);">[자료4]는 청년 정규직 비율이 2015년 48.3%에서 2024년 35.1%로 13.2%p 감소한 반면, 플랫폼 노동(주업+부업) 합산 비율은 4.3%에서 31.1%로 <strong style="color:var(--tx)">26.8%p 급증</strong>했음을 보여준다. 구직·무직 비율도 13.3%에서 5.7%로 감소해, 플랫폼 노동이 청년 실업의 실질적 완충 역할을 하고 있다. [자료2]에서도 20대 비율이 2016년 31.2%에서 2024년 57.4%로 상승하고 주업 비율이 47.2%에 달해, 이 변화가 선택이 아닌 <strong style="color:var(--tx)">청년 노동의 새로운 주류 형태</strong>로 자리잡고 있음을 확인할 수 있다. [자료1]의 대졸 이상 참여자 평균 월수입(247만원)이 고졸 이하(128만원)의 약 1.9배인 점도, 플랫폼 노동 내에서도 역량에 따라 수입 격차가 분명히 존재함을 뒷받침한다.</p>
      </div>

      <div style="margin-bottom:14px;padding:13px 15px;background:var(--surf2);border-radius:6px;border-left:3px solid var(--pur);">
        <div style="font-size:11px;font-family:'IBM Plex Mono',monospace;color:var(--pur);margin-bottom:8px;letter-spacing:.8px;">④ 반론 인식 및 재반박</div>
        <p style="font-size:13px;line-height:1.9;color:var(--tx2);">물론 플랫폼 노동이 긍정적 변화만을 의미하지는 않는다. [자료3]에서 전문직 카테고리의 변동계수가 0.72로 가장 높아 수입 불안정성이 극심하며, 번역·글쓰기 직종의 하위 10% 월수입은 41만원에 불과해 생활 유지조차 어려운 수준이다. 그러나 이는 플랫폼 노동 전체의 문제가 아닌 <strong style="color:var(--tx)">직종별 양극화</strong>의 문제다. [자료3]에서 IT·개발 직종은 중위수입 287만원에 변동계수 0.41로 상대적으로 안정적이며, [자료2]에서 전체 평균 월수입이 2016년 87만원에서 2024년 172만원으로 2배 증가한 사실은 플랫폼 노동의 경제적 가치가 꾸준히 개선되고 있음을 보여준다. 따라서 불안정성은 제도적 보완으로 해결해야 할 과제이지, 플랫폼 경제 자체를 부정할 근거가 될 수 없다.</p>
      </div>

      <div style="padding:13px 15px;background:var(--surf2);border-radius:6px;border-left:3px solid var(--teal);">
        <div style="font-size:11px;font-family:'IBM Plex Mono',monospace;color:var(--teal);margin-bottom:8px;letter-spacing:.8px;">⑤ 결론 및 사회적 제언</div>
        <p style="font-size:13px;line-height:1.9;color:var(--tx2);">4개 자료는 공통적으로 플랫폼 경제가 청년 노동시장의 구조를 돌이킬 수 없이 재편하고 있음을 가리킨다. 이 변화에 효과적으로 대응하기 위해 세 가지 제언을 제시한다. 첫째, 플랫폼 워커에게도 <strong style="color:var(--tx)">사회보험 적용 범위를 확대</strong>하고 최소 수입 보장 제도를 도입해야 한다. 둘째, [자료3]에서 변동계수가 높게 나타난 직종 종사자를 대상으로 <strong style="color:var(--tx)">수입 다각화 및 역량 강화 교육</strong>을 지원해야 한다. 셋째, [자료1]과 같은 플랫폼 노동 통합 데이터베이스를 국가 차원에서 구축하고, 카디널리티 변화 추이를 지속 모니터링하여 정책의 근거로 활용해야 한다. 데이터는 변화를 부정하는 도구가 아니라, 변화를 더 잘 관리하기 위한 나침반이다.</p>
      </div>

    </div>
  </div>
</div>

<!-- ════════════════ PANEL: 채점기준 (교사전용) ════════════════ -->
<div id="panel-rubric" class="panel">
  <div class="note gold"><strong>채점 배점:</strong> 만점 20점 · 8점 / 11~20점(1점 단위) · 대부분 학생이 15점 이상 취득 가능하도록 설계</div>

  <div style="background:var(--surf);border:1px solid var(--bdr);border-radius:8px;overflow:hidden;margin-bottom:16px;">
    <div style="padding:12px 18px;border-bottom:1px solid var(--bdr2);display:flex;align-items:center;justify-content:space-between;"><h4 style="font-size:14px;font-weight:700;">채점 기준표</h4><span style="font-family:'IBM Plex Mono',monospace;font-size:13px;color:var(--gold);font-weight:700;">총 20점</span></div>
    <table style="width:100%;border-collapse:collapse;font-size:13px;">
      <thead><tr style="background:var(--surf2);">
        <th style="padding:10px 14px;text-align:left;border-bottom:1px solid var(--bdr);font-size:12px;color:var(--tx2);">항목</th>
        <th style="padding:10px 14px;text-align:center;border-bottom:1px solid var(--bdr);font-size:12px;color:var(--tx2);">만점</th>
        <th style="padding:10px 14px;text-align:left;border-bottom:1px solid var(--bdr);font-size:12px;color:var(--tx2);">A (만점)</th>
        <th style="padding:10px 14px;text-align:left;border-bottom:1px solid var(--bdr);font-size:12px;color:var(--tx2);">감점 기준</th>
      </tr></thead>
      <tbody>
        <tr style="border-bottom:1px solid var(--bdr2);">
          <td style="padding:10px 14px;font-weight:700;color:var(--tx);">① 주장의 명확성</td>
          <td style="padding:10px 14px;text-align:center;font-family:'IBM Plex Mono',monospace;color:var(--gold);font-weight:700;">3점</td>
          <td style="padding:10px 14px;color:var(--tx2);font-size:12px;">플랫폼 경제와 청년 노동 구조 변화를 명확히 연결, 주장의 핵심 방향 제시</td>
          <td style="padding:10px 14px;color:var(--red);font-size:12px;">논제 이탈 -2점 / 주장 모호 -1점</td>
        </tr>
        <tr style="border-bottom:1px solid var(--bdr2);background:rgba(255,255,255,.015);">
          <td style="padding:10px 14px;font-weight:700;color:var(--tx);">② DB 개념 활용 (차수·카디널리티)</td>
          <td style="padding:10px 14px;text-align:center;font-family:'IBM Plex Mono',monospace;color:var(--gold);font-weight:700;">5점</td>
          <td style="padding:10px 14px;color:var(--tx2);font-size:12px;">2개 이상 개념 정확 활용 + 수치 인용 + 논거 연결</td>
          <td style="padding:10px 14px;color:var(--red);font-size:12px;">개념 1개 -2점 / 개념 없음 -4점 / 수치 없음 -1점</td>
        </tr>
        <tr style="border-bottom:1px solid var(--bdr2);">
          <td style="padding:10px 14px;font-weight:700;color:var(--tx);">③ 데이터 인용·해석 (자료3개↑)</td>
          <td style="padding:10px 14px;text-align:center;font-family:'IBM Plex Mono',monospace;color:var(--gold);font-weight:700;">5점</td>
          <td style="padding:10px 14px;color:var(--tx2);font-size:12px;">3개↑ 자료 번호+수치 인용, 변화율·맥락 해석, 자료 간 연결</td>
          <td style="padding:10px 14px;color:var(--red);font-size:12px;">자료 2개 -1점 / 1개 -3점 / 수치 없음 -1점</td>
        </tr>
        <tr style="border-bottom:1px solid var(--bdr2);background:rgba(255,255,255,.015);">
          <td style="padding:10px 14px;font-weight:700;color:var(--tx);">④ 반론 인식 + 재반박</td>
          <td style="padding:10px 14px;text-align:center;font-family:'IBM Plex Mono',monospace;color:var(--gold);font-weight:700;">4점</td>
          <td style="padding:10px 14px;color:var(--tx2);font-size:12px;">불안정 고용·수입 변동 인정 + 데이터로 재반박 + 논리 일관성</td>
          <td style="padding:10px 14px;color:var(--red);font-size:12px;">재반박 미흡 -2점 / 반론 없음 -3점</td>
        </tr>
        <tr>
          <td style="padding:10px 14px;font-weight:700;color:var(--tx);">⑤ 결론 + 구체적 제언</td>
          <td style="padding:10px 14px;text-align:center;font-family:'IBM Plex Mono',monospace;color:var(--gold);font-weight:700;">3점</td>
          <td style="padding:10px 14px;color:var(--tx2);font-size:12px;">논증 종합 + 정책·교육·제도 제언 구체적 1개↑</td>
          <td style="padding:10px 14px;color:var(--red);font-size:12px;">제언 없음 -1점 / 결론 미흡 -1점</td>
        </tr>
      </tbody>
      <tfoot><tr style="background:var(--surf2);"><td colspan="2" style="padding:10px 14px;font-size:12px;color:var(--tx3);">※ 배점: 8점(백지·미제출) / 11~20점(1점 단위) · 9점·10점 없음 · 아무 말이나 쓴 경우 11점</td><td colspan="2" style="padding:10px 14px;font-size:12px;color:var(--tx3);">15점 이상: 조건①~④ 기본 충족 시 달성 가능</td></tr></tfoot>
    </table>
  </div>
</div>
<!-- ════════════════ PANEL: 교사 채점 ════════════════ -->
<div id="panel-teacher" class="panel">
  <div id="teacher-login">
    <div class="login-wrap">
      <h2>🔐 교사 인증</h2>
      <p>채점·예시답안·기준표는 교사 전용입니다.</p>
      <div class="pw-row">
        <input class="pw-in" id="pw-in" type="password" placeholder="비밀번호" onkeydown="if(event.key==='Enter')chkPw()">
        <button class="pw-btn" onclick="chkPw()">확인</button>
      </div>
      <div class="pw-err" id="pw-err"></div>
      <div class="note blue" style="margin-top:16px;text-align:left;font-size:12px;">
        비밀번호를 잊으셨으면 담당 교사에게 문의하세요.
      </div>
    </div>
  </div>

  <div id="teacher-dash" style="display:none">
    <!-- View Toggle -->
    <div style="display:flex;gap:8px;margin-bottom:16px;align-items:center;flex-wrap:wrap;">
      <button class="tbtn sec on" id="view-score-btn" onclick="showView('score',this)">📊 점수 요약표</button>
      <button class="tbtn sec" id="view-detail-btn" onclick="showView('detail',this)">📋 답안 상세</button>
      <button class="tbtn sec" id="view-feedback-btn" onclick="showView('feedback',this)">📄 피드백 카드</button>
      <div style="margin-left:auto;display:flex;gap:8px;">
        <button class="tbtn pri" id="grade-all-btn" onclick="gradeAll()">🤖 일괄 AI 채점</button>
        <button class="tbtn sec" onclick="exportCSV()">📊 CSV</button>
        <button class="tbtn sec" onclick="loadDash()">🔄 새로고침</button>
        <button class="tbtn danger" onclick="teacherLogout()">↩ 로그아웃</button>
      </div>
    </div>

    <!-- Stats -->
    <div style="display:flex;gap:8px;margin-bottom:16px;flex-wrap:wrap;">
      <div class="sbox"><div class="snum" id="st-total">0</div><div class="slbl">총 제출</div></div>
      <div class="sbox"><div class="snum" style="color:var(--grn)" id="st-graded">0</div><div class="slbl">채점완료</div></div>
      <div class="sbox"><div class="snum" style="color:var(--org)" id="st-ungraded">0</div><div class="slbl">미채점</div></div>
      <div class="sbox"><div class="snum" id="st-avg" style="color:var(--pur)">—</div><div class="slbl">평균점수</div></div>
      <div class="sbox"><div class="snum" id="st-above15" style="color:var(--teal)">—</div><div class="slbl">15점이상(%)</div></div>
    </div>

    <!-- Sort & Filter -->
    <div class="sort-row">
      <span class="sort-lbl">정렬:</span>
      <button class="sort-btn on" onclick="setSort('sid',this)">학번순</button>
      <button class="sort-btn" onclick="setSort('name',this)">이름순</button>
      <button class="sort-btn" onclick="setSort('score',this)">점수순</button>
      <button class="sort-btn" onclick="setSort('time',this)">제출시간순</button>
      <span class="sort-lbl" style="margin-left:10px">필터:</span>
      <input class="filter-input" id="filter-inp" placeholder="학번 또는 이름 검색" oninput="renderAll()">
      <select id="filter-class" onchange="renderAll()" style="background:var(--surf2);border:1px solid var(--bdr);color:var(--tx2);padding:6px 10px;font-size:11px;border-radius:5px;outline:none;font-family:'IBM Plex Mono',monospace;">
        <option value="">전체 반</option>
        <option value="201">1반 (201xx)</option>
        <option value="202">2반 (202xx)</option>
        <option value="203">3반 (203xx)</option>
        <option value="204">4반 (204xx)</option>
        <option value="205">5반 (205xx)</option>
        <option value="206">6반 (206xx)</option>
        <option value="207">7반 (207xx)</option>
        <option value="208">8반 (208xx)</option>
        <option value="209">9반 (209xx)</option>
        <option value="210">10반 (210xx)</option>
        <option value="211">11반 (211xx)</option>
        <option value="212">12반 (212xx)</option>
        <option value="213">13반 (213xx)</option>
      </select>
    </div>

    <!-- Score Summary View -->
    <div id="view-score">
      <div class="score-tbl-wrap">
        <div style="max-height:600px;overflow-y:auto;">
          <table class="score-tbl">
            <thead><tr>
              <th style="width:90px">학번</th>
              <th style="width:80px">이름</th>
              <th style="width:70px">점수</th>
              <th style="width:60px">주장<br><small style="font-weight:400;color:var(--tx3)">/3</small></th>
              <th style="width:60px">DB개념<br><small style="font-weight:400;color:var(--tx3)">/5</small></th>
              <th style="width:60px">데이터<br><small style="font-weight:400;color:var(--tx3)">/5</small></th>
              <th style="width:60px">반론<br><small style="font-weight:400;color:var(--tx3)">/4</small></th>
              <th style="width:60px">결론<br><small style="font-weight:400;color:var(--tx3)">/3</small></th>
              <th>제출시각</th>
              <th style="width:60px">작업</th>
            </tr></thead>
            <tbody id="score-tbl-body"></tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- Detail View -->
    <div id="view-detail" style="display:none">
      <div id="detail-list" class="sub-list"></div>
    </div>

    <!-- Feedback Card View -->
    <div id="view-feedback" style="display:none">
      <div class="note blue"><strong>피드백 카드:</strong> 각 학생의 감점 근거를 확인하고 학생에게 제공할 수 있습니다. "인쇄" 버튼으로 개별 출력 가능.</div>
      <div id="feedback-list"></div>
    </div>
  </div>
</div>

</main>

<!-- Feedback Modal -->
<div class="modal-bg" id="feedback-modal">
  <div class="modal">
    <div class="modal-hdr">
      <h3 id="modal-title">피드백 카드</h3>
      <button class="modal-close" onclick="closeModal()">✕</button>
    </div>
    <div id="modal-body"></div>
    <div style="margin-top:16px;display:flex;gap:8px;">
      <button class="tbtn pri" onclick="window.print()">🖨️ 인쇄</button>
      <button class="tbtn sec" onclick="closeModal()">닫기</button>
    </div>
  </div>
</div>

<!-- Teacher corner -->
<button id="t-corner" onclick="switchTab('teacher',document.getElementById('tab-teacher'))" style="position:fixed;bottom:18px;right:18px;z-index:400;background:var(--surf2);border:1px solid var(--bdr);color:var(--tx3);font-size:11px;font-family:'IBM Plex Mono',monospace;padding:7px 13px;border-radius:4px;cursor:pointer;transition:all .2s;">🔐 교사</button>
<script>
// ══ CONFIG ══
const TEACHER_PW = '11154';
// ▼ Apps Script 배포 후 아래 URL을 교체하세요
const APPS_URL = 'https://script.google.com/macros/s/AKfycbx45QQRWdyGUcqVu1rkXGaP1seiGvhCGyCwlMp6gHj_5zN3pLSDVJzxhLeNAQShl8gsGQ/exec';

const RUBRIC = [
  {id:'r1', name:'주장의 명확성', max:3},
  {id:'r2', name:'DB 개념 활용 (차수·카디널리티)', max:5},
  {id:'r3', name:'데이터 인용·해석', max:5},
  {id:'r4', name:'반론 인식·재반박', max:4},
  {id:'r5', name:'결론·사회적 제언', max:3},
];
const FIELDS_META = ['주장 (Thesis)','근거1 - DB 구조','근거2 - 통계·차트','반론 인식 및 재반박','결론 및 사회적 제언'];
let currentSort = 'sid';
let currentView = 'score';
let isTeacher = false;

// ══ VALID SCORES: 8 / 11~20 (배점표 준수) ══
// 배점: 8점(백지·미제출) / 11~20점(1점 단위)
// 9점·10점은 존재하지 않음
function snapScore(raw, totalChars) {
  // 백지 또는 너무 짧은 경우
  if (!totalChars || totalChars < 50) return 8;
  // raw 합산 0~10이면 최소 11 (아무 말이나 쓴 경우 포함)
  if (raw <= 10) return 11;
  // 11~20 범위로 클램프
  return Math.min(20, Math.max(11, raw));
}

// ══ TABS ══
function switchTab(id, btn) {
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('on'));
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('on'));
  document.getElementById('panel-' + id).classList.add('on');
  if (btn) btn.classList.add('on');
  document.getElementById('t-corner').style.display = (id === 'teacher') ? 'none' : 'block';
  if (id === 'teacher' && isTeacher) loadDash();
}

// ══ CHAR COUNT ══
function cnt(n) {
  const v = document.getElementById('ans'+n).value;
  const el = document.getElementById('fc'+n);
  el.textContent = v.length + '자';
  el.style.color = v.length >= 80 ? 'var(--grn)' : v.length >= 40 ? 'var(--org)' : 'var(--tx3)';
  let tot = 0;
  for (let i = 1; i <= 5; i++) tot += (document.getElementById('ans'+i).value||'').length;
  const tc = document.getElementById('total-c');
  tc.textContent = tot;
  tc.style.color = tot >= 500 ? 'var(--grn)' : tot >= 250 ? 'var(--org)' : 'var(--red)';
}

// ══ SUBMIT ══
async function submitAnswer() {
  const sid = document.getElementById('inp-sid').value.trim();
  const name = document.getElementById('inp-name').value.trim();
  if (!sid) { alert('학번을 입력해주세요.'); return; }
  if (!name) { alert('이름을 입력해주세요.'); return; }
  if (!/^2\d{4}$/.test(sid)) { alert('학번은 2학년 형식(20xxx~213xx)으로 입력해주세요.'); return; }

  // 중복 확인 (서버)
  try {
    const dupCheck = await apiCall({action:'checkDuplicate', sid});
    if (dupCheck.exists) {
      alert(`학번 ${sid}(${dupCheck.name})는 이미 ${dupCheck.submittedAt}에 제출되었습니다.\n재제출이 불가합니다.`);
      return;
    }
  } catch(e) { /* 네트워크 오류 시 제출 진행 (서버에서 최종 중복 차단) */ }

  let tot = 0;
  for (let i = 1; i <= 5; i++) tot += (document.getElementById('ans'+i).value||'').length;
  if (tot < 100) { alert('답안을 더 작성해주세요. (현재: ' + tot + '자)'); return; }
  if (!confirm(`[${sid}] ${name} 학생으로 제출하시겠습니까?\n제출 후 수정이 불가합니다.`)) return;

  const fields = {};
  for (let i = 1; i <= 5; i++) fields['f'+i] = document.getElementById('ans'+i).value;

  const sbtn = document.querySelector('.sbtn');
  sbtn.disabled = true; sbtn.innerHTML = '<span class="spin"></span>제출 중...';

  try {
    const result = await apiCall({
      action:'submit', sid, name, chars:tot,
      f1:fields.f1, f2:fields.f2, f3:fields.f3, f4:fields.f4, f5:fields.f5
    });
    if (!result.ok) {
      alert(result.error || '제출에 실패했습니다. 다시 시도해주세요.');
      sbtn.disabled = false; sbtn.textContent = '📤 최종 제출 (학번당 1회)';
      return;
    }
    sessionStorage.setItem('my_sub_sid', sid);
    sessionStorage.setItem('my_sub_name', name);
    sessionStorage.setItem('my_sub_time', result.submittedAt);
    document.getElementById('answer-form').style.display = 'none';
    document.getElementById('answer-done').style.display = 'block';
    document.getElementById('done-msg').innerHTML =
      `<strong style="color:var(--tx)">[${sid}] ${name}</strong> 학생 답안 저장 완료<br>
       제출 시각: <strong style="color:var(--acc);font-family:'IBM Plex Mono',monospace">${result.submittedAt}</strong> · 총 ${tot}자`;
  } catch(e) {
    alert('제출 오류: ' + e.message + '\n잠시 후 다시 시도해주세요.');
    sbtn.disabled = false; sbtn.textContent = '📤 최종 제출 (학번당 1회)';
  }
}

// ══ API HELPERS ══
async function apiCall(params) {
  for (let attempt = 1; attempt <= 3; attempt++) {
    try {
      const controller = new AbortController();
      const tid = setTimeout(() => controller.abort(), 15000);
      const res = await fetch(APPS_URL, {
        method: 'POST',
        signal: controller.signal,
        headers: { 'Content-Type': 'text/plain' },
        body: JSON.stringify(params)
      });
      clearTimeout(tid);
      const data = await res.json();
      return data;
    } catch(e) {
      if (attempt === 3) throw e;
      await new Promise(r => setTimeout(r, 1500 * attempt));
    }
  }
}

// ══ TEACHER AUTH ══
function chkPw() {
  if (document.getElementById('pw-in').value === TEACHER_PW) {
    isTeacher = true;
    document.getElementById('teacher-login').style.display = 'none';
    document.getElementById('teacher-dash').style.display = 'block';
    document.getElementById('detail-list').innerHTML = '<div class="empty"><div class="eicon">⏳</div><p>답안 불러오는 중...</p></div>';
    document.getElementById('score-tbl-body').innerHTML = '<tr><td colspan="10" style="text-align:center;padding:20px;color:var(--tx3)">불러오는 중...</td></tr>';
    document.getElementById('mode-chip').textContent = '교사 모드';
    document.getElementById('mode-chip').classList.add('locked');
    document.body.classList.add('teacher-mode');
    // Show teacher tabs
    document.querySelectorAll('.teacher-only').forEach(t => t.classList.add('visible'));
    loadDash();
  } else {
    document.getElementById('pw-err').textContent = '비밀번호가 올바르지 않습니다.';
    document.getElementById('pw-in').value = '';
  }
}
function teacherLogout() {
  isTeacher = false;
  document.getElementById('teacher-login').style.display = 'block';
  document.getElementById('teacher-dash').style.display = 'none';
  document.getElementById('pw-in').value = '';
  document.getElementById('pw-err').textContent = '';
  document.getElementById('mode-chip').textContent = '수행평가';
  document.getElementById('mode-chip').classList.remove('locked');
  document.body.classList.remove('teacher-mode');
  document.querySelectorAll('.teacher-only').forEach(t => t.classList.remove('visible'));
  switchTab('data', document.getElementById('tab-data'));
}

// ══ SORT & FILTER ══
let sortDir = 1;
function setSort(key, btn) {
  if (currentSort === key) sortDir *= -1; else sortDir = 1;
  currentSort = key;
  document.querySelectorAll('.sort-btn').forEach(b => b.classList.remove('on'));
  btn.classList.add('on');
  renderAll();
}
function getFiltered() {
  let list = window._subsCache || [];
  const q = (document.getElementById('filter-inp').value||'').toLowerCase();
  const cls = document.getElementById('filter-class').value;
  if (q) list = list.filter(s => s.sid.includes(q) || s.name.toLowerCase().includes(q));
  if (cls) list = list.filter(s => s.sid.startsWith(cls));
  list.sort((a,b) => {
    let av, bv;
    if (currentSort==='sid') { av=a.sid; bv=b.sid; }
    else if (currentSort==='name') { av=a.name; bv=b.name; }
    else if (currentSort==='score') { av=a.grade?.total??-1; bv=b.grade?.total??-1; }
    else { av=a.submittedAt; bv=b.submittedAt; }
    return (av<bv?-1:av>bv?1:0)*sortDir;
  });
  return list;
}

// ══ LOAD DASHBOARD ══
async function loadDash() {
  try {
    const result = await apiCall({action:'getAll'});
    if (!result.ok) { console.error('loadDash error:', result.error); return; }
    const list = result.submissions || [];
  const graded = list.filter(s => s.grade);
  const avg = graded.length > 0 ? (graded.reduce((a,s)=>a+s.grade.total,0)/graded.length).toFixed(1) : null;
  const above15 = graded.length > 0 ? Math.round(graded.filter(s=>s.grade.total>=15).length/graded.length*100) : null;
  document.getElementById('st-total').textContent = list.length;
  document.getElementById('st-graded').textContent = graded.length;
  document.getElementById('st-ungraded').textContent = list.length - graded.length;
  document.getElementById('st-avg').textContent = avg ?? '—';
  document.getElementById('st-above15').textContent = above15 !== null ? above15+'%' : '—';
  const ung = list.filter(s=>!s.grade).length;
  document.getElementById('grade-all-btn').textContent = ung > 0 ? `🤖 일괄 AI 채점 (${ung}명)` : '🤖 일괄 AI 채점';
  document.getElementById('grade-all-btn').disabled = ung === 0;
  // Cache for sync renders
  window._subsCache = list;
  renderAll(list);
  } catch(e) { console.error('loadDash:', e); }
}

function renderAll(list) {
  if (currentView === 'score') renderScoreTable();
  else if (currentView === 'detail') renderDetailList();
  else renderFeedbackList();
}

// ══ VIEW TOGGLE ══
function showView(v, btn) {
  currentView = v;
  ['score','detail','feedback'].forEach(x => document.getElementById('view-'+x).style.display = 'none');
  document.getElementById('view-'+v).style.display = 'block';
  document.querySelectorAll('#teacher-dash .tbtn.sec').forEach(b => b.classList.remove('on'));
  btn.classList.add('on');
  renderAll();
}

// ══ SCORE TABLE ══
function renderScoreTable() {
  const list = getFiltered();
  const tb = document.getElementById('score-tbl-body');
  if (list.length === 0) { tb.innerHTML = '<tr><td colspan="10" style="text-align:center;padding:30px;color:var(--tx3)">제출 답안 없음</td></tr>'; return; }
  tb.innerHTML = list.map((s,i) => {
    const g = s.grade;
    const total = g ? g.total : null;
    const sc = cls => `<span class="score-pill sp-${cls}">${total ?? '—'}</span>`;
    const badge = total === null ? sc('none') : total >= 18 ? sc('a') : total >= 15 ? sc('b') : total >= 11 ? sc('c') : sc('d');
    const scs = g ? RUBRIC.map(r => (g.scores||[]).find(x=>x.id===r.id)?.score ?? '—') : Array(5).fill('—');
    return `<tr>
      <td class="name-col" style="font-family:'IBM Plex Mono',monospace;font-size:12px;">${s.sid}</td>
      <td class="name-col">${s.name}</td>
      <td>${badge}</td>
      ${scs.map(v=>`<td style="font-family:'IBM Plex Mono',monospace;font-size:12px;color:var(--tx2)">${v}</td>`).join('')}
      <td class="time-col">${formatTime(s.submittedAt)}</td>
      <td style="display:flex;gap:4px;">
        <button class="gbtn sec" style="font-size:10px;padding:4px 8px;flex:none;" onclick="${g?'regrade':'gradeOne'}('${s.id}',this)">${g?'재채점':'채점'}</button>
        <button class="gbtn sec" style="font-size:10px;padding:4px 6px;flex:none;color:var(--red);border-color:var(--red);" onclick="deleteSub('${s.id}','${s.sid}','${s.name}')">🗑</button>
      </td>
    </tr>`;
  }).join('');
}

// ══ DETAIL LIST ══
function renderDetailList() {
  const list = getFiltered();
  const container = document.getElementById('detail-list');
  if (list.length === 0) { container.innerHTML = '<div class="empty"><div class="eicon">📭</div><p>제출 없음</p></div>'; return; }
  container.innerHTML = list.map((s,i) => {
    const g = s.grade;
    const total = g ? g.total : null;
    const badgeCls = total === null ? 'none' : total >= 18 ? 'a' : total >= 15 ? 'b' : total >= 11 ? 'c' : 'd';
    const ansHtml = FIELDS_META.map((title,fi) => {
      const txt = s.fields['f'+(fi+1)]||'';
      return `<div class="sans-item ${txt?'has':''}">
        <div class="sans-title">${fi+1}. ${title}</div>
        <div class="sans-text">${txt||'<span style="color:var(--tx3);font-style:italic">미작성</span>'}</div>
      </div>`;
    }).join('');
    const gradeHtml = g ? buildGradeHtml(g,s.id) : `<div class="grade-actions"><button class="gbtn pri" onclick="gradeOne('${s.id}',this)">🤖 AI 채점</button></div>`;
    return `<div class="scard" id="card-${s.id}">
      <div class="scard-hdr" onclick="togCard('${s.id}')">
        <div class="shdr-l">
          <span class="sno">${s.sid}</span>
          <div><div class="sname">${s.name}</div><div class="stime">${formatTime(s.submittedAt)} · ${s.chars}자</div></div>
        </div>
        <div class="shdr-r">
          <span class="sbadge ${badgeCls}">${total !== null ? total+'점' : '미채점'}</span>
          <span style="color:var(--tx3);font-size:13px" id="arr-${s.id}">▼</span>
        </div>
      </div>
      <div class="scard-body" id="body-${s.id}">${ansHtml}<div class="divider"></div><div id="ga-${s.id}">${gradeHtml}</div></div>
    </div>`;
  }).join('');
}
function togCard(id) {
  document.getElementById('body-'+id).classList.toggle('open');
  const a = document.getElementById('arr-'+id);
  if (a) a.textContent = a.textContent === '▼' ? '▲' : '▼';
}

// ══ FEEDBACK LIST ══
function renderFeedbackList() {
  const list = getFiltered().filter(s => s.grade);
  const container = document.getElementById('feedback-list');
  if (list.length === 0) { container.innerHTML = '<div class="empty"><div class="eicon">💬</div><p>채점된 답안이 없습니다.</p></div>'; return; }
  container.innerHTML = list.map(s => buildFeedbackCard(s)).join('');
}
function buildFeedbackCard(s) {
  const g = s.grade;
  const items = RUBRIC.map(r => {
    const sc = (g.scores||[]).find(x=>x.id===r.id);
    const earned = sc?.score ?? 0;
    const isOk = earned >= r.max - 1;
    return `<div class="fc-item ${isOk?'ok':'deduct'}">
      <div class="fc-item-top">
        <span class="fc-item-name">${r.name}</span>
        <span class="fc-item-score">${earned}/${r.max}점</span>
      </div>
      <div class="fc-item-comment">${sc?.comment || (isOk ? '✓ 잘 작성되었습니다.' : '감점 사유 없음')}</div>
    </div>`;
  }).join('');
  return `<div class="feedback-card" id="fc-${s.id}">
    <div class="fc-header">
      <div>
        <div style="font-size:11px;color:var(--tx3);font-family:'IBM Plex Mono',monospace;margin-bottom:2px">${s.sid}</div>
        <h4>${s.name}</h4>
      </div>
      <span class="fc-score">${g.total}점<small style="font-size:13px;color:var(--tx3);font-weight:400;">/20</small></span>
      <button class="tbtn sec" style="font-size:11px;padding:5px 10px;" onclick="openFeedbackModal('${s.id}')">🔍 상세보기</button>
    </div>
    <div class="fc-items">${items}</div>
    ${g.overall_comment ? `<div class="gfeedback" style="margin-top:10px"><strong>종합 코멘트:</strong> ${g.overall_comment}</div>` : ''}
  </div>`;
}

function openFeedbackModal(id) {
  const s = (window._subsCache||[]).find(x=>x.id===id);
  if (!s || !s.grade) return;
  document.getElementById('modal-title').textContent = `[${s.sid}] ${s.name} — 채점 피드백 (${s.grade.total}점/20점)`;
  document.getElementById('modal-body').innerHTML = buildFeedbackCard(s).replace(/id="fc-[^"]+"/,'');
  document.getElementById('feedback-modal').classList.add('open');
}
function closeModal() { document.getElementById('feedback-modal').classList.remove('open'); }

// ══ GRADE HTML ══
function buildGradeHtml(g, id) {
  const items = RUBRIC.map(r => {
    const s = (g.scores||[]).find(x=>x.id===r.id);
    const sc = s?.score ?? 0;
    const pct = Math.round((sc/r.max)*100);
    const col = pct>=90?'var(--grn)':pct>=70?'var(--acc)':pct>=50?'var(--org)':'var(--red)';
    return `<div class="gitem">
      <div class="gi-name">${r.name}</div>
      <div class="gi-sc">${sc}<small>/${r.max}점</small></div>
      <div class="pbar-w"><div class="pbar" style="width:${pct}%;background:${col}"></div></div>
      <div class="gi-deduct ${sc>=r.max-1?'none':''}">${s?.comment||(sc>=r.max-1?'✓ 충족':'감점 사유 확인 필요')}</div>
    </div>`;
  }).join('');
  return `<div class="grade-box">
    <div class="grade-box-title">🤖 AI 채점 결과</div>
    <div class="total-score-row"><span class="tsl">총점</span><span class="tsr">${g.total}<small>/20점</small></span></div>
    <div class="gitems">${items}</div>
    <div class="gfeedback"><strong>💬 종합 코멘트:</strong> ${g.overall_comment||''}</div>
    <div class="grade-actions"><button class="gbtn sec" onclick="regrade('${id}',this)">🔄 재채점</button></div>
  </div>`;
}

// ══ AI GRADE ══
async function callAI(s) {
  const answerText = FIELDS_META.map((t,i)=>`[${t}]\n${s.fields['f'+(i+1)]||'(미작성)'}`).join('\n\n');
  const prompt = `당신은 고등학교 데이터과학 수행평가 채점 전문가입니다.

[논제] 온라인 플랫폼 경제의 성장이 한국 청년 노동시장 구조를 어떻게 변화시키고 있는가

[채점 기준 - 총 20점, 8점 또는 11~20점만 가능]
- r1 주장의 명확성 (3점): 플랫폼 경제와 청년 노동 연결, 명확한 주장 방향
- r2 자료 비교·연결 분석 (5점): 2개 이상 자료를 비교하며 수치 근거로 변화 패턴 해석
- r3 데이터 인용·해석 (5점): 3개↑ 자료 번호+수치 인용, 변화율 해석
- r4 반론 인식·재반박 (4점): 불안정 고용 인정 + 데이터 재반박
- r5 결론·사회적 제언 (3점): 구체적 정책·제도 제언 1개↑

[학생 답안 - ${s.name}(${s.sid})]
${answerText}

반드시 아래 JSON만 반환하세요 (다른 텍스트 없이):
{"scores":[
  {"id":"r1","score":점수,"comment":"잘한점 또는 감점사유 1~2문장"},
  {"id":"r2","score":점수,"comment":"잘한점 또는 감점사유 1~2문장"},
  {"id":"r3","score":점수,"comment":"잘한점 또는 감점사유 1~2문장"},
  {"id":"r4","score":점수,"comment":"잘한점 또는 감점사유 1~2문장"},
  {"id":"r5","score":점수,"comment":"잘한점 또는 감점사유 1~2문장"}
],"raw_total":합계점수,"overall_comment":"종합 피드백 2~3문장 (교사 관찰 시점)"}

점수 배정 규칙:
- 각 항목 0~만점 사이 정수로 채점. raw_total은 합계(0~20).
- 최종 점수는 8점(백지/미제출) 또는 11~20점(1점 단위)으로만 부여됨. 9점·10점 없음.
- 논증 구조 없이 아무 말이나 쓴 경우: 각 항목 최소점수 부여 → raw_total 10 이하 → 최종 11점으로 처리됨.`;

  for (let attempt = 1; attempt <= 3; attempt++) {
    try {
      const controller = new AbortController();
      const tid = setTimeout(() => controller.abort(), 30000);
      const res = await fetch('https://api.anthropic.com/v1/messages', {
        method:'POST', headers:{'Content-Type':'application/json'},
        signal: controller.signal,
        body: JSON.stringify({model:'claude-sonnet-4-20250514',max_tokens:1200,messages:[{role:'user',content:prompt}]})
      });
      clearTimeout(tid);
      if (!res.ok) throw new Error('HTTP ' + res.status);
      const data = await res.json();
      if (!data.content || !data.content.length) throw new Error('빈 응답');
      const text = data.content.map(b=>b.text||'').join('');
      const parsed = JSON.parse(text.replace(/```json|```/g,'').trim());
      if (!parsed.scores) throw new Error('JSON 형식 오류');
      parsed.total = snapScore(parsed.raw_total, s.chars);
      return parsed;
    } catch(e) {
      console.warn('채점 시도 ' + attempt + '/3 실패 (' + s.name + '):', e.message);
      if (attempt === 3) {
        return {
          scores:[
            {id:'r1',score:0,comment:'⚠ 채점 오류 — 수동 채점 필요'},
            {id:'r2',score:0,comment:'⚠ 채점 오류 — 수동 채점 필요'},
            {id:'r3',score:0,comment:'⚠ 채점 오류 — 수동 채점 필요'},
            {id:'r4',score:0,comment:'⚠ 채점 오류 — 수동 채점 필요'},
            {id:'r5',score:0,comment:'⚠ 채점 오류 — 수동 채점 필요'}
          ],
          raw_total:0,
          total: snapScore(0, s.chars),
          overall_comment:'⚠ AI 채점 오류 (' + e.message + '). 재채점 버튼을 눌러주세요.',
          _error:true
        };
      }
      await new Promise(r=>setTimeout(r, 2000*attempt));
    }
  }
}

async function gradeOne(id, btn) {
  const list = window._subsCache || [];
  const s = list.find(x=>x.id===id);
  if (!s) return;
  if (btn) { btn.disabled=true; btn.innerHTML='<span class="spin lt"></span>채점중'; }
  try {
    const result = await callAI(s);
    await apiCall({action:'updateGrade', id:id, grade:result});
    if (window._subsCache) {
      const ci = window._subsCache.findIndex(x=>x.id===id);
      if (ci>=0) window._subsCache[ci].grade = result;
    }
    // Update UI
    const ga = document.getElementById('ga-'+id);
    if (ga) ga.innerHTML = buildGradeHtml(result, id);
    const badge = document.querySelector(`#card-${id} .sbadge`);
    if (badge) { badge.textContent=result.total+'점'; badge.className='sbadge '+scCls(result.total); }
    loadDash();
  } catch(e) {
    console.error('채점 오류:', e);
  }
  if (btn) { btn.disabled=false; btn.textContent='재채점'; }
}

async function regrade(id, btn) {
  if (!confirm('재채점 하시겠습니까?')) return;
  if (window._subsCache) {
    const idx = window._subsCache.findIndex(x=>x.id===id);
    if (idx>=0) window._subsCache[idx].grade = null;
  }
  await apiCall({action:'updateGrade', id:id, grade:null});
  const ga = document.getElementById('ga-'+id);
  if (ga) ga.innerHTML = `<div class="grade-actions"><button class="gbtn pri" onclick="gradeOne('${id}',this)">🤖 AI 채점</button></div>`;
  const badge = document.querySelector(`#card-${id} .sbadge`);
  if (badge) { badge.textContent='미채점'; badge.className='sbadge none'; }
  loadDash();
}

async function gradeAll() {
  const list = window._subsCache || [];
  const ung = list.filter(s=>!s.grade);
  if (!ung.length) { alert('모두 채점되었습니다.'); return; }
  if (!confirm(`${ung.length}명 일괄 채점합니다.`)) return;
  const btn = document.getElementById('grade-all-btn');
  btn.disabled = true;
  for (let i = 0; i < ung.length; i++) {
    btn.innerHTML = `<span class="spin lt"></span>채점 중 (${i+1}/${ung.length})`;
    const s = ung[i];
    try {
      const result = await callAI(s);
      await apiCall({action:'updateGrade', id:s.id, grade:result});
      if (window._subsCache) {
        const idx = window._subsCache.findIndex(x=>x.id===s.id);
        if (idx>=0) window._subsCache[idx].grade = result;
      }
    } catch(e) { console.error(s.name, e); }
  }
  btn.disabled = false;
  loadDash();
  alert('일괄 채점 완료!');
}

// ══ DELETE SUBMISSION ══
async function deleteSub(id, sid, name) {
  if (!confirm(`[${sid}] ${name} 학생의 답안을 삭제하시겠습니까?\n이 작업은 되돌릴 수 없습니다.`)) return;
  await apiCall({action:'delete', id});
  if (window._subsCache) window._subsCache = window._subsCache.filter(s => s.id !== id);
  loadDash();
}

// ══ CSV EXPORT ══
function exportCSV() {
  const list = window._subsCache || [];
  if (!list.length) { alert('제출 없음'); return; }
  let csv = '학번,이름,제출시각,총글자수,총점,주장(3),DB개념(5),데이터(5),반론(4),결론(3),종합코멘트\n';
  list.forEach(s => {
    const g = s.grade;
    const scs = g ? RUBRIC.map(r=>(g.scores||[]).find(x=>x.id===r.id)?.score??'') : Array(5).fill('');
    csv += `"${s.sid}","${s.name}","${formatTime(s.submittedAt)}",${s.chars},${g?g.total:''},${scs.join(',')},"${(g?.overall_comment||'').replace(/"/g,'""')}"\n`;
  });
  const a = document.createElement('a');
  a.href = URL.createObjectURL(new Blob(['\uFEFF'+csv],{type:'text/csv;charset=utf-8;'}));
  a.download = '데이터과학_수행평가_결과.csv'; a.click();
}

async function clearAll() {
  if (!confirm('⚠ 모든 제출 데이터를 삭제합니다.\nGoogle Sheets 시트를 직접 비우거나 각 답안을 개별 삭제해주세요.')) return;
  // 개별 삭제
  const list = window._subsCache || [];
  for (const s of list) {
    await apiCall({action:'delete', id:s.id});
  }
  window._subsCache = [];
  loadDash();
}

// ══ HELPERS ══
function scCls(s) { return s>=18?'a':s>=15?'b':s>=11?'c':'d'; }
function formatTime(ts) {
  if (!ts) return '—';
  const d = new Date(ts);
  return `${d.getMonth()+1}/${d.getDate()} ${String(d.getHours()).padStart(2,'0')}:${String(d.getMinutes()).padStart(2,'0')}`;
}

// ══ EXAMPLE TOGGLE ══
function toggleEx(bodyId, btnId) {
  const body = document.getElementById(bodyId);
  const btn = document.getElementById(btnId);
  if (!body) return;
  const isOpen = body.style.display === 'block';
  body.style.display = isOpen ? 'none' : 'block';
  if (btn) btn.textContent = isOpen ? '▼ 보기' : '▲ 닫기';
}

// ══ ALREADY SUBMITTED CHECK ══
window.addEventListener('load', () => {
  const submittedSid = sessionStorage.getItem('my_sub_sid');
  if (submittedSid) {
    const sname = sessionStorage.getItem('my_sub_name') || '';
    const stime = sessionStorage.getItem('my_sub_time') || '';
    document.getElementById('answer-form').style.display='none';
    document.getElementById('answer-done').style.display='block';
    document.getElementById('done-msg').innerHTML=
      `<strong style="color:var(--tx)">[${submittedSid}] ${sname}</strong> 학생 답안 저장 완료<br>
       제출 시각: <strong style="color:var(--acc);font-family:'IBM Plex Mono',monospace">${stime}</strong>`;
  }
  setTimeout(initCharts, 80);
});

// ══ CHARTS (Pure Canvas) ══
function drawLineBar(cid, labels, datasets, opts={}) {
  const canvas = document.getElementById(cid); if (!canvas) return;
  const W = canvas.width = canvas.offsetWidth||440, H = canvas.height = canvas.offsetHeight||200;
  const p = {t:22,r:opts.dualY?52:18,b:36,l:50};
  const pw=W-p.l-p.r, ph=H-p.t-p.b;
  const ctx = canvas.getContext('2d'); ctx.clearRect(0,0,W,H);
  const barDs=datasets.filter(d=>d.type!=='line'), lineDs=datasets.filter(d=>d.type==='line');
  const allBar=barDs.flatMap(d=>d.data), allLine=lineDs.flatMap(d=>d.data);
  const maxY1=Math.max(...allBar)*1.18||1, maxY2=allLine.length?Math.max(...allLine)*1.18||1:1;
  const xC=i=>p.l+(i+.5)*(pw/labels.length);
  const yB=v=>p.t+ph-(v/maxY1)*ph, yL=v=>p.t+ph-(v/maxY2)*ph;
  // grid
  for(let g=0;g<=4;g++){
    const y=p.t+(g/4)*ph;
    ctx.strokeStyle='#1e2d45';ctx.lineWidth=1;ctx.beginPath();ctx.moveTo(p.l,y);ctx.lineTo(p.l+pw,y);ctx.stroke();
    ctx.fillStyle='#566080';ctx.font='10px IBM Plex Mono,monospace';ctx.textAlign='right';
    ctx.fillText(Math.round(maxY1-(g/4)*maxY1), p.l-5, y+3);
  }
  if(lineDs.length&&opts.dualY){
    for(let g=0;g<=4;g++){
      const y=p.t+(g/4)*ph, v=Math.round(maxY2-(g/4)*maxY2);
      ctx.fillStyle='#566080';ctx.font='10px IBM Plex Mono,monospace';ctx.textAlign='left';
      ctx.fillText(v+'%',p.l+pw+5,y+3);
    }
  }
  // bars
  const bw=(pw/labels.length)*0.6;
  barDs.forEach(ds=>{
    ds.data.forEach((v,i)=>{
      const bh=(v/maxY1)*ph;
      ctx.fillStyle=ds.color||'rgba(79,158,255,.7)';
      ctx.beginPath();ctx.roundRect(xC(i)-bw/2,p.t+ph-bh,bw,bh,[3,3,0,0]);ctx.fill();
    });
  });
  // lines
  lineDs.forEach(ds=>{
    ctx.beginPath();ctx.strokeStyle=ds.color;ctx.lineWidth=2;
    ds.data.forEach((v,i)=>i===0?ctx.moveTo(xC(i),yL(v)):ctx.lineTo(xC(i),yL(v)));
    ctx.stroke();
    ds.data.forEach((v,i)=>{ctx.beginPath();ctx.arc(xC(i),yL(v),4,0,Math.PI*2);ctx.fillStyle=ds.color;ctx.fill();ctx.strokeStyle='#0b0f18';ctx.lineWidth=1.5;ctx.stroke();});
  });
  // x labels
  ctx.fillStyle='#566080';ctx.font='10px Noto Sans KR,sans-serif';ctx.textAlign='center';
  labels.forEach((l,i)=>ctx.fillText(l,xC(i),H-8));
  // legend
  let lx=p.l;
  datasets.forEach(ds=>{ctx.fillStyle=ds.color;ctx.fillRect(lx,7,11,8);ctx.fillStyle='#8899b8';ctx.font='10px IBM Plex Mono,monospace';ctx.textAlign='left';ctx.fillText(ds.label,lx+14,15);lx+=ctx.measureText(ds.label).width+28;});
}
function drawHorizBar(cid, labels, data, colors) {
  const canvas=document.getElementById(cid);if(!canvas)return;
  const W=canvas.width=canvas.offsetWidth||440,H=canvas.height=canvas.offsetHeight||200;
  const p={t:14,r:40,b:14,l:90};
  const pw=W-p.l-p.r,ph=H-p.t-p.b;
  const ctx=canvas.getContext('2d');ctx.clearRect(0,0,W,H);
  const maxV=Math.max(...data)*1.1||1;
  const bh=ph/labels.length*0.58,gap=ph/labels.length;
  labels.forEach((lbl,i)=>{
    const y=p.t+i*gap+gap/2, w=(data[i]/maxV)*pw;
    ctx.fillStyle=colors[i]||'var(--acc)';
    ctx.beginPath();ctx.roundRect(p.l,y-bh/2,Math.max(w,3),bh,[0,3,3,0]);ctx.fill();
    ctx.fillStyle='#8899b8';ctx.font='11px Noto Sans KR,sans-serif';ctx.textAlign='right';ctx.fillText(lbl,p.l-5,y+4);
    ctx.fillStyle='#e2e8f4';ctx.font='10px IBM Plex Mono,monospace';ctx.textAlign='left';ctx.fillText(data[i]+'만원',p.l+w+5,y+4);
  });
}
function drawStacked(cid, labels, datasets) {
  const canvas=document.getElementById(cid);if(!canvas)return;
  const W=canvas.width=canvas.offsetWidth||460,H=canvas.height=canvas.offsetHeight||210;
  const p={t:22,r:20,b:36,l:42};
  const pw=W-p.l-p.r,ph=H-p.t-p.b;
  const ctx=canvas.getContext('2d');ctx.clearRect(0,0,W,H);
  // grid
  for(let g=0;g<=5;g++){const y=p.t+(g/5)*ph;ctx.strokeStyle='#1e2d45';ctx.lineWidth=1;ctx.beginPath();ctx.moveTo(p.l,y);ctx.lineTo(p.l+pw,y);ctx.stroke();ctx.fillStyle='#566080';ctx.font='9px IBM Plex Mono,monospace';ctx.textAlign='right';ctx.fillText(100-(g/5)*100+'%',p.l-4,y+3);}
  const bw=(pw/labels.length)*0.6;
  labels.forEach((lbl,li)=>{
    let base=0;
    datasets.forEach(ds=>{
      const bh=(ds.data[li]/100)*ph;
      ctx.fillStyle=ds.color;
      ctx.fillRect(p.l+(li+.5)*(pw/labels.length)-bw/2,p.t+ph-((base+ds.data[li])/100)*ph,bw,bh);
      base+=ds.data[li];
    });
    ctx.fillStyle='#566080';ctx.font='10px Noto Sans KR,sans-serif';ctx.textAlign='center';ctx.fillText(lbl,p.l+(li+.5)*(pw/labels.length),H-8);
  });
  // legend
  let lx=p.l;
  datasets.forEach(ds=>{ctx.fillStyle=ds.color;ctx.fillRect(lx,7,11,8);ctx.fillStyle='#8899b8';ctx.font='9px IBM Plex Mono,monospace';ctx.textAlign='left';ctx.fillText(ds.label,lx+13,15);lx+=ctx.measureText(ds.label).width+24;});
}

function initCharts() {
  // c2: bar + line (신규워커 + 20대비율)
  drawLineBar('c2',['2016','2018','2020','2022','2024'],[
    {label:'신규워커(명)',data:[1204,3871,8940,7213,5187],color:'rgba(79,158,255,.7)'},
    {label:'주업비율(%)',data:[18.4,24.1,31.7,38.9,47.2],type:'line',color:'#f0883e'},
    {label:'20대비율(%)',data:[31.2,38.6,44.8,51.3,57.4],type:'line',color:'#34c06a'},
  ],{dualY:true});
  // c3: horiz bar (중위수입)
  drawHorizBar('c3',
    ['전문직','IT·개발','디자인','배달·운송','번역·글쓰기','가사·청소'],
    [342,287,198,163,134,121],
    ['rgba(240,176,41,.8)','rgba(79,158,255,.8)','rgba(167,139,250,.8)','rgba(52,192,106,.7)','rgba(245,136,58,.7)','rgba(86,96,128,.7)']
  );
  // c4: stacked bar (고용형태 변화)
  drawStacked('c4',['2015','2024'],[
    {label:'정규직',data:[48.3,35.1],color:'rgba(79,158,255,.75)'},
    {label:'비정규직',data:[22.4,19.8],color:'rgba(245,136,58,.7)'},
    {label:'플랫폼(주업)',data:[1.2,12.7],color:'rgba(52,192,106,.8)'},
    {label:'플랫폼(부업)',data:[3.1,18.4],color:'rgba(34,211,174,.7)'},
    {label:'자영업',data:[11.7,8.3],color:'rgba(167,139,250,.7)'},
    {label:'기타',data:[13.3,5.7],color:'rgba(86,96,128,.6)'},
  ]);
}
window.addEventListener('resize',()=>{setTimeout(initCharts,80);});
</script>
</body>
</html>
