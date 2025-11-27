# Curso Tech Advanced Security - EDR
> Apresentador: Guillermo Marquez - MEX.

- Objetivos do curso:
  - Necessidade do EDR
  - Compreender aspectos tecnicos do Advanced Security + EDR
  - Como configurar, provisionar e navagar no EDR
 
## Teoria
### O que é o EDR e o que achei do curso?
 - **Curso**
   - Um tema muito bom, que explorou estigmas importantes da segurança digital
   - Poderia ter sido um pouco menor, conforme conversado com o pessoal, muitos concordaram que poderia ter sido um pouco menor se tivessem ido direto ao ponto
   - Mexicano e Tosses
 - **EDR = ENDPOINT DETECTION AND RESPONSE**
   - O objetivo do EDR é DETECTAR e RESPONDER a ataques, ataques avançados, que muitas vezes por outras defesas passam despercebidos mas pelo EDR existe essa INVESTIGAÇÃO e PROTEÇÃO.
   - O EDR por ser uma plataforma de segurança entre correlação de eventos combina o poder da sua proteção com a sua alta percepção de riscos a integridade dos sistema em minutos
   - Salientada no curso algo bem legal de se discutir e comparar o ANTIMALWARE x EDR como essa tabelinha descreve a nós:
---
| X | ANTIMALWARE | EDR |
|---------|----------|----------|
| FOCO  | Bloquear Ataques   | Detectar e já ter uma resposta   |
| VISIBILIDADE  | Baixa, somente os detectados   | ALTO! Mostra descritivo de todos passos   |
| RESPOSTA  | Bloqueia e Quarentena   | Isolamento, investigação, mitigação e remediação   |
---
   - Como o EDR funciona?
     - Um exemplo que foi dado no curso e eu adaptei é:
     - Um técnico acessa o sistema, faz uma consulta estranha no BD e executa algo fora do padrão; o EDR detecta, investiga a origem, bloqueia a ação e orienta como evitar novamente.
     - EDR usa técnicas de Machine Learning e IA para detectar comportamentos anormais em tempo real e agir com precisão para prevenir ataques maiores ao sistema.
     - A necessidade de EDR hoje é evidente; ataques estão mais sofisticados e só podem ser enfrentados com segurança avançada capaz de detectar, responder e conter ameaças em tempo real.
     - Regulamentos exigem que incidentes de segurança sejam relatados em até 72h, com EDR identificamos rapidamente o ataque, coletando evidências, mostrando o impacto e permitindo reportar com precisão dentro do prazo.
     - Com o EDR temos uma fragmentação precisa e um efeito em cascata para rastrear de onde veio o estigma
       - 1. **Onde começou**
       - Identifica o primeiro ponto de entrada
      
          - 2. **Como entrou**
          - Rastreia a técnica usada (vulnerabilidade, credencial,...)
      
              - 3. **Como se escondeu**
              - Detecta técnicas e processos suspeitos
      
                  - 4. **O que prejudicou**
                  - Mostra arquivos, serviços, máquinas e dados afetados
      
                      - 5. **Como espalhou**
                      - Exibe o movimento lateral e a progressão do ataque pela rede
---          
## Estrutura de Investigação e Resposta ao Incidente 
### 1. Classificação do Evento
- Analista N1 monitora os eventos e identifica atividades suspeitas na rede.
- **Com EDR**: essa etapa é automatizada (detecção e classificação em tempo real).

### 2. Priorização, Investigação e Triagem
- Analista N1 prioriza os eventos mais críticos, investiga e repassa incidentes à equipe de segurança.
- **Com EDR**: a ferramenta já correlaciona, prioriza e investiga automaticamente, eliminando grande parte do trabalho manual.

### 3. Contenção e Reparos
- Reúne dados sobre a origem do ataque, realiza a contenção, recupera e restaura os sistemas afetados.

### 4. Prevenção de Ataques Adicionais
- Identifica lacunas exploradas pelo ataque e cria medidas preventivas para bloquear futuras tentativas.

### 5. Avaliação e Auditoria
- Analisa a evolução do ataque, consolida evidências e elabora recomendações e conclusões pós-incidente.
  
## Regra 1 - 10 - 60
- O que o EDR resolve nessa regra é reduzir detecção de horas para minutos, reduz investigação de dias para minutos, gera linha do tempo completa do ataque, ajuda em tarefas que exigem tempos apertados serem reduzidas para minutos.
---
| X | DETECTAR | INVESTIGAR | RESPONDER |
|---------|---------|----------|----------|
| IDEAL  | 1 MIN  | 10 MIN   | 60 MIN |
| REALIDADE | Os tempos são dificeis de medir  | Investigação pode levar 2 a 6hrs   | 32hrs de Contenção, 120hrs recuperar dados |
| COM EDR    | Segundos–minutos     | 5–20 min  | 10–60 min (isolamento e remediação) |
---

## Prática 
- Curso também no Mod. 4 mostra bastante de como é a interface do Sistema
- Na parte de EDR como vamos habilitar?
  - LOCATARIO
    - Aba de CLIENTS
    - Clica no `...`
    - Vai na parte de Configure
    - Marcamos a opção de `ADVANCED SECURITY EDR`
  - CLIENT
    - Aba de GERENCIAMENTO
    - Planos de Proteção
    - Modificamos algum Plano
    - Ativamos o Botão EDR
- Alertas
 - Pode ser escolhido receber alertas via E-Mail, console ou ambos
 - E-mail sempre é bom mandar um e-mail teste para ver se esta chegando corretamente as informações
 - No momento que o EDR detecta um ataque ele manda um aviso via E-Mail e na Plataforma dizendo onde, o que afetou, pq ele é um suspeito, ação que foi feita e os arquivos
 - Na aba **INCIDENTES** é possível visualizar o passo a passo do que o atacante realizou, em uma linha do tempo detalhada (efeito cascata), permitindo rastrear cada ação executada ou tentada.
- Quando nenhuma ação de resposta foi tomada, o incidente aparece como **`Pendente`** (não remediado).
- Após a análise dos passos e do comportamento detectado, o incidente pode ser classificado como:
  - **Mitigado** – ação aplicada e ameaça neutralizada.
  - **Não mitigado** – ameaça detectada, mas ainda sem resposta efetiva.
  - **Falso Positivo** – o EDR detectou algo como ameaça, mas **não era** (ex.: script legítimo, rotina do sistema, ferramenta de TI).
  - **Verdadeiro Positivo** – o alerta realmente era uma ameaça ou comportamento malicioso confirmado.
