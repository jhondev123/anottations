[[Tipos de Referência]]
[[Gambiarra]]

Utilidade:
Permite armazenar valores de qualquer tipo, mas seu tipo real só é resolvido em tempo de execução. Ele é útil quando se trabalha com Reflection, COM Interop, APIs dinâmicas (como JSON e XML dinâmico) e scripts, mas deve ser usado com cuidado, pois perde a verificação de tipo em tempo de compilação.

Tamanho do valor armazenado:
Depende do tipo real atribuído a ele. Como dynamic é baseado em System.Object, ele ocupa pelo menos 4 ou 8 bytes (tamanho de um ponteiro, dependendo da arquitetura), mas o valor real armazenado pode ocupar mais espaço.

⚠️ Observação: O uso excessivo de dynamic pode impactar a performance e aumentar o risco de erros em tempo de execução. Se possível, prefira var ou tipos fortemente tipados.