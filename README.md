# Componentes de Arquitetura do Azure
---
Este repositório contém o resumo das lições aprendidas durante o desenvolvimento do lab Construindo Arquiteturas no Azure na plataforma DIO

---
## Introdução
Neste laboratório foi apresentado como a arquitetura do Azure é composta por diversos componentes que garantem alta disponibilidade, desempenho e segurança para os recursos em nuvem. Estes componentes incluem as regiões e zonas de disponibilidade, que permitem a replicação e resiliência dos dados, e as assinaturas e grupos de recursos, que facilitam a organização e gerenciamento dos serviços. Além disso, também mostra como as regiões soberanas atendem às necessidades específicas de governos, além de conjuntos de disponibilidade que garantem a continuidade dos serviços. 

---

## Regiões
- Ao criar um recurso, especifica-se a região onde ele ficará localizado (ex.: Brazil South, East US).
- Quanto mais próxima a região do usuário, menor a latência e melhor a performance.
- Preços podem variar entre regiões devido a impostos e disponibilidade de recursos.
- Nem todos os recursos estão disponíveis em todas as regiões.
- Azure possui uma cobertura global com datacenters em diversas regiões.
- Idealmente, são três datacenters por região, com comunicação de baixa latência gerida pela Microsoft.
- Os datacenters de uma região são interligados e replicam dados automaticamente, garantindo alta disponibilidade.
- Em caso de falha total de uma região, ocorre o *Disaster Recovery*, replicando recursos essenciais em outra região.
- As regiões garantem a conformidade com leis de residência de dados e a Microsoft preserva a segurança das informações.

## Zonas de Disponibilidade
- Proporcionam proteção contra falhas ao replicar dados entre datacenters dentro da mesma região.
- Datacenters são fisicamente separados, com alimentação, resfriamento e rede independentes.
- Interligados por redes privadas de fibra ótica, garantindo baixa latência e alta performance.

## Pares de Regiões
- Cada região possui uma região par, que serve como zona secundária em casos de indisponibilidade.
- Distância mínima de 300 milhas entre regiões pares.
- Replicação pode ser automática para alguns serviços.
- Atualizações são distribuídas de forma sequencial para minimizar o tempo de inatividade.
- Prioridade na recuperação de regiões em caso de interrupções.

## Regiões Soberanas
- Azure possui duas regiões soberanas: Governamental dos EUA e Azure China.
- Regiões exclusivas, não disponíveis para clientes comuns, com foco em segurança e conformidade.
- **Serviços Governamentais dos EUA**: atendem às agências federais, estaduais e locais dos EUA.
  - Isolada das implantações regulares do Azure.
- **Azure China**: separada dos serviços tradicionais do Azure, disponível apenas para o governo chinês, garantindo conformidade com as leis locais.

## Conjuntos de Disponibilidade (*Availability Sets*)
- Composto por domínios de atualização e domínios de falha.
- **Domínios de falha** isolam recursos em racks físicos diferentes, protegendo contra falhas de hardware.
- **Domínios de atualização** garantem que atualizações de software afetem apenas parte dos recursos, minimizando o impacto.

## Recursos do Azure
- Exemplo de recursos: armazenamento, máquinas virtuais e redes.
- Importante conhecer os recursos e produtos adicionais da Microsoft, como segurança, ambientes híbridos e monitoramento.

## Grupos de Recursos
- Organizam recursos por afinidade e função para facilitar o gerenciamento.
- Um recurso pode existir em apenas um grupo, mas os recursos podem estar em diferentes regiões.
- Grupos de recursos podem ser movidos e reutilizados em diferentes projetos.
- Possível aplicar regras e políticas específicas para grupos de recursos.

## Assinaturas do Azure
- Ao criar uma conta, geralmente se tem uma assinatura associada.
- É possível adquirir mais assinaturas para diferentes finalidades (desenvolvimento, teste, produção, etc.).
- Cada assinatura tem controle de acesso e faturamento separados.
- Assinaturas podem ser criadas para diferentes grupos de trabalho para segmentar o controle de acesso.

## Grupos de Gerenciamento
- Agrupam várias assinaturas e permitem a aplicação de regras de forma centralizada.
- As condições aplicadas a um grupo de gerenciamento são herdadas pelas assinaturas associadas.

# Construindo Arquiteturas no Azure

- Para mais informações sobre a infraestrutura global da Azure:
  - [Azure Global Infrastructure](https://azure.microsoft.com/en-us/explore/global-infrastructure)
  - [Learn About Azure Regions](https://datacenters.microsoft.com)

## Regiões no Brasil
- **Brazil South (São Paulo)**: disponível para todos os clientes e parceiros, com replicação automática para os EUA.
- **Brazil Southeast (Rio de Janeiro)**: reservado para clientes que necessitam de *disaster recovery* no país, com replicação para Brazil South.

## Criando um Grupo de Recursos no Portal Azure
1. No portal, acesse "Grupos de Recursos" na barra lateral ou busque por "Grupo de Recursos".
2. Escolha a assinatura e crie um nome para o grupo (ex.: AZ-900_Lab_DIO).
3. Selecione uma região (ex.: East US 2).
4. Avance para marcações (opcional), para organizar e identificar recursos.
5. Revise e clique em "Criar".

### Gerenciando Grupos de Recursos
- **Log de Atividades**: monitora criação, exclusão e alterações.
- **IAM (Controle de Acesso)**: define permissões, sendo recomendável dar o menor acesso possível.
- **Visualizador de Recursos**: exibe os recursos criados em uma estrutura hierárquica.
- **Eventos**: permitem automação e integração entre serviços na nuvem.

## Redes Virtuais (VNet)
- Configuração de rede necessária para ambientes, como máquinas virtuais, que precisam de um IP da rede virtual criada.
