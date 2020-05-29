---
title: Configurar analisadores do FxCop usando editorconfig
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 182042db9a744d037e295a8448f8c49a9c7b3a97
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184790"
---
# <a name="configure-fxcop-analyzers"></a>Configurar analisadores FxCop

O [pacote de analisadores do FxCop](install-fxcop-analyzers.md) consiste nas regras mais importantes do "FxCop" da análise herdada convertida em analisadores de código baseados em .net Compiler Platform. Para determinadas regras do FxCop, você pode refinar a quais partes de sua base de código elas devem ser aplicadas por meio de [opções configuráveis](fxcop-analyzer-options.md). Cada opção é especificada adicionando um par chave-valor a um arquivo [EditorConfig](https://editorconfig.org) . Um arquivo de configuração pode ser [específico para um projeto](#per-project-configuration) ou pode ser [compartilhado](#shared-configuration) entre dois ou mais projetos.

> [!TIP]
> Adicione um arquivo. editorconfig ao seu projeto clicando com o botão direito do mouse no projeto em **Gerenciador de soluções** e selecionando **Adicionar**  >  **novo item**. Na janela **Adicionar novo item** , insira **editorconfig** na caixa de pesquisa. Selecione o modelo de **arquivo editorconfig (padrão)** e escolha **Adicionar**.
>
> ![Adicionar arquivo editorconfig ao projeto no Visual Studio](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Para obter informações sobre como configurar a severidade de uma regra (por exemplo, se é um erro ou um aviso), consulte [definir severidade de regra em um arquivo EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Ou então, você pode escolher um dos [arquivos EditorConfig ou conjuntos de regras](analyzer-rule-sets.md) internos para habilitar ou desabilitar rapidamente uma categoria de regras.

::: moniker-end

O restante deste artigo aborda a sintaxe geral das [opções que refinam](fxcop-analyzer-options.md) o local em que as regras do FxCop são aplicadas.

> [!NOTE]
> Não é possível configurar regras do FxCop herdadas usando um arquivo EditorConfig. Para obter informações sobre as diferenças entre análise herdada e analisadores de FxCop, consulte [FAQ sobre analisadores do FxCop](fxcop-analyzers-faq.md).

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

### <a name="vs2019-163-and-later--fxcopanalyzers-package-version-33x-and-later"></a>VS2019 16,3 e posterior + FxCopAnalyzers pacote versão 3.3. x e posterior

A configuração do analisador baseado em EditorConfig pode ser habilitada para os seguintes escopos:

- Documentos (s) específicos
- Pastas específicas
- Projetos específicos
- Solução (ões) específica (s)
- Repositório inteiro

Para habilitar a configuração, adicione um arquivo *. editorconfig* com as opções no diretório correspondente. Esse arquivo também pode conter entradas de configuração de severidade de diagnóstico com base em EditorConfig. Clique [aqui](use-roslyn-analyzers.md#rule-severity) para obter mais detalhes.

### <a name="prior-to-vs2019-163-or-using-an-fxcopanalyzers-package-version-prior-to-33x"></a>Antes do VS2019 16,3 ou usando uma versão do pacote FxCopAnalyzers anterior à 3.3. x

#### <a name="per-project-configuration"></a>Configuração por projeto

Para habilitar a configuração do analisador baseado em EditorConfig para um projeto específico, adicione um arquivo *. EditorConfig* ao diretório raiz do projeto.

#### <a name="shared-configuration"></a>Configuração compartilhada

Você pode compartilhar um arquivo. editorconfig para a configuração do FxCop Analyzer entre dois ou mais projetos, mas ele requer algumas etapas adicionais.

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
> O local de compartilhamento arbitrário do arquivo EditorConfig descrito aqui se aplica somente à configuração do escopo de determinadas regras do analisador do FxCop. Para outras configurações, como severidade da regra, configurações gerais do editor e estilo de código, o arquivo EditorConfig sempre deve ser colocado na pasta do projeto ou em uma pasta pai.

## <a name="see-also"></a>Veja também

- [Opções de escopo da regra para analisadores do FxCop](fxcop-analyzer-options.md)
- [Configuração do analisador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [Analisadores FxCop](install-fxcop-analyzers.md)
- [Convenções de codificação .NET para EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
