# Soluções de Negócio e Automações de Infraestrutura
Construção de fluxos de trabalho e agentes de IA para eliminar tarefas manuais e otimizar operações no setor de TI

🏢 **Gestão Automatizada de Ativos e Identidade (GLPI + Active Directory):**

**Resumo Executivo:**
Integração de infraestrutura implementada em uma diretoria administrativa do Exército para unificar o gerenciamento de parque tecnológico e gestão de identidades. A solução orquestra o Active Directory e o GLPI para automatizar o rastreamento de hardware, otimizar fluxos de onboarding/offboarding de colaboradores e centralizar a telemetria de segurança em um ambiente de rede com rigorosos requisitos de acesso militar.

📊 **Dashboard Funcional e Visão Macro:**
O projeto culminou na criação de um painel de controle interativo que elimina a necessidade de planilhas manuais. Atualmente, o sistema monitora em tempo real 81 computadores, 157 monitores e 2 impressoras. A categorização granular permite visualizar instantaneamente a distribuição por fabricante (com predominância de 67 máquinas da Dell Inc.) e modelos específicos, destacando a alocação de 44 estações do modelo Precision e 52 monitores DELL P2319H.

<img width="1590" height="613" alt="image" src="https://github.com/user-attachments/assets/b73a5fd5-66fd-4505-8358-598765487346" />




🚩**O Desafio Operacional (Antes):**
Devido às restrições de segurança do domínio militar, o controle da infraestrutura de TI da diretoria dependia de auditorias manuais. O processo apresentava gargalos críticos de produtividade:

- **Levantamento Físico de Hardware**
  Para realizar qualquer estudo de atualização ou remanejamento de máquinas, os técnicos precisavam ir fisicamente de mesa em mesa para documentar configurações de CPU, RAM, patrimônio e versão do sistema operacional (cerca de 15 minutos gastos por estação).

- **Gestão de Ciclo de Vida Lenta:**
  A identificação de sistemas legados ou vulneráveis (sem antivírus ativo) era baseada em planilhas descentralizadas e suscetíveis a falhas humanas.

- **Onboarding Manual:**
  A associação de qual colaborador utilizava qual computador dependia de registros estáticos que ficavam rapidamente desatualizados em cenários de transferências internas de seção.

💡 **A Arquitetura da Solução:**
Foi estabelecido um processo padronizado conectando os computadores físicos ao banco de dados do GLPI, com metadados alimentados dinamicamente pelo Active Directory:

- **Sincronização de Identidade (AD):**
  Configuração de integração direta para puxar o nome do usuário logado na rede militar e vinculá-lo automaticamente ao inventário da máquina física.

- **Autenticação Centralizada:**
  Implementação de login via Active Directory no GLPI, garantindo que os acessos sigam as mesmas políticas de segurança e senhas da rede militar.

- **Telemetria de Ativos:**
  Instalação de agentes locais configurados com o IP do servidor de inventário para coleta contínua de telemetria de hardware e software (com script de automação de deploy em fase de desenvolvimento).

📈 **Impacto de Negócios e Horas Economizadas:**
A transformação dos dados em um dashboard centralizado permitiu consultas em tempo real, gerando resultados operacionais imediatos:

- ⏳ **~10 Horas Economizadas por Ciclo de Auditoria:**
  O mapeamento do parque tecnológico exigia horas de trabalho manual para verificação de patrimônio e seção. Hoje, a verificação do inventário e a contagem de modelos específicos é feita visualmente no painel em segundos, liberando a equipe para tarefas analíticas e HelpDesk.

- 🛡️ **Prevenção e Migração Ágil (Windows 11):**
  Através dos filtros de software do GLPI, foi possível identificar instantaneamente todos os terminais rodando Windows 10. Isso permitiu o planejamento e a execução de uma estratégia de migração antecipada para o Windows 11 antes do fim do suporte oficial em 2026, mitigando riscos.

- 💰 **Otimização de Orçamento e Remanejamento:**
  A capacidade de cruzar a "Seção", "Nome do Usuário" e o "Modelo do Computador" (ex: mapeando as workstations Precision de alta performance) viabilizou o remanejamento estratégico. Máquinas ociosas foram redirecionadas para usuários com necessidades gráficas, evitando aquisições desnecessárias

- 🔒 **Conformidade de Segurança:**
  Geração de relatórios programados para auditar painéis de controle e identificar máquinas ativas na rede que estejam com o serviço de antivírus desabilitado ou desatualizado.

🚀 **Próximos Passos (Roadmap):**

**ITSM e Service Desk Integrado:**
Evolução do portal atual para englobar a abertura e o roteamento inteligente de chamados de suporte técnico, utilizando a base de usuários do AD e vinculando automaticamente os tickets ao hardware inventariado do solicitante.

**Deploy Automatizado (Zero-Touch):**
Finalização dos scripts de implantação para que a instalação do agente GLPI ocorra de forma automatizada via GPO (Group Policy Object) no momento em que a máquina ingressa no domínio.
