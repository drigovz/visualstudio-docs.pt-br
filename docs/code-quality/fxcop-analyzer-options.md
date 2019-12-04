---
title: Opções de configuração do FxCop Analyzer
ms.date: 09/23/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2d97552a79b520bd522cb8ec768d7d36fe2fb052
ms.sourcegitcommit: c222052906362bf1a3762ec4d4623170e4e06702
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74809815"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Opções de escopo da regra para analisadores do FxCop

Algumas regras do analisador do FxCop permitem refinar a quais partes de sua base de código elas devem ser aplicadas. Esta página lista as opções de configuração de escopo disponíveis, seus valores permitidos e as regras às quais elas podem ser aplicadas. Para usar essas opções, especifique-as em um [arquivo EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

Essas opções de configuração estão disponíveis a partir da versão 2.6.3 do pacote NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .

> [!TIP]
> Para ver a lista completa de opções disponíveis para uma determinada versão do pacote FxCopAnalyzers, examine o arquivo *Configuration.MD do analisador* na pasta de *documentação* do pacote. O arquivo está localizado em *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<versão\>\documentation\Analyzer Configuration.MD*. Esse arquivo de documentação de configuração está incluído em cada versão do pacote, a partir da versão 2.6.5. Veja um exemplo de como uma opção é documentada no arquivo *Configuration.MD do analisador* :
>
> Nome da opção: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Valores de opção: valores integrais \
> Valor padrão: específico para cada regra configurável (' 100000 ' por padrão para a maioria das regras) \
> Exemplo: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Qual parte da superfície da API deve ser analisada | `public`<br/>`internal` ou `friend`<br/>`private`<br/>`all`<br/><br/>Separe vários valores com uma vírgula (,) | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Se os métodos assíncronos que não retornam um valor devem ser ignorados | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> Na versão 2.6.3 e anteriores do pacote do analisador, essa opção foi denominada `skip_async_void_methods`.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Se os [parâmetros de tipo](/dotnet/csharp/programming-guide/generics/generic-type-parameters) de caractere único devem ser excluídos da regra, por exemplo, `S` em `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> Na versão 2.6.3 e anteriores do pacote do analisador, essa opção foi denominada `allow_single_letter_type_parameters`.

## <a name="output_kind"></a>output_kind

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Especifica que o código em um projeto que gera esse tipo de assembly deve ser analisado | Um ou mais campos da enumeração de <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Separe vários valores com uma vírgula (,) | Todos os tipos de saída | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Especifica os modificadores necessários para as APIs que devem ser analisadas | Um ou mais valores da tabela de modificadores permitidos abaixo<br/><br/>Separe vários valores com uma vírgula (,) | Depende de cada regra | [CA1802](ca1802.md) |

| Modificador permitido | Resumo |
| --- | --- |
| `none` | Nenhum requisito de modificador |
| `static` ou `Shared` | Deve ser declarado como "Static" ("Shared" em Visual Basic) |
| `const` | Deve ser declarado como ' const ' |
| `readonly` | Deve ser declarado como ' ReadOnly ' |
| `abstract` | Deve ser declarado como ' Abstract ' |
| `virtual` | Deve ser declarado como ' virtual ' |
| `override` | Deve ser declarado como ' override ' |
| `sealed` | Deve ser declarado como ' sealed ' |
| `extern` | Deve ser declarado como ' extern ' |
| `async` | Deve ser declarado como ' async ' |

## <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Se deseja ignorar a análise para o parâmetro de `this` dos métodos de extensão | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Os nomes dos métodos de validação de verificação nula que validam argumentos passados para o método são não nulos | Formatos de nome de método permitidos (separados por `|`):<br/> -Somente nome do método (inclui todos os métodos com o nome, independentemente do tipo ou namespace que o contém)<br/> -Nomes totalmente qualificados no [formato de ID de documentação](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)do símbolo, com um prefixo de `M:` opcional | {1&gt;Nenhum&lt;1} | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Nomes de métodos de formatação de cadeia de caracteres adicionais | Formatos de nome de método permitidos (separados por `|`):<br/> -Somente nome do método (inclui todos os métodos com o nome, independentemente do tipo ou namespace que o contém)<br/> -Nomes totalmente qualificados no [formato de ID de documentação](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)do símbolo, com um prefixo de `M:` opcional | {1&gt;Nenhum&lt;1} | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Nomes de tipos, de modo que o tipo e todos os seus tipos derivados sejam excluídos para análise | Formatos de nome de símbolo permitidos (separados por `|`):<br/> -Somente nome do tipo (inclui todos os tipos com o nome, independentemente do tipo ou namespace que a contém)<br/> -Nomes totalmente qualificados no [formato de ID de documentação](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)do símbolo, com um prefixo de `T:` opcional | {1&gt;Nenhum&lt;1} | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Nomes de símbolos que são excluídos para análise | Formatos de nome de símbolo permitidos (separados por `|`):<br/> -Somente nome do símbolo (inclui todos os símbolos com o nome, independentemente do tipo ou namespace que o contém)<br/> -Nomes totalmente qualificados no [formato de ID de documentação](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)do símbolo. Cada nome de símbolo requer um prefixo de tipo de símbolo, como prefixo "M:" para métodos, prefixo "T:" para tipos, prefixo "N:" para namespaces, etc.<br/> - `.ctor` para construtores e `.cctor` para construtores estáticos | {1&gt;Nenhum&lt;1} | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Nomes de símbolos que não são permitidos no contexto da análise | Formatos de nome de símbolo permitidos (separados por `|`):<br/> -Somente nome do símbolo (inclui todos os símbolos com o nome, independentemente do tipo ou namespace que o contém)<br/> -Nomes totalmente qualificados no [formato de ID de documentação](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)do símbolo. Cada nome de símbolo requer um prefixo de tipo de símbolo, como prefixo "M:" para métodos, prefixo "T:" para tipos, prefixo "N:" para namespaces, etc.<br/> - `.ctor` para construtores e `.cctor` para construtores estáticos | {1&gt;Nenhum&lt;1} | [CA1031](ca1031.md) |

