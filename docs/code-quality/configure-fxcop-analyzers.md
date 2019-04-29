---
title: Configurar analisadores FxCop usando editorconfig
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ac751b7ec130b6bfbb18752c02b491b6c342f172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816905"
---
# <a name="configure-fxcop-analyzers"></a>Configurar analisadores FxCop

O [analisadores FxCop](install-fxcop-analyzers.md) consistem em regras "FxCop" mais importantes da análise de código estático, convertido em Analisadores de Roslyn. Você pode configurar os analisadores de código FxCop de duas maneiras:

- Com uma [conjunto de regras](#fxcop-analyzer-rule-sets), que permite habilitar ou desabilitar a regra e definir a gravidade quanto a violações de regra individual.

- Versão 2.6.3 da partir de [fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) de pacote do NuGet, por meio um [arquivo. editorconfig](#editorconfig-file). O [opções configuráveis](fxcop-analyzer-options.md) permitem que você refine as partes da sua base de código para analisar.

> [!TIP]
> Para obter informações sobre as diferenças entre a análise de código estático do FxCop e analisadores FxCop, consulte [analisadores FxCop perguntas frequentes sobre](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>Conjuntos de regras do analisador de FxCop

Uma maneira de configurar os analisadores FxCop é por meio de um XML *conjunto de regras*. Um conjunto de regras é um agrupamento de regras de análise de código que identificam problemas direcionados e condições específicas. Conjuntos de regras permitem que você habilitar ou desabilitar a regra e definir a gravidade quanto a violações de regra individual.

O pacote de NuGet do analisador de FxCop inclui conjuntos de regras predefinidas para as seguintes categorias de regra:

- design
- documentação
- facilidade de manutenção
- nomenclatura
- desempenho
- confiabilidade
- segurança
- uso

Para obter mais informações, consulte [conjuntos de regras para analisadores de Roslyn](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Arquivo EditorConfig

Você pode configurar regras do analisador de pela adição de pares chave-valor para um [. editorconfig](https://editorconfig.org) arquivo. Um arquivo de configuração pode ser [específicas a um projeto](#per-project-configuration) ou pode ser [compartilhado](#shared-configuration) entre dois ou mais projetos.

### <a name="per-project-configuration"></a>Configuração por projeto

Para habilitar a configuração do analisador com base em. editorconfig para um projeto específico, adicione uma *. editorconfig* arquivo para o diretório raiz do projeto.

> [!TIP]
> Você pode adicionar um arquivo. editorconfig ao seu projeto clicando com o projeto no **Gerenciador de soluções** e selecionando **Add** > **Novo Item**. No **Adicionar Novo Item** janela, insira **editorconfig** na caixa de pesquisa. Selecione o **(padrão) do arquivo de editorconfig** modelo e escolha **Add**.
>
> ![Adicionar item de editorconfig ao projeto no Visual Studio](media/add-editorconfig-file.png)

Atualmente não há nenhum suporte hierárquico para "combinar". editorconfig os arquivos que existem nos níveis de diretório diferente, por exemplo, o nível de solução e projeto.

### <a name="shared-configuration"></a>Configuração compartilhada

Você pode compartilhar um arquivo. editorconfig para configuração do analisador entre dois ou mais projetos, mas ele requer algumas etapas adicionais.

1. Salvar a *. editorconfig* arquivo em um local comum.

2. Criar uma *Props* arquivo com o seguinte conteúdo:

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

3. Adicione uma linha ao seu *. csproj* ou *. vbproj* arquivo para importar o *Props* arquivo que você criou na etapa anterior. Essa linha deve ser colocada antes de todas as linhas que importar o analisador de FxCop *Props* arquivos. Por exemplo, se o arquivo de. Props *editorconfig.props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Recarrega o projeto.

> [!NOTE]
> É possível configurar as regras FxCop herdadas (análise de código estático FxCop) usando um arquivo. editorconfig.

## <a name="option-scopes"></a>Escopos de opção

Cada opção pode ser configurada para todas as regras, para uma categoria de regras (por exemplo, nomenclatura ou Design) ou para uma regra específica.

### <a name="all-rules"></a>Todas as regras

A sintaxe para uma opção para todas as regras de configuração é da seguinte maneira:

|Sintaxe|Exemplo|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Categoria de regras

A sintaxe para a configuração de uma opção para um *categoria* de regras (por exemplo, nomenclatura, Design ou desempenho) é o seguinte:

|Sintaxe|Exemplo|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Regra específica

A sintaxe para a configuração de uma opção para uma regra específica é da seguinte maneira:

|Sintaxe|Exemplo|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Consulte também

- [Configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analisadores FxCop](install-fxcop-analyzers.md)
