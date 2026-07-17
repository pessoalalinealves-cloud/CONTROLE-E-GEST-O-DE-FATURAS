<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>CGF · Controle e Gestão de Faturas</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@500;600;700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --tinta:#1E2A38;
    --tinta-2:#2C3B4E;
    --papel:#F7F4EE;
    --papel-2:#EFEBE1;
    --ambar:#F2A93B;
    --azul:#3E6FA6;
    --azul-bg:#E6EEF6;
    --verde:#3A7256;
    --verde-bg:#E4EFE7;
    --tijolo:#B84A3E;
    --tijolo-bg:#F6E6E3;
    --cinza:#8A8878;
    --cinza-bg:#EDEAE0;
    --linha:#D8D2C2;
    --texto-mudo:#6B6A63;
  }
  *{box-sizing:border-box;}
  body{
    margin:0;
    background:var(--papel);
    color:var(--tinta);
    font-family:'Inter', sans-serif;
  }
  h1,h2,h3{ font-family:'Barlow Condensed', sans-serif; font-weight:600; margin:0; }
  .mono{ font-family:'JetBrains Mono', monospace; }

  /* --- Login --- */
  #tela-login{
    min-height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
    background:var(--tinta);
  }
  .card-login{
    background:#fff;
    border-radius:12px;
    padding:2.5rem 2.5rem 1.6rem;
    width:360px;
  }
  .login-rodape{
    text-align:center;
    font-size:11.5px;
    color:var(--texto-mudo);
    margin:1.2rem 0 0;
  }
  .logo-login{
    display:flex;
    align-items:center;
    gap:10px;
    margin-bottom:1.6rem;
  }
  .logo-login .titulo{ font-size:1.3rem; font-weight:600; }
  .logo-marca{
    width:40px; height:34px;
    background:var(--ambar);
    border-radius:8px;
    display:flex; align-items:center; justify-content:center;
    font-family:'Barlow Condensed', sans-serif;
    font-weight:700;
    color:var(--tinta);
    font-size:15px;
    letter-spacing:0.02em;
  }
  .campo-login{ margin-bottom:1rem; }
  .campo-login label{
    display:block;
    font-size:12px;
    font-weight:600;
    color:var(--texto-mudo);
    text-transform:uppercase;
    letter-spacing:0.04em;
    margin-bottom:6px;
  }
  .campo-login input[type=text], .campo-login input[type=password]{
    width:100%;
    padding:10px 12px;
    border:1px solid var(--linha);
    border-radius:6px;
    font-size:14px;
    font-family:'Inter', sans-serif;
  }
  .btn-entrar{
    width:100%;
    background:#3350D8;
    color:#fff;
    border:none;
    border-radius:8px;
    padding:12px;
    font-weight:600;
    font-size:14px;
    cursor:pointer;
  }
  .btn-entrar:hover{ background:#2942BE; }

  /* --- App shell --- */
  #app{ display:none; min-height:100vh; }
  .sidebar{
    width:220px;
    background:var(--tinta);
    color:var(--papel);
    flex-shrink:0;
    padding:1.4rem 0;
    display:flex;
    flex-direction:column;
  }
  .sidebar .logo-login{ padding:0 1.2rem; margin-bottom:2rem; }
  .usuario-sidebar{
    margin-top:auto;
    margin:auto 1rem 0;
    background:var(--tinta-2);
    border-radius:10px;
    padding:1.1rem 1rem;
    text-align:center;
  }
  .avatar-usuario-sidebar{
    width:44px; height:44px;
    border-radius:50%;
    background:rgba(255,255,255,0.12);
    display:flex; align-items:center; justify-content:center;
    font-size:18px;
    margin:0 auto 8px;
  }
  .nome-usuario-sidebar{
    font-size:13px;
    font-weight:500;
    color:var(--papel);
    margin-bottom:10px;
  }
  .btn-sair{
    width:100%;
    background:var(--azul);
    color:#fff;
    border:none;
    border-radius:6px;
    padding:8px;
    font-size:13px;
    font-weight:600;
    cursor:pointer;
  }
  .btn-sair:hover{ opacity:0.9; }
  .nav-item{
    display:flex;
    align-items:center;
    gap:10px;
    padding:11px 1.2rem;
    color:#C7CDD6;
    font-size:14px;
    cursor:pointer;
    border-left:3px solid transparent;
  }
  .nav-item:hover{ background:var(--tinta-2); color:#fff; }
  .nav-item.ativo{
    background:var(--tinta-2);
    color:#fff;
    border-left-color:var(--ambar);
  }
  .nav-icone{ width:16px; text-align:center; font-size:13px; }
  .layout{ display:flex; }
  .conteudo{ flex:1; padding:2rem 2.4rem; max-width:1180px; }
  .topo-pagina{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:1.6rem;
  }
  .topo-pagina h1{ font-size:1.7rem; }
  .usuario-chip{
    display:flex; align-items:center; gap:8px;
    font-size:13px;
    color:var(--texto-mudo);
  }
  .avatar{
    width:28px;height:28px;border-radius:50%;
    background:var(--azul-bg); color:var(--azul);
    display:flex;align-items:center;justify-content:center;
    font-size:12px; font-weight:600;
  }

  /* --- Dashboard --- */
  .grid-stats{
    display:grid;
    grid-template-columns:repeat(5, 1fr);
    gap:14px;
    margin-bottom:1.6rem;
  }
  .card-stat{
    background:#fff;
    border:1px solid var(--linha);
    border-radius:10px;
    padding:1.1rem 1.2rem;
  }
  .card-stat .rot{ font-size:12px; color:var(--texto-mudo); margin-bottom:4px; }
  .card-stat .num{ font-size:1.9rem; font-weight:700; }
  .card-stat.recebida .num{ color:var(--cinza); }
  .card-stat.conferencia .num{ color:var(--azul); }
  .card-stat.liberada .num{ color:var(--verde); }
  .card-stat.paga .num{ color:var(--tinta); }

  .duas-colunas{ display:grid; grid-template-columns:1.3fr 1fr; gap:16px; }
  .painel{
    background:#fff;
    border:1px solid var(--linha);
    border-radius:10px;
    padding:1.3rem 1.4rem;
  }
  .painel h2{ font-size:1.15rem; margin-bottom:1rem; }
  .linha-vencendo{
    display:flex; justify-content:space-between; align-items:center;
    padding:9px 0;
    border-bottom:1px solid var(--linha);
    font-size:13px;
  }
  .linha-vencendo:last-child{ border-bottom:none; }
  .linha-vencendo .empresa{ font-weight:500; }
  .linha-vencendo .venc{ color:var(--tijolo); font-weight:600; }

  .valor-aberto{ font-size:2.2rem; font-weight:700; margin:0.4rem 0 0.2rem; }
  .valor-aberto-rot{ font-size:13px; color:var(--texto-mudo); }

  /* --- Selos de status --- */
  .selo{
    display:inline-block;
    font-size:11.5px;
    font-weight:600;
    padding:3px 10px;
    border-radius:20px;
    white-space:nowrap;
  }
  .selo.recebida{ background:var(--cinza-bg); color:#5C5A4E; }
  .selo.conferencia{ background:var(--azul-bg); color:var(--azul); }
  .selo.liberada{ background:var(--verde-bg); color:var(--verde); }
  .selo.paga{ background:var(--tinta); color:var(--papel); }
  .selo.divergencia{ background:var(--tijolo-bg); color:var(--tijolo); }

  /* --- Lista de faturas --- */
  .barra-filtros{
    display:flex; gap:10px; margin-bottom:1.2rem; flex-wrap:wrap;
  }
  .barra-filtros input, .barra-filtros select{
    padding:9px 12px;
    border:1px solid var(--linha);
    border-radius:6px;
    font-size:13px;
    font-family:'Inter', sans-serif;
  }
  table.faturas{
    width:100%;
    border-collapse:collapse;
    background:#fff;
    border:1px solid var(--linha);
    border-radius:10px;
    overflow:hidden;
  }
  table.faturas th{
    text-align:left;
    font-size:11.5px;
    text-transform:uppercase;
    letter-spacing:0.03em;
    color:var(--texto-mudo);
    padding:10px 14px;
    background:var(--papel-2);
    border-bottom:1px solid var(--linha);
  }
  table.faturas td{
    padding:11px 14px;
    font-size:13.5px;
    border-bottom:1px solid var(--linha);
  }
  table.faturas tr:last-child td{ border-bottom:none; }
  table.faturas tr.linha-clicavel{ cursor:pointer; }
  table.faturas tr.linha-clicavel:hover{ background:var(--papel-2); }
  .icone-pdf{ color:var(--tijolo); font-weight:600; font-size:12px; }

  /* --- Tela de aprovação --- */
  .aprovacao-grid{ display:grid; grid-template-columns:1fr 1.1fr; gap:20px; }
  .pdf-mock{
    background:var(--tinta);
    border-radius:10px;
    aspect-ratio:3/4;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    color:#8B96A3;
    font-size:13px;
    gap:8px;
  }
  .pdf-mock .arquivo-nome{ color:var(--papel); font-family:'JetBrains Mono', monospace; font-size:12px; }
  .campo-dado{ margin-bottom:0.9rem; }
  .campo-dado label{
    display:block; font-size:11.5px; color:var(--texto-mudo);
    text-transform:uppercase; letter-spacing:0.03em; margin-bottom:3px;
  }
  .campo-dado .valor{ font-size:14.5px; }
  textarea.obs{
    width:100%; min-height:70px;
    border:1px solid var(--linha); border-radius:6px;
    padding:9px 11px; font-family:'Inter', sans-serif; font-size:13.5px;
    resize:vertical;
  }
  .acoes-aprovacao{ display:flex; gap:10px; margin-top:1.2rem; }
  .btn-acao{
    flex:1;
    padding:11px;
    border-radius:6px;
    font-weight:600;
    font-size:13.5px;
    cursor:pointer;
    border:1px solid transparent;
  }
  .btn-liberar{ background:var(--verde); color:#fff; }
  .btn-liberar:hover{ opacity:0.9; }
  .btn-divergencia{ background:#fff; color:var(--tijolo); border-color:var(--tijolo); }
  .btn-divergencia:hover{ background:var(--tijolo-bg); }

  .link-voltar{
    font-size:13px; color:var(--texto-mudo); cursor:pointer; margin-bottom:1rem; display:inline-block;
  }
  .link-voltar:hover{ color:var(--tinta); }
</style>
</head>
<body>

<!-- TELA DE LOGIN -->
<div id="tela-login">
  <div class="card-login">
    <div class="logo-login">
      <div class="logo-marca">CGF</div>
      <div class="titulo">Controle e Gestão de Faturas</div>
    </div>
    <p style="font-size:12.5px; color:var(--texto-mudo); line-height:1.5; margin:-1rem 0 1.4rem;">O CGF foi desenvolvido para centralizar o recebimento, conferência e liberação de faturas, trazendo mais controle, agilidade e segurança ao processo financeiro.</p>
    <div class="campo-login">
      <label>E-mail</label>
      <input type="text" placeholder="nome@empresa.com" value="ana.logistica@empresa.com">
    </div>
    <div class="campo-login">
      <label>Senha</label>
      <input type="password" placeholder="••••••••" value="••••••••">
    </div>
    <p style="text-align:right; margin:-0.4rem 0 1rem;"><a href="#" style="font-size:12.5px; color:var(--tinta); text-decoration:none;" onclick="document.getElementById('tela-login').style.display='none'; document.getElementById('tela-recuperar').style.display='flex'; return false;">Esqueceu sua senha?</a></p>
    <button class="btn-entrar" onclick="document.getElementById('tela-login').style.display='none'; document.getElementById('app').style.display='flex';">Entrar</button>
    <p class="login-rodape">© 2026 CGF · Aline Alves</p>
  </div>
</div>

<!-- TELA DE RECUPERAR SENHA -->
<div id="tela-recuperar" style="display:none; min-height:100vh; align-items:center; justify-content:center; background:var(--tinta);">
  <div class="card-login">
    <div class="logo-login">
      <div class="logo-marca">CGF</div>
      <div class="titulo" style="font-size:1.15rem;">Redefinir senha</div>
    </div>
    <p style="font-size:12.5px; color:var(--texto-mudo); line-height:1.5; margin:-1rem 0 1.4rem;">Informe seu e-mail corporativo. Vamos enviar um link para você criar uma nova senha.</p>
    <div class="campo-login">
      <label>E-mail</label>
      <input type="text" id="email-recuperar" placeholder="nome@empresa.com">
    </div>
    <button class="btn-entrar" onclick="
      document.getElementById('form-recuperar').style.display='none';
      document.getElementById('confirmacao-recuperar').style.display='block';
    " id="btn-enviar-recuperar">Enviar link de redefinição</button>
    <p id="confirmacao-recuperar" style="display:none; font-size:13px; color:var(--verde); background:var(--verde-bg); padding:10px 12px; border-radius:6px; margin-top:1rem;">Se esse e-mail estiver cadastrado, você vai receber um link para redefinir sua senha em instantes.</p>
    <p style="text-align:center; margin-top:1.2rem;"><a href="#" style="font-size:12.5px; color:var(--tinta);" onclick="document.getElementById('tela-recuperar').style.display='none'; document.getElementById('tela-login').style.display='flex'; document.getElementById('confirmacao-recuperar').style.display='none'; return false;">← Voltar para o login</a></p>
  </div>
</div>
</div>

<!-- APP -->
<div id="app">
  <div class="layout" style="width:100%;">
    <div class="sidebar">
      <div class="logo-login">
        <div class="logo-marca">CGF</div>
        <div class="titulo" style="font-size:1.05rem;">CGF</div>
      </div>
      <div class="nav-item ativo" data-pagina="dashboard"><span class="nav-icone">▤</span> Dashboard</div>
      <div class="nav-item" data-pagina="lista"><span class="nav-icone">≡</span> Faturas</div>
      <div class="nav-item" data-pagina="aprovacao"><span class="nav-icone">✓</span> Conferência</div>
      <div class="nav-item" data-pagina="canhotos"><span class="nav-icone">📎</span> Canhotos</div>
      <div class="nav-item" data-pagina="nao-lancados"><span class="nav-icone">⛔</span> Não lançados</div>
      <div class="nav-item" data-pagina="divergencias"><span class="nav-icone">⚠</span> Divergências</div>
      <div class="nav-item" data-pagina="usuarios"><span class="nav-icone">☺</span> Usuários</div>

      <div class="usuario-sidebar" onclick="mostrarPagina('perfil')" style="cursor:pointer;">
        <div class="avatar-usuario-sidebar">👤</div>
        <div class="nome-usuario-sidebar">Aline de Paula Alves</div>
        <button class="btn-sair" onclick="event.stopPropagation(); document.getElementById('app').style.display='none'; document.getElementById('tela-login').style.display='flex';">Sair</button>
      </div>
    </div>

    <div class="conteudo">

      <!-- DASHBOARD -->
      <div class="pagina" id="pagina-dashboard">
        <div class="topo-pagina">
          <h1>Dashboard</h1>
          <div class="usuario-chip"><div class="avatar">AL</div> Ana · Logística</div>
        </div>

        <div class="grid-stats">
          <div class="card-stat recebida"><div class="rot">Recebidas</div><div class="num">14</div></div>
          <div class="card-stat conferencia"><div class="rot">Em conferência</div><div class="num">6</div></div>
          <div class="card-stat liberada"><div class="rot">Liberadas p/ pagamento</div><div class="num">9</div></div>
          <div class="card-stat paga"><div class="rot">Pagas (semana)</div><div class="num">22</div></div>
          <div class="card-stat" style="cursor:pointer;" onclick="mostrarPagina('divergencias')"><div class="rot">Divergências de valor</div><div class="num" style="color:var(--tijolo);">1</div></div>
        </div>

        <div class="duas-colunas">
          <div class="painel">
            <h2>Vencendo nos próximos dias</h2>
            <div class="linha-vencendo"><span class="empresa">J Silveira Transportes LTDA</span><span class="venc">Vence hoje</span></div>
            <div class="linha-vencendo"><span class="empresa">Log 2 Bebedouro Transportes</span><span class="venc">Vence amanhã</span></div>
            <div class="linha-vencendo"><span class="empresa">Maria Fumaça Log LTDA</span><span class="venc">Em 2 dias</span></div>
            <div class="linha-vencendo"><span class="empresa">Ghelere Transportes LTDA</span><span class="venc">Em 3 dias</span></div>
          </div>
          <div class="painel">
            <h2>Valor em aberto</h2>
            <div class="valor-aberto">R$ 84.320,00</div>
            <div class="valor-aberto-rot">15 faturas aguardando pagamento</div>
          </div>
        </div>
      </div>

      <!-- LISTA DE FATURAS -->
      <div class="pagina" id="pagina-lista" style="display:none;">
        <div class="topo-pagina">
          <h1>Faturas</h1>
          <div class="usuario-chip"><div class="avatar">AL</div> Ana · Logística</div>
        </div>

        <div class="barra-filtros">
          <input type="text" id="busca-transportadora" placeholder="Buscar por transportadora...">
          <input type="text" id="busca-numero" placeholder="Nº da fatura ou do CT-e...">
          <button class="btn-acao" onclick="filtrarFaturas()" style="flex:none; padding:9px 16px; background:var(--tinta); color:#fff; display:flex; align-items:center; gap:6px;">🔍 Buscar</button>
          <select id="filtro-status-faturas" onchange="filtrarFaturas()">
            <option value="pendentes">Pendentes (não pagas)</option>
            <option value="todos">Todos os status</option>
            <option value="recebida">Recebida</option>
            <option value="conferencia">Em conferência</option>
            <option value="liberada">Pagamento liberado</option>
            <option value="pago">Pago</option>
            <option value="divergencia">Divergência</option>
          </select>
        </div>

        <table class="faturas">
          <thead>
            <tr>
              <th>Transportadora</th><th>Nº fatura</th><th>CT-e</th><th>Valor</th><th>Vencimento</th><th>Status</th><th>PDF</th>
            </tr>
          </thead>
          <tbody id="corpo-tabela-faturas">
            <tr class="linha-clicavel" data-status="pago" onclick="mostrarPagina('aprovacao')">
              <td>Log 2 Bebedouro Transportes</td><td class="mono">F-58118</td><td class="mono">1553</td><td class="mono">R$ 4.001,00</td><td>10/07/2026</td><td><span class="selo paga">Pago</span></td><td class="icone-pdf">PDF ↗</td>
            </tr>
            <tr class="linha-clicavel" data-status="recebida" onclick="mostrarPagina('aprovacao')">
              <td>J Silveira Transportes LTDA</td><td class="mono">89953-A</td><td class="mono">89953</td><td class="mono">R$ 7.094,00</td><td>15/07/2026</td><td><span class="selo recebida">Recebida</span></td><td class="icone-pdf">PDF ↗</td>
            </tr>
            <tr class="linha-clicavel" data-status="liberada" onclick="mostrarPagina('aprovacao')">
              <td>Maria Fumaça Log LTDA</td><td class="mono">MF-0431</td><td class="mono">431, 432</td><td class="mono">R$ 9.130,28</td><td>18/07/2026</td><td><span class="selo liberada">Pagamento liberado</span></td><td class="icone-pdf">PDF ↗</td>
            </tr>
            <tr class="linha-clicavel" data-status="conferencia" onclick="mostrarPagina('aprovacao')">
              <td>Log 2 Bebedouro Transportes</td><td class="mono">F-58231</td><td class="mono">1570, 1571, 1572</td><td class="mono">R$ 19.800,00</td><td>21/07/2026</td><td><span class="selo conferencia">Em conferência</span></td><td class="icone-pdf">PDF ↗</td>
            </tr>
            <tr class="linha-clicavel" data-status="divergencia" onclick="mostrarPagina('aprovacao')">
              <td>Ghelere Transportes LTDA</td><td class="mono">GH-2201</td><td class="mono">146926</td><td class="mono">R$ 4.200,00</td><td>22/07/2026</td><td><span class="selo divergencia">Divergência</span></td><td class="icone-pdf">PDF ↗</td>
            </tr>
          </tbody>
        </table>
      </div>

      <!-- TELA DE APROVAÇÃO -->
      <div class="pagina" id="pagina-aprovacao" style="display:none;">
        <span class="link-voltar" onclick="mostrarPagina('lista')">← Voltar para a lista</span>
        <div class="topo-pagina">
          <h1>Conferência da fatura</h1>
          <span class="selo liberada" id="selo-status-aprovacao">Pagamento liberado</span>
        </div>
        <div style="margin-bottom:0.8rem;">
          <label style="font-size:11.5px; color:var(--texto-mudo); text-transform:uppercase; letter-spacing:0.03em;">Simular status desta fatura (demonstração)</label><br>
          <select id="simulador-status" onchange="simularStatus()" style="margin-top:4px; padding:7px 10px; border:1px solid var(--linha); border-radius:6px; font-size:13px;">
            <option value="recebida">Recebida</option>
            <option value="conferencia">Em conferência</option>
            <option value="liberada" selected>Pagamento liberado</option>
            <option value="paga">Pago</option>
            <option value="divergencia">Divergência</option>
          </select>
        </div>

        <div style="display:flex; gap:8px; margin-bottom:1.2rem; align-items:center;">
          <span style="font-size:12px; color:var(--texto-mudo); align-self:center; margin-right:4px;">Ver como:</span>
          <button class="btn-acao" id="btn-visao-logistica" onclick="mudarVisaoAprovacao('logistica')" style="flex:none; padding:6px 14px; font-size:12.5px; background:#fff; color:var(--tinta); border:1px solid var(--linha);">Logística</button>
          <button class="btn-acao" id="btn-visao-financeiro" onclick="mudarVisaoAprovacao('financeiro')" style="flex:none; padding:6px 14px; font-size:12.5px; background:var(--tinta); color:#fff;">Financeiro</button>
          <span style="font-size:11.5px; color:var(--texto-mudo); margin-left:6px;">(como Administradora, você tem acesso às duas visões)</span>
        </div>

        <div class="aprovacao-grid">
          <div>
            <div class="pdf-mock">
              <div style="font-size:32px;">📄</div>
              <div class="arquivo-nome">fatura_LOG2_F-58231.pdf</div>
              <div>Pré-visualização do documento</div>
            </div>
          </div>

          <div>
            <div class="painel">
              <div class="campo-dado"><label>Transportadora</label><div class="valor">Log 2 Bebedouro Transportes LTDA</div></div>
              <div class="campo-dado"><label>Número da fatura</label><div class="valor mono">F-58231</div></div>
              <div class="campo-dado"><label>CT-e vinculados</label><div class="valor mono">1570 · 1571 · 1572</div></div>
              <div class="campo-dado">
                <label>Canhotos</label>
                <div class="valor" id="status-canhotos-fatura">2 de 3 anexados — <span style="color:var(--tijolo); font-weight:600;">CT-e 1572 pendente</span></div>
              </div>
              <div class="campo-dado"><label>Valor total</label><div class="valor mono">R$ 19.800,00</div></div>
              <div class="campo-dado"><label>Data de vencimento</label><div class="valor">21/07/2026</div></div>
              <div class="campo-dado"><label>Data de recebimento</label><div class="valor">14/07/2026</div></div>
              <div class="campo-dado">
                <label>Observações</label>
                <textarea class="obs" placeholder="Anote aqui qualquer divergência ou observação sobre essa fatura..."></textarea>
              </div>

              <div id="acoes-logistica" class="acoes-aprovacao" style="display:none;">
                <button class="btn-acao btn-liberar" id="btn-liberar-pagamento" disabled title="Existe canhoto pendente — anexe antes de liberar" style="opacity:0.5; cursor:not-allowed;">🔒 Liberar para pagamento</button>
                <button class="btn-acao btn-divergencia">Marcar divergência</button>
              </div>

              <div id="acoes-financeiro">
                <div id="financeiro-pode-agir">
                  <div class="campo-dado"><label>Data do pagamento</label><input type="date" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
                  <div class="acoes-aprovacao">
                    <button class="btn-acao btn-liberar">Marcar como pago</button>
                  </div>
                </div>
                <p id="financeiro-somente-visualizacao" style="display:none; font-size:13px; color:var(--texto-mudo); background:var(--papel-2); padding:10px 12px; border-radius:6px;">Esta fatura ainda não foi liberada pela logística — disponível apenas para consulta.</p>
                <p id="financeiro-ja-pago" style="display:none; font-size:13px; color:var(--verde); background:var(--verde-bg); padding:10px 12px; border-radius:6px;">✓ Pagamento já realizado. Nenhuma ação adicional necessária.</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- DIVERGÊNCIAS -->
      <div class="pagina" id="pagina-divergencias" style="display:none;">
        <div class="topo-pagina">
          <h1>Divergências de valor</h1>
          <button class="btn-acao btn-liberar" style="flex:none; padding:9px 18px;" onclick="document.getElementById('form-nova-divergencia').style.display='block';">+ Registrar divergência</button>
        </div>
        <p style="font-size:13px; color:var(--texto-mudo); margin-top:-0.6rem; margin-bottom:1.2rem;">Registro de CT-e/faturas com valor cobrado diferente do valor validado pelo portal — substitui o e-mail manual, ficando visível e consultável por todos com acesso.</p>

        <div class="painel" id="form-nova-divergencia" style="display:none; margin-bottom:1.2rem;">
          <h2>Registrar nova divergência</h2>
          <div class="aprovacao-grid" style="grid-template-columns:1fr 1fr 1fr;">
            <div class="campo-dado"><label>Data da carga</label><input type="date" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Transportadora</label><input type="text" placeholder="Nome da transportadora" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>CT-e</label><input type="text" placeholder="Número do CT-e" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Unidade</label><input type="text" placeholder="Ex: Norte Pioneiro" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Fábrica</label><input type="text" placeholder="Ex: Agudos" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Tipo</label>
              <select style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;">
                <option>Retorno</option><option>Ida</option><option>Saindo revenda</option>
              </select>
            </div>
            <div class="campo-dado"><label>Valor Portal (esperado)</label><input type="text" id="input-valor-portal" placeholder="R$ 0,00" oninput="calcularDiferenca()" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Valor CT-e (cobrado)</label><input type="text" id="input-valor-cte" placeholder="R$ 0,00" oninput="calcularDiferenca()" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Diferença</label><div id="valor-diferenca-calculada" class="valor mono" style="padding:9px 0; color:var(--tijolo); font-weight:600;">R$ 0,00</div></div>
          </div>
          <div class="campo-dado"><label>Motivo</label><input type="text" placeholder="Ex: Valor frete mínimo não validado" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
          <div class="campo-dado"><label>Forma / data de pagamento</label><input type="text" placeholder="Ex: Pix em 07/07/2026" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
          <div class="acoes-aprovacao">
            <button class="btn-acao btn-liberar">Salvar divergência</button>
            <button class="btn-acao btn-divergencia" onclick="document.getElementById('form-nova-divergencia').style.display='none';">Cancelar</button>
          </div>
        </div>

        <div style="display:flex; gap:8px; margin-bottom:1rem; align-items:center;">
          <input type="text" id="busca-motivo-divergencia" placeholder="Pesquisar por motivo..." onkeydown="if(event.key==='Enter') buscarDivergenciaPorMotivo();" style="padding:8px 12px; border:1px solid var(--linha); border-radius:6px; font-size:13px; min-width:220px;">
          <button class="btn-acao" onclick="buscarDivergenciaPorMotivo()" style="flex:none; padding:8px 14px; background:var(--tinta); color:#fff;">→</button>
        </div>

        <table class="faturas">
          <thead>
            <tr>
              <th>Data carga</th><th>Transportadora</th><th>CT-e</th><th>Unidade</th><th>Fábrica</th><th>Tipo</th><th>Valor Portal</th><th>Valor CT-e</th><th>Diferença</th><th>Motivo</th>
            </tr>
          </thead>
          <tbody id="corpo-tabela-divergencias">
            <tr data-motivo="valor frete mínimo não validado" data-diferenca="-810.00">
              <td>07/07</td><td>Boa Viagem</td><td class="mono">118637</td><td>Norte Pioneiro</td><td>Agudos</td><td>Retorno</td>
              <td class="mono" style="background:var(--verde-bg);">R$ 3.990,00</td>
              <td class="mono">R$ 4.800,00</td>
              <td class="mono" style="background:var(--tijolo-bg); color:var(--tijolo);">-R$ 810,00</td>
              <td style="font-size:12.5px;">Valor frete mínimo não validado</td>
            </tr>
          </tbody>
        </table>
        <div style="text-align:right; margin-top:10px; font-size:14px;">
          <span style="color:var(--texto-mudo);">Somatório das diferenças:</span>
          <span id="somatorio-divergencias" class="mono" style="font-weight:700; color:var(--tijolo); margin-left:6px;">-R$ 810,00</span>
        </div>
      </div>

      <!-- CANHOTOS -->
      <div class="pagina" id="pagina-canhotos" style="display:none;">
        <div class="topo-pagina">
          <h1>Canhotos</h1>
          <button class="btn-acao btn-liberar" style="flex:none; padding:9px 18px;" onclick="document.getElementById('form-novo-canhoto').style.display='block';">+ Registrar canhoto</button>
        </div>
        <p style="font-size:13px; color:var(--texto-mudo); margin-top:-0.6rem; margin-bottom:1.2rem;">Comprovantes de entrega assinados pelo destinatário. Uma fatura só pode ser liberada para pagamento quando o canhoto de todos os seus CT-e estiver anexado aqui.</p>

        <div class="painel" id="form-novo-canhoto" style="display:none; margin-bottom:1.2rem;">
          <h2>Registrar novo canhoto</h2>
          <div class="aprovacao-grid" style="grid-template-columns:1fr 1fr 1fr;">
            <div class="campo-dado"><label>Data validação</label><input type="date" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Transportadora</label><input type="text" placeholder="Nome da transportadora" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Data emissão CT-e</label><input type="date" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Nº CT-e</label><input type="text" placeholder="Número do CT-e" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Anexo do canhoto (opcional agora)</label><input type="file" style="width:100%; font-size:13px;"></div>
          </div>
          <div class="acoes-aprovacao">
            <button class="btn-acao btn-liberar" onclick="registrarNovoCanhoto();">Salvar canhoto</button>
            <button class="btn-acao btn-divergencia" onclick="document.getElementById('form-novo-canhoto').style.display='none';">Cancelar</button>
          </div>
        </div>

        <div style="display:flex; gap:8px; margin-bottom:1rem; align-items:center;">
          <button class="btn-acao filtro-canhoto ativo" data-filtro="pendente" onclick="filtrarCanhotos('pendente', this)" style="flex:none; padding:7px 16px; background:var(--tinta); color:#fff;">Pendentes</button>
          <button class="btn-acao filtro-canhoto" data-filtro="todos" onclick="filtrarCanhotos('todos', this)" style="flex:none; padding:7px 16px; background:#fff; color:var(--tinta); border:1px solid var(--linha);">Todos</button>
          <input type="text" id="busca-canhoto" placeholder="Pesquisar nº CT-e..." onkeydown="if(event.key==='Enter') buscarCanhoto();" style="padding:8px 12px; border:1px solid var(--linha); border-radius:6px; font-size:13px; margin-left:8px;">
          <button class="btn-acao" onclick="buscarCanhoto()" style="flex:none; padding:8px 14px; background:var(--tinta); color:#fff;">→</button>
        </div>

        <table class="faturas">
          <thead>
            <tr>
              <th>Data validação</th><th>Transportadora</th><th>Data emissão CT-e</th><th>Nº CT-e</th><th>Status</th><th>Data anexo</th><th>Ação</th>
            </tr>
          </thead>
          <tbody id="corpo-tabela-canhotos">
            <tr data-status-canhoto="anexado" data-data-validacao="2026-06-08">
              <td>08/jun</td><td>Verdes Campos</td><td>05/jun</td><td class="mono">138611</td>
              <td><span class="selo liberada canhoto-selo">Anexado</span></td><td class="canhoto-data-anexo">10/jun</td>
              <td class="icone-pdf">PDF ↗</td>
            </tr>
            <tr data-status-canhoto="anexado" data-data-validacao="2026-06-12">
              <td>12/jun</td><td>Verdes Campos</td><td>10/jun</td><td class="mono">138695</td>
              <td><span class="selo liberada canhoto-selo">Anexado</span></td><td class="canhoto-data-anexo">15/jun</td>
              <td class="icone-pdf">PDF ↗</td>
            </tr>
            <tr data-status-canhoto="anexado" data-data-validacao="2026-06-15">
              <td>15/jun</td><td>Castoldi</td><td>11/jun</td><td class="mono">88852</td>
              <td><span class="selo liberada canhoto-selo">Anexado</span></td><td class="canhoto-data-anexo">16/jun</td>
              <td class="icone-pdf">PDF ↗</td>
            </tr>
            <tr data-status-canhoto="pendente" data-data-validacao="2026-06-27">
              <td>27/jun</td><td>Expresso Ponta Grossa</td><td>25/jun</td><td class="mono">1619</td>
              <td><span class="selo recebida canhoto-selo">Pendente</span></td><td class="canhoto-data-anexo">—</td>
              <td><button class="btn-acao btn-liberar btn-anexar-canhoto" style="flex:none; padding:6px 14px; font-size:12px;" onclick="anexarCanhoto(this)">📎 Anexar canhoto</button></td>
            </tr>
            <tr data-status-canhoto="pendente" data-data-validacao="2026-06-29">
              <td>29/jun</td><td>Expresso Ponta Grossa</td><td>25/jun</td><td class="mono">1621</td>
              <td><span class="selo recebida canhoto-selo">Pendente</span></td><td class="canhoto-data-anexo">—</td>
              <td><button class="btn-acao btn-liberar btn-anexar-canhoto" style="flex:none; padding:6px 14px; font-size:12px;" onclick="anexarCanhoto(this)">📎 Anexar canhoto</button></td>
            </tr>
          </tbody>
        </table>
      </div>

      <!-- CT-E NÃO LANÇADOS -->
      <div class="pagina" id="pagina-nao-lancados" style="display:none;">
        <div class="topo-pagina">
          <h1>CT-e não lançados</h1>
          <button class="btn-acao btn-liberar" style="flex:none; padding:9px 18px;" onclick="document.getElementById('form-novo-nao-lancado').style.display='block';">+ Registrar</button>
        </div>
        <p style="font-size:13px; color:var(--texto-mudo); margin-top:-0.6rem; margin-bottom:1.2rem;">CT-e que não são lançados no sistema interno, com a justificativa registrada — substitui o controle manual em planilha.</p>

        <div class="painel" id="form-novo-nao-lancado" style="display:none; margin-bottom:1.2rem;">
          <h2>Registrar CT-e não lançado</h2>
          <div class="aprovacao-grid" style="grid-template-columns:1fr 1fr 1fr;">
            <div class="campo-dado"><label>Revenda</label><input type="text" placeholder="Ex: Ponta Grossa" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Data lançamento</label><input type="date" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Transportadora</label><input type="text" placeholder="Nome da transportadora" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Nº CT-e</label><input type="text" placeholder="Número do CT-e" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Nota</label><input type="text" placeholder="Ex: Vasilhame" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
            <div class="campo-dado"><label>Situação</label>
              <select id="select-situacao-nao-lancado" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;">
                <option value="cancelado">Cancelado</option>
                <option value="desacordo">Desacordo</option>
                <option value="estoque">Estoque fechado</option>
              </select>
            </div>
          </div>
          <div class="campo-dado"><label>Motivo</label><input type="text" id="input-motivo-nao-lancado" placeholder="Ex: Virada do mês" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
          <div class="acoes-aprovacao">
            <button class="btn-acao btn-liberar" onclick="registrarNaoLancado();">Salvar</button>
            <button class="btn-acao btn-divergencia" onclick="document.getElementById('form-novo-nao-lancado').style.display='none';">Cancelar</button>
          </div>
        </div>

        <div style="display:flex; gap:8px; margin-bottom:1rem;">
          <button class="btn-acao filtro-nao-lancado ativo" data-filtro="todos" onclick="filtrarNaoLancados('todos', this)" style="flex:none; padding:7px 16px; background:var(--tinta); color:#fff;">Todos</button>
          <button class="btn-acao filtro-nao-lancado" data-filtro="cancelado" onclick="filtrarNaoLancados('cancelado', this)" style="flex:none; padding:7px 16px; background:#fff; color:var(--tinta); border:1px solid var(--linha);">Cancelados</button>
          <button class="btn-acao filtro-nao-lancado" data-filtro="desacordo" onclick="filtrarNaoLancados('desacordo', this)" style="flex:none; padding:7px 16px; background:#fff; color:var(--tinta); border:1px solid var(--linha);">Desacordo</button>
          <button class="btn-acao filtro-nao-lancado" data-filtro="estoque" onclick="filtrarNaoLancados('estoque', this)" style="flex:none; padding:7px 16px; background:#fff; color:var(--tinta); border:1px solid var(--linha);">Estoque fechado</button>
        </div>

        <table class="faturas">
          <thead>
            <tr>
              <th>Revenda</th><th>Data lançamento</th><th>Transportadora</th><th>Nº CT-e</th><th>Nota</th><th>Situação</th><th>Motivo</th>
            </tr>
          </thead>
          <tbody id="corpo-tabela-nao-lancados">
            <tr data-situacao="estoque">
              <td>Ponta Grossa</td><td>01/jul</td><td>Maria Fumaça</td><td class="mono">18109</td><td>Vasilhame</td>
              <td><span class="selo recebida">Estoque fechado</span></td><td style="font-size:12.5px;">Virada do mês</td>
            </tr>
          </tbody>
        </table>
      </div>

      <!-- USUÁRIOS -->
      <div class="pagina" id="pagina-usuarios" style="display:none;">
        <div class="topo-pagina">
          <h1>Usuários</h1>
          <button class="btn-acao btn-liberar" style="flex:none; padding:9px 18px;" onclick="document.getElementById('form-novo-usuario').style.display='block';">+ Novo usuário</button>
        </div>

        <div class="painel" id="form-novo-usuario" style="display:none; margin-bottom:1.2rem;">
          <h2>Convidar novo usuário</h2>
          <div class="campo-dado"><label>Nome completo</label><input type="text" placeholder="Nome da pessoa" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
          <div class="campo-dado"><label>E-mail corporativo</label><input type="text" placeholder="nome.sobrenome@empresa.com" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
          <div class="campo-dado"><label>Setor</label>
            <select style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;">
              <option>Logística</option>
              <option>Financeiro</option>
              <option>Administrador</option>
            </select>
          </div>
          <div class="acoes-aprovacao">
            <button class="btn-acao btn-liberar" onclick="
              document.getElementById('confirmacao-convite').style.display='block';
            ">Enviar convite</button>
            <button class="btn-acao btn-divergencia" onclick="document.getElementById('form-novo-usuario').style.display='none'; document.getElementById('confirmacao-convite').style.display='none';">Cancelar</button>
          </div>
          <p id="confirmacao-convite" style="display:none; font-size:13px; color:var(--verde); background:var(--verde-bg); padding:10px 12px; border-radius:6px; margin-top:1rem;">Convite enviado! Peça para a pessoa verificar o e-mail e seguir o link para criar a senha.</p>
        </div>

        <table class="faturas">
          <thead><tr><th>Nome</th><th>E-mail</th><th>Setor</th><th>Status</th></tr></thead>
          <tbody>
            <tr><td>Aline de Paula Alves</td><td class="mono">aline.alves@empresa.com</td><td>Administrador</td><td><span class="selo liberada">Ativo</span></td></tr>
            <tr><td>Ana Souza</td><td class="mono">ana.souza@empresa.com</td><td>Logística</td><td><span class="selo liberada">Ativo</span></td></tr>
            <tr><td>Marcos Lima</td><td class="mono">marcos.lima@empresa.com</td><td>Financeiro</td><td><span class="selo liberada">Ativo</span></td></tr>
            <tr><td>Carla Nunes</td><td class="mono">carla.nunes@empresa.com</td><td>Logística</td><td><span class="selo recebida">Convite pendente</span></td></tr>
          </tbody>
        </table>
      </div>

      <!-- MEU PERFIL -->
      <div class="pagina" id="pagina-perfil" style="display:none;">
        <div class="topo-pagina"><h1>Meu perfil</h1></div>

        <div class="painel" style="max-width:420px;">
          <h2>Dados de acesso</h2>
          <div class="campo-dado"><label>Nome</label><input type="text" value="Aline de Paula Alves" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
          <div class="campo-dado"><label>E-mail (login)</label><input type="text" value="aline.alves@empresa.com" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
          <div class="campo-dado"><label>Senha atual</label><input type="password" placeholder="Digite sua senha atual" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
          <div class="campo-dado"><label>Nova senha</label><input type="password" placeholder="Digite a nova senha" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
          <div class="campo-dado"><label>Confirmar nova senha</label><input type="password" placeholder="Repita a nova senha" style="width:100%; padding:9px 11px; border:1px solid var(--linha); border-radius:6px; font-size:13.5px;"></div>
          <button class="btn-acao btn-liberar" style="width:100%; margin-top:0.4rem;">Salvar alterações</button>
        </div>
      </div>

    </div>
  </div>
</div>

<script>
function filtrarFaturas(){
  const filtro = document.getElementById('filtro-status-faturas').value;
  document.querySelectorAll('#corpo-tabela-faturas tr').forEach(linha => {
    const status = linha.dataset.status;
    let mostrar = true;
    if(filtro === 'pendentes') mostrar = status !== 'pago';
    else if(filtro !== 'todos') mostrar = status === filtro;
    linha.style.display = mostrar ? '' : 'none';
  });
}
filtrarFaturas();

const rotulosStatus = {
  recebida: 'Recebida',
  conferencia: 'Em conferência',
  liberada: 'Pagamento liberado',
  paga: 'Pago',
  divergencia: 'Divergência',
};

function simularStatus(){
  const valor = document.getElementById('simulador-status').value;
  const selo = document.getElementById('selo-status-aprovacao');
  selo.className = 'selo ' + valor;
  selo.textContent = rotulosStatus[valor];
  atualizarAcaoFinanceiro();
}

function atualizarAcaoFinanceiro(){
  const statusAtual = document.getElementById('simulador-status').value;
  const podeAgir = (statusAtual === 'liberada');
  const jaPago = (statusAtual === 'paga');
  document.getElementById('financeiro-pode-agir').style.display = podeAgir ? 'block' : 'none';
  document.getElementById('financeiro-somente-visualizacao').style.display = (!podeAgir && !jaPago) ? 'block' : 'none';
  document.getElementById('financeiro-ja-pago').style.display = jaPago ? 'block' : 'none';
}

function mudarVisaoAprovacao(visao){
  const btnLog = document.getElementById('btn-visao-logistica');
  const btnFin = document.getElementById('btn-visao-financeiro');
  const acoesLog = document.getElementById('acoes-logistica');
  const acoesFin = document.getElementById('acoes-financeiro');

  if(visao === 'logistica'){
    acoesLog.style.display = 'flex';
    acoesFin.style.display = 'none';
    btnLog.style.background = 'var(--tinta)'; btnLog.style.color = '#fff'; btnLog.style.border = 'none';
    btnFin.style.background = '#fff'; btnFin.style.color = 'var(--tinta)'; btnFin.style.border = '1px solid var(--linha)';
  }else{
    acoesLog.style.display = 'none';
    acoesFin.style.display = 'block';
    btnFin.style.background = 'var(--tinta)'; btnFin.style.color = '#fff'; btnFin.style.border = 'none';
    btnLog.style.background = '#fff'; btnLog.style.color = 'var(--tinta)'; btnLog.style.border = '1px solid var(--linha)';
    atualizarAcaoFinanceiro();
  }
}

function paraNumero(texto){
  const limpo = String(texto).replace('R$','').replace(/\s/g,'').replace(/\./g,'').replace(',','.');
  const n = parseFloat(limpo);
  return isNaN(n) ? 0 : n;
}

const rotulosSituacao = {
  cancelado: 'Cancelado',
  desacordo: 'Desacordo',
  estoque: 'Estoque fechado',
};

function filtrarNaoLancados(filtro, botao){
  document.querySelectorAll('.filtro-nao-lancado').forEach(b => {
    b.style.background = '#fff'; b.style.color = 'var(--tinta)'; b.style.border = '1px solid var(--linha)';
  });
  botao.style.background = 'var(--tinta)'; botao.style.color = '#fff'; botao.style.border = 'none';

  document.querySelectorAll('#corpo-tabela-nao-lancados tr').forEach(linha => {
    const situacao = linha.dataset.situacao;
    linha.style.display = (filtro === 'todos' || situacao === filtro) ? '' : 'none';
  });
}

function registrarNaoLancado(){
  const form = document.getElementById('form-novo-nao-lancado');
  const textos = form.querySelectorAll('input[type=text]');
  const [revenda, transportadora, numeroCte, nota] = Array.from(textos).map(i => i.value);
  const dataLancamentoISO = form.querySelector('input[type=date]').value;
  const situacao = document.getElementById('select-situacao-nao-lancado').value;
  const motivo = document.getElementById('input-motivo-nao-lancado').value;

  const corpo = document.getElementById('corpo-tabela-nao-lancados');
  const novaLinha = document.createElement('tr');
  novaLinha.dataset.situacao = situacao;
  novaLinha.innerHTML = `
    <td>${revenda || '—'}</td><td>${formatarDataCurta(dataLancamentoISO)}</td><td>${transportadora || '—'}</td><td class="mono">${numeroCte || '—'}</td><td>${nota || '—'}</td>
    <td><span class="selo recebida">${rotulosSituacao[situacao]}</span></td><td style="font-size:12.5px;">${motivo || '—'}</td>
  `;
  corpo.appendChild(novaLinha);

  form.style.display = 'none';
  textos.forEach(i => i.value = '');
  form.querySelector('input[type=date]').value = '';
  document.getElementById('input-motivo-nao-lancado').value = '';
}

function formatarDataCurta(dataISO){
  if(!dataISO) return '—';
  const [ano, mes, dia] = dataISO.split('-');
  const meses = ['jan','fev','mar','abr','mai','jun','jul','ago','set','out','nov','dez'];
  return `${dia}/${meses[parseInt(mes,10)-1]}`;
}

function buscarDivergenciaPorMotivo(){
  const termo = document.getElementById('busca-motivo-divergencia').value.trim().toLowerCase();
  document.querySelectorAll('#corpo-tabela-divergencias tr').forEach(linha => {
    const motivo = linha.dataset.motivo || '';
    linha.style.display = (!termo || motivo.includes(termo)) ? '' : 'none';
  });
  atualizarSomatorioDivergencias();
}

function atualizarSomatorioDivergencias(){
  let total = 0;
  document.querySelectorAll('#corpo-tabela-divergencias tr').forEach(linha => {
    if(linha.style.display === 'none') return;
    total += parseFloat(linha.dataset.diferenca || '0');
  });
  const el = document.getElementById('somatorio-divergencias');
  el.textContent = (total < 0 ? '-' : '') + 'R$ ' + Math.abs(total).toLocaleString('pt-BR', {minimumFractionDigits:2});
  el.style.color = total < 0 ? 'var(--tijolo)' : 'var(--verde)';
}

function ordenarCanhotos(){
  const corpo = document.getElementById('corpo-tabela-canhotos');
  const linhas = Array.from(corpo.querySelectorAll('tr'));
  linhas.sort((a, b) => a.dataset.dataValidacao.localeCompare(b.dataset.dataValidacao));
  linhas.forEach(linha => corpo.appendChild(linha));
}

function registrarNovoCanhoto(){
  const form = document.getElementById('form-novo-canhoto');
  const inputs = form.querySelectorAll('input[type=text], input[type=date]');
  const [dataValidacaoISO, transportadora, dataEmissaoISO, numeroCte] = Array.from(inputs).map(i => i.value);

  const corpo = document.getElementById('corpo-tabela-canhotos');
  const novaLinha = document.createElement('tr');
  novaLinha.dataset.statusCanhoto = 'pendente';
  novaLinha.dataset.dataValidacao = dataValidacaoISO || '9999-99-99';
  novaLinha.innerHTML = `
    <td>${formatarDataCurta(dataValidacaoISO)}</td><td>${transportadora || '—'}</td><td>${formatarDataCurta(dataEmissaoISO)}</td><td class="mono">${numeroCte || '—'}</td>
    <td><span class="selo recebida canhoto-selo">Pendente</span></td><td class="canhoto-data-anexo">—</td>
    <td><button class="btn-acao btn-liberar btn-anexar-canhoto" style="flex:none; padding:6px 14px; font-size:12px;" onclick="anexarCanhoto(this)">📎 Anexar canhoto</button></td>
  `;
  corpo.appendChild(novaLinha);
  ordenarCanhotos();

  form.style.display = 'none';
  inputs.forEach(i => i.value = '');
  filtrarCanhotos(filtroCanhotoAtual, document.querySelector(`.filtro-canhoto[data-filtro="${filtroCanhotoAtual}"]`));
}

let filtroCanhotoAtual = 'pendente';
ordenarCanhotos();

function filtrarCanhotos(filtro, botao){
  filtroCanhotoAtual = filtro;
  document.querySelectorAll('.filtro-canhoto').forEach(b => {
    b.style.background = '#fff'; b.style.color = 'var(--tinta)'; b.style.border = '1px solid var(--linha)';
  });
  botao.style.background = 'var(--tinta)'; botao.style.color = '#fff'; botao.style.border = 'none';
  document.getElementById('busca-canhoto').value = '';

  document.querySelectorAll('#corpo-tabela-canhotos tr').forEach(linha => {
    const status = linha.dataset.statusCanhoto;
    linha.style.display = (filtro === 'todos' || status === filtro) ? '' : 'none';
  });
}

function buscarCanhoto(){
  const termo = document.getElementById('busca-canhoto').value.trim().toLowerCase();
  document.querySelectorAll('#corpo-tabela-canhotos tr').forEach(linha => {
    if(!termo){
      const status = linha.dataset.statusCanhoto;
      linha.style.display = (filtroCanhotoAtual === 'todos' || status === filtroCanhotoAtual) ? '' : 'none';
      return;
    }
    const numeroCte = linha.querySelector('td.mono').textContent.toLowerCase();
    linha.style.display = numeroCte.includes(termo) ? '' : 'none';
  });
}

function anexarCanhoto(botao){
  const linha = botao.closest('tr');
  const numeroCte = linha.querySelector('td.mono').textContent;
  const confirmado = confirm(`Confirma que o canhoto assinado do CT-e ${numeroCte} está sendo anexado?`);
  if(!confirmado) return;

  linha.dataset.statusCanhoto = 'anexado';
  const selo = linha.querySelector('.canhoto-selo');
  selo.textContent = 'Anexado';
  selo.className = 'selo liberada canhoto-selo';
  const hoje = new Date().toISOString().slice(0, 10);
  linha.querySelector('.canhoto-data-anexo').textContent = formatarDataCurta(hoje);
  const celulaAcao = botao.parentElement;
  celulaAcao.innerHTML = '<span class="icone-pdf">PDF ↗</span>';
  if(filtroCanhotoAtual === 'pendente'){
    linha.style.display = 'none';
  }
}

function calcularDiferenca(){
  const valorPortal = paraNumero(document.getElementById('input-valor-portal').value);
  const valorCte = paraNumero(document.getElementById('input-valor-cte').value);
  const diferenca = valorPortal - valorCte;
  const el = document.getElementById('valor-diferenca-calculada');
  el.textContent = (diferenca < 0 ? '-' : '') + 'R$ ' + Math.abs(diferenca).toLocaleString('pt-BR', {minimumFractionDigits:2});
  el.style.color = diferenca < 0 ? 'var(--tijolo)' : 'var(--verde)';
}

function mostrarPagina(nome){
  document.querySelectorAll('.pagina').forEach(p => p.style.display = 'none');
  document.getElementById('pagina-' + nome).style.display = 'block';
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('ativo'));
  const navCorrespondente = document.querySelector(`.nav-item[data-pagina="${nome}"]`);
  if(navCorrespondente) navCorrespondente.classList.add('ativo');
}

document.querySelectorAll('.nav-item').forEach(item => {
  item.addEventListener('click', () => mostrarPagina(item.dataset.pagina));
});
</script>

</body>
</html>
