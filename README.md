# Resumo da aula

- Não podemos deifinir uma margem superior e inferior nos elementos in-line. Motivo pelo qual é importante alterarmos o display quando necessaŕio.

- Mudar um elemento que é in-line para block nem sempre é muito bom. Pq um determinado elemento in-line é assim por uma boa razão. Motivo pelo qual adicionamos a propriedade display não na âncora neste caso, mas sim no elemento <li> ([ver linha 32 do main.css](https://github.com/Filipe-vilela-felix/css-complete-guide/blob/main/main.css#L32))

- Logo em seguida, ao invés de adicionarmos o <display: block>, preferimos adicionar o <display: inline-block>. Pois assim, há uma mistura no comportamento de ambos (in-line e block). Como elemento inline, esses elementos podem ficar próximos uns dos outros, mas ainda se comportam com elementos de nível de bloco quando se trata em definir margens superior e inferior, dentre outros