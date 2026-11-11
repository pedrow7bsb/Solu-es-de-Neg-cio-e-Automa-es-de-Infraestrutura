# Solu-es-de-Neg-cio-e-Automa-es-de-Infraestrutura
Construção de fluxos de trabalho e agentes de IA para eliminar tarefas manuais e otimizar operações no setor de TI

🏢 **Gestão Automatizada de Ativos e Identidade (GLPI + Active Directory):**

**Resumo Executivo:**
Integração de infraestrutura implementada no 7°CTA para unificar o gerenciamento de parque tecnológico e gestão de identidades. A solução orquestra o Active Directory e o GLPI para automatizar o rastreamento de hardware, otimizar fluxos de onboarding/offboarding de colaboradores e centralizar a telemetria de segurança em um ambiente de rede com rigorosos requisitos de acesso militar.

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

- ⏳ **~48 Horas Economizadas por Ciclo de Auditoria:**
  O mapeamento do parque tecnológico (estimado em 200 máquinas) exigia aproximadamente 50 horas de trabalho manual para verificação de hardware, patrimônio e seção. Hoje, a mesma verificação é feita gerando um relatório no GLPI em menos de 5 minutos, liberando a equipe de TI para tarefas analíticas.

- 🛡️ **Prevenção e Migração Ágil (Windows 11):**
  Através dos filtros de software do GLPI, foi possível identificar instantaneamente todos os terminais rodando Windows 10. Isso permitiu o planejamento e a execução de uma estratégia de migração antecipada para o Windows 11 antes do fim do suporte oficial em 2026, mitigando riscos de segurança da informação.

- 💰 **Otimização de Orçamento e Remanejamento:**
  A capacidade de cruzar a "Seção", "Nome do Usuário" e "Hardware" viabilizou o remanejamento estratégico de ativos. Máquinas ociosas de alta performance foram redirecionadas para usuários com necessidades gráficas ou de processamento intensivo, evitando aquisições desnecessárias e fundamentando estudos técnicos para novas licitações.

- 🔒 **Conformidade de Segurança:**
  Geração de relatórios programados para auditar painéis de controle e identificar máquinas ativas na rede que estejam com o serviço de antivírus desabilitado ou desatualizado.

🚀 **Próximos Passos (Roadmap):**

**ITSM e Service Desk Integrado:**
Evolução do portal atual para englobar a abertura e o roteamento inteligente de chamados de suporte técnico, utilizando a base de usuários do AD e vinculando automaticamente os tickets ao hardware inventariado do solicitante.

**Deploy Automatizado (Zero-Touch):**
Finalização dos scripts de implantação para que a instalação do agente GLPI ocorra de forma automatizada via GPO (Group Policy Object) no momento em que a máquina ingressa no domínio.
