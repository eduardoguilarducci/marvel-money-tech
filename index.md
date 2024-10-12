# MarvelMoney Tech docs

Padrões de Arquitetura
O time decidiu usar uma arquitetura 'mista', baseada principalmente na Arquitetura Monolítica.
Porém, por conta das necessidades de comunicação assíncrona relevantes para o negócio, como Invoycee e PJBank, esta arquitetura também terá uma etapa dos processos usando uma Arquitetura Orientada a Eventos. (EDA).

Arquitetura Monolítica

Foi escolhida, por prover dentre todas as arquiteturas avaliadas a melhor custo-benefício e também ter aderência como atual conhecimento técnico do time da MarvelMoney.
Pelo time técnico ser pequeno, usar uma arquitetura mais simples, que condensa todo conhecimento de código e regras de negócios em um único lugar será bastante vantajoso para o time.
Além disso, como é um projeto sem grande escala de transações no momento, e todos os componentes ainda terão um uso de carga similar, ainda não se tinha maturidade e/ou indicadores que justificassem uma arquitetura mais moderna, como uma Arquitetura de MicroServiços.
Desta forma, foram documentados os Prós e Contras dessa escolha:

Benefícios:

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
