---
title: Configurar analisadores do FxCop usando editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0152ae9f76ea1318f717c41a70d3d46351c9021a
ms.sourcegitcommit: 2bbcba305fd0f8800fd3d9aa16f7647ee27f3a4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300619"
---
# <a name="configure-fxcop-analyzers"></a>Configurar analisadores do FxCop

Os [analisadores do FxCop](install-fxcop-analyzers.md) consistem nas regras mais importantes do "FxCop" da análise de código estático, convertidas em analisadores Roslyn. Você pode configurar analisadores de código do FxCop de duas maneiras:

- Com um [conjunto de regras](#fxcop-analyzer-rule-sets), que permite habilitar ou desabilitar a regra e definir a severidade para violações de regra individuais.

- A partir da versão 2.6.3 do pacote NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) , por meio de um [arquivo. editorconfig](#editorconfig-file). As [opções configuráveis](fxcop-analyzer-options.md) permitem refinar as partes da base de código a serem analisadas.

> [!TIP]
> Para obter informações sobre as diferenças entre análise de código estático do FxCop e analisadores do FxCop, consulte [FAQ sobre analisadores do FxCop](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Conjuntos de regras do FxCop Analyzer

Uma maneira de configurar analisadores do FxCop é usando um *conjunto de regras*XML. Um conjunto de regras é um agrupamento de regras de análise de código que identificam problemas direcionados e condições específicas. Os conjuntos de regras permitem habilitar ou desabilitar a regra e definir a severidade para violações de regra individuais.

O pacote NuGet do FxCop Analyzer inclui conjuntos de regras predefinidos para as seguintes categorias de regra:

- design
- documentação
- facilidade de manutenção
- nomenclatura
- desempenho
- confiabilidade
- segurança
- uso

Para obter mais informações, consulte [conjuntos de regras para analisadores Roslyn](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Arquivo EditorConfig

Você pode configurar regras do analisador adicionando pares chave-valor a um arquivo [. editorconfig](https://editorconfig.org) . Um arquivo de configuração pode ser [específico para um projeto](#per-project-configuration) ou pode ser [compartilhado](#shared-configuration) entre dois ou mais projetos.

### <a name="per-project-configuration"></a>Configuração por projeto

Para habilitar a configuração do analisador baseado em editorconfig para um projeto específico, adicione um arquivo *. editorconfig* ao diretório raiz do projeto.

> [!TIP]
> Você pode adicionar um arquivo. editorconfig ao seu projeto clicando com o botão direito do mouse no projeto em **Gerenciador de soluções** e selecionando **Adicionar** > **novo item**. Na janela **Adicionar novo item** , insira **editorconfig** na caixa de pesquisa. Selecione o modelo de **arquivo editorconfig (padrão)** e escolha **Adicionar**.
>
> ![Adicionar item editorconfig ao projeto no Visual Studio](media/add-editorconfig-file.png)

Atualmente, não há suporte hierárquico para "combinar" arquivos. editorconfig que existem em diferentes níveis de diretório, por exemplo, a solução e o nível de projeto.

### <a name="shared-configuration"></a>Configuração compartilhada

Você pode compartilhar um arquivo. editorconfig para a configuração do analisador entre dois ou mais projetos, mas requer algumas etapas adicionais.

1. Salve o arquivo *. editorconfig* em um local comum.

2. Crie um arquivo *. props* com o seguinte conteúdo:

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. Adicione uma linha a seu arquivo *. csproj* ou *. vbproj* para importar o arquivo *. props* criado na etapa anterior. Essa linha deve ser colocada antes de qualquer linha que importe os arquivos do FxCop Analyzer *. props* . Por exemplo, se o arquivo. props for nomeado *editorconfig. props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Recarregue o projeto.

> [!NOTE]
> Você não pode configurar regras do FxCop herdadas (análise de código estático FxCop) usando um arquivo. editorconfig.

## <a name="option-scopes"></a>Escopos de opção

Cada opção pode ser configurada para todas as regras, para uma categoria de regras (por exemplo, nomenclatura ou Design) ou para uma regra específica.

### <a name="all-rules"></a>Todas as regras

A sintaxe para configurar uma opção para todas as regras é a seguinte:

|Sintaxe|Exemplo|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Categoria de regras

A sintaxe para configurar uma opção para uma *categoria* de regras (como nomenclatura, design ou desempenho) é a seguinte:

|Sintaxe|Exemplo|
|-|-|
| dotnet_code_quality. RuleCategory. optionName = optionvalue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Regra específica

A sintaxe para configurar uma opção para uma regra específica é a seguinte:

|Sintaxe|Exemplo|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Consulte também

- [Configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analisadores do FxCop](install-fxcop-analyzers.md)
- [Convenções de codificação .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
