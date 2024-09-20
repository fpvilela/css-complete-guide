# Resumo das aulas

- Não podemos deifinir uma margem superior e inferior nos elementos in-line. Motivo pelo qual é importante alterarmos o display quando necessaŕio.

- Mudar um elemento que é in-line para block nem sempre é muito bom. Pq um determinado elemento in-line é assim por uma boa razão. Motivo pelo qual adicionamos a propriedade display não na âncora neste caso, mas sim no elemento <li> ([ver linha 32 do main.css](https://github.com/Filipe-vilela-felix/css-complete-guide/blob/main/main.css#L32))

- Logo em seguida, ao invés de adicionarmos o <display: block>, preferimos adicionar o <display: inline-block>. Pois assim, há uma mistura no comportamento de ambos (in-line e block). Como elemento inline, esses elementos podem ficar próximos uns dos outros, mas ainda se comportam com elementos de nível de bloco quando se trata em definir margens superior e inferior, dentre outros

## Theory Time - Pseudo Classes & Pseudo Elements

- Pseudo Classes: define o estilo de um estado especial de um elemento;

- Pseudo Element: define o estilo de uma parte específica de um elemento;

Um exemplo de pseudo element:

```css
.main-nav__item a::after {
    content: " (Link)";
    color: red;
}
```
### Section 3: Properties Worth to Remember & wrap up

```
selector {
    property: value;
}
```

- Quais propriedades foram usadas?
    color:
    background-color:
    display:
    padding:
    padding:
    border:
    margin:
    width:
    height:

- O que foi aprendido neste módulo?
    - Modelo de caixa: 
        Cada elemento é tratado como uma caixa, não importa se é elemento, linha ou bloco, é tratado como uma caixa. Com excessão dos elementos inline;
    - Largura e altura:
        - px ou % (ou outras unidades)
        - %
        - width e height
        - box-sizing, content-box (padrão) ou border-box
    - Propriedade display:
        Podemos alterar o comportamento de elementos de nível de bloco ou elementos em linha;
    - Pseudo classes e elementos:
        É possível estilizar diferentes estdados de um elemento ou segmentar diferentes tipos de elementos ;