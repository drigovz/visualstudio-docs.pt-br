---
title: Configurar analisadores de qualidade de código .NET usando o editorconfig
ms.date: 09/01/2020
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc237082ec1188d71241facead975db1df2cf3af
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035424"
---
# <a name="configure-net-code-quality-analysis-with-editorconfig"></a>Configurar a análise de qualidade de código do .NET com o EditorConfig

Cada analisador de qualidade de código (aqueles cujas IDs de regra começam com `CA` ) pode ser refinado para ser aplicado às partes da sua base de código por meio de opções configuráveis. Cada opção é especificada adicionando um par chave-valor a um arquivo [EditorConfig](https://editorconfig.org) . Um arquivo de configuração pode ser específico para um arquivo, projeto, solução ou o repositório inteiro.

> [!TIP]
> Adicione um arquivo. editorconfig ao seu projeto clicando com o botão direito do mouse no projeto em **Gerenciador de soluções** e selecionando **Adicionar**  >  **novo item**. Na janela **Adicionar novo item** , insira **editorconfig** na caixa de pesquisa. Selecione o modelo de **arquivo editorconfig (padrão)** e escolha **Adicionar**.
>
> ![Adicionar arquivo EditorConfig ao projeto no Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Para obter informações sobre como configurar a severidade de uma regra (por exemplo, se é um erro ou um aviso), consulte [definir severidade de regra em um arquivo EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Ou então, você pode escolher um dos [arquivos EditorConfig ou conjuntos de regras](analyzer-rule-sets.md) internos para habilitar ou desabilitar rapidamente uma categoria de regras.

::: moniker-end

O restante deste artigo aborda a sintaxe geral das opções que refinam o local em que os analisadores de qualidade de código .NET são aplicados.

## <a name="option-scopes"></a>Escopos de opção

Cada opção de refinamento pode ser configurada para todas as regras, para uma categoria de regras (por exemplo, segurança ou Design) ou para uma regra específica.

### <a name="all-rules"></a>Todas as regras

A sintaxe para configurar uma opção para *todas* as regras é a seguinte:

|Sintaxe|Exemplo|
|-|-|
| dotnet_code_quality. OptionName = optionvalue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Categoria de regras

A sintaxe para configurar uma opção para uma *categoria* de regras (como nomenclatura, design ou desempenho) é a seguinte:

|Sintaxe|Exemplo|
|-|-|
| dotnet_code_quality. RuleCategory. optionName = optionvalue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Regra específica

A sintaxe para configurar uma opção para uma regra *específica* é a seguinte:

|Sintaxe|Exemplo|
|-|-|
| dotnet_code_quality. RuleId. ValorDeOpção = optionvalue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="enabling-editorconfig-based-configuration"></a>Habilitando a configuração baseada em EditorConfig

A configuração do analisador baseado em EditorConfig pode ser habilitada para os seguintes escopos:

- Documentos (s) específicos
- Pastas específicas
- Projetos específicos
- Solução (ões) específica (s)
- Repositório inteiro

Para habilitar a configuração, adicione um arquivo *. editorconfig* com as opções no diretório correspondente. Esse arquivo também pode conter entradas de configuração de severidade de diagnóstico com base em EditorConfig. Veja [aqui](use-roslyn-analyzers.md#configure-severity-levels) para obter mais detalhes.

## <a name="enable-a-category-of-rules"></a>Habilitar uma categoria de regras

Os pacotes do Analyzer podem incluir [EditorConfig](use-roslyn-analyzers.md#configure-severity-levels) predefinidos e/ou arquivos de [conjunto de regras](using-rule-sets-to-group-code-analysis-rules.md) que tornam rápido e fácil habilitar uma categoria de regras, como segurança ou regras de design. O pacote do analisador NuGet do [Microsoft. CodeAnalysis. Netanalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) inclui arquivos EditorConfig e conjuntos de regras. Ao habilitar uma categoria específica de regras, você pode identificar problemas direcionados e condições específicas.

> [!NOTE]
> A habilitação das regras do analisador e a definição de sua gravidade usando um arquivo EditorConfig tem suporte a partir do Visual Studio 2019 versão 16,3.

O pacote NuGet do netanalyzers inclui arquivos EditorConfig predefinidos e conjuntos de regras para as seguintes categorias de regra:

- Todas as regras
- Fluxo de dados
- Design
- Documentação
- Globalização
- Interoperabilidade
- Facilidade de manutenção
- Nomenclatura
- Desempenho
- Portado do FxCop
- Confiabilidade
- Segurança
- Uso

Cada uma dessas categorias de regras tem um EditorConfig ou um arquivo de conjunto de regras para:

- Habilitar todas as regras na categoria (e desabilitar todas as outras regras)
- Usar a severidade padrão de cada regra e habilitada por configuração padrão (e desabilitar todas as outras regras)

> [!TIP]
> A categoria "todas as regras" tem um EditorConfig adicional ou um arquivo de conjunto de regras para desabilitar todas as regras. Use esse arquivo para eliminar rapidamente qualquer erro ou aviso do analisador em um projeto.

> [!TIP]
> Se você estiver migrando da análise "FxCop" herdada para a análise de código baseada em .NET Compiler Platform, os arquivos de conjunto de regras e EditorConfig permitem que você continue usando configurações de regra semelhantes [àquelas usadas anteriormente](rule-set-reference.md).

## <a name="predefined-editorconfig-files"></a>Arquivos EditorConfig predefinidos

Os arquivos EditorConfig predefinidos para o pacote do analisador Microsoft. CodeAnalysis. netanalyzers estão localizados no diretório *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig* . Por exemplo, o arquivo EditorConfig para habilitar todas as regras de segurança está localizado em *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig\SecurityRulesEnabled \\ . EditorConfig*.

Copie o arquivo. editorconfig escolhido para o diretório raiz do projeto.

## <a name="predefined-rule-sets"></a>Conjuntos de regras predefinidas

Os arquivos de conjunto de regras predefinidos para o pacote do analisador Microsoft. CodeAnalysis. netanalyzers estão localizados no diretório *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets* Por exemplo, o arquivo de conjunto de regras para habilitar todas as regras de segurança está localizado em *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets\SecurityRulesEnabled.RuleSet*.

Copie um ou mais conjuntos de regras e cole-os no diretório que contém o projeto do Visual Studio ou diretamente no **Gerenciador de soluções**.

Você também pode [Personalizar um conjunto de regras predefinidas](how-to-create-a-custom-rule-set.md) para sua preferência. Por exemplo, você pode alterar a severidade de uma ou mais regras para que as violações apareçam como erros ou avisos no **lista de erros**.


## <a name="rule-scope-options-for-net-code-quality-analyzers"></a>Opções de escopo de regra para analisadores de qualidade de código .NET

Você pode especificar opções em um [arquivo EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project). Por exemplo, você pode especificar as opções a seguir.

> [!TIP]
> Para ver a lista completa de opções disponíveis, consulte este arquivo do [analisador Configuration.MD](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md). Veja um exemplo de como uma opção é documentada no arquivo *Configuration.MD do analisador* :
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
> Na versão 2.6.3 e anteriores do pacote do analisador, essa opção foi nomeada `skip_async_void_methods` .

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Se os [parâmetros de tipo](/dotnet/csharp/programming-guide/generics/generic-type-parameters) de caractere único devem ser excluídos da regra, por exemplo, `S` em `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> Na versão 2.6.3 e anteriores do pacote do analisador, essa opção foi nomeada `allow_single_letter_type_parameters` .

## <a name="output_kind"></a>output_kind

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Especifica que o código em um projeto que gera esse tipo de assembly deve ser analisado | Um ou mais campos da <xref:Microsoft.CodeAnalysis.OutputKind> enumeração<br/><br/>Separe vários valores com uma vírgula (,) | Todos os tipos de saída | [CA2007](ca2007.md) |

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
| Se deseja ignorar a análise para o `this` parâmetro de métodos de extensão | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Os nomes dos métodos de validação de verificação nula que validam argumentos passados para o método são não nulos | Formatos de nome de método permitidos (separados por `|` ):<br/> -Somente nome do método (inclui todos os métodos com o nome, independentemente do tipo ou namespace que o contém)<br/> -Nomes totalmente qualificados no [formato de ID de documentação](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)do símbolo, com um `M:` prefixo opcional | Nenhum | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Nomes de métodos de formatação de cadeia de caracteres adicionais | Formatos de nome de método permitidos (separados por `|` ):<br/> -Somente nome do método (inclui todos os métodos com o nome, independentemente do tipo ou namespace que o contém)<br/> -Nomes totalmente qualificados no [formato de ID de documentação](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)do símbolo, com um `M:` prefixo opcional | Nenhum | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Nomes de tipos, de modo que o tipo e todos os seus tipos derivados sejam excluídos para análise | Formatos de nome de símbolo permitidos (separados por `|` ):<br/> -Somente nome do tipo (inclui todos os tipos com o nome, independentemente do tipo ou namespace que a contém)<br/> -Nomes totalmente qualificados no [formato de ID de documentação](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)do símbolo, com um `T:` prefixo opcional | Nenhum | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Nomes de símbolos que são excluídos para análise | Formatos de nome de símbolo permitidos (separados por `|` ):<br/> -Somente nome do símbolo (inclui todos os símbolos com o nome, independentemente do tipo ou namespace que o contém)<br/> -Nomes totalmente qualificados no [formato de ID de documentação](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)do símbolo. Cada nome de símbolo requer um prefixo de tipo de símbolo, como prefixo "M:" para métodos, prefixo "T:" para tipos, prefixo "N:" para namespaces, etc.<br/> - `.ctor` para construtores e `.cctor` para construtores estáticos | Nenhum | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Descrição | Valores permitidos | Valor padrão | Regras configuráveis |
| - | - | - | - |
| Nomes de símbolos que não são permitidos no contexto da análise | Formatos de nome de símbolo permitidos (separados por `|` ):<br/> -Somente nome do símbolo (inclui todos os símbolos com o nome, independentemente do tipo ou namespace que o contém)<br/> -Nomes totalmente qualificados no [formato de ID de documentação](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)do símbolo. Cada nome de símbolo requer um prefixo de tipo de símbolo, como prefixo "M:" para métodos, prefixo "T:" para tipos, prefixo "N:" para namespaces, etc.<br/> - `.ctor` para construtores e `.cctor` para construtores estáticos | Nenhum | [CA1031](ca1031.md) |

## <a name="see-also"></a>Confira também

- [Configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Convenções de codificação .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
