---
title: Convenções de formatação de EditorConfig do C++
titleSuffix: ''
description: Saiba mais sobre como usar o EditorConfig para formatar o código C++ no Visual Studio.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jmartens
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: 490a7b29d6e3d8a2dc63c27b9e9d7226b5d22662
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970875"
---
# <a name="c-editorconfig-formatting-conventions"></a>Convenções de formatação de EditorConfig do C++

O formatador C++ do Visual Studio tem um conjunto rico de configurações configuráveis que podem ser aplicadas globalmente. Para definir as configurações de formatação de C++ para um espaço de trabalho específico, use [clangformat](https://clang.llvm.org/docs/ClangFormat.html) ou [EditorConfig](https://editorconfig.org/). Tanto o Visual Studio quanto o Visual Studio Code têm suporte interno a EditorConfig para cada uma das configurações de formatação global do Visual Studio C++, com as configurações de EditorConfig que têm precedência. Isso significa que você pode adicionar arquivos EditorConfig ao seu espaço de trabalho para configurar a formatação do C++ em um nível mais granular e impor o estilo de código consistente para todos que contribuem para o projeto.

## <a name="c-formatting-conventions"></a>Convenções de formatação de C++

As configurações de EditorConfig de formatação de C++ são prefixadas com `cpp_` . Aqui está um exemplo de como o arquivo EditorConfig pode ser:

```ini
[*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

O restante deste documento lista todas as configurações de formatação do EditorConfig C++ com suporte no Visual Studio e VS Code.

### <a name="indentation-settings"></a>Configurações de recuo

**Recuar chaves**

- Nome: `cpp_indent_braces`
- Valores: `true` , `false`

**Recuar cada linha relativamente a**

- Nome: `cpp_indent_multi_line_relative_to`
- Valores:
  - `outermost_parenthesis` -Quando uma nova linha é digitada, ela é recuada com relação ao parênteses de abertura mais externo.
  - `innermost_parenthesis` -Quando uma nova linha é digitada, ela é recuada com relação ao parênteses de abertura mais interno.
  - `statement_begin` -Quando uma nova linha é digitada, ela é recuada relativamente ao início da instrução atual.

**Entre parênteses, alinhar novas linhas quando as digitar**

- Nome: `cpp_indent_within_parentheses`
- Valores:
  - `align_to_parenthesis` -Alinhar conteúdo ao parêntese de abertura.
  - `indent` -Recuar novas linhas.

**No código existente, não use a configuração para o alinhamento de novas linhas entre parênteses**

- Nome: `cpp_indent_preserve_within_parentheses`
- Valores: `true` , `false`

**Recuar conteúdo de caso**

- Nome: `cpp_indent_case_contents`
- Valores: `true` , `false`

**Recuar rótulos de caso**

- Nome: `cpp_indent_case_labels`
- Valores: `true` , `false`

**Recuar chaves após uma instrução Case**

- Nome: `cpp_indent_case_contents_when_block`
- Valores: `true` , `false`

**Recuar chaves de lambdas usadas como parâmetros**

- Nome: `cpp_indent_lambda_braces_when_parameter`
- Valores: `true` , `false`

**Posição dos rótulos goto**

- Nome: `cpp_indent_goto_labels`
- Valores:
  - `one_left` -Um recuo para a esquerda
  - `leftmost_column` -Mover para a coluna mais à esquerda
  - `none` -Deixar recuado

**Posição das diretivas de pré-processador**

- Nome: `cpp_indent_preprocessor`
- Valores:
  - `one_left` -Um recuo para a esquerda
  - `leftmost_column` -Mover para a coluna mais à esquerda
  - `none` -Deixar recuado

**Recuar especificadores de acesso**

- Nome: `cpp_indent_access_specifiers`
- Valores: `true` , `false`

**Recuar conteúdo do namespace**

- Nome: `cpp_indent_namespace_contents`
- Valores: `true` , `false`

**Preservar recuo de comentários**

- Nome: `cpp_indent_preserve_comments`
- Valores: `true` , `false`

### <a name="newline-settings"></a>Configurações de nova linha

**Posição de chaves de abertura para namespaces**

- Nome: `cpp_new_line_before_open_brace_namespace`
- Valores:
  - `new_line` -Mover para uma nova linha
  - `same_line` -Manter na mesma linha, mas adicionar um espaço antes
  - `ignore` -Não reposicionar automaticamente

**Posição das chaves de abertura para tipos**

- Nome: `cpp_new_line_before_open_brace_type`
- Valores:
  - `new_line` -Mover para uma nova linha
  - `same_line` -Manter na mesma linha, mas adicionar um espaço antes
  - `ignore` -Não reposicionar automaticamente

**Posição das chaves de abertura para funções**

- Nome: `cpp_new_line_before_open_brace_function`
- Valores:
  - `new_line` -Mover para uma nova linha
  - `same_line` -Manter na mesma linha, mas adicionar um espaço antes
  - `ignore` -Não reposicionar automaticamente

**Posição das chaves de abertura para blocos de controle**

- Nome: `cpp_new_line_before_open_brace_block`
- Valores:
  - `new_line` -Mover para uma nova linha
  - `same_line` -Manter na mesma linha, mas adicionar um espaço antes
  - `ignore` -Não reposicionar automaticamente

**Posição das chaves de abertura para lambdas**

- Nome: `cpp_new_line_before_open_brace_lambda`
- Valores:
  - `new_line` -Mover para uma nova linha
  - `same_line` -Manter na mesma linha, mas adicionar um espaço antes
  - `ignore` -Não reposicionar automaticamente
 
**Posicionar chaves de escopo em linhas separadas**

- Nome: `cpp_new_line_scope_braces_on_separate_lines`
- Valores: `true` , `false`

**Para tipos vazios, mova as chaves de fechamento para a mesma linha que as chaves de abertura**

- Nome: `cpp_new_line_close_brace_same_line_empty_type`
- Valores: `true` , `false`

**Para corpos de funções vazias, mova as chaves de fechamento para a mesma linha que as chaves de abertura**

- Nome: `cpp_new_line_close_brace_same_line_empty_function`
- Valores: `true` , `false`

**Coloque ' Catch ' e palavras-chave semelhantes em uma nova linha**

- Nome: `cpp_new_line_before_catch`
- Valores: `true` , `false`

**Posicionar ' else ' em uma nova linha**

- Nome: `cpp_new_line_before_else`
- Valores: `true` , `false`

**Coloque ' While ' em um loop do-while em uma nova linha**

- Nome: `cpp_new_line_before_while_in_do_while`
- Valores: `true` , `false`

### <a name="spacing-settings"></a>Configurações de espaçamento

**Espaçamento entre nomes de função e parênteses de abertura de listas de argumentos**

- Nome: `cpp_space_before_function_open_parenthesis`
- Valores:
  - `insert` -Inserir um espaço
  - `remove` -Remover espaços
  - `ignore` -Não alterar espaços

**Inserir espaço dentro dos parênteses de uma lista de argumentos**

- `cpp_space_within_parameter_list_parentheses`Valores de nome: `true` ,`false`

**Inserir espaço entre parênteses quando a lista de argumentos estiver vazia**

- Nome: `cpp_space_between_empty_parameter_list_parentheses`
- Valores: `true` , `false`

**Inserir espaço entre a palavra-chave e o parêntese de abertura em instruções de fluxo de controle**

- Nome: `cpp_space_after_keywords_in_control_flow_statements`
- Valores: `true` , `false`

**Inserir espaço dentro dos parênteses de uma instrução de controle**

- Nome: `cpp_space_within_control_flow_statement_parentheses`
- Valores: `true` , `false`

**Inserir espaço antes do parêntese de abertura de listas de argumentos lambda**

- Nome: `cpp_space_before_lambda_open_parenthesis`
- Valores: `true` , `false`

**Inserir espaço dentro dos parênteses de uma conversão C-Style**

- Nome: `cpp_space_within_cast_parentheses`
- Valores: `true` , `false`

**Inserir espaço após o parêntese de fechamento da conversão C-Style**

- Nome: `cpp_space_after_cast_close_parenthesis`
- Valores: `true` , `false`

**Inserir espaço dentro dos parênteses de uma expressão entre parênteses**

- Nome: `cpp_space_within_expression_parentheses`
- Valores: `true` , `false`

**Inserir espaço antes de abrir a chave dos blocos**

- Nome: `cpp_space_before_block_open_brace`
- Valores: `true` , `false`

**Inserir espaço entre chaves vazias**

- Nome: `cpp_space_between_empty_braces`
- Valores: `true` , `false`

**Inserir espaço antes de abrir chaves de inicialização uniforme e listas de inicializadores**

- Nome: `cpp_space_before_initializer_list_open_brace`
- Valores: `true` , `false`

**Inserir espaço dentro das chaves de inicialização uniforme e listas de inicializadores**

- Nome: `cpp_space_within_initializer_list_braces`
- Valores: `true` , `false`

**Preservar os espaços dentro de listas de inicialização e inicializador uniforme**

- Nome: `cpp_space_preserve_in_initializer_list`
- Valores: `true` , `false`

**Inserir espaço antes de colchetes de abertura**

- Nome: `cpp_space_before_open_square_bracket`
- Valores: `true` , `false`

**Inserir espaço dentro do colchete**

- Nome: `cpp_space_within_square_brackets`
- Valores: `true` , `false`

**Inserir espaço antes de colchetes vazios**

- Nome: `cpp_space_before_empty_square_brackets`
- Valores: `true` , `false`

**Inserir espaço entre colchetes vazios**

- Nome: `cpp_space_between_empty_square_brackets`
- Valores: `true` , `false`

**Agrupar colchetes para matrizes multidimensionais juntas**

- Nome: `cpp_space_group_square_brackets`
- Valores: `true` , `false`

**Inserir espaço dentro de colchetes para lambdas**

- Nome: `cpp_space_within_lambda_brackets`
- Valores: `true` , `false`

**SpaceBetweenEmptyLambdaBrackets**

- Nome: `cpp_space_between_empty_lambda_brackets`
- Valores: `true` , `false`

**Inserir espaço antes de vírgulas**

- Nome: `cpp_space_before_comma`
- Valores: `true` , `false`

**Inserir espaço após vírgulas**

- Nome: `cpp_space_after_comma`
- Valores: `true` , `false`

**Remover espaços antes e depois dos operadores de membro**

- Nome: `cpp_space_remove_around_member_operators`
- Valores: `true` , `false`

**Inserir espaço antes de dois-pontos para declarações de base em tipo**

- Nome: `cpp_space_before_inheritance_colon`
- Valores: `true` , `false`

**Inserir espaço antes dos dois-pontos para construtores**

- Nome: `cpp_space_before_constructor_colon`
- Valores: `true` , `false`

**Remover espaço antes de ponto e vírgula**

- Nome: `cpp_space_remove_before_semicolon`
- Valores: `true` , `false`

**Inserir espaço após ponto e vírgula**

- Nome: `cpp_space_after_semicolon`
- Valores: `true` , `false`

**Remover espaços entre operadores unários e seus operandos**

- Nome: `cpp_space_remove_around_unary_operator`
- Valores: `true` , `false`

**Espaçamento para operadores binários**

- Nome: `cpp_space_around_binary_operator`
- Valores:
  - `insert` -Inserir espaços antes e depois dos operadores binários.
  - `remove` -Remover espaços em volta de operadores binários.
  - `ignore` -Não altere espaços em volta de operadores binários.

**Espaçamento para operadores de atribuição**

- Nome: `cpp_space_around_assignment_operator`
- Valores:
  - `insert` -Inserir espaços em volta de operadores de atribuição.
  - `remove` -Remover espaços em volta de operadores de atribuição.
  - `ignore` -Não altere espaços em volta de operadores de atribuição.

**Alinhamento de ponteiro/referência**

- Nome: `cpp_space_pointer_reference_alignment`
- Valores:
  - `left` -Alinhar à esquerda.
  - `center` -Alinhar centro.
  - `right` -Alinhar à direita.
  - `ignore` -Deixe inalterado.

**Espaçamento de operadores condicionais**

- Nome: `cpp_space_around_ternary_operator`
- Valores:
  - `insert` -Inserir espaços em volta de operadores condicionais.
  - `remove` -Remover espaços em volta de operadores condicionais.
  - `ignore` -Não altere espaços em volta de operadores condicionais.

### <a name="wrapping-options"></a>Opções de encapsulamento

**Opções de encapsulamento para blocos**

- Nome: `cpp_wrap_preserve_blocks`
- Valores:
  - `one_liners` -Não quebrar blocos de código de uma linha.
  - `all_one_line_scopes` -Não quebrar blocos de código em que as chaves de abertura e fechamento estejam na próxima linha.
  - `never` -Sempre aplicar configurações de novas linhas para blocos.

## <a name="see-also"></a>Consulte também

- [EditorConfig.org](https://editorconfig.org/)
- [Dando suporte ao EditorConfig para um serviço de linguagem](../extensibility/supporting-editorconfig.md)
- [Recursos do editor de código](writing-code-in-the-code-and-text-editor.md)
