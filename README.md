# Projeto Módulo 3 – Low Code/No Code/Vibecode

## 📌 Desafio Escolhido:

Descreva aqui o desafio proposto pelo grupo: 
Eu acabei escolhendo trabalhar com o desafio de Falhas de Conexão com Banco de Dados: automatizar a detecção e recuperação de falhas de conexão com bancos de dados, garantindo alta disponibilidade e notificação imediata da equipe técnica em caso de incidentes. 

O fluxo automatizado monitora periodicamente a disponibilidade do banco de dados e, ao detectar uma falha, dispara ações de recuperação e envia alertas automáticos via e-mail, tudo sem escrever uma linha de código.

---

## 🖥️ Protótipo

- Veja o diagrama do fluxo automatizado em /docs/prototipo.png
- O protótipo foi construído na plataforma Make (ex-Integromat)
- Como funciona:
Um agendador (Schedule) aciona o fluxo a cada 5 minutos.
Um módulo HTTP Request tenta se conectar ao endpoint do banco de dados.
Um Router avalia o resultado:

✅ Conexão bem-sucedida → registra log de sucesso em uma planilha Google Sheets.
❌ Falha detectada → dispara um e-mail de alerta para a equipe e tenta uma reconexão automática após 30 segundos.


Se a reconexão falhar novamente, um segundo e-mail de escalonamento é enviado ao responsável técnico.

> Os arquivos de imagem e documentação estão na pasta /docs.

## ⚙️ Plataforma Utilizada

- Make (ex-Integromat) — https://www.make.com
- Justificativa da escolha:
O Make foi escolhido por ser uma plataforma 100% no-code com interface visual intuitiva de arrastar e soltar. Possui plano gratuito robusto para prototipagem, ampla biblioteca de integrações nativas como: (Google Sheets, Gmail, Slack, etc), e suporte a lógica condicional avançada por meio de Routers e Filters permitindo simular cenários reais de falha e recuperação.

## ✅ Vantagens Identificadas

1- Prototipagem rápida: O fluxo completo foi montado em poucos dias.
2- Integração simples: Conexão nativa com Gmail, Google Sheets e requisições HTTP sem configuração de servidores.
3- Automação de processos: O monitoramento roda de forma autônoma a cada 5 minutos, eliminando necessidade de intervenção manual.
4- Visualização clara do fluxo: O canvas visual do Make facilita a compreensão do processo por toda a equipe, inclusive membros não técnicos.
5- Baixo custo: O plano gratuito do Make suporta até 1.000 operações/mês, suficiente para um protótipo funcional.

## ⚠️ Limitações Encontradas

1- Customização limitada: Não é possível implementar lógicas muito complexas de retry com backoff exponencial sem workarounds criativos.
2- Dependência da plataforma: O fluxo fica hospedado nos servidores do Make; uma instabilidade na plataforma impacta o monitoramento.
3- Risco de lock-in tecnológico: Migrar o fluxo para outra ferramenta exigiria reconstrução completa, pois o formato é proprietário.
4- Limitação de operações no plano gratuito: Em produção real, o volume de verificações poderia exceder o limite do plano free rapidamente.

## 📚 Reflexão Crítica

Para superar a limitação de customização do retry, utilizei o módulo Sleep do Make combinado com um segundo Router, simulando um mecanismo de tentativa de reconexão com atraso. Essa solução mostrou que, mesmo dentro das limitações no-code, é possível aproximar o comportamento de soluções profissionais.
A experiência reforçou que ferramentas no-code são excelentes para validar ideias rapidamente, mas projetos de produção críticos podem exigir complementação com código para cenários mais complexos.

## 👥 Colaboração

Como fiz sozinho, acabei sendo o responsável por 95% do projeto, pois pedi um auxílio de um conhecido.

## 📝 Registro da Aula

Data: **11/05/2026**  

Atividade: Discussão crítica + mini-projeto de aplicação  

Local: Laboratório de informática / Quadro branco  

Professor(a): Kadidja Valéria  

## 🚀 Próximos Passos

1- Integração com Slack: Adicionar notificação via canal do Slack da equipe além do e-mail.
2- Dashboard de monitoramento: Criar um painel no Google Sheets com histórico de falhas e tempo médio de recuperação.
3- Aumento da frequência: Reduzir o intervalo de verificação para 1 minuto no plano pago.
4- Evolução para o Projeto Final: Expandir o monitoramento para múltiplos bancos de dados e integrar com uma ferramenta de IA (como o Claude API) para análise automática do padrão de 5-
falhas e sugestão de soluções.
