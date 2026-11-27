# Documentação de Testes — nassauTickets

## 1. Objetivo

Documentar os testes funcionais do sistema de Controle de Atendimento para um Laboratório de Análises Clínicas, verificando o funcionamento dos principais módulos e suas regras de negócio.

## 2. Ambiente de Testes

- Sistema: nassauTickets
- Navegador: Google Chrome
- Interface: Aplicação Web
- Módulos avaliados: Totem, Painel, Atendente e Gestor.

## 3. Casos de Teste

### CT01 — Emissão de Senhas (Totem)

**Procedimento:**
1. Acessar a rota `/totem`.
2. Selecionar a opção de emissão de senha.
3. Verificar a geração da senha.
4. Conferir o tipo e a numeração gerada.

**Resultado esperado:** O sistema deve emitir uma senha com identificação e numeração conforme o padrão estabelecido.

### CT02 — Priorização da Fila

**Procedimento:**
1. Emitir senhas dos tipos SP, SE e SG.
2. Acompanhar a ordem de atendimento.
3. Verificar a alternância entre as categorias.

**Resultado esperado:** A fila deve respeitar as regras de prioridade e alternância definidas no sistema.

### CT03 — Painel de Chamadas

**Procedimento:**
1. Acessar a rota `/painel`.
2. Realizar uma chamada pelo terminal do atendente.
3. Observar a atualização do painel.
4. Verificar a reprodução do áudio.

**Resultado esperado:** O painel deve apresentar a senha chamada e reproduzir o aviso sonoro.

### CT04 — Operações do Atendente

**Procedimento:**
1. Acessar a rota `/atendente`.
2. Realizar login.
3. Chamar a próxima senha.
4. Iniciar um atendimento.
5. Finalizar o atendimento.
6. Verificar a opção de registrar não comparecimento.

**Resultado esperado:** O sistema deve permitir as operações do atendente e atualizar o estado das senhas corretamente.

### CT05 — Relatórios do Gestor

**Procedimento:**
1. Acessar a rota `/gestor`.
2. Consultar os relatórios disponíveis.
3. Verificar os indicadores de atendimento.
4. Testar a exportação dos dados em CSV.

**Resultado esperado:** O gestor deve conseguir consultar os indicadores, relatórios e registros de auditoria disponíveis.

## 4. Registro dos Resultados

Os resultados de cada caso de teste devem ser registrados após a execução, utilizando os seguintes status:

- Aprovado: comportamento esperado confirmado.
- Reprovado: comportamento diferente do esperado.
- Pendente: teste ainda não executado.

## 5. Considerações Finais

Os testes têm como finalidade verificar a funcionalidade dos módulos, a aplicação das regras de negócio e a integração entre as interfaces do sistema.

A documentação deverá ser atualizada conforme os testes forem executados e seus resultados observados.

