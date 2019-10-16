---
title: Opções de configuração do FxCop Analyzer
ms.date: 09/23/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7d9ca8c8bd46b4f8455c7aa750170d38f03321f6
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349674"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Opções de escopo da regra para analisadores do FxCop

Algumas regras do analisador do FxCop permitem refinar a quais partes de sua base de código elas devem ser aplicadas. Esta página lista as opções de configuração de escopo disponíveis, seus valores permitidos e as regras às quais elas podem ser aplicadas. Para usar essas opções, especifique-as em um [arquivo EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

Essas opções de configuração estão disponíveis a partir da versão 2.6.3 do pacote NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .

> [!TIP]
> Para ver a lista completa de opções disponíveis para uma determinada versão do pacote FxCopAnalyzers, examine o arquivo *Configuration.MD do analisador* na pasta de *documentação* do pacote. O arquivo está localizado em *% USERPROFILE% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-2 @ no__t-3version @ no__t-4\documentation\Analyzer Configuration.MD*. Esse arquivo de documentação de configuração está incluído em cada versão do pacote, a partir da versão 2.6.5. Veja um exemplo de como uma opção é documentada no arquivo *Configuration.MD do analisador* :
>
> Nome da opção: `sufficient_IterationCount_for_weak_KDF_algorithm` @ no__t-1
> Valores de opção: valores integrais \
> Valor padrão: específico para cada regra configurável (' 100000 ' por padrão para a maioria das regras) \
> Exemplo: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Qual parte da superfície da API deve ser analisada | `public`<br/>`internal` ou `friend`<br/>`private`<br/>`all`<br/><br/>Separe vários valores com uma vírgula (,) | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802](ca1802.md)<br/>[CA1815](ca1815.md)<br/>[CA1819](ca1819.md)<br/>[CA2217](ca2217.md)<br/>[CA2225](ca2225.md)<br/>[CA2226](ca2226.md)<br/>[CA2231](ca2231.md)<br/>[CA2234](ca2234.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Se os métodos assíncronos que não retornam um valor devem ser ignorados | `true`<br/>`false` | `false` | [CA2007](ca2007-do-not-directly-await-task.md) |

> [!NOTE]
> Na versão 2.6.3 e anteriores do pacote do analisador, essa opção foi denominada `skip_async_void_methods`.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Se os [parâmetros de tipo](/dotnet/csharp/programming-guide/generics/generic-type-parameters) de caractere único devem ser excluídos da regra, por exemplo, `S` em `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> Na versão 2.6.3 e anteriores do pacote do analisador, essa opção foi denominada `allow_single_letter_type_parameters`.

## <a name="output_kind"></a>output_kind

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Especifica que o código em um projeto que gera esse tipo de assembly deve ser analisado | Um ou mais campos da enumeração <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Separe vários valores com uma vírgula (,) | Todos os tipos de saída | [CA2007](ca2007-do-not-directly-await-task.md) |