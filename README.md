# gerencia-Azure
Conceitos e gerenciamento de máquinas virtuais no Azure

Conceitos Fundamentais do Azure
- Computação em Nuvem: Azure é uma plataforma de cloud computing que oferece serviços sob demanda como servidores,
- armazenamento, bancos de dados, redes, inteligência artificial e muito mais.
- 
- Modelos de Serviço:
- IaaS (Infraestrutura como Serviço): Você gerencia VMs, redes e armazenamento.
- PaaS (Plataforma como Serviço): Ideal para desenvolvedores que querem focar no código sem se preocupar com infraestrutura.
- SaaS (Software como Serviço): Aplicações completas hospedadas na nuvem (como o Microsoft 365).

- Regiões e Zonas de Disponibilidade: Azure está presente em mais de 60 regiões globais, com zonas redundantes para alta disponibilidade.

 Criação de Máquinas Virtuais (VMs)
As VMs do Azure são um dos serviços mais usados. Elas permitem executar sistemas operacionais como Windows ou Linux na nuvem.
Passos para criar uma VM:
- Escolha a região e o grupo de recursos.
- Selecione a imagem do sistema operacional (ex: Ubuntu, Windows Server).
- Defina o tamanho da VM (CPU, RAM).
- Configure autenticação (senha ou chave SSH).
- Configure rede virtual, disco e monitoramento.
- Revise e crie.

Pontos de atenção:
- Escolha o tamanho da VM com base na carga de trabalho.
- Use tags para organização e controle de custos.
- Ative backup e monitoramento com Azure Monitor.
- Considere o uso de reservas ou instâncias Spot para economizar.

Principais Serviços do Azure
| Categoria                  | Serviços                                                                              | 
| Computação                 | Azure Virtual Machines, Azure Kubernetes Service (AKS), Azure Functions, App Services | 
| Armazenamento              | Blob Storage, File Storage, Disk Storage, Archive Storage                             | 
| Banco de Dados             | Azure SQL Database, Cosmos DB, PostgreSQL, MySQL, Redis Cache                         | 
| Rede                       | Virtual Network, Load Balancer, Application Gateway, ExpressRoute                     | 
| Segurança                  | Azure Active Directory, Key Vault, Defender for Cloud, Firewall                       | 
| DevOps                     | Azure DevOps, GitHub Actions, Azure Pipelines                                         | 
| IA e Machine Learning      | Azure Cognitive Services, Azure Machine Learning, Bot Services                        | 
| Gerenciamento e Governança | Azure Monitor, Azure Policy, Cost Management, Azure Arc                               | 
| Migração                   | Azure Migrate, Site Recovery, Database Migration Service                              | 

Pontos de Atenção Gerais
- Custos: Use a calculadora de preços do Azure para estimar gastos.
- Segurança: Implemente políticas de acesso com RBAC e autenticação multifator.
- Compliance: Verifique se os serviços atendem às normas da sua indústria.
- Escalabilidade: Use escalonamento automático para lidar com variações de carga.
- Monitoramento: Configure alertas e dashboards com Azure Monitor e Log Analytics.

- 1. Gerenciamento de Máquinas Virtuais (VMs)
   Configurações Iniciais
- Tamanho da VM: Escolha baseado na carga de trabalho (ex: B-series para testes, D-series para produção).
- Sistema Operacional: Windows Server, Ubuntu, Red Hat, etc.
- Discos:
- OS Disk: Disco do sistema operacional.
- Data Disks: Para armazenar dados adicionais.
- Tipos: Standard HDD, Standard SSD, Premium SSD.

 Gerenciamento Diário
- Azure Portal: Interface gráfica para iniciar/parar, redimensionar, monitorar.
- Azure CLI / PowerShell: Automação de tarefas (ex: az vm start, az vm resize).
- Azure Resource Manager (ARM): Infraestrutura como código (IaC).
- Extensões de VM: Scripts de inicialização, antivírus, agentes de monitoramento.
- 
   Pontos de Atenção
- Evite redimensionar VMs em produção sem planejamento.
- Use tags para organização e controle de custos.
- Monitore o uso de CPU/RAM para evitar sobrecarga.

 2. Backup de Máquinas Virtuais
    
   Serviço Utilizado
- Azure Backup: Solução nativa para proteger VMs, bancos de dados e arquivos.

Como Funciona
- Crie um Cofre dos Serviços de Recuperação.
- Associe uma política de backup (frequência, retenção).
- Habilite o backup para a VM desejada.

Gerenciamento
- Centro de Backup: Painel centralizado para monitorar e operar backups em escala.
- Políticas: Diárias, semanais, retenção por anos.
- Restauração: Pode ser feita para a mesma VM ou nova instância.

  Segurança
- Criptografia AES-256.
- Exclusão reversível: Retenção de 14 dias após exclusão acidental.
- Autenticação multifator para operações críticas.

  Pontos de Atenção
  
- Escolha entre LRS, GRS ou ZRS para redundância de armazenamento.
- Teste periodicamente a restauração.
- Monitore o tamanho dos snapshots para evitar custos inesperados.
  
 3. Alta Disponibilidade e Recuperação de Desastres

  Componentes-Chave
- Availability Sets:
- Distribuem VMs entre domínios de falha e atualização.
- Protegem contra falhas de hardware e reinicializações simultâneas.
- Availability Zones:
- Zonas físicas separadas dentro de uma região.
- Ideal para cargas críticas (ex: bancos de dados).
- Azure Load Balancer:
- Distribui tráfego entre instâncias de VM.
- Azure Site Recovery (ASR):
- Replica VMs para outra região.
- Permite failover automático em caso de desastre.

  Pontos de Atenção
  
- Use Availability Zones para aplicações com SLA elevado.
- Combine ASR + Backup para máxima resiliência.
- Avalie RTO (tempo de recuperação) e RPO (perda de dados aceitável).

4. Monitoramento e Governança
🔍 Ferramentas
- Azure Monitor: Coleta métricas e logs.
- Log Analytics: Consulta avançada de logs.
- Azure Advisor: Sugestões de otimização.
- Azure Policy: Impõe regras de conformidade.
- Cost Management: Acompanha gastos e orçamentos.
  
  Pontos de Atenção
- Configure alertas para CPU, disco, falhas de backup.
- Use dashboards personalizados para visualização rápida.
- Automatize respostas com Azure Automation ou Logic Apps.

O que são Zonas de Disponibilidade?
As Zonas de Disponibilidade (Availability Zones) são locais físicos distintos dentro de uma mesma região do Azure. 
Cada zona é composta por um ou mais datacenters independentes, com:
- Energia elétrica própria
- Resfriamento dedicado
- Rede isolada
Essas zonas são separadas fisicamente por vários quilômetros, mas próximas o suficiente para garantir
baixa latência entre elas (menos de 2 ms).

Função de Cada Zona
Embora as zonas não tenham nomes específicos como “Zona 1”, “Zona 2”, etc., cada uma representa uma unidade isolada de falha. 
Isso significa que, se uma zona sofrer uma interrupção (queda de energia, incêndio, falha de rede), as outras continuam operando normalmente.

Tipos de suporte a zonas:
- Recursos Zonais: São implantados em uma zona específica (ex: uma VM na Zona 1).
- Recursos com Redundância de Zona: São replicados automaticamente entre várias zonas (ex: Azure SQL com redundância de zona).

 Quando Usar Cada Tipo de Zona
| Cenário                                            | Tipo de Implantação                                         | Justificativa                                       | 
| Aplicações críticas com alta disponibilidade       | Recursos com Redundância de Zona                            | Garante continuidade mesmo com falha em uma zona    | 
| Aplicações distribuídas com balanceamento de carga | Recursos Zonais + Load Balancer                             | Permite distribuir tráfego entre zonas              | 
| Ambientes de desenvolvimento/teste                 | Recursos Zonais (única zona)                                | Reduz custo sem necessidade de alta disponibilidade | 
| Bancos de dados resilientes                        | ZRS (Zone-Redundant Storage) ou SQL com redundância de zona | Protege dados contra falhas de zona                 | 


📌 Pontos de Atenção

- Nem todas as regiões do Azure oferecem zonas de disponibilidade. Verifique a lista de regiões compatíveis.
- Serviços compatíveis: Nem todos os serviços do Azure suportam redundância de zona. Consulte a documentação de cada serviço.
- Custo: Implantar recursos em múltiplas zonas pode aumentar o custo, mas oferece SLA de até 99,99% para VMs.
- Design de arquitetura: Use Load Balancer, Application Gateway e Azure Front Door para distribuir tráfego entre zonas.










