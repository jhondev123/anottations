Na unity, os scripts em geralmente herdam da classe monobehavior
* Awake(), é chamado uma vez, quando o objeto é carregado na cena
* Start(), chamado antes do primeiro frame, usado na inicialização
* Update(), Chamado a cada frame, usado para lógica em tempo real.
* FixedUpdate(), Chamado a cada atualização física, útil para cálculos com [[RigidBody]]
* OnDestroy, chamado quando um objeto é destruído