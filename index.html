import { useState, useEffect, useRef } from "react";

// ─── DESIGN TOKENS ───────────────────────────────────────────────────────────
const S = `
@import url('https://fonts.googleapis.com/css2?family=Sora:wght@300;400;500;600;700&family=DM+Mono:wght@400;500&display=swap');
*{margin:0;padding:0;box-sizing:border-box}
:root{
  --bg:#06060a;--bg2:#0d0d14;--bg3:#13131e;--bg4:#181828;
  --border:rgba(255,255,255,0.07);--border2:rgba(255,255,255,0.13);
  --text:#f1f0ff;--muted:rgba(241,240,255,0.45);--dim:rgba(241,240,255,0.2);
  --accent:#7c6fff;--accent2:#4f8bff;--green:#34d399;--red:#f87171;
  --font:'Sora',sans-serif;--mono:'DM Mono',monospace;
}
body{background:var(--bg);font-family:var(--font);color:var(--text);min-height:100vh}
@keyframes fadeUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
@keyframes fadeIn{from{opacity:0}to{opacity:1}}
@keyframes slideDown{from{opacity:0;transform:translateY(-8px)}to{opacity:1;transform:translateY(0)}}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.4}}
@keyframes spin{to{transform:rotate(360deg)}}
@keyframes shimmer{0%{background-position:-200% 0}100%{background-position:200% 0}}
@keyframes gradMove{0%,100%{background-position:0% 50%}50%{background-position:100% 50%}}
`;

// ─── SUBJECTS ────────────────────────────────────────────────────────────────
const SUBJECTS = [
  {id:1,name:"Matemática",icon:"∑",color:"#a78bfa",topics:["Função do 2º grau","Progressão Aritmética","Trigonometria","Probabilidade","Geometria Plana"]},
  {id:2,name:"Física",icon:"⚡",color:"#60a5fa",topics:["Leis de Newton","Cinemática","Termodinâmica","Eletricidade","Óptica"]},
  {id:3,name:"Biologia",icon:"◎",color:"#34d399",topics:["Fotossíntese","Genética","Ecologia","Evolução","Citologia"]},
  {id:4,name:"História",icon:"⊕",color:"#f472b6",topics:["Revolução Industrial","Segunda Guerra","Brasil Colonial","República Velha","Ditadura Militar"]},
  {id:5,name:"Química",icon:"◈",color:"#fbbf24",topics:["Ligações Químicas","Estequiometria","Termoquímica","Eletroquímica","Soluções"]},
  {id:6,name:"Literatura",icon:"❧",color:"#fb923c",topics:["Romantismo","Modernismo","Realismo","Barroco","Pré-modernismo"]},
];

// ─── AI LESSON GENERATOR ─────────────────────────────────────────────────────
async function generateLesson(subject, topic) {
  const prompt = `Você é um professor expert no ENEM. Gere uma aula completa sobre "${topic}" de ${subject} no estilo ENEM.

Retorne APENAS um JSON válido neste formato exato (sem texto extra, sem markdown):
{
  "explicacao": ["linha 1 da explicação (máx 40 palavras)", "linha 2", "linha 3", "linha 4"],
  "formula": ["fórmula ou conceito chave 1", "fórmula 2", "fórmula 3"],
  "video": "texto exato para buscar no YouTube (ex: Função quadrática ENEM Ferreto)",
  "exercicios": [
    {
      "enunciado": "Texto da questão contextualizad no estilo ENEM (2-3 linhas)",
      "opcoes": ["texto da alternativa A", "texto da alternativa B", "texto da alternativa C", "texto da alternativa D", "texto da alternativa E"],
      "correta": 0,
      "explicacao": "Explicação curta da resposta correta (1-2 linhas)"
    },
    {
      "enunciado": "Segunda questão",
      "opcoes": ["A", "B", "C", "D", "E"],
      "correta": 2,
      "explicacao": "Explicação"
    },
    {
      "enunciado": "Terceira questão",
      "opcoes": ["A", "B", "C", "D", "E"],
      "correta": 1,
      "explicacao": "Explicação"
    }
  ],
  "flashcards": [
    {"pergunta": "Pergunta do flashcard 1?", "resposta": "Resposta clara e direta"},
    {"pergunta": "Pergunta 2?", "resposta": "Resposta 2"},
    {"pergunta": "Pergunta 3?", "resposta": "Resposta 3"}
  ]
}`;

  const res = await fetch("https://api.anthropic.com/v1/messages", {
    method: "POST",
    headers: {"Content-Type": "application/json"},
    body: JSON.stringify({
      model: "claude-sonnet-4-20250514",
      max_tokens: 1000,
      messages: [{role: "user", content: prompt}]
    })
  });
  const data = await res.json();
  const text = data.content.map(b => b.text || "").join("");
  const clean = text.replace(/```json|```/g, "").trim();
  return JSON.parse(clean);
}

// ─── UTILITY COMPONENTS ───────────────────────────────────────────────────────
function Spinner({size=14}) {
  return <span style={{width:size,height:size,border:`2px solid rgba(255,255,255,0.2)`,borderTopColor:"#fff",borderRadius:"50%",display:"inline-block",animation:"spin .7s linear infinite",flexShrink:0}} />;
}

function Toast({msg, type, onClose}) {
  useEffect(() => { const t = setTimeout(onClose, 3800); return () => clearTimeout(t); }, []);
  const colors = type==="success"
    ? {bg:"rgba(52,211,153,0.13)",border:"rgba(52,211,153,0.25)",color:"#34d399"}
    : {bg:"rgba(239,68,68,0.12)",border:"rgba(239,68,68,0.22)",color:"#f87171"};
  return (
    <div style={{position:"fixed",bottom:24,left:"50%",transform:"translateX(-50%)",padding:"11px 20px",borderRadius:10,fontSize:13,fontWeight:500,display:"flex",alignItems:"center",gap:10,zIndex:9999,animation:"slideDown .3s cubic-bezier(.22,1,.36,1) both",backdropFilter:"blur(12px)",whiteSpace:"nowrap",background:colors.bg,border:`1px solid ${colors.border}`,color:colors.color,fontFamily:"var(--font)"}}>
      {type==="success" ? "✓" : "✕"} {msg}
    </div>
  );
}

// ─── TOPBAR ──────────────────────────────────────────────────────────────────
function Topbar({page, onLogout, onLogin, onBuy, hasAccess}) {
  return (
    <div style={{display:"flex",alignItems:"center",justifyContent:"space-between",padding:"16px 28px",borderBottom:"1px solid var(--border)",background:"rgba(6,6,10,0.9)",backdropFilter:"blur(12px)",position:"sticky",top:0,zIndex:100}}>
      <div style={{display:"flex",alignItems:"center",gap:9}}>
        <div style={{width:30,height:30,borderRadius:8,background:"linear-gradient(135deg,#7c6fff,#4f8bff)",display:"flex",alignItems:"center",justifyContent:"center",fontSize:13,fontWeight:700}}>S</div>
        <span style={{fontSize:16,fontWeight:700,letterSpacing:"-0.04em"}}>study<span style={{color:"var(--accent)"}}>.</span>io</span>
      </div>
      <div style={{display:"flex",gap:8,alignItems:"center"}}>
        {page==="dashboard" ? (
          <button onClick={onLogout} style={{background:"rgba(239,68,68,0.1)",border:"1px solid rgba(239,68,68,0.2)",color:"#f87171",padding:"7px 16px",borderRadius:9,fontSize:12,fontWeight:600,cursor:"pointer",fontFamily:"var(--font)"}}>Sair</button>
        ) : (
          <>
            {!hasAccess && <button onClick={onBuy} style={{background:"rgba(255,255,255,0.05)",border:"1px solid var(--border2)",color:"var(--text)",padding:"7px 16px",borderRadius:9,fontSize:12,fontWeight:600,cursor:"pointer",fontFamily:"var(--font)"}}>Comprar acesso</button>}
            <button onClick={onLogin} style={{background:"linear-gradient(135deg,#7c6fff,#4f8bff)",border:"none",color:"#fff",padding:"7px 18px",borderRadius:9,fontSize:12,fontWeight:600,cursor:"pointer",fontFamily:"var(--font)",boxShadow:"0 0 0 1px rgba(124,111,255,0.4)"}}>Entrar</button>
          </>
        )}
      </div>
    </div>
  );
}

// ─── MODAL BASE ───────────────────────────────────────────────────────────────
function Modal({children, onClose}) {
  return (
    <div onClick={e => e.target===e.currentTarget && onClose()} style={{position:"fixed",inset:0,background:"rgba(6,6,10,0.85)",display:"flex",alignItems:"center",justifyContent:"center",zIndex:200,backdropFilter:"blur(6px)",animation:"fadeIn .2s both"}}>
      <div style={{background:"var(--bg2)",border:"1px solid var(--border2)",borderRadius:20,padding:28,maxWidth:400,width:"90%",animation:"fadeUp .3s cubic-bezier(.22,1,.36,1) both",position:"relative"}}>
        <button onClick={onClose} style={{position:"absolute",top:14,right:14,width:26,height:26,borderRadius:7,background:"rgba(255,255,255,0.05)",border:"1px solid var(--border)",color:"var(--muted)",cursor:"pointer",fontSize:16,display:"flex",alignItems:"center",justifyContent:"center"}}>×</button>
        {children}
      </div>
    </div>
  );
}

// ─── PURCHASE MODAL ───────────────────────────────────────────────────────────
function PurchaseModal({onClose, onPurchase}) {
  const [loading, setLoading] = useState(false);
  const [done, setDone] = useState(false);

  const handleBuy = () => {
    setLoading(true);
    setTimeout(() => { setLoading(false); setDone(true); setTimeout(() => { onPurchase(); onClose(); }, 1800); }, 1600);
  };

  return (
    <Modal onClose={onClose}>
      {done ? (
        <div style={{textAlign:"center",padding:"16px 0"}}>
          <div style={{width:72,height:72,borderRadius:"50%",background:"radial-gradient(circle,rgba(52,211,153,0.3),rgba(52,211,153,0.05))",display:"flex",alignItems:"center",justifyContent:"center",fontSize:28,margin:"0 auto 16px"}}>✓</div>
          <div style={{fontSize:20,fontWeight:700,letterSpacing:"-0.03em",marginBottom:8}}>Acesso liberado!</div>
          <div style={{fontSize:13,color:"var(--muted)"}}>Sua assinatura foi ativada. Redirecionando...</div>
        </div>
      ) : (
        <>
          <div style={{width:48,height:48,borderRadius:13,background:"rgba(124,111,255,0.12)",display:"flex",alignItems:"center",justifyContent:"center",fontSize:20,marginBottom:18}}>🎓</div>
          <div style={{fontSize:20,fontWeight:700,letterSpacing:"-0.03em",marginBottom:6}}>Plano Completo</div>
          <div style={{fontSize:13,color:"var(--muted)",marginBottom:20,lineHeight:1.6}}>Acesso vitalício à plataforma com aulas geradas por IA em qualquer tema do ENEM.</div>
          <div style={{background:"rgba(124,111,255,0.06)",border:"1px solid rgba(124,111,255,0.2)",borderRadius:14,padding:18,marginBottom:18}}>
            <div style={{display:"flex",alignItems:"center",justifyContent:"space-between",marginBottom:12}}>
              <span style={{fontSize:13,fontWeight:600,color:"#c4bbff"}}>Acesso Total</span>
              <span style={{fontSize:10,fontFamily:"var(--mono)",background:"rgba(124,111,255,0.2)",color:"#a78bfa",padding:"3px 8px",borderRadius:5}}>VITALÍCIO</span>
            </div>
            <div style={{fontSize:30,fontWeight:700,letterSpacing:"-0.04em",marginBottom:12}}>R$ 97<span style={{fontSize:13,fontWeight:400,color:"var(--muted)"}}>/único</span></div>
            {["6 matérias + aulas geradas por IA","Exercícios interativos","Flashcards automáticos","Suporte dedicado"].map(f => (
              <div key={f} style={{display:"flex",alignItems:"center",gap:8,fontSize:12,color:"var(--muted)",marginBottom:7}}>
                <span style={{color:"#34d399"}}>✓</span> {f}
              </div>
            ))}
          </div>
          <button onClick={handleBuy} disabled={loading} style={{width:"100%",padding:"12px",borderRadius:10,border:"none",background:"linear-gradient(135deg,#7c6fff,#4f8bff)",color:"#fff",fontSize:13,fontWeight:600,cursor:"pointer",fontFamily:"var(--font)",display:"flex",alignItems:"center",justifyContent:"center",gap:8,boxShadow:"0 0 0 1px rgba(124,111,255,0.4)"}}>
            {loading ? <><Spinner /> Processando...</> : "Comprar agora — R$ 97"}
          </button>
          <p style={{textAlign:"center",fontSize:11,color:"var(--dim)",marginTop:10}}>Simulação · Nenhum pagamento real</p>
        </>
      )}
    </Modal>
  );
}

// ─── LOGIN MODAL ──────────────────────────────────────────────────────────────
function LoginModal({hasAccess, onClose, onEnter}) {
  return (
    <Modal onClose={onClose}>
      <div style={{width:48,height:48,borderRadius:13,background:"rgba(79,139,255,0.1)",display:"flex",alignItems:"center",justifyContent:"center",fontSize:20,marginBottom:18}}>🔐</div>
      <div style={{fontSize:20,fontWeight:700,letterSpacing:"-0.03em",marginBottom:6}}>Entrar na plataforma</div>
      <div style={{fontSize:13,color:"var(--muted)",marginBottom:20,lineHeight:1.6}}>{hasAccess ? "Bem-vindo de volta! Acesse sua conta." : "Você precisa comprar o acesso para continuar."}</div>
      {["E-mail","Senha"].map(label => (
        <div key={label} style={{marginBottom:14}}>
          <div style={{fontSize:10,fontWeight:600,color:"var(--dim)",letterSpacing:".08em",textTransform:"uppercase",marginBottom:6}}>{label}</div>
          <input defaultValue={label==="E-mail"?"aluno@studyio.com":"••••••••"} type={label==="Senha"?"password":"text"} style={{width:"100%",background:"rgba(255,255,255,0.04)",border:"1px solid var(--border)",borderRadius:9,padding:"10px 14px",fontSize:13,fontFamily:"var(--font)",color:"var(--text)",outline:"none"}} />
        </div>
      ))}
      {hasAccess ? (
        <button onClick={onEnter} style={{width:"100%",padding:"12px",borderRadius:10,border:"none",background:"linear-gradient(135deg,#7c6fff,#4f8bff)",color:"#fff",fontSize:13,fontWeight:600,cursor:"pointer",fontFamily:"var(--font)",marginTop:6}}>
          Acessar plataforma →
        </button>
      ) : (
        <div style={{background:"rgba(239,68,68,0.08)",border:"1px solid rgba(239,68,68,0.18)",borderRadius:10,padding:"12px 16px",display:"flex",gap:10,marginTop:6}}>
          <span style={{fontSize:15,flexShrink:0}}>🔒</span>
          <div>
            <div style={{fontSize:13,fontWeight:600,color:"#f87171",marginBottom:4}}>Sem acesso</div>
            <div style={{fontSize:12,color:"rgba(248,113,113,0.7)"}}>Você precisa comprar o acesso para entrar na plataforma.</div>
          </div>
        </div>
      )}
    </Modal>
  );
}

// ─── HOME PAGE ────────────────────────────────────────────────────────────────
function Home({hasAccess, onOpenBuy, onOpenLogin}) {
  return (
    <div style={{flex:1,display:"flex",alignItems:"center",justifyContent:"center",position:"relative",overflow:"hidden",minHeight:"calc(100vh - 61px)"}}>
      <div style={{position:"absolute",width:600,height:600,borderRadius:"50%",background:"radial-gradient(circle,rgba(124,111,255,0.07) 0%,transparent 70%)",top:"50%",left:"50%",transform:"translate(-50%,-50%)",pointerEvents:"none"}} />
      <div style={{textAlign:"center",maxWidth:520,padding:"60px 24px",animation:"fadeUp .7s cubic-bezier(.22,1,.36,1) both"}}>
        <div style={{display:"inline-flex",alignItems:"center",gap:7,background:"rgba(124,111,255,0.1)",border:"1px solid rgba(124,111,255,0.22)",borderRadius:99,padding:"5px 14px",fontSize:11,color:"#b8b0ff",fontWeight:500,letterSpacing:".04em",marginBottom:24,fontFamily:"var(--mono)"}}>
          <span style={{width:6,height:6,borderRadius:"50%",background:"var(--accent)",animation:"pulse 2s infinite"}} />
          {hasAccess ? "✓ Acesso ativo" : "Aulas geradas por IA · Estilo ENEM"}
        </div>
        <h1 style={{fontSize:"clamp(28px,5vw,44px)",fontWeight:700,letterSpacing:"-0.04em",lineHeight:1.1,marginBottom:16}}>
          Aprenda com <span style={{color:"var(--accent)"}}>IA</span>,<br />passe no ENEM
        </h1>
        <p style={{fontSize:15,color:"var(--muted)",lineHeight:1.7,marginBottom:36,fontWeight:300}}>
          Escolha o tema, a IA gera a aula completa — explicação, exercícios interativos e flashcards — na hora.
        </p>
        <div style={{display:"flex",gap:12,justifyContent:"center",flexWrap:"wrap"}}>
          <button onClick={onOpenLogin} style={{padding:"12px 24px",borderRadius:10,border:"none",background:"linear-gradient(135deg,#7c6fff,#4f8bff)",color:"#fff",fontSize:13,fontWeight:600,cursor:"pointer",fontFamily:"var(--font)",boxShadow:"0 0 0 1px rgba(124,111,255,0.4),0 4px 24px rgba(124,111,255,0.2)"}}>
            {hasAccess ? "Acessar plataforma →" : "Entrar"}
          </button>
          {!hasAccess && (
            <button onClick={onOpenBuy} style={{padding:"12px 24px",borderRadius:10,background:"rgba(255,255,255,0.04)",border:"1px solid var(--border2)",color:"var(--text)",fontSize:13,fontWeight:600,cursor:"pointer",fontFamily:"var(--font)"}}>
              Comprar acesso
            </button>
          )}
        </div>
        {hasAccess && <p style={{marginTop:14,fontSize:12,color:"var(--muted)"}}>✓ Acesso ativo — clique para entrar</p>}
      </div>
    </div>
  );
}

// ─── LESSON VIEW ──────────────────────────────────────────────────────────────
function LessonView({lesson, subject, topic, onBack}) {
  const [revealed, setRevealed] = useState({});
  const [chosen, setChosen] = useState({});
  const [flipped, setFlipped] = useState({});
  const letters = ["A","B","C","D","E"];

  const handleAnswer = (qi, oi) => {
    if (chosen[qi] !== undefined) return;
    setChosen(p => ({...p, [qi]: oi}));
    setRevealed(p => ({...p, [qi]: true}));
  };

  return (
    <div style={{animation:"fadeUp .4s cubic-bezier(.22,1,.36,1) both"}}>
      {/* Header */}
      <div style={{display:"flex",alignItems:"center",gap:12,marginBottom:24}}>
        <button onClick={onBack} style={{background:"rgba(255,255,255,0.05)",border:"1px solid var(--border)",borderRadius:8,color:"var(--muted)",padding:"7px 12px",fontSize:12,cursor:"pointer",fontFamily:"var(--font)"}}>← Voltar</button>
        <div>
          <div style={{fontSize:11,color:"var(--dim)",fontFamily:"var(--mono)",textTransform:"uppercase",letterSpacing:".06em"}}>{subject}</div>
          <div style={{fontSize:18,fontWeight:700,letterSpacing:"-0.03em"}}>{topic}</div>
        </div>
        <div style={{marginLeft:"auto",display:"inline-flex",alignItems:"center",gap:6,background:"rgba(124,111,255,0.1)",border:"1px solid rgba(124,111,255,0.2)",borderRadius:99,padding:"4px 12px",fontSize:11,color:"#b8b0ff",fontFamily:"var(--mono)"}}>
          ✦ Gerado por IA
        </div>
      </div>

      {/* Explicação */}
      <Section badge="Explicação" color="#3C3489" bg="#EEEDFE">
        <div style={{background:"var(--bg3)",borderRadius:12,padding:"16px 18px",border:"1px solid var(--border)"}}>
          {lesson.explicacao.map((linha, i) => (
            <p key={i} style={{color:"var(--muted)",fontSize:13,lineHeight:1.65,marginBottom: i < lesson.explicacao.length-1 ? 8 : 0}}>{linha}</p>
          ))}
          {lesson.formula?.length > 0 && (
            <div style={{display:"flex",flexWrap:"wrap",gap:8,marginTop:14}}>
              {lesson.formula.map((f,i) => (
                <span key={i} style={{background:"var(--bg2)",border:"1px solid var(--border2)",borderRadius:8,padding:"5px 12px",fontSize:12,fontWeight:500,fontFamily:"var(--mono)",color:"var(--text)"}}>{f}</span>
              ))}
            </div>
          )}
        </div>
      </Section>

      {/* Vídeo */}
      <Section badge="Vídeo sugerido" color="#633806" bg="#FAEEDA">
        <div style={{background:"var(--bg3)",borderRadius:12,padding:"14px 16px",border:"1px solid var(--border)",display:"flex",alignItems:"center",gap:14}}>
          <div style={{width:40,height:40,borderRadius:10,background:"rgba(239,68,68,0.15)",display:"flex",alignItems:"center",justifyContent:"center",fontSize:18,flexShrink:0}}>▶</div>
          <div>
            <div style={{fontSize:12,color:"var(--dim)",marginBottom:3}}>Buscar no YouTube:</div>
            <div style={{fontSize:13,fontWeight:600,color:"var(--text)",lineHeight:1.4}}>"{lesson.video}"</div>
          </div>
        </div>
      </Section>

      {/* Exercícios */}
      <Section badge="Exercícios" color="#26215C" bg="#EEEDFE">
        <div style={{display:"flex",flexDirection:"column",gap:12}}>
          {lesson.exercicios.map((ex, qi) => (
            <div key={qi} style={{background:"var(--bg3)",borderRadius:12,padding:"16px",border:"1px solid var(--border)"}}>
              <div style={{fontSize:10,color:"var(--dim)",fontFamily:"var(--mono)",textTransform:"uppercase",letterSpacing:".06em",marginBottom:8}}>Questão {qi+1}</div>
              <div style={{fontSize:13,color:"var(--text)",marginBottom:14,lineHeight:1.6}}>{ex.enunciado}</div>
              <div style={{display:"flex",flexDirection:"column",gap:6}}>
                {ex.opcoes.map((op, oi) => {
                  const isCorrect = oi === ex.correta;
                  const isChosen = chosen[qi] === oi;
                  const show = revealed[qi];
                  let bg = "transparent", border = "var(--border)", color = "var(--muted)";
                  if (show && isCorrect)  { bg = "rgba(52,211,153,0.1)"; border = "rgba(52,211,153,0.4)"; color = "#34d399"; }
                  if (show && isChosen && !isCorrect) { bg = "rgba(239,68,68,0.1)"; border = "rgba(239,68,68,0.3)"; color = "#f87171"; }
                  return (
                    <div key={oi} onClick={() => handleAnswer(qi, oi)} style={{display:"flex",alignItems:"flex-start",gap:8,padding:"8px 10px",borderRadius:8,border:`0.5px solid ${border}`,cursor:show?"default":"pointer",background:bg,color,fontSize:12,transition:"all .2s"}}>
                      <span style={{fontFamily:"var(--mono)",fontWeight:500,flexShrink:0}}>{letters[oi]})</span>
                      {op}
                    </div>
                  );
                })}
              </div>
              {revealed[qi] && (
                <div style={{marginTop:12,background:"rgba(52,211,153,0.08)",border:"0.5px solid rgba(52,211,153,0.2)",borderRadius:8,padding:"10px 12px",fontSize:12,color:"#34d399",lineHeight:1.5}}>
                  ✓ {ex.explicacao}
                </div>
              )}
            </div>
          ))}
        </div>
      </Section>

      {/* Flashcards */}
      <Section badge="Flashcards" color="#085041" bg="#E1F5EE">
        <div style={{display:"grid",gridTemplateColumns:"repeat(auto-fill,minmax(180px,1fr))",gap:10}}>
          {lesson.flashcards.map((fc, i) => (
            <div key={i} onClick={() => setFlipped(p=>({...p,[i]:!p[i]}))} style={{borderRadius:12,border:"0.5px solid var(--border2)",overflow:"hidden",cursor:"pointer",transition:"all .25s"}}>
              <div style={{padding:14,background:"var(--bg3)",minHeight:90}}>
                <div style={{fontSize:12,fontWeight:500,color:"var(--text)",lineHeight:1.45,marginBottom:8}}>{fc.pergunta}</div>
                {!flipped[i] && <div style={{fontSize:10,color:"var(--dim)"}}>toque para ver →</div>}
              </div>
              {flipped[i] && (
                <div style={{padding:14,background:"var(--bg4)",borderTop:"0.5px solid var(--border)",animation:"fadeIn .2s both"}}>
                  <div style={{fontSize:12,color:"var(--muted)",lineHeight:1.55}}>{fc.resposta}</div>
                </div>
              )}
            </div>
          ))}
        </div>
      </Section>
    </div>
  );
}

function Section({badge, color, bg, children}) {
  return (
    <div style={{marginBottom:20}}>
      <div style={{display:"inline-flex",alignItems:"center",marginBottom:10}}>
        <span style={{fontSize:10,fontWeight:500,padding:"3px 10px",borderRadius:99,letterSpacing:".06em",textTransform:"uppercase",background:bg,color}}>{badge}</span>
      </div>
      {children}
    </div>
  );
}

// ─── SUBJECT CARD ─────────────────────────────────────────────────────────────
function SubjectCard({subject, onClick, delay}) {
  return (
    <div onClick={onClick} style={{background:"var(--bg3)",border:"1px solid var(--border)",borderRadius:14,padding:"18px 16px",cursor:"pointer",transition:"all .22s",animation:`fadeUp .5s cubic-bezier(.22,1,.36,1) ${delay}s both`}}
      onMouseEnter={e=>{e.currentTarget.style.borderColor="var(--border2)";e.currentTarget.style.transform="translateY(-2px)"}}
      onMouseLeave={e=>{e.currentTarget.style.borderColor="var(--border)";e.currentTarget.style.transform="translateY(0)"}}>
      <div style={{width:38,height:38,borderRadius:10,background:`${subject.color}18`,color:subject.color,display:"flex",alignItems:"center",justifyContent:"center",fontSize:18,marginBottom:12,fontWeight:600}}>{subject.icon}</div>
      <div style={{fontSize:13,fontWeight:600,marginBottom:4}}>{subject.name}</div>
      <div style={{fontSize:11,color:"var(--muted)"}}>{subject.topics.length} tópicos disponíveis</div>
    </div>
  );
}

// ─── TOPIC SELECTOR ───────────────────────────────────────────────────────────
function TopicSelector({subject, onSelect, onBack}) {
  return (
    <div style={{animation:"fadeUp .4s cubic-bezier(.22,1,.36,1) both"}}>
      <div style={{display:"flex",alignItems:"center",gap:12,marginBottom:24}}>
        <button onClick={onBack} style={{background:"rgba(255,255,255,0.05)",border:"1px solid var(--border)",borderRadius:8,color:"var(--muted)",padding:"7px 12px",fontSize:12,cursor:"pointer",fontFamily:"var(--font)"}}>← Voltar</button>
        <div>
          <div style={{fontSize:11,color:"var(--dim)",fontFamily:"var(--mono)",textTransform:"uppercase",letterSpacing:".06em",marginBottom:2}}>Matéria selecionada</div>
          <div style={{fontSize:18,fontWeight:700,letterSpacing:"-0.03em"}}>{subject.name}</div>
        </div>
      </div>
      <div style={{fontSize:13,color:"var(--muted)",marginBottom:16}}>Escolha um tópico para a IA gerar sua aula completa:</div>
      <div style={{display:"flex",flexDirection:"column",gap:8}}>
        {subject.topics.map((topic, i) => (
          <div key={i} onClick={() => onSelect(topic)} style={{display:"flex",alignItems:"center",justifyContent:"space-between",background:"var(--bg3)",border:"1px solid var(--border)",borderRadius:11,padding:"14px 16px",cursor:"pointer",transition:"all .18s"}}
            onMouseEnter={e=>{e.currentTarget.style.borderColor="var(--border2)";e.currentTarget.style.background="var(--bg4)"}}
            onMouseLeave={e=>{e.currentTarget.style.borderColor="var(--border)";e.currentTarget.style.background="var(--bg3)"}}>
            <div style={{display:"flex",alignItems:"center",gap:10}}>
              <div style={{width:8,height:8,borderRadius:"50%",background:subject.color,flexShrink:0}} />
              <span style={{fontSize:13,fontWeight:500}}>{topic}</span>
            </div>
            <span style={{fontSize:11,color:"var(--dim)"}}>Gerar aula ✦</span>
          </div>
        ))}
      </div>
      <div style={{marginTop:16,padding:"12px 16px",background:"rgba(124,111,255,0.06)",border:"1px solid rgba(124,111,255,0.15)",borderRadius:11}}>
        <div style={{fontSize:12,color:"#b8b0ff",marginBottom:3,fontWeight:500}}>✦ Como funciona</div>
        <div style={{fontSize:12,color:"var(--muted)",lineHeight:1.6}}>A IA analisa o tópico e gera em segundos: explicação simplificada, sugestão de vídeo, 3 exercícios no estilo ENEM com gabarito e 3 flashcards interativos.</div>
      </div>
    </div>
  );
}

// ─── LOADING LESSON ───────────────────────────────────────────────────────────
function LoadingLesson({topic}) {
  const msgs = ["Analisando o conteúdo do ENEM...","Preparando a explicação...","Criando os exercícios...","Montando os flashcards..."];
  const [idx, setIdx] = useState(0);
  useEffect(() => { const t = setInterval(() => setIdx(i => (i+1)%msgs.length), 1200); return () => clearInterval(t); }, []);
  return (
    <div style={{display:"flex",flexDirection:"column",alignItems:"center",justifyContent:"center",minHeight:340,gap:20,animation:"fadeIn .3s both"}}>
      <div style={{width:56,height:56,borderRadius:16,background:"rgba(124,111,255,0.12)",display:"flex",alignItems:"center",justifyContent:"center"}}>
        <Spinner size={22} />
      </div>
      <div style={{textAlign:"center"}}>
        <div style={{fontSize:16,fontWeight:600,letterSpacing:"-0.02em",marginBottom:6}}>Gerando aula: {topic}</div>
        <div style={{fontSize:13,color:"var(--muted)",animation:"fadeIn .3s both",key:idx}}>{msgs[idx]}</div>
      </div>
    </div>
  );
}

// ─── DASHBOARD ────────────────────────────────────────────────────────────────
function Dashboard({onLogout}) {
  const [view, setView] = useState("home"); // home | topics | loading | lesson
  const [selectedSubject, setSelectedSubject] = useState(null);
  const [selectedTopic, setSelectedTopic] = useState(null);
  const [lesson, setLesson] = useState(null);
  const [error, setError] = useState(null);

  const handleSubjectClick = (subject) => { setSelectedSubject(subject); setView("topics"); };

  const handleTopicSelect = async (topic) => {
    setSelectedTopic(topic);
    setView("loading");
    setError(null);
    try {
      const data = await generateLesson(selectedSubject.name, topic);
      setLesson(data);
      setView("lesson");
    } catch(e) {
      setError("Erro ao gerar aula. Verifique sua conexão e tente novamente.");
      setView("topics");
    }
  };

  const navItems = [
    {id:"subjects",label:"Matérias",icon:"◈"},
    {id:"progress",label:"Progresso",icon:"↗"},
    {id:"saved",label:"Salvos",icon:"◎"},
  ];

  return (
    <div style={{display:"flex",flex:1,minHeight:"calc(100vh - 61px)"}}>
      {/* Sidebar */}
      <div style={{width:210,borderRight:"1px solid var(--border)",padding:"20px 14px",display:"flex",flexDirection:"column",gap:4,background:"var(--bg)",flexShrink:0}}>
        <div style={{fontSize:10,fontWeight:600,letterSpacing:".1em",color:"var(--dim)",textTransform:"uppercase",padding:"0 10px",marginBottom:6}}>Menu</div>
        <div style={{display:"flex",alignItems:"center",gap:10,padding:"9px 10px",borderRadius:8,fontSize:13,fontWeight:500,background:"rgba(124,111,255,0.12)",color:"#c4bbff",cursor:"pointer"}}>
          <span style={{width:18,textAlign:"center"}}>⊞</span> Início
        </div>
        {navItems.map(n => (
          <div key={n.id} style={{display:"flex",alignItems:"center",gap:10,padding:"9px 10px",borderRadius:8,fontSize:13,fontWeight:500,color:"var(--muted)",cursor:"pointer",transition:"all .18s"}}
            onMouseEnter={e=>e.currentTarget.style.background="rgba(255,255,255,0.04)"}
            onMouseLeave={e=>e.currentTarget.style.background="transparent"}>
            <span style={{width:18,textAlign:"center"}}>{n.icon}</span> {n.label}
          </div>
        ))}
        <div style={{flex:1}} />
        <div onClick={onLogout} style={{display:"flex",alignItems:"center",gap:10,padding:"9px 10px",borderRadius:8,fontSize:13,fontWeight:500,color:"var(--muted)",cursor:"pointer",transition:"all .18s"}}
          onMouseEnter={e=>e.currentTarget.style.background="rgba(239,68,68,0.08)"}
          onMouseLeave={e=>e.currentTarget.style.background="transparent"}>
          <span style={{width:18,textAlign:"center"}}>→</span> Sair
        </div>
      </div>

      {/* Main */}
      <div style={{flex:1,padding:28,overflowY:"auto",background:"var(--bg)"}}>
        {error && <div style={{marginBottom:16,background:"rgba(239,68,68,0.1)",border:"1px solid rgba(239,68,68,0.2)",borderRadius:10,padding:"12px 16px",fontSize:13,color:"#f87171"}}>{error}</div>}

        {view === "home" && (
          <div style={{animation:"fadeUp .5s cubic-bezier(.22,1,.36,1) both"}}>
            <div style={{display:"flex",alignItems:"center",justifyContent:"space-between",marginBottom:24}}>
              <div>
                <div style={{fontSize:22,fontWeight:700,letterSpacing:"-0.03em",marginBottom:4}}>Bem-vindo de volta <span style={{color:"var(--accent)"}}>👋</span></div>
                <div style={{fontSize:13,color:"var(--muted)"}}>Escolha uma matéria e a IA gera sua aula agora</div>
              </div>
              <div style={{width:40,height:40,borderRadius:"50%",background:"linear-gradient(135deg,#7c6fff,#4f8bff)",display:"flex",alignItems:"center",justifyContent:"center",fontSize:14,fontWeight:700}}>A</div>
            </div>

            {/* Stats */}
            <div style={{display:"grid",gridTemplateColumns:"repeat(3,1fr)",gap:12,marginBottom:28}}>
              {[{num:"14h",lbl:"Estudadas essa semana"},{num:"38",lbl:"Exercícios feitos"},{num:"✦ IA",lbl:"Aulas geradas"}].map((s,i) => (
                <div key={i} style={{background:"var(--bg3)",border:"1px solid var(--border)",borderRadius:14,padding:"16px 18px",animation:`fadeUp .5s cubic-bezier(.22,1,.36,1) ${i*0.08}s both`}}>
                  <div style={{fontSize:24,fontWeight:700,letterSpacing:"-0.04em"}}>{s.num}</div>
                  <div style={{fontSize:11,color:"var(--muted)",marginTop:4}}>{s.lbl}</div>
                </div>
              ))}
            </div>

            {/* Subjects */}
            <div style={{display:"flex",alignItems:"center",justifyContent:"space-between",marginBottom:14}}>
              <span style={{fontSize:14,fontWeight:600}}>Matérias</span>
              <span style={{fontSize:11,color:"var(--accent)"}}>6 disponíveis</span>
            </div>
            <div style={{display:"grid",gridTemplateColumns:"repeat(auto-fill,minmax(150px,1fr))",gap:12}}>
              {SUBJECTS.map((s,i) => <SubjectCard key={s.id} subject={s} onClick={() => handleSubjectClick(s)} delay={i*0.07} />)}
            </div>

            <div style={{marginTop:20,padding:"14px 16px",background:"rgba(124,111,255,0.06)",border:"1px solid rgba(124,111,255,0.15)",borderRadius:12,display:"flex",alignItems:"center",gap:12}}>
              <div style={{fontSize:20,flexShrink:0}}>✦</div>
              <div>
                <div style={{fontSize:13,fontWeight:600,color:"#c4bbff",marginBottom:3}}>Aulas geradas por IA</div>
                <div style={{fontSize:12,color:"var(--muted)",lineHeight:1.5}}>Clique em qualquer matéria, escolha o tópico e receba uma aula completa no estilo ENEM em segundos — explicação, exercícios e flashcards.</div>
              </div>
            </div>
          </div>
        )}

        {view === "topics" && selectedSubject && (
          <TopicSelector subject={selectedSubject} onSelect={handleTopicSelect} onBack={() => setView("home")} />
        )}

        {view === "loading" && <LoadingLesson topic={selectedTopic} />}

        {view === "lesson" && lesson && (
          <LessonView lesson={lesson} subject={selectedSubject?.name} topic={selectedTopic}
            onBack={() => setView("topics")} />
        )}
      </div>
    </div>
  );
}

// ─── APP ROOT ─────────────────────────────────────────────────────────────────
export default function App() {
  const [hasAccess, setHasAccess] = useState(false);
  const [page, setPage] = useState("home");
  const [modal, setModal] = useState(null);
  const [toast, setToast] = useState(null);

  const showToast = (msg, type="success") => setToast({msg, type});

  const handlePurchase = () => { setHasAccess(true); showToast("Acesso liberado com sucesso!", "success"); };
  const handleEnter = () => { setModal(null); setPage("dashboard"); };
  const handleLogout = () => { setPage("home"); showToast("Sessão encerrada.", "success"); };

  return (
    <>
      <style>{S}</style>
      <div style={{display:"flex",flexDirection:"column",minHeight:"100vh"}}>
        <Topbar page={page} hasAccess={hasAccess} onLogout={handleLogout} onLogin={() => setModal("login")} onBuy={() => setModal("purchase")} />
        {page === "home" && <Home hasAccess={hasAccess} onOpenBuy={() => setModal("purchase")} onOpenLogin={() => setModal("login")} />}
        {page === "dashboard" && <Dashboard onLogout={handleLogout} />}
        {modal === "purchase" && <PurchaseModal onClose={() => setModal(null)} onPurchase={handlePurchase} />}
        {modal === "login" && <LoginModal hasAccess={hasAccess} onClose={() => setModal(null)} onEnter={handleEnter} />}
        {toast && <Toast msg={toast.msg} type={toast.type} onClose={() => setToast(null)} />}
      </div>
    </>
  );
}
