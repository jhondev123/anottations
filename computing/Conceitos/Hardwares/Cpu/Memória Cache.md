
[[Hardware]]
[[Cpu]]
[[Memória RAM]]
[[Multi-Core]]
A **cache** é uma memória de **alto desempenho** que armazena dados e instruções frequentemente usados pela CPU, para evitar que ela precise buscar essas informações na memória RAM, que é mais lenta. A **cache** serve para reduzir o **gap de velocidade** entre a CPU e a RAM.

#### **Tipos de Cache:**

1. **Cache L1 (nível 1):**
    - Integrada diretamente no chip da CPU e a mais rápida, mas de menor capacidade.
    - Armazena dados e instruções de uso imediato.
2. **Cache L2 (nível 2):**
    - Um pouco maior e mais lenta do que a L1, mas ainda mais rápida que a RAM.
    - Pode ser externa ao chip da CPU ou compartilhada entre múltiplos núcleos.
3. **Cache L3 (nível 3):**
    - Compartilhada entre os núcleos de uma CPU multi-core. É maior e mais lenta, mas ainda bem mais rápida que a RAM.

#### **Impacto da Cache na Performance:**

- A cache permite que a CPU acesse **dados frequentemente usados** mais rapidamente, **reduzindo o tempo de espera** pela RAM e aumentando a eficiência do processamento.
- **Localidade temporal e espacial** são conceitos que se relacionam à eficiência da cache. Localidade temporal se refere ao acesso repetido aos mesmos dados, e localidade espacial se refere ao acesso a dados próximos entre si.