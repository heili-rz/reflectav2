<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Reflecta Toolkit — Practical, Anonymous Tools</title>
<link rel="stylesheet" href="/src/styles/globals.css" onerror="this.remove()">
<style>
:root{--bg:#f5f8fa;--card:#fff;--accent:#2b9fda;--accent-light:#eaf6ff;--muted:#6b7280;--text:#0f172a;--radius:14px;--shadow-sm:0 4px 12px rgba(15,23,42,0.05);--shadow-md:0 8px 22px rgba(15,23,42,0.08)}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
body{margin:0;background:var(--bg);color:var(--text);font-family:Inter,system-ui,-apple-system,"Segoe UI",Roboto,"Helvetica Neue",Arial;line-height:1.55}
header{background:linear-gradient(90deg,#e8f6ff,transparent);padding:20px 0 16px;border-bottom:1px solid #e3edf7}
.container{max-width:900px;margin:auto;padding:0 18px}
.branding{display:flex;gap:12px;align-items:center}
.branding h1{margin:0;font-size:1.6rem;font-weight:700}
.branding small{color:var(--muted);font-size:.92rem}
.nav-list{list-style:none;padding:0;margin:12px 0 0;display:flex;gap:10px;flex-wrap:wrap}
.nav-list a{display:inline-block;padding:8px 14px;border-radius:12px;text-decoration:none;color:var(--accent);font-weight:600;transition:.18s;border:1px solid transparent}
.nav-list a:hover{background:var(--accent-light);border-color:rgba(43,159,218,0.18)}
.card{background:var(--card);border-radius:var(--radius);padding:20px 22px;margin-bottom:20px;box-shadow:var(--shadow-sm);transition:box-shadow .2s ease,transform .08s ease}
.card:hover{box-shadow:var(--shadow-md)}
button{cursor:pointer;border:0;border-radius:10px;padding:10px 16px;font-weight:600;transition:.16s;font-family:inherit}
button:not(.ghost){background:var(--accent);color:#fff}
button:not(.ghost):hover{opacity:.95}
button.ghost{background:#fff;border:1px solid rgba(43,159,218,.22);color:var(--accent)}
button.ghost:hover{background:var(--accent-light)}
.emoji-btn{font-size:16px;padding:10px 12px;background:#fff;border-radius:12px;border:1px solid #eef6ff;transition:.16s}
.emoji-btn:hover{background:var(--accent-light)}
.emoji-btn.selected{outline:3px solid rgba(43,159,218,.28)}
#breath-circle{width:130px;height:130px;border-radius:50%;display:flex;align-items:center;justify-content:center;background:var(--accent-light);margin:16px auto;font-weight:700;transition:transform 1.2s ease,box-shadow .2s}
input,textarea,select{width:100%;font-family:inherit;padding:10px 12px;border-radius:12px;border:1px solid #dbe7f3;background:#fff;transition:.12s}
input:focus,textarea:focus,select:focus{border-color:var(--accent);outline:3px solid rgba(43,159,218,.14)}
.tool-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:18px}
.prompt{background:#f0fbff;padding:12px;border-radius:12px;border:1px solid #d3ecf8}
.result{margin-top:14px;background:#fff9d6;border:1px solid #f1e6a3;border-radius:12px;padding:12px}
footer{max-width:900px;margin:50px auto 80px;padding:0 18px;color:var(--muted);font-size:.9rem}
.overlay{position:fixed;inset:0;background:rgba(0,0,0,.45);display:none;align-items:center;justify-content:center}
.overlay[open]{display:flex}
.modal{background:#fff;border-radius:14px;padding:24px;max-width:520px;width:calc(100% - 40px);box-shadow:var(--shadow-md)}
.post{background:#fbfdff;border:1px solid #e2eef7;padding:14px;border-radius:12px;margin-bottom:14px}
.post .meta{color:var(--muted);font-size:.85rem;margin-bottom:6px}
.sr-only{position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0,0,0,0);white-space:nowrap;border:0}
@media(max-width:640px){#breath-circle{width:110px;height:110px}}
</style>
</head>
<body>
<header>
<div class="container" role="banner">
<div class="branding"><div><h1>Reflecta Toolkit</h1><div style="color:var(--muted);font-size:.9rem">Practical, anonymous tools to reflect and cope</div></div></div>
<nav aria-label="Main menu"><ul class="nav-list"><li><a href="#about">About</a></li><li><a href="#toolkit">Toolkit</a></li><li><a href="#test">Wellness check</a></li><li><a href="#forum">Open forum</a></li><li><a href="#mood">Mood picker</a></li><li><a href="#resources">Resources</a></li></ul></nav>
</div>
</header>
<main class="container" role="main">
<section id="about" style="margin-top:18px"><div class="card" aria-labelledby="about-title"><h2 id="about-title">What is Reflecta Toolkit?</h2><p class="lead">A local-first collection of short, evidence-informed exercises and anonymous spaces to help reduce distress and build small, repeatable habits. Not a replacement for professional care.</p></div></section>

<section id="toolkit" style="margin-top:12px">
<div class="card" aria-labelledby="toolkit-title"><h2 id="toolkit-title">Toolkit — quick practice tools</h2><p class="lead">Short exercises you can try now. Results stay on your device.</p>
<div class="tool-grid" role="list">
<div class="card"><h3>2:4 Breathing</h3><div id="breath-circle">Breathe</div><div style="text-align:center"><button id="start-breath">Start 1 cycle</button><button id="stop-breath" class="ghost">Stop</button></div><p style="margin-top:8px;color:var(--muted)">Inhale 2s — exhale 4s. One minute can calm the nervous system.</p></div>
<div class="card"><h3>Guided journaling</h3><div id="prompt" class="prompt">Click "New prompt" for a short writing cue.</div><div style="display:flex;gap:8px;margin-top:8px"><button id="new-prompt">New prompt</button><button id="save-journal" class="ghost">Save (local)</button></div><textarea id="journal" rows="4" placeholder="Write a few lines..." style="margin-top:8px;"></textarea><small style="color:var(--muted)">Saved entries are stored locally and anonymous.</small></div>
<div class="card"><h3>Simple thought record</h3><input id="situation" placeholder="Situation"><input id="thought" placeholder="Automatic thought" style="margin-top:8px"><input id="alternative" placeholder="Alternative balanced thought" style="margin-top:8px"><div style="display:flex;gap:8px;margin-top:8px"><button id="save-thought">Save</button><button id="clear-thought" class="ghost">Clear</button></div><div id="thought-list" style="margin-top:8px;color:var(--muted)"></div></div>
<div class="card"><h3>Micro-actions</h3><div id="micro" class="prompt">Try a small action now.</div><div style="display:flex;gap:8px;margin-top:8px"><button id="next-micro">Next</button><button id="done-micro" class="ghost">Mark done</button></div><small style="color:var(--muted);display:block;margin-top:8px">Small, concrete steps that are easy to complete.</small></div>
</div></div>
</section>

<section id="test" style="margin-top:12px">
<div class="card" aria-labelledby="test-title"><h2 id="test-title">Free anonymous wellness check</h2><p class="lead">A short, anonymous self-check to reflect on recent weeks. Non-diagnostic.</p>
<form id="wellness-form" onsubmit="return false;">
<div class="q"><label>1. Felt down or hopeless?</label><select data-q="0" class="qsel"><option value="0">Not at all</option><option value="1">Several days</option><option value="2">More than half the days</option><option value="3">Nearly every day</option></select></div>
<div class="q"><label>2. Little interest or pleasure?</label><select data-q="1" class="qsel"><option value="0">Not at all</option><option value="1">Several days</option><option value="2">More than half the days</option><option value="3">Nearly every day</option></select></div>
<div style="display:flex;gap:8px;align-items:center;margin-top:8px"><button id="test-run" type="button">Run check</button><button id="test-clear" class="ghost" type="button">Clear</button></div>
<div id="test-result" aria-live="polite"></div>
</form></div></section>

<section id="forum" style="margin-top:12px">
<div class="card" aria-labelledby="forum-title"><h2 id="forum-title">Open anonymous forum</h2><p class="lead">Write freely. Posts are anonymous and local to your device.</p>
<form id="post-form" onsubmit="return false;"><textarea id="post-text" rows="4" maxlength="500" placeholder="Share how you're feeling..." style="width:100%;padding:10px;border-radius:8px;border:1px solid #e6eef6"></textarea>
<div style="display:flex;justify-content:space-between;align-items:center;margin-top:8px"><small id="char-count">0/500</small><div><button id="post-btn">Post anonymously</button><button id="clear-btn" class="ghost">Clear</button></div></div></form>
<div id="posts" style="margin-top:12px" aria-live="polite"></div></div></section>

<section id="mood" style="margin-top:12px">
<div class="card" aria-labelledby="mood-title"><h2 id="mood-title">What is your mood today?</h2><p class="lead">Choose an emoji. A motivational quote will appear.</p>
<div class="buttons" role="list" id="mood-picker"><button class="emoji-btn" data-mood="happy">🙂 Happy</button><button class="emoji-btn" data-mood="sad">😢 Sad</button><button class="emoji-btn" data-mood="confuse">😕 Confuse</button><button class="emoji-btn" data-mood="afraid">😨 Afraid</button><button class="emoji-btn" data-mood="mad">😡 Mad</button></div></div></section>

<section id="resources" style="margin-top:12px">
<div class="card" aria-labelledby="resources-title"><h2 id="resources-title">Resources</h2><p class="lead">If in crisis, contact local emergency services or a crisis line. This toolkit is a demo and not crisis care.</p>
<ul><li><a href="#" onclick="openModal('Resources','In production, list trusted hotlines and local services.');return false;">Sample resources (demo)</a></li></ul></div></section>
</main>

<footer><div class="container">Local-first demo. Content stays on this device unless you export it.</div></footer>

<div id="overlay" class="overlay" role="dialog" aria-modal="true" aria-hidden="true">
<div class="modal"><button id="close" aria-label="Close" style="float:right;background:transparent;border:0;font-size:18px;cursor:pointer">✕</button><h3 id="modal-title">Title</h3><p id="modal-body">Message</p><div class="actions" style="text-align:right"><button id="modal-ok">Okay</button></div></div>
</div>

<script>
const overlay=document.getElementById('overlay'),modalTitle=document.getElementById('modal-title'),modalBody=document.getElementById('modal-body');
function openModal(t,m){modalTitle.textContent=t;modalBody.innerHTML=m||'';overlay.setAttribute('open','');overlay.setAttribute('aria-hidden','false')}
function closeModal(){overlay.removeAttribute('open');overlay.setAttribute('aria-hidden','true')}
document.getElementById('close').addEventListener('click',closeModal);
document.getElementById('modal-ok').addEventListener('click',closeModal);
overlay.addEventListener('click',e=>{if(e.target===overlay)closeModal()});
document.addEventListener('keydown',e=>{if(e.key==='Escape')closeModal()});

const moodButtons=document.querySelectorAll('.emoji-btn'),moodTag={happy:'happiness',sad:'hope',confuse:'wisdom',afraid:'courage',mad:'anger'},fallback={happy:["Keep shining — your joy matters. — Reflecta"],sad:["Small steps matter. — Reflecta"],confuse:["Clarity comes with time. — Reflecta"],afraid:["Courage is small steps forward. — Reflecta"],mad:["Feelings pass — tend to them safely. — Reflecta"]};
async function fetchQuoteForMood(m){const tag=moodTag[m]||'inspirational';openModal('Finding a quote...','<span class="spinner" aria-hidden="true"></span> Finding an uplifting quote...');try{const r=await fetch(`https://api.quotable.io/random?tags=${encodeURIComponent(tag)}`);if(!r.ok)throw 0;const d=await r.json();openModal('Here is a quote for you',`${d.content}${d.author?` — ${d.author}`:''}`)}catch(e){const l=fallback[m]||["You are not alone. — Reflecta"];openModal('Here is a quote for you',l[Math.floor(Math.random()*l.length)])}}
moodButtons.forEach(b=>b.addEventListener('click',()=>{document.querySelectorAll('.emoji-btn').forEach(x=>x.classList.remove('selected'));b.classList.add('selected');fetchQuoteForMood(b.getAttribute('data-mood'))}));

const postText=document.getElementById('post-text'),postBtn=document.getElementById('post-btn'),clearBtn=document.getElementById('clear-btn'),postsContainer=document.getElementById('posts'),charCount=document.getElementById('char-count');
function updateCharCount(){if(!postText)return;charCount.textContent=`${postText.value.length}/500`}
postText&&postText.addEventListener('input',updateCharCount);
function loadPosts(){postsContainer.innerHTML='';let s=[];try{s=JSON.parse(localStorage.getItem('forum_posts')||'[]')}catch(e){s=[]}if(!s.length){const e=document.createElement('div');e.className='empty';e.textContent='No posts yet — be the first to share.';postsContainer.appendChild(e);return}s.slice().reverse().forEach(p=>renderPost(p))}
function renderPost(p){const d=document.createElement('div');d.className='post';const m=document.createElement('div');m.className='meta';let t='';try{t=new Date(p.createdAt).toLocaleString()}catch(e){}m.textContent=`Anonymous ● ${t}`;const c=document.createElement('div');c.className='content';c.textContent=p.text;d.appendChild(m);d.appendChild(c);postsContainer.appendChild(d)}
function savePost(t){let a=[];try{a=JSON.parse(localStorage.getItem('forum_posts')||'[]')}catch(e){a=[]}a.push({text:t,createdAt:new Date().toISOString()});try{localStorage.setItem('forum_posts',JSON.stringify(a))}catch(e){}}
if(postBtn)postBtn.addEventListener('click',()=>{const t=postText.value.trim();if(!t){openModal('Post is empty','Please write something before posting.');return}savePost(t);postsContainer.querySelectorAll('.empty').forEach(n=>n.remove());renderPost({text:t,createdAt:new Date().toISOString()});postText.value='';updateCharCount();openModal('Post successful','Your post has been added anonymously and is visible on this device.')})
clearBtn&&clearBtn.addEventListener('click',()=>{postText.value='';updateCharCount()})
loadPosts()

let breathTimer=null,circle=document.getElementById('breath-circle'),startBreath=document.getElementById('start-breath'),stopBreath=document.getElementById('stop-breath');
function animateBreathOnce(){circle.style.transform='scale(1.15)';circle.textContent='Inhale';setTimeout(()=>{circle.style.transform='scale(0.9)';circle.textContent='Exhale';setTimeout(()=>{circle.style.transform='scale(1)';circle.textContent='Done';setTimeout(()=>{circle.textContent='Breathe'},800)},4000)},2000)}
startBreath&&startBreath.addEventListener('click',()=>{animateBreathOnce()});
stopBreath&&stopBreath.addEventListener('click',()=>{circle.style.transform='';circle.textContent='Breathe';if(breathTimer){clearInterval(breathTimer);breathTimer=null}});

const prompts=["Name one thing you can be kind to yourself for today.","Describe a small moment that felt okay recently.","What is one small thing you can do right now to feel a bit better?","Write a short message to your future self in two sentences."],
promptEl=document.getElementById('prompt'),newPrompt=document.getElementById('new-prompt'),
journal=document.getElementById('journal'),saveJournal=document.getElementById('save-journal');
function setRandomPrompt(){if(!promptEl)return;promptEl.textContent=prompts[Math.floor(Math.random()*prompts.length)]}
newPrompt&&newPrompt.addEventListener('click',setRandomPrompt)
saveJournal&&saveJournal.addEventListener('click',()=>{const t=(journal&&journal.value.trim())||'';if(!t){openModal('Empty','Write something before saving.');return}let a=[];try{a=JSON.parse(localStorage.getItem('journals')||'[]')}catch(e){a=[]}a.push({text:t,ts:new Date().toISOString()});try{localStorage.setItem('journals',JSON.stringify(a));if(journal)journal.value='';openModal('Saved','Journal entry saved locally.')}catch(e){openModal('Error','Unable to save locally.')}})

const sit=document.getElementById('situation'),thought=document.getElementById('thought'),alt=document.getElementById('alternative'),
saveThought=document.getElementById('save-thought'),clearThought=document.getElementById('clear-thought'),thoughtList=document.getElementById('thought-list');
function loadThoughts(){let a=[];try{a=JSON.parse(localStorage.getItem('thoughts')||'[]')}catch(e){a=[]}if(!a.length){thoughtList&&(thoughtList.textContent='No saved thought records.');return}thoughtList.innerHTML='';a.slice().reverse().forEach(t=>{const d=document.createElement('div');d.style.padding='8px';d.style.borderRadius='8px';d.style.background='#fff';d.style.marginBottom='8px';d.textContent=`${new Date(t.ts).toLocaleString()} — ${t.situation} → ${t.thought} → ${t.alternative}`;thoughtList.appendChild(d)})}
saveThought&&saveThought.addEventListener('click',()=>{const s=(sit&&sit.value.trim())||'',th=(thought&&thought.value.trim())||'',al=(alt&&alt.value.trim())||'';if(!s||!th||!al){openModal('Missing','Fill all fields before saving.');return}let a=[];try{a=JSON.parse(localStorage.getItem('thoughts')||'[]')}catch(e){a=[]}a.push({situation:s,thought:th,alternative:al,ts:new Date().toISOString()});try{localStorage.setItem('thoughts',JSON.stringify(a));sit.value='';thought.value='';alt.value='';loadThoughts();openModal('Saved','Thought record saved locally.')}catch(e){openModal('Error','Unable to save locally.')}})
clearThought&&clearThought.addEventListener('click',()=>{if(sit)sit.value='';if(thought)thought.value='';if(alt)alt.value=''})
loadThoughts()

const microList=["Stand up and stretch for 30s","Drink a glass of water","Step outside for 1 minute of fresh air","Send a short message to a friend","Name 3 things you can see right now"],
microEl=document.getElementById('micro'),nextMicro=document.getElementById('next-micro'),doneMicro=document.getElementById('done-micro');
function setMicro(){if(!microEl)return;microEl.textContent=microList[Math.floor(Math.random()*microList.length)]}
nextMicro&&nextMicro.addEventListener('click',setMicro)
doneMicro&&doneMicro.addEventListener('click',()=>{openModal('Nice work','Small actions add up.');setMicro()})
setMicro()

const runBtn=document.getElementById('test-run'),clearTestBtn=document.getElementById('test-clear'),resultEl=document.getElementById('test-result');
function computeScore(){return Array.from(document.querySelectorAll('.qsel')).reduce((s,e)=>s+Number(e.value||0),0)}
function interpretScore(s){return s<=1?{level:'Low',msg:'Mild/low responses.'}:s<=3?{level:'Moderate',msg:'Some symptoms — consider support.'}:{level:'Elevated',msg:'Notable distress — consider contacting a professional.'}}
runBtn&&runBtn.addEventListener('click',()=>{const s=computeScore(),i=interpretScore(s);if(resultEl)resultEl.innerHTML=`<div class="result"><strong>Score: ${s}</strong> — ${i.level}<div style="margin-top:8px;color:var(--muted)">${i.msg}</div></div>`;try{localStorage.setItem('last_wellness_check',JSON.stringify({score:s,ts:new Date().toISOString()}))}catch(e){}});
clearTestBtn&&clearTestBtn.addEventListener('click',()=>{document.querySelectorAll('.qsel').forEach(s=>s.selectedIndex=0);if(resultEl)resultEl.innerHTML='';});
</script>
</body>
</html>
