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
    grid-template-columns:repeat(4, 1fr);
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
          <input type="text" placeholder="Buscar por transportadora...">
          <input type="text" placeholder="Nº da fatura ou do CT-e...">
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
              <div class="campo-dado"><label>Valor total</label><div class="valor mono">R$ 19.800,00</div></div>
              <div class="campo-dado"><label>Data de vencimento</label><div class="valor">21/07/2026</div></div>
              <div class="campo-dado"><label>Data de recebimento</label><div class="valor">14/07/2026</div></div>
              <div class="campo-dado">
                <label>Observações</label>
                <textarea class="obs" placeholder="Anote aqui qualquer divergência ou observação sobre essa fatura..."></textarea>
              </div>

              <div id="acoes-logistica" class="acoes-aprovacao" style="display:none;">
                <button class="btn-acao btn-liberar">Liberar para pagamento</button>
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
