---
title: Configurar analisadores de qualidade de código .NET usando o editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a131b7d69eec61f9b9106f7a4274b3882c51f0ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800730"
---
# <a name="configure-net-code-quality-analyzers"></a>Configurar analisadores de qualidade de código .NET

Para determinados analisadores de qualidade de código .NET (aqueles cujas IDs de regra começam com `CA` ), você pode refinar a quais partes de sua base de código eles devem ser aplicadas por meio de [opções configuráveis](fxcop-analyzer-options.md). Cada opção é especificada adicionando um par chave-valor a um arquivo [EditorConfig](https://editorconfig.org) . Um arquivo de configuração pode ser específico para um arquivo, projeto, solução ou o repositório inteiro.

> [!TIP]
> Adicione um arquivo. editorconfig ao seu projeto clicando com o botão direito do mouse no projeto em **Gerenciador de soluções** e selecionando **Adicionar**  >  **novo item**. Na janela **Adicionar novo item** , insira **editorconfig** na caixa de pesquisa. Selecione o modelo de **arquivo editorconfig (padrão)** e escolha **Adicionar**.
>
> ![Adicionar arquivo editorconfig ao projeto no Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Para obter informações sobre como configurar a severidade de uma regra (por exemplo, se é um erro ou um aviso), consulte [definir severidade de regra em um arquivo EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Ou então, você pode escolher um dos [arquivos EditorConfig ou conjuntos de regras](analyzer-rule-sets.md) internos para habilitar ou desabilitar rapidamente uma categoria de regras.

::: moniker-end

O restante deste artigo aborda a sintaxe geral das [opções que refinam](fxcop-analyzer-options.md) o local em que os analisadores de qualidade de código .NET são aplicados.

## <a name="option-scopes"></a>Escopos de opção

Cada opção de refinamento pode ser configurada para todas as regras, para uma categoria de regras (por exemplo, nomenclatura ou Design) ou para uma regra específica.

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

## <a name="enabling-editorconfig-based-configuration"></a>Habilitando a configuração baseada em Editorconfig

A configuração do analisador baseado em EditorConfig pode ser habilitada para os seguintes escopos:

- Documentos (s) específicos
- Pastas específicas
- Projetos específicos
- Solução (ões) específica (s)
- Repositório inteiro

Para habilitar a configuração, adicione um arquivo *. editorconfig* com as opções no diretório correspondente. Esse arquivo também pode conter entradas de configuração de severidade de diagnóstico com base em EditorConfig. Veja [aqui](use-roslyn-analyzers.md#rule-severity) para obter mais detalhes.

## <a name="see-also"></a>Confira também

- [Opções de escopo de regra para analisadores de qualidade de código .NET](fxcop-analyzer-options.md)
- [Configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Convenções de codificação .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
