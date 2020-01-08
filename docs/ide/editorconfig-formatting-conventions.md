---
title: Convenções de formatação do .NET para EditorConfig
ms.date: 07/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 64f6a45b3a5cc49cd541ceb905356093ea4ec221
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589221"
---
# <a name="formatting-conventions"></a>Convenções de formatação

As convenções de formatação para o EditorConfig no Visual Studio se enquadram nestas categorias:

- [Configurações de formatação do .NET](#net-formatting-settings)

- [Configurações de formatação de C#](#c-formatting-settings)

## <a name="rule-format"></a>Formatação de regra

As regras para as convenções de formatação tem o seguinte formato:

`rule_name = value`

Para muitas regras, você especifica `true` (preferir esse estilo) ou `false` (não preferir esse estilo) para `value`. Para outras regras, você especifica um valor como `flush_left` ou `before_and_after` para descrever quando e onde aplicar a regra. Você não especifica uma gravidade.

## <a name="net-formatting-settings"></a>Configurações de formatação do .NET

As regras de formatação nesta seção aplicam-se ao código do C# e do Visual Basic.

- [Organizar usos](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Organizar usando diretivas

Essas regras de formatação referem-se à classificação e à exibição de diretivas `using` e instruções `Imports`.

Exemplo de arquivo *.editorconfig*:

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>dotnet\_sort\_system\_directives_first

|||
|-|-|
| **Nome da regra** | dotnet_sort_system_directives_first |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – Classificar diretivas `using` System.* em ordem alfabética e colocá-las antes de outras diretivas using.<br /><br />`false` – não coloque diretivas `using` System.* antes de outras diretivas `using`. |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnet_separate_import_directive_groups"></a>dotnet\_separate\_import\_directive\_groups

|||
|-|-|
| **Nome da regra** | dotnet_separate_import_directive_groups |
| **Linguagens aplicáveis** | C# e Visual Basic |
| **Versão introduzida** | Visual Studio 2017 versão 15.5 |
| **Valores** | `true` – coloque uma linha em branco entre os grupos de diretivas `using`.<br /><br />`false` – não coloque uma linha em branco entre os grupos de diretivas `using`. |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-settings"></a>Configurações de formatação de C#

As regras de formatação nesta seção aplicam-se somente a código em C#.

- [Opções de nova linha](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Opções de recuo](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [Opções de espaçamento](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_declaration_name_and_open_parenthesis
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_after_comma
  - csharp_space_before_comma
  - csharp_space_after_dot
  - csharp_space_before_dot
  - csharp_space_after_semicolon_in_for_statement
  - csharp_space_before_semicolon_in_for_statement
  - csharp_space_around_declaration_statements
  - csharp_space_before_open_square_brackets
  - csharp_space_between_empty_square_brackets
  - csharp_space_between_square_brackets
- [Encapsular opções](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks

### <a name="new-line-options"></a>Opções de nova linha

Essas regras de formatação envolvem o uso de novas linhas para formatar o código.

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharp_new_line_before_open_brace"></a>csharp\_new\_line\_before\_open_brace

Essa regra está relacionada a se uma chave de abertura `{` devem ser colocada na mesma linha que a do código anterior ou em uma nova linha. Para essa regra, você especifica **all**, **none** ou um ou mais elementos de código, como **métodos** ou **propriedades**, para definir quando essa regra deve ser aplicada. Para especificar vários elementos de código, separe-os com uma vírgula (,).

|||
|-|-|
| **Nome da regra** | csharp_new_line_before_open_brace |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `all` – requer que as chaves estejam em uma nova linha para todas as expressões (estilo "Allman").<br /><br />`none` – requer que as chaves estejam na mesma linha para todas as expressões ("K&R").<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` – requer que as chaves estejam em uma nova linha para o elemento de código especificado (estilo "Allman"). |
| **Padrão do Visual Studio** | `all` |

Exemplos de código:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharp_new_line_before_else"></a>csharp\_new\_line\_before_else

|||
|-|-|
| **Nome da regra** | csharp_new_line_before_else |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – insira as instruções `else` em uma nova linha.<br /><br />`false` – insira as instruções `else` na mesma linha. |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharp_new_line_before_catch"></a>csharp\_new\_line\_before_catch

|||
|-|-|
| **Nome da regra** | csharp_new_line_before_catch |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – insira as instruções `catch` em uma nova linha.<br /><br />`false` – insira as instruções `catch` na mesma linha. |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharp_new_line_before_finally"></a>csharp\_new\_line\_before_finally

|||
|-|-|
| **Nome da regra** | csharp_new_line_before_finally |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – exigir que as instruções `finally` estejam em uma nova linha após a chave de fechamento.<br /><br />`false` – exigir que as instruções `finally` estejam na mesma linha como a chave de fechamento. |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>csharp\_new\_line\_before\_members\_in\_object_initializers

|||
|-|-|
| **Nome da regra** | csharp_new_line_before_members_in_object_initializers |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – exigir que membros dos inicializadores de objetos estejam em linhas separadas<br /><br />`false` – exigir que membros dos inicializadores de objetos estejam na mesma linha |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>csharp\_new\_line\_before\_members\_in\_anonymous_types

|||
|-|-|
| **Nome da regra** | csharp_new_line_before_members_in_anonymous_types |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – exigir que membros de tipos anônimos estejam em linhas separadas<br /><br />`false` – exigir que membros de tipos anônimos estejam na mesma linha |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_between_query_expression_clauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Nome da regra** | csharp_new_line_between_query_expression_clauses |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – exigir que elementos das cláusulas de expressão de consulta estejam em linhas separadas<br /><br />`false` – exigir que elementos das cláusulas de expressão de consulta estejam na mesma linha |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a>Opções de recuo

Essas regras de formatação envolvem o uso de recuo para formatar o código.

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a>csharp\_indent\_case_contents

|||
|-|-|
| **Nome da regra** | csharp_indent_case_contents |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – recuar `switch` conteúdo de caso<br /><br />`false` – não recuar `switch` conteúdo de caso |
| **Padrão do Visual Studio** | `true` |

- Quando essa regra é definida como **true**, i.
- Quando essa regra é definida como **true**, d.

Exemplos de código:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_switch_labels"></a>csharp\_indent\_switch_labels

|||
|-|-|
| **Nome da regra** | csharp_indent_switch_labels |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – recuar `switch` rótulos<br /><br />`false` – não recuar `switch` rótulos |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_labels"></a>csharp\_indent_labels

|||
|-|-|
| **Nome da regra** | csharp_indent_labels |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `flush_left` – os rótulos são posicionados na coluna mais à esquerda<br /><br />`one_less_than_current` – os rótulos são posicionados em um recuo a menos do que o contexto atual<br /><br />`no_change` – os rótulos são posicionados no mesmo recuo do contexto atual |
| **Padrão do Visual Studio** | `no_change` |

Exemplos de código:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### <a name="csharp_indent_block_contents"></a>csharp_indent_block_contents

|||
|-|-|
| **Nome da regra** | csharp_indent_block_contents |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` - <br /><br />`false` -  |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a>csharp_indent_braces

|||
|-|-|
| **Nome da regra** | csharp_indent_braces |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` - <br /><br />`false` -  |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a>csharp_indent_case_contents_when_block

|||
|-|-|
| **Nome da regra** | csharp_indent_case_contents_when_block |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` - <br /><br />`false` -  |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a>Opções de espaçamento

Essas regras de formatação envolvem o uso de caracteres de espaço para formatar o código.

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a>csharp\_space\_after_cast

|||
|-|-|
| **Nome da regra** | csharp_space_after_cast |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – inserir um caractere de espaço entre uma conversão e o valor<br /><br />`false` – Remover o espaço entre a conversão e o valor |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Nome da regra** | csharp_space_after_keywords_in_control_flow_statements |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – inserir um caractere de espaço após uma palavra-chave em uma instrução de fluxo de controle, como um loop `for`<br /><br />`false` – remover um espaço após uma palavra-chave em uma instrução de fluxo de controle, como um loop `for` |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Nome da regra** | csharp_space_between_parentheses |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `control_flow_statements` – inserir espaço entre parênteses das instruções de fluxo de controle<br /><br />`expressions` – inserir espaço entre os parênteses das expressões<br /><br />`type_casts` – inserir espaço entre os parênteses nas conversões de tipo |
| **Padrão do Visual Studio** | `false` |

Se você omitir essa regra ou usar um valor diferente de `control_flow_statements`, `expressions` ou `type_casts`, a configuração não será aplicada.

Exemplos de código:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|||
|-|-|
| **Nome da regra** | csharp_space_before_colon_in_inheritance_clause |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.7 |
| **Valores** | `true` – remover um caractere de espaço antes dos dois-pontos para bases ou interfaces em uma declaração de tipo<br /><br />`false` – remover um espaço antes dos dois-pontos para bases ou interfaces em uma declaração de tipo |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|||
|-|-|
| **Nome da regra** | csharp_space_after_colon_in_inheritance_clause |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.7 |
| **Valores** | `true` – inserir um caractere de espaço após os dois-pontos para bases ou interfaces em uma declaração de tipo<br /><br />`false` – remover um espaço após os dois-pontos para bases ou interfaces em uma declaração de tipo |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharp_space_around_binary_operators"></a>csharp\_space\_around\_binary_operators

|||
|-|-|
| **Nome da regra** | csharp_space_around_binary_operators |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.7 |
| **Valores** | `before_and_after` – inserir espaço antes e depois do operador binário<br /><br />`none` – remover espaços antes e depois do operador binário<br /><br />`ignore` – ignorar espaços em torno de operadores binários |
| **Padrão do Visual Studio** | `before_and_after` |

Se você omitir essa regra ou usar um valor diferente de `before_and_after`, `none` ou `ignore`, a configuração não será aplicada.

Exemplos de código:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Nome da regra** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – posicionar um caractere de espaço após o parêntese de abertura e antes do parêntese de fechamento de uma lista de parâmetros de declaração de método<br /><br />`false` – remover caracteres de espaço após o parêntese de abertura e antes do parêntese de fechamento de uma lista de parâmetros de declaração de método |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Nome da regra** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.7 |
| **Valores** | `true` – inserir um espaço nos parênteses vazios da lista de parâmetros para uma declaração de método<br /><br />`false` – remover um espaço nos parênteses vazios da lista de parâmetros para uma declaração de método |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a>csharp_space_between_method_declaration_name_and_open_parenthesis

|||
|-|-|
| **Nome da regra** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – inserir um caractere de espaço entre o nome do método e o parêntese de abertura na declaração do método<br /><br />`false` – remover um caractere de espaço entre o nome do método e o parêntese de abertura na declaração do método |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Nome da regra** | csharp_space_between_method_call_parameter_list_parentheses |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – posicionar um caractere de espaço após o parêntese de abertura e antes do parêntese de fechamento de uma chamada de método<br /><br />`false` – remover caracteres de espaço após o parêntese de abertura e antes do parêntese de fechamento de uma chamada de método |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Nome da regra** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.7 |
| **Valores** | `true` – inserir espaço dentro dos parênteses da lista de argumentos vazia<br /><br />`false` – remover espaço dentro dos parênteses da lista de argumentos vazia |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Nome da regra** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.7 |
| **Valores** | `true` – inserir espaço entre o nome da chamada de método e o parêntese de abertura<br /><br />`false` – remover espaço entre o nome da chamada de método e o parêntese de abertura |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_after_comma"></a>csharp_space_after_comma

|||
|-|-|
| **Nome da regra** | csharp_space_after_comma |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – inserir espaço após uma vírgula<br /><br />`false` – remover o espaço após uma vírgula |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a>csharp_space_before_comma

|||
|-|-|
| **Nome da regra** | csharp_space_before_comma |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – inserir espaço antes de uma vírgula<br /><br />`false` – remover espaço antes de uma vírgula |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a>csharp_space_after_dot

|||
|-|-|
| **Nome da regra** | csharp_space_after_dot |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – inserir espaço após um ponto<br /><br />`false` – remover o espaço após um ponto |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a>csharp_space_before_dot

|||
|-|-|
| **Nome da regra** | csharp_space_before_dot |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – inserir espaço antes de um ponto <br /><br />`false` – remover espaço antes de um ponto |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a>csharp_space_after_semicolon_in_for_statement

|||
|-|-|
| **Nome da regra** | csharp_space_after_semicolon_in_for_statement |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – inserir espaço após cada ponto e vírgula em uma instrução `for`<br /><br />`false` – remover espaço após cada ponto e vírgula em uma instrução `for` |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a>csharp_space_before_semicolon_in_for_statement

|||
|-|-|
| **Nome da regra** | csharp_space_before_semicolon_in_for_statement |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – inserir espaço antes de cada ponto e vírgula em uma instrução `for` <br /><br />`false` – remover espaço antes de cada ponto e vírgula em uma instrução `for` |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a>csharp_space_around_declaration_statements

|||
|-|-|
| **Nome da regra** | csharp_space_around_declaration_statements |
| **Linguagens aplicáveis** | C# |
| **Valores** | `ignore` – não remover caracteres de espaço extra em instruções de declaração<br /><br />`false` – remover caracteres de espaço extra em instruções de declaração |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a>csharp_space_before_open_square_brackets

|||
|-|-|
| **Nome da regra** | csharp_space_before_open_square_brackets |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – inserir espaço antes dos colchetes de abertura `[` <br /><br />`false` – remover espaço antes dos colchetes de abertura `[` |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a>csharp_space_between_empty_square_brackets

|||
|-|-|
| **Nome da regra** | csharp_space_between_empty_square_brackets |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – inserir espaço entre colchetes vazios `[ ]` <br /><br />`false` – remover espaço entre colchetes vazios `[]` |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a>csharp_space_between_square_brackets

|||
|-|-|
| **Nome da regra** | csharp_space_between_square_brackets |
| **Linguagens aplicáveis** | C# |
| **Valores** | `true` – inserir caracteres de espaço em colchetes não vazios `[ 0 ]` <br /><br />`false` – remover caracteres de espaço em colchetes não vazios `[0]` |
| **Padrão do Visual Studio** | `false` |

Exemplos de código:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Encapsular opções

Essas regras de formatação referem-se ao uso de linhas únicas em comparação com linhas separadas para instruções e blocos de código.

Exemplo de arquivo *.editorconfig*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **Nome da regra** | csharp_preserve_single_line_statements |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – deixar instruções e declarações de membros na mesma linha<br /><br />`false` – deixar instruções e declarações de membros em linhas diferentes |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **Nome da regra** | csharp_preserve_single_line_blocks |
| **Linguagens aplicáveis** | C# |
| **Versão introduzida** | Visual Studio 2017 versão 15.3 |
| **Valores** | `true` – deixar bloco de códigos em uma linha única<br /><br />`false` – deixar bloco de códigos em linhas separadas |
| **Padrão do Visual Studio** | `true` |

Exemplos de código:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

## <a name="see-also"></a>Veja também

- [Convenções de linguagem](editorconfig-language-conventions.md)
- [Convenções de nomenclatura](editorconfig-naming-conventions.md)
- [Configurações de convenção de codificação do .NET para o EditorConfig](editorconfig-code-style-settings-reference.md)
