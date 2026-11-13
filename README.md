<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>MindLog TCC — Diário de Pensamentos e Humor</title>
  <link rel="stylesheet" href="style.css" />
  <!-- Chart.js para os gráficos de evolução emocional -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>
  <header class="topbar">
    <div class="container topbar-content">
      <div>
        <h1>MindLog <span class="badge">TCC</span></h1>
        <p class="subtitle">Registro de Pensamentos Disfuncionais & Monitoramento Emocional</p>
      </div>
      <nav class="tabs">
        <button class="tab-btn active" data-tab="paciente">Visão Paciente</button>
        <button class="tab-btn" data-tab="clinico">Painel Clínico (Psicólogo)</button>
      </nav>
    </div>
  </header>

  <main class="container">
    <!-- ABA 1: VISÃO DO PACIENTE (NOVO REGISTRO RPD) -->
    <section id="tab-paciente" class="tab-content active">
      <div class="card">
        <h2>Novo Registro Emocional (RPD)</h2>
        <form id="rpd-form">
          <!-- Escala de Humor -->
          <div class="form-group">
            <label for="humor-range">Como está seu humor agora? <strong id="humor-label">3 - Neutro</strong></label>
            <input type="range" id="humor-range" min="1" max="5" value="3" />
            <div class="range-ticks">
              <span>1 (Muito Mal)</span>
              <span>2 (Mal)</span>
              <span>3 (Neutro)</span>
              <span>4 (Bem)</span>
              <span>5 (Muito Bem)</span>
            </div>
          </div>

          <!-- Seleção de Emoções -->
          <div class="form-group">
            <label>Quais emoções você está sentindo?</label>
            <div class="chips-container" id="emocoes-container">
              <button type="button" class="chip" data-emocao="Ansiedade">Ansiedade</button>
              <button type="button" class="chip" data-emocao="Tristeza">Tristeza</button>
              <button type="button" class="chip" data-emocao="Raiva">Raiva</button>
              <button type="button" class="chip" data-emocao="Frustração">Frustração</button>
              <button type="button" class="chip" data-emocao="Medo">Medo</button>
              <button type="button" class="chip" data-emocao="Culpa">Culpa</button>
              <button type="button" class="chip" data-emocao="Calma">Calma</button>
              <button type="button" class="chip" data-emocao="Alegria">Alegria</button>
            </div>
          </div>

          <!-- Campos da TCC -->
          <div class="form-group">
            <label for="situacao">1. Situação / Gatilho (O que aconteceu?)</label>
            <textarea id="situacao" rows="2" placeholder="Ex: Recebi uma crítica no trabalho durante a reunião..." required></textarea>
          </div>

          <div class="form-group">
            <label for="pensamento">2. Pensamento Automático (O que passou pela sua cabeça?)</label>
            <textarea id="pensamento" rows="2" placeholder="Ex: Eu nunca faço nada direito, vão me demitir..." required></textarea>
          </div>

          <div class="form-group checkbox-group">
            <input type="checkbox" id="pensamento-forte" />
            <label for="pensamento-forte">Marcar como <strong>Pensamento Forte / Intrusivo</strong> (destaque para sessão)</label>
          </div>

          <div class="form-group">
            <label for="comportamento">3. Comportamento / Reação (O que você fez?)</label>
            <textarea id="comportamento" rows="2" placeholder="Ex: Fiquei em silêncio, me isolei e evitei responder mensagens..." required></textarea>
          </div>

          <button type="submit" class="btn-primary">Salvar Registro</button>
        </form>
      </div>

      <!-- Histórico Recente do Paciente -->
      <div class="card">
        <h3>Seus Registros Recentes</h3>
        <div id="lista-registros-paciente" class="registros-list"></div>
      </div>
    </section>

    <!-- ABA 2: PAINEL CLÍNICO (PSICÓLOGO) -->
    <section id="tab-clinico" class="tab-content">
      <div class="grid-charts">
        <div class="card">
          <h3>Evolução do Humor (Média por Registro)</h3>
          <canvas id="chart-humor"></canvas>
        </div>
        <div class="card">
          <h3>Frequência de Emoções</h3>
          <canvas id="chart-emocoes"></canvas>
        </div>
      </div>

      <div class="card">
        <div class="clinical-header">
          <h3>Relatório Clínico de RPD</h3>
          <div class="clinical-actions">
            <label class="filter-label">
              <input type="checkbox" id="filtro-fortes" /> Apenas Pensamentos Fortes
            </label>
            <button id="btn-exportar-csv" class="btn-secondary">Exportar CSV</button>
            <button id="btn-limpar-dados" class="btn-danger">Limpar Tudo</button>
          </div>
        </div>
        <div id="lista-registros-clinico" class="registros-list"></div>
      </div>
    </section>
  </main>

  <footer class="footer">
    <p>Aviso: Ferramenta educativa de apoio baseada em TCC. Não substitui acompanhamento psicológico ou médico. Em caso de crise, ligue 188 (CVV).</p>
  </footer>

  <script src="app.js"></script>
</body>
</html>
