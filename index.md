# MarvelMoney Tech docs

Padrões de Arquitetura
O time decidiu usar uma arquitetura 'mista', baseada principalmente na Arquitetura Monolítica.
Porém, por conta das necessidades de comunicação assíncrona relevantes para o negócio, como Invoycee e PJBank, esta arquitetura também terá uma etapa dos processos usando uma Arquitetura Orientada a Eventos. (EDA).

Arquitetura Monolítica

Foi escolhida, por prover dentre todas as arquiteturas avaliadas a melhor custo-benefício e também ter aderência como atual conhecimento técnico do time da MarvelMoney.
Pelo time técnico ser pequeno, usar uma arquitetura mais simples, que condensa todo conhecimento de código e regras de negócios em um único lugar será bastante vantajoso para o time.
Além disso, como é um projeto sem grande escala de transações no momento, e todos os componentes ainda terão um uso de carga similar, ainda não se tinha maturidade e/ou indicadores que justificassem uma arquitetura mais moderna, como uma Arquitetura de MicroServiços.
Desta forma, foram documentados os Prós e Contras dessa escolha:

Prós:
Simplicidade: Mais fácil de desenvolver, testar e implementar, pois todos os componentes estão integrados em um único código.
Desempenho: Comunicação interna entre componentes é rápida, sem a latência de chamadas de rede.
Gerenciamento: Menor complexidade de deploy e monitoramento, pois há apenas um artefato para gerenciar.

Contras:

Escalabilidade limitada: Dificuldade em escalar componentes individualmente, exigindo escalar o sistema inteiro.

    Mitigação do Risco: Ainda sem métricas que justifiquem pensar em uma escalabilidade de componentes.

Manutenção complicada: Com o crescimento do sistema, o código pode se tornar grande e difícil de manter.

    Mitigação do Risco: Não se aplica no momento, dado que o escopo está bem definido para os próximos 17 meses.

Dependências fortes: Mudanças em uma parte podem impactar todo o sistema, aumentando o risco de bugs.

    Mitigação do Risco: Risco aceito.

Arquitetura Orientada a Eventos (EDA)

Para atender as necessidades de comunicação com sistemas externos críticos, foi definido usar o Kafka, como sistema de mensageria, e o uso de tópicos para controle das mensagens via Consumer e Subscriber.

Desta forma, a comunicação com os sistemas internos não impactará o uso e recursos da API dada a característica de retornos não síncronos da maioria das Prefeituras do país.
Desta forma, foram documentados os Prós e Contras dessa escolha:

Prós:
Desacoplamento: Componentes interagem por meio de eventos, permitindo que eles evoluam e escalem de forma independente.
Resiliência: Se um serviço falhar, outros podem continuar processando eventos, promovendo tolerância a falhas.
Processamento assíncrono: Capacidade de processar eventos em segundo plano sem bloquear operações, permitindo maior eficiência.
Contras:
Complexidade: Projetar, implementar e gerenciar sistemas orientados a eventos exige mais esforço técnico e ferramentas de monitoramento.

    Mitigação do Risco: A consultoria possui conhecimento e dará suporte à operação.

Garantias de consistência: Manter a consistência entre diferentes serviços pode ser desafiador e requer mecanismos extras, como transações distribuídas ou compensações.
Mitigação do Risco: Manter a simplicidade como primeira escolha.
Monitoramento e Debug: A depuração e o monitoramento são mais complicados devido à natureza assíncrona e distribuída dos eventos.
Mitigação do Risco: Risco aceito
