## UC01 — Realizar Cadastro de Aluno
### Ator Principal
Recepcionista
### Objetivo
Permitir cadastrar novos alunos com dados pessoais e vincular a um plano contratado.
### Pré-condições
O usuário deve estar logado no sistema com perfil de Recepcionista ou Gerente.
### Pós-condições
Registro do aluno salvo com sucesso no banco de dados.
ID único do aluno gerado.
### Fluxo Principal
O usuário acessa a funcionalidade "Novo Aluno".
O sistema exibe o formulário de cadastro.
O usuário preenche os dados pessoais, contato e endereço.
O usuário seleciona o plano contratado.
O sistema valida as informações e salva os dados.
### Fluxos Alternativos
A1 — Dados incompletos: O sistema exibe uma mensagem de erro solicitando o preenchimento dos campos obrigatórios.
### RF Relacionados
RF01 — Cadastro de Alunos
### RNF Relacionados
RNF02 — Segurança
RNF04 — Usabilidade
### RN Relacionadas
RN06 — Acesso restrito por perfil

<img width="681" height="788" alt="Captura de tela 2026-03-18 215304" src="https://github.com/user-attachments/assets/e417795c-32e0-4b56-b70e-ace2498fb31c" />


## UC02 — Gerenciar Planos
### Ator Principal
Gerente
### Objetivo
Permitir a criação, edição, ativação e desativação de tipos de planos na academia.
### Pré-condições
O usuário deve estar logado no sistema com perfil de Gerente.
### Pós-condições
Lista de planos atualizada e disponível para novas matrículas.
### Fluxo Principal
O usuário acessa o menu "Planos".
O sistema lista todos os planos existentes.
O usuário seleciona "Novo Plano" (ou editar) e preenche os dados.
O usuário confirma a operação.
O sistema salva as alterações e atualiza a lista.
### Fluxos Alternativos
A1 — Nome do plano duplicado: O sistema impede a gravação e exibe mensagem de que o nome já existe.
### RF Relacionados
RF02 — Gerenciamento de Planos
### RNF Relacionados
RNF04 — Usabilidade
### RN Relacionadas
RN06 — Acesso restrito por perfil

<img width="910" height="656" alt="Captura de tela 2026-03-18 215355" src="https://github.com/user-attachments/assets/af3379c7-e745-46ed-a2fd-9fd8eff1ff50" />


## UC03 — Registrar Pagamentos
### Ator Principal
Recepcionista / Aluno
### Objetivo
Registrar pagamentos (dinheiro, cartão, PIX) ou gerar cobranças online.
### Pré-condições
Existência de uma fatura ou mensalidade pendente vinculada a um aluno.
### Pós-condições
Mensalidade atualizada para "Paga" ou link de cobrança gerado.
### Fluxo Principal
O usuário seleciona a mensalidade em aberto.
O usuário escolhe o método de pagamento.
O sistema apresenta o valor integral da mensalidade.
O sistema processa o pagamento.
O sistema atualiza o status para "Pago" e gera o comprovante.
### Fluxos Alternativos
A1 — Pagamento Online: O sistema gera o boleto/cartão e envia o link ao aluno, mantendo o status "Pendente" até a compensação.
### RF Relacionados
RF03 — Controle de Pagamentos
RF04 — Regularidade do Aluno
### RNF Relacionados
RNF02 — Segurança
### RN Relacionadas
RN04 — Pagamento parcial
RN07 — Atualização automática da regularidade

<img width="715" height="551" alt="Captura de tela 2026-03-18 215404" src="https://github.com/user-attachments/assets/2fffc0e0-c1b4-46d1-b569-2756ee9cfab1" />


## UC04 — Regularidade do Aluno
### Ator Principal
Sistema
### Objetivo
Verificar automaticamente se a mensalidade do aluno está em dia.
### Pré-condições
Alunos cadastrados no sistema com datas de vencimento configuradas.
### Pós-condições
Status do aluno (Regular ou Inadimplente) atualizado no banco de dados.
### Fluxo Principal
O sistema inicia a varredura diária de verificações.
O sistema compara a data atual com a data de vencimento da mensalidade de cada aluno.
O sistema atualiza o status de acesso para "Regular" ou "Inadimplente".
O sistema encerra a rotina.
### Fluxos Alternativos
A1 — Aluno recém-matriculado: O sistema ignora a verificação se o prazo do primeiro pagamento ainda não tiver expirado.
### RF Relacionados
RF04 — Regularidade do Aluno
### RNF Relacionados
RNF01 — Disponibilidade
RNF03 — Performance
### RN Relacionadas
RN01 — Bloqueio por inadimplência

<img width="712" height="565" alt="Captura de tela 2026-03-18 215413" src="https://github.com/user-attachments/assets/7e43b95c-15f5-4b9b-bd9e-d9f5ae76a9f7" />


## UC05 — Controle de Acesso
### Ator Principal
Aluno
### Objetivo
Validar a entrada do aluno na academia integrando o sistema à catraca via RFID.
### Pré-condições
Catraca conectada ao sistema via API e aluno portando cartão/tag RFID.
### Pós-condições
Liberação da catraca e registro da entrada no histórico.
### Fluxo Principal
O aluno aproxima o RFID na catraca.
A catraca envia o ID para o sistema.
O sistema verifica o status de regularidade do aluno.
O sistema confirma que o status é "Regular".
O sistema envia o comando e a catraca é destravada.
### Fluxos Alternativos
A1 — Aluno Inadimplente: O sistema identifica o status "Inadimplente", retorna comando de bloqueio e exibe mensagem na catraca.
### RF Relacionados
RF05 — Controle de Acesso
### RNF Relacionados
RNF03 — Performance
RNF06 — Integração
### RN Relacionadas
RN01 — Bloqueio por inadimplência

<img width="923" height="524" alt="Captura de tela 2026-03-18 215427" src="https://github.com/user-attachments/assets/290a26cf-ccb0-4be8-aedb-449930b93f7c" />


## UC06 — Agendamento de Aulas
### Ator Principal
Aluno
### Objetivo
Permitir ao aluno visualizar horários e reservar vagas nas aulas disponíveis.
### Pré-condições
O aluno deve estar logado e a grade de aulas cadastrada.
### Pós-condições
Vaga reservada e limite da turma atualizado.
### Fluxo Principal
O aluno acessa a grade de horários.
O aluno seleciona a aula desejada.
O sistema verifica a disponibilidade de vagas.
O sistema confirma a reserva e exibe os detalhes ao aluno.
O sistema subtrai a vaga do limite da turma.
### Fluxos Alternativos
A1 — Turma Lotada: O sistema exibe mensagem de limite atingido e oferece opção de fila de espera.
### RF Relacionados
RF06 — Agendamento de Aulas
### RNF Relacionados
RNF04 — Usabilidade
### RN Relacionadas
RN02 — Limite de vagas

<img width="785" height="661" alt="Captura de tela 2026-03-18 215437" src="https://github.com/user-attachments/assets/2ca47965-0ae3-4059-b022-6b5b7e896ab6" />


## UC07 — Lista de Presença
### Ator Principal
Instrutor
### Objetivo
Permitir que o instrutor registre a presença física dos alunos na aula agendada.
### Pré-condições
Usuário logado como Instrutor e aula prestes a iniciar ou em andamento.
### Pós-condições
Histórico de frequência da turma atualizado.
### Fluxo Principal
O instrutor acessa o menu da aula no dia vigente.
O sistema lista os alunos com agendamento confirmado.
O instrutor marca a presença dos alunos que compareceram.
O sistema salva a lista atualizada.
### Fluxos Alternativos
A1 — Aluno sem agendamento: O instrutor adiciona manualmente o aluno na lista, caso haja vaga física no ambiente da aula.
### RF Relacionados
RF07 — Lista de Presença
### RNF Relacionados
RNF04 — Usabilidade
### RN Relacionadas
RN06 — Acesso restrito por perfil

<img width="753" height="751" alt="Captura de tela 2026-03-18 215444" src="https://github.com/user-attachments/assets/283e9ca1-f019-4eeb-a65c-0a02443fdcde" />


## UC08 — Avaliação Física
### Ator Principal
Instrutor
### Objetivo
Registrar métricas corporais e anexar arquivos da evolução do aluno.
### Pré-condições
Aluno com cadastro ativo e usuário logado com perfil de Instrutor.
### Pós-condições
Avaliação vinculada ao histórico do aluno no sistema.
### Fluxo Principal
O instrutor seleciona o perfil do aluno.
O sistema valida a regularidade do aluno.
O instrutor preenche os dados técnicos da avaliação.
O instrutor anexa arquivos complementares (opcional).
O sistema salva a avaliação física no histórico.
### Fluxos Alternativos
A1 — Aluno irregular: O sistema bloqueia a tela de avaliação e avisa que o aluno não cumpre os requisitos de regularidade.
### RF Relacionados
RF08 — Avaliação Física
### RNF Relacionados
RNF02 — Segurança
### RN Relacionadas
RN05 — Avaliação física
RN06 — Acesso restrito por perfil

<img width="796" height="710" alt="Captura de tela 2026-03-18 215456" src="https://github.com/user-attachments/assets/ecc6f2ec-7896-43b8-a540-7b6e07194a9a" />

## UC09 — Relatórios Gerenciais
### Ator Principal
Gerente
### Objetivo
Emitir relatórios estratégicos de inadimplência, alunos ativos, acessos e ocupação.
### Pré-condições
Usuário logado com permissão de Gerente.
### Pós-condições
Relatório gerado em tela com opção de exportação.
### Fluxo Principal
O gerente acessa a área de relatórios.
O gerente seleciona o tipo de relatório e o período desejado.
O sistema compila as informações no banco de dados.
O sistema exibe os dados processados na interface.
### Fluxos Alternativos
A1 — Sem dados no período: O sistema exibe a mensagem informando que não há registros para os filtros selecionados.
### RF Relacionados
RF09 — Relatórios Gerenciais
### RNF Relacionados
RNF03 — Performance
### RN Relacionadas
RN06 — Acesso restrito por perfil

<img width="678" height="540" alt="Captura de tela 2026-03-18 215506" src="https://github.com/user-attachments/assets/a5b808e6-ce61-48fa-ba11-6f0525a4d615" />

## UC10 — Enviar Notificações
### Ator Principal
Sistema
### Objetivo
Enviar avisos automáticos sobre vencimentos, agendamentos e novas avaliações.
### Pré-condições
Gatilho do evento acionado (ex: data de vencimento se aproximando).
### Pós-condições
Mensagem enviada ao aluno e registrada no log.
### Fluxo Principal
O sistema detecta o evento programado.
O sistema identifica o aluno e seu contato.
O sistema compõe a mensagem com o template correspondente.
O sistema dispara a notificação (e-mail/SMS/Push).
O sistema registra o sucesso no log de envio.
### Fluxos Alternativos
A1 — Falha no envio: O sistema registra o erro no log e faz uma nova tentativa automática em ciclo posterior.
### RF Relacionados
RF10 — Notificações
### RNF Relacionados
RNF01 — Disponibilidade
### RN Relacionadas
(Nenhuma específica aplicável)

<img width="467" height="543" alt="Captura de tela 2026-03-18 215519" src="https://github.com/user-attachments/assets/8ee2d658-91b3-42eb-9299-09c62dae55f4" />


## UC11 — Bloqueio por inadimplência 

### Ator Principal
Aluno

### Objetivo
Bloqueiar o acesso do aluno

### Pré-condições
- Aluno deve estar com a mensalidade vencida há mais de 5 dias.
### Pós-condições
- O aluno é impedido de entrar na academia

### Fluxo Principal
1. O aluno chega na academia.
2. O sistema valida as credenciais.
3. O sistema verifica se o aluno está com a mensalidade em dia.

### Fluxos Alternativos
- **A1 — Em atraso :**  
  O sistema exibe uma mensagem de que não é possível entrar na academia.

- **A2 — Em dia :**  
  O sistema exibe uma mensagem de boas vindas.
  
### RF Relacionados
- RF04 — Regularidade do Aluno

### RN Relacionadas
- RN01 — Bloqueio por inadimplência

<img width="656" height="482" alt="11" src="https://github.com/user-attachments/assets/e14eec22-5e9a-4fd5-ac6f-293675710239" />


## UC12 — Limite de vagas
### Ator Principal
Aluno

### Objetivo
Permitir que o aluno possa se cadastrar em uma aula.

### Pré-condições
- deve haver aulas cadastrada no sistema.

### Pós-condições
- Reserva de vaga confirmada.
- O número de vagas na aula é modificado

### Fluxo Principal

1- O aluno seleciona a aula e o horário desejado.
2- O sistema verifica a disponibilidade de vagas.
3- O sistema registra o agendamento para o aluno.
4- O sistema confirma o sucesso do agendamento e exibe os detalhes.

### Fluxos Alternativos
- **A1 — Turma lotada:**  
  O sistema exibe mensagem de que a turma não tem mais vagas disponíveis.

- **A2 — Choque de horário:**  
  O sistema identifica que o aluno já tem outra aula nesse mesmo horário.

### RN Relacionadas
RN02 — Limite de vagas

<img width="664" height="434" alt="12" src="https://github.com/user-attachments/assets/992818f6-de33-4920-989b-1102a9f6ddd4" />


## UC13 — Cancelamento de agendamento

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno cancele uma reserva.

### Pré-condições
- O aluno deve cancelar pelo menos 1 hora antes do inicio da aula.

### Pós-condições
- Aula cancelada.

### Fluxo Principal
1. O usuário cancela a aula.
2. O sistema muda o número de vagas da aula.

### Fluxos Alternativos
- **A1 — Depois de uma hora:**  
  O sistema exibe mensagem de erro falando que o aluno não pode mais cancelar a aula.

### RN Relacionadas
RN03 — Cancelamento de agendamento

<img width="643" height="485" alt="13" src="https://github.com/user-attachments/assets/294e56d8-181a-4acc-b695-064ced49efd6" />


## UC14 — Pagamento parcial

### Ator Principal
aluno

### Objetivo
Não permitir o parcelamento da mensalidade.

### Pré-condições
- Existência de uma fatura ou mensalidade em aberto.

### Pós-condições
- Mensalidade marcada como "Paga".
- Comprovante de transação gerado.

### Fluxo Principal
1. O usuário visualiza a mensalidade em aberto.
2. O usuário seleciona o método de pagamento.
3. O sistema apresenta o valor total da mensalidade.
4. O usuário confirma o pagamento do valor integral.
5. O sistema processa a transação com a operadora financeira.
6. O sistema confirma o recebimento e atualiza o status para "Pago".

### Fluxos Alternativos
- **A1 — Tentativa de Pagamento Parcial :**  
  O sistema bloqueia a operação e exibe mensagem: "Não é permitido o pagamento parcial. O valor deve ser quitado integralmente."

- **A2 — Pagamento Rejeitado pela Operadora::**  
  O sistema notifica o usuário e mantém a mensalidade como "Pendente".
  
### RF Relacionados
- RF03 — Controle de Pagamentos

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN04 — Pagamento parcial

<img width="656" height="559" alt="14" src="https://github.com/user-attachments/assets/4c0f5bae-e1dd-496f-be4a-a7ecc64b5eb6" />


## UC15 — Avaliação física

### Ator Principal
Aluno/instrutor

### Objetivo
Permitir que o usuário faça uma avaliação fisica.

### Pré-condições
- O aluno deve possuir cadastro ativo.
- O aluno deve estar frequentando a academia a pelo menos 4 dias na semana

### Pós-condições
- O aluno tem sua condição avaliada por um instrutor.

### Fluxo Principal
1. O sistema verifica o status do aluno (Ativo e Regular).
2. O sistema libera o formulário de coleta de dados.
3. O instrutor insere as informações técnicas da avaliação.
4. O sistema disponibiliza o resultado para consulta do aluno e do instrutor.

### Fluxos Alternativos
- **A1 — Aluno inativo ou irregular:**  
  O sistema bloqueia a abertura do formulário.

### RF Relacionados
- RF07 — Lista de Presença
- RF08 — Avaliação Física

### RN Relacionadas
- RN05 — Avaliação física

<img width="657" height="465" alt="15" src="https://github.com/user-attachments/assets/c2b95499-d02d-4fa6-b715-96c65f67941b" />


## UC16 — Acesso restrito por perfil

### Ator Principal
Recepcionista, Instrutor ou Gerente

### Objetivo
Garantir que cada colaborador acesse apenas as funcionalidades permitidas para o seu cargo.

### Pré-condições
- Usuário deve estar autenticado
- O perfil do usuário deve estar previamente configurado no banco de dados.

### Pós-condições
- Acesso concedido apenas às áreas autorizadas.

### Fluxo Principal
1. O usuário realiza o login no sistema.
2. O sistema identifica o perfil vinculado ao usuário .
3. O sistema renderiza exibindo apenas os módulos permitidos.
4. O usuário seleciona a funcionalidade desejada.
5. O sistema valida a permissão .

### Fluxos Alternativos
- **A1 —Alteração de perfil em tempo real:**  
  O Gerente altera o perfil de um colaborador de "Instrutor" para "Gerente".

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN06 — Acesso restrito por perfil

<img width="521" height="859" alt="16" src="https://github.com/user-attachments/assets/b96ed323-8a54-4167-86f8-9210743c6005" />


## UC17 — Atualização automática da regularidade

### Ator Principal
Aluno

### Objetivo
Atualizar o pagamento imediatamente.

### Pré-condições
- O aluno deve fazer o pagamento.

### Pós-condições
- O sistema deve reconhecer o pagamento.
- O sistema deve atualizar imediatamente a situação do aluno.

### Fluxo Principal
1. O Aluno faz o pagamento.
2. O sistema valida o pagamento.
3. O sistema atualiza a situação do aluno.

### Fluxos Alternativos
- **A1 — Estorno ou Cancelamento de Pagamento:**  
  O sistema reverte a situação do aluno para "Irregular" ou "Inadimplente".

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN07 — Atualização automática da regularidade

<img width="570" height="565" alt="17" src="https://github.com/user-attachments/assets/831167f5-abc6-45cc-854b-b683995b6e0d" />


## UC18 — Disponibilidade

### Ator Principal
Sistema/Gerente

### Objetivo
Garantir que o sistema permaneça operacional

### Pré-condições
- O sistema deve estar em ambiente de produção.
- Ferramentas de monitoramento de servidor devem estar ativas.

### Pós-condições
- Alertas enviados em caso de queda.

### Fluxo Principal
1. O sistema monitora continuamente o status dos serviços (Banco de Dados, Servidor Web).
2. O sistema registra o tempo de atividade (uptime) em logs de performance.
3. O sistema disponibiliza para o Gerente um painel de status em tempo real.
4. Em caso de operação normal, o sistema mantém a meta de 99% .

### Fluxos Alternativos
- ** Manutenção Programada:**  
 O Gerente agenda uma janela de manutenção
 O sistema exibe um aviso prévio aos usuários sobre a indisponibilidade temporária.

### RNF Relacionados
- RNF01 — Disponibilidade

<img width="649" height="827" alt="18" src="https://github.com/user-attachments/assets/70ab3105-9516-47b6-b3ae-4686745fca0d" />


## UC19 — Segurança

### Ator Principal
Sistema 

### Objetivo
Garantir a confidencialidade das informações dos usuários e registros financeiros.

### Pré-condições
- Recebimento de dados via formulários (Cadastro, Pagamento, Avaliação).
- Conexão ativa com o banco de dados.

### Pós-condições
- Dados armazenados no banco de dados em formato ilegível
- Chaves de criptografia gerenciadas de forma segura.

### Fluxo Principal
1. O sistema recebe dados de entrada do usuário
2. O sistema identifica quais campos são classificados como "sensíveis"
3. O sistema aplica o algoritmo de criptografia
4. O sistema grava a informação criptografada no banco de dados.
5. O sistema confirma a persistência segura do dado.

### Fluxos Alternativos
- **A1 — Recuperação de Dados para Exibição:**  
  O usuário solicita a visualização de um dado sensível.
  O sistema descriptografa a informação utilizando a chave mestra.
  O sistema exibe o dado em texto claro na interface.

### RF Relacionados
- RF09 — Relatórios Gerenciais
  
### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN06 — Acesso restrito por perfil
  
<img width="509" height="833" alt="19" src="https://github.com/user-attachments/assets/2b94062b-3272-4a6f-aa40-6a155f646c09" />


## UC20 —  Performance

### Ator Principal
Sistema

### Objetivo
Garantir que as interações do usuário, especialmente as validações de acesso e regras de negócio, ocorram dentro do limite aceitável de tempo.

### Pré-condições
- sistema deve estar operacional

### Pós-condições
- Resposta entregue ao usuário em tempo hábil.

### Fluxo Principal
1. O usuário aciona uma funcionalidade
2. O sistema inicia o processamento das regras associadas
3. O sistema processa a requisição e retorna o resultado
4. O tempo total entre o clique e a resposta é de até 3 segundos

### Fluxos Alternativos
- **A1 — Timeout:**  
O processamento ultrapassa o limite técnico de segurança
O sistema interrompe a requisição para não travar
O sistema exibe a mensagem: "O sistema demorou a responder. Por favor, tente novamente em instantes."

### RNF Relacionados
- RNF03 — Performance

### RN Relacionadas
- RN07 — Atualização automática da regularidade

<img width="519" height="606" alt="20" src="https://github.com/user-attachments/assets/2eadc40c-cbc2-43ff-aec6-b1e056e42e8d" />
