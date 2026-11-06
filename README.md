
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mi Cuadernito | Agenda personal</title>
<style>
:root {
  --paper:#fffdf6;
  --ink:#34352f;
  --muted:#858579;
  --line:#e9e4d7;
  --accent:#73966b;
  --accent2:#e7efdf;
  --pink:#f4e5e2;
  --yellow:#f7efcf;
}
*{box-sizing:border-box}
body{
  margin:0;background:#e9e7df;color:var(--ink);
  font-family:"Trebuchet MS",Arial,sans-serif;padding:24px
}
.book{
  max-width:1100px;margin:auto;background:var(--paper);
  min-height:90vh;border-radius:18px;
  box-shadow:0 12px 45px #3332;overflow:hidden;
  border:1px solid #ded9ca
}
header{
  padding:28px 34px 22px;
  background:linear-gradient(120deg,#f5f1e5,#e9efdf);
  border-bottom:1px solid var(--line)
}
.top{
  display:flex;justify-content:space-between;
  align-items:center;gap:16px;flex-wrap:wrap
}
h1{
  font-family:Georgia,serif;font-weight:normal;
  font-size:34px;margin:0 0 6px
}
.subtitle{color:#77796d;margin:0;font-size:14px}
.date-pill{
  background:#fffdf6;border:1px solid var(--line);
  padding:10px 14px;border-radius:30px;
  color:#66775e;font-size:13px
}
.layout{display:grid;grid-template-columns:260px 1fr;min-height:650px}
aside{
  padding:24px 18px;border-right:1px solid var(--line);
  background:#fbfaf4
}
.month-head{
  display:flex;align-items:center;
  justify-content:space-between;margin-bottom:15px;
  font-weight:bold
}
button{cursor:pointer;font:inherit;border:0}
.arrow{
  background:white;border:1px solid var(--line);
  border-radius:8px;width:30px;height:30px;color:#687b60
}
.week,.calendar{
  display:grid;grid-template-columns:repeat(7,1fr);
  gap:5px;text-align:center
}
.week{font-size:11px;color:var(--muted);margin-bottom:7px}
.day{
  height:31px;border-radius:8px;background:transparent;
  color:#4e5048;font-size:12px;position:relative
}
.day:hover{background:var(--accent2)}
.day.selected{background:var(--accent);color:white;font-weight:bold}
.day.today{outline:1px solid var(--accent)}
.day.marked:after{
  content:"";position:absolute;width:5px;height:5px;
  border-radius:50%;background:#d29b63;
  bottom:2px;left:calc(50% - 2.5px)
}
.day.selected.marked:after{background:white}
.legend{font-size:11px;color:var(--muted);margin:13px 2px 24px}
.nav-title{
  font-size:11px;text-transform:uppercase;
  letter-spacing:1.5px;color:#999687;margin:18px 8px 8px
}
.nav button{
  display:block;width:100%;text-align:left;
  padding:11px 12px;border-radius:9px;
  background:transparent;color:#626359;margin:3px 0;
  font-size:14px
}
.nav button.active,.nav button:hover{
  background:var(--accent2);color:#425c3d
}
main{padding:30px 34px;max-width:800px;width:100%;margin:auto}
.day-title{
  display:flex;justify-content:space-between;
  align-items:flex-start;gap:12px;margin-bottom:22px;
  flex-wrap:wrap
}
h2{font-family:Georgia,serif;font-size:27px;font-weight:normal;margin:0 0 5px}
.small{color:var(--muted);font-size:13px}
.done-label{
  display:flex;align-items:center;gap:8px;
  background:var(--accent2);padding:9px 12px;
  border-radius:20px;font-size:12px;color:#52694c
}
.done-label input{accent-color:var(--accent);width:16px;height:16px}
.section{display:none}
.section.active{display:block}
.panel{
  border:1px solid var(--line);border-radius:12px;
  padding:18px;margin-bottom:15px;background:#fffefa
}
.panel h3{font-family:Georgia,serif;font-weight:normal;font-size:19px;margin:0 0 12px}
.panel p.hint{font-size:12px;color:var(--muted);margin:-5px 0 12px}
textarea,input[type=text]{
  width:100%;border:1px solid #e9e5da;border-radius:8px;
  padding:11px;background:#fffefa;color:var(--ink);
  font:14px Arial,sans-serif;outline:none
}
textarea{min-height:100px;resize:vertical;line-height:1.55}
textarea:focus,input:focus{border-color:#a5b89b}
.task-row{display:flex;align-items:center;gap:9px;margin:10px 0}
.task-row input[type=checkbox]{accent-color:var(--accent);width:16px;height:16px}
.task-row input[type=text]{flex:1}
.add{
  margin-top:10px;padding:8px 12px;border-radius:8px;
  background:var(--accent2);color:#4d6847;font-size:13px
}
.save-note{font-size:11px;color:#999687;text-align:right;margin-top:12px}
.two{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.color-note{background:#fff9e7}
.pink-note{background:#fff7f5}
.progress-top{
  display:flex;justify-content:space-between;
  align-items:center;font-size:13px;color:#52694c;
  margin:14px 0 8px
}
.progress-track{
  height:10px;background:#edf0e8;
  border-radius:20px;overflow:hidden;margin-bottom:18px
}
.progress-track div{
  height:100%;width:0;background:#78996e;
  border-radius:20px;transition:width .2s
}
.weekly{display:grid;grid-template-columns:repeat(7,1fr);gap:8px;text-align:center}
.week-day{font-size:11px;color:var(--muted)}
.week-bar{
  height:68px;background:#f0eee5;border-radius:8px;
  display:flex;align-items:flex-end;overflow:hidden;margin:6px 0
}
.week-fill{
  width:100%;background:#9bb38e;
  border-radius:7px 7px 0 0;min-height:2px
}
.week-count{font-size:10px;color:#747568}
footer{
  text-align:center;padding:16px;color:#aaa697;
  font-size:11px;border-top:1px solid var(--line)
}
@media(max-width:720px){
  body{padding:0}
  .book{border-radius:0;min-height:100vh}
  .layout{grid-template-columns:1fr}
  aside{border-right:0;border-bottom:1px solid var(--line);padding:18px}
  .calendar{max-width:350px}
  .nav{display:flex;overflow-x:auto;gap:4px}
  .nav-title{display:none}
  .nav button{white-space:nowrap;width:auto;padding:9px 11px}
  main{padding:23px 17px}
  .two{grid-template-columns:1fr}
  header{padding:22px 18px}
  h1{font-size:29px}
}
</style>
</head>
<body>
<div class="book">
<header>
  <div class="top">
    <div>
      <h1>Mi cuadernito ✿</h1>
      <p class="subtitle">Un lugar para guardar mis días, ideas y pequeños logros.</p>
    </div>
    <div class="date-pill" id="todayLabel"></div>
  </div>
</header>

<div class="layout">
<aside>
  <div class="month-head">
    <button class="arrow" id="prev">‹</button>
    <span id="monthLabel"></span>
    <button class="arrow" id="next">›</button>
  </div>

  <div class="week">
    <span>L</span><span>M</span><span>X</span>
    <span>J</span><span>V</span><span>S</span><span>D</span>
  </div>
  <div class="calendar" id="calendar"></div>
  <div class="legend">● Puntito = día con notas guardadas</div>

  <div class="nav-title">Mi agenda</div>
  <nav class="nav">
    <button class="active" data-section="resumen">☀ Mi día</button>
    <button data-section="tareas">✓ Pendientes</button>
    <button data-section="hecho">✎ Lo que hice</button>
    <button data-section="notas">♡ Notas e ideas</button>
    <button data-section="habitos">✿ Hábitos</button>
    <button data-section="metas">☆ Metas</button>
  </nav>
</aside>

<main>
  <div class="day-title">
    <div>
      <h2 id="selectedTitle"></h2>
      <div class="small">Cada día cuenta, incluso los más tranquilos.</div>
    </div>
    <label class="done-label">
      <input type="checkbox" id="dayDone">
      Marcar día como completado
    </label>
  </div>

  <section class="section active" id="resumen">
    <div class="two">
      <div class="panel color-note">
        <h3>☀ Lo mejor del día</h3>
        <textarea data-field="best" placeholder="¿Qué fue lo mejor de hoy?"></textarea>
      </div>
      <div class="panel pink-note">
        <h3>♡ ¿Cómo me sentí?</h3>
        <textarea data-field="mood" placeholder="Escribe cómo estuvo tu día..."></textarea>
      </div>
    </div>
    <div class="panel">
      <h3>📌 Resumen rápido</h3>
      <textarea data-field="summary" placeholder="Cuenta brevemente cómo fue tu día..."></textarea>
    </div>
  </section>

  <section class="section" id="tareas">
    <div class="panel">
      <h3>✓ Cosas que tengo que hacer</h3>
      <p class="hint">Agrega pendientes y márcalos cuando los termines.</p>
      <div id="taskList"></div>
      <button class="add" id="addTask">＋ Agregar pendiente</button>
    </div>
  </section>

  <section class="section" id="hecho">
    <div class="panel">
      <h3>✎ Lo que hice hoy</h3>
      <p class="hint">Anota actividades, momentos o cosas que lograste.</p>
      <textarea data-field="did" placeholder="Hoy hice..."></textarea>
    </div>
    <div class="panel">
      <h3>🏆 Mi pequeño logro</h3>
      <textarea data-field="win" placeholder="Algo de lo que me siento orgulloso..."></textarea>
    </div>
  </section>

  <section class="section" id="notas">
    <div class="panel">
      <h3>♡ Notas e ideas</h3>
      <textarea data-field="notes" placeholder="Ideas, recordatorios, pensamientos..."></textarea>
    </div>
    <div class="panel">
      <h3>🎯 Algo que no quiero olvidar</h3>
      <textarea data-field="remember" placeholder="Escribe aquí..."></textarea>
    </div>
  </section>

  <section class="section" id="habitos">
    <div class="panel">
      <h3>✿ Mi progreso de hoy</h3>
      <p class="hint">Marca lo que hiciste. Tu avance se guarda por fecha para que puedas ver tu constancia.</p>
      <div class="progress-top">
        <strong id="progressText">0 de 8 completados</strong>
        <span id="progressPercent">0%</span>
      </div>
      <div class="progress-track"><div id="progressBar"></div></div>
      <div id="habitList"></div>
      <button class="add" id="addHabit">＋ Agregar mi propio hábito</button>
    </div>
    <div class="panel color-note">
      <h3>📈 Mi constancia</h3>
      <p class="hint">Un pequeño resumen de los últimos 7 días, según los hábitos que marcaste.</p>
      <div id="weeklyProgress" class="weekly"></div>
    </div>
  </section>

  <section class="section" id="metas">
    <div class="panel">
      <h3>☆ Mis metas</h3>
      <textarea data-field="goals" placeholder="¿Qué quiero conseguir? ¿Qué paso puedo dar?"></textarea>
    </div>
    <div class="panel">
      <h3>🌙 Para mañana</h3>
      <textarea data-field="tomorrow" placeholder="¿Qué quiero hacer mañana?"></textarea>
    </div>
  </section>

  <div class="save-note">Se guarda automáticamente en este dispositivo ✿</div>
</main>
</div>
<footer>Hecho para tus días · Mi cuadernito personal</footer>
</div>

<script>
const $=s=>document.querySelector(s);
const today=new Date();
let selected=new Date(today.getFullYear(),today.getMonth(),today.getDate());
let view=new Date(today.getFullYear(),today.getMonth(),1);

const key=d=>
`${d.getFullYear()}-${String(d.getMonth()+1).padStart(2,'0')}-${String(d.getDate()).padStart(2,'0')}`;

const storeKey=d=>'miCuadernito:'+key(d);

const defaultHabits=()=>[
 {name:'Limpiar u ordenar la casa',done:false},
 {name:'Ordenar mi habitación',done:false},
 {name:'Hacer ejercicio o moverme',done:false},
 {name:'Estudiar o hacer tareas',done:false},
 {name:'Leer o aprender algo',done:false},
 {name:'Tomar suficiente agua',done:false},
 {name:'Ayudar en casa',done:false},
 {name:'Practicar un deporte o habilidad',done:false}
];

const blank=()=>({
 tasks:[],
 habits:defaultHabits(),
 done:false
});

let data;

function load(){
  try{
    data=JSON.parse(localStorage.getItem(storeKey(selected)))||blank();
  }catch(e){
    data=blank();
  }

  if(!Array.isArray(data.habits)||data.habits.length===0)
    data.habits=defaultHabits();

  document.querySelectorAll('[data-field]').forEach(el=>{
    el.value=data[el.dataset.field]||'';
  });

  $('#dayDone').checked=!!data.done;
  renderLists();
  renderCalendar();
  updateTitle();
}

function save(){
  document.querySelectorAll('[data-field]').forEach(el=>{
    data[el.dataset.field]=el.value;
  });

  data.done=$('#dayDone').checked;

  try{
    localStorage.setItem(storeKey(selected),JSON.stringify(data));
  }catch(e){
    alert('No se pudieron guardar los datos. Revisá el almacenamiento del navegador.');
  }

  renderCalendar();
}

function updateTitle(){
  const opts={
    weekday:'long',
    day:'numeric',
    month:'long',
    year:'numeric'
  };

  $('#selectedTitle').textContent=
    selected.toLocaleDateString('es',opts);

  $('#todayLabel').textContent=
    'Hoy · '+today.toLocaleDateString('es',{
      day:'numeric',
      month:'short',
      year:'numeric'
    });
}

function renderCalendar(){
  const y=view.getFullYear();
  const m=view.getMonth();
  const first=(new Date(y,m,1).getDay()+6)%7;
  const days=new Date(y,m+1,0).getDate();

  $('#monthLabel').textContent=
    view.toLocaleDateString('es',{month:'long',year:'numeric'});

  let out='';

  for(let i=0;i<first;i++) out+='<span></span>';

  for(let d=1;d<=days;d++){
    let date=new Date(y,m,d);
    let k=key(date);
    let saved=localStorage.getItem('miCuadernito:'+k);
    let marked=false;

    try{
      let obj=JSON.parse(saved);
      marked=!!obj&&(
        obj.done||
        Object.values(obj).some(v=>typeof v==='string'&&v.trim())||
        (obj.tasks||[]).some(t=>t.name)||
        (obj.habits||[]).some(h=>h.done)
      );
    }catch(e){}

    out+=`<button class="day
      ${key(selected)===k?'selected':''}
      ${key(today)===k?'today':''}
      ${marked?'marked':''}"
      data-day="${d}">${d}</button>`;
  }

  $('#calendar').innerHTML=out;

  document.querySelectorAll('[data-day]').forEach(b=>{
    b.onclick=()=>{
      selected=new Date(y,m,+b.dataset.day);
      load();
    };
  });
}

function renderLists(){
  $('#taskList').innerHTML='';

  (data.tasks||[]).forEach((t,i)=>{
    let row=document.createElement('div');
    row.className='task-row';

    let cb=document.createElement('input');
    cb.type='checkbox';
    cb.checked=!!t.done;
    cb.onchange=()=>{
      data.tasks[i].done=cb.checked;
      save();
    };

    let inp=document.createElement('input');
    inp.type='text';
    inp.placeholder='Escribe un pendiente...';
    inp.value=t.name||'';
    inp.oninput=()=>{
      data.tasks[i].name=inp.value;
      save();
    };

    let del=document.createElement('button');
    del.className='arrow';
    del.textContent='×';
    del.title='Eliminar';
    del.onclick=()=>{
      data.tasks.splice(i,1);
      save();
      renderLists();
    };

    row.append(cb,inp,del);
    $('#taskList').append(row);
  });

  $('#habitList').innerHTML='';

  (data.habits||[]).forEach((h,i)=>{
    let row=document.createElement('div');
    row.className='task-row';

    let cb=document.createElement('input');
    cb.type='checkbox';
    cb.checked=!!h.done;
    cb.onchange=()=>{
      data.habits[i].done=cb.checked;
      save();
      renderLists();
    };

    let inp=document.createElement('input');
    inp.type='text';
    inp.value=h.name;
    inp.oninput=()=>{
      data.habits[i].name=inp.value;
      save();
    };

    let del=document.createElement('button');
    del.className='arrow';
    del.textContent='×';
    del.title='Quitar hábito';
    del.onclick=()=>{
      data.habits.splice(i,1);
      save();
      renderLists();
    };

    row.append(cb,inp,del);
    $('#habitList').append(row);
  });

  const total=(data.habits||[]).length;
  const done=(data.habits||[]).filter(h=>h.done).length;
  const pct=total?Math.round(done/total*100):0;

  $('#progressText').textContent=`${done} de ${total} completados`;
  $('#progressPercent').textContent=pct+'%';
  $('#progressBar').style.width=pct+'%';

  renderWeekly();
}

function renderWeekly(){
  const el=$('#weeklyProgress');
  if(!el)return;

  el.innerHTML='';

  for(let offset=6;offset>=0;offset--){
    let d=new Date(selected);
    d.setDate(d.getDate()-offset);

    let obj;
    try{
      obj=JSON.parse(localStorage.getItem('miCuadernito:'+key(d)))||null;
    }catch(e){
      obj=null;
    }

    const habits=obj&&Array.isArray(obj.habits)?obj.habits:[];
    const total=habits.length;
    const done=habits.filter(h=>h.done).length;
    const pct=total?Math.round(done/total*100):0;

    const item=document.createElement('div');
    item.className='week-day';

    const bar=document.createElement('div');
    bar.className='week-bar';

    const fill=document.createElement('div');
    fill.className='week-fill';
    fill.style.height=pct+'%';

    bar.append(fill);

    const name=document.createElement('div');
    name.textContent=d.toLocaleDateString('es',{
      weekday:'short'
    }).replace('.','');

    const count=document.createElement('div');
    count.className='week-count';
    count.textContent=total?done+'/'+total:'—';

    item.append(name,bar,count);
    el.append(item);
  }
}

$('#addTask').onclick=()=>{
  data.tasks.push({name:'',done:false});
  save();
  renderLists();

  let inputs=$('#taskList').querySelectorAll('input[type=text]');
  inputs[inputs.length-1].focus();
};

$('#addHabit').onclick=()=>{
  data.habits.push({name:'',done:false});
  save();
  renderLists();

  let inputs=$('#habitList').querySelectorAll('input[type=text]');
  inputs[inputs.length-1].focus();
};

$('#dayDone').onchange=save;

document.querySelectorAll('[data-field]').forEach(el=>{
  el.addEventListener('input',save);
});

$('#prev').onclick=()=>{
  view.setMonth(view.getMonth()-1);
  renderCalendar();
};

$('#next').onclick=()=>{
  view.setMonth(view.getMonth()+1);
  renderCalendar();
};

document.querySelectorAll('.nav button').forEach(b=>{
  b.onclick=()=>{
    document.querySelectorAll('.nav button').forEach(x=>{
      x.classList.toggle('active',x===b);
    });

    document.querySelectorAll('.section').forEach(x=>{
      x.classList.toggle('active',x.id===b.dataset.section);
    });
  };
});

load();
</script>
</body>
