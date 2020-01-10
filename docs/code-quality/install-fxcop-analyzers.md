---
title: Instalar analisadores do FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 06362bcf00bc35fdef701e26fe03694b038e88b1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587453"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Instalar analisadores do FxCop no Visual Studio

A Microsoft criou um conjunto de analisadores, chamado [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), que contém as regras mais importantes do "FxCop" da análise herdada. Esses analisadores verificam o código em busca de problemas de segurança, desempenho e design, entre outros.

Você pode instalar esses analisadores do FxCop como um pacote NuGet ou como uma extensão VSIX para o Visual Studio. Para saber mais sobre os prós e contras de cada um, consulte [pacote NuGet versus extensão VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>Pacote NuGet

::: moniker range=">=vs-2019"

No Visual Studio 2019 versão 16,3 e posterior, você pode instalar o pacote NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) diretamente da página de propriedades de análise de código do projeto:

1. Clique com o botão direito do mouse no nó do projeto em **Gerenciador de soluções**, selecione **Propriedades**e, em seguida, selecione a guia **análise de código** .

   ![Instalar o pacote de analisadores do FxCop na página de propriedades no Visual Studio](media/install-fxcop-properties-page.png)

2. Clique em **Instalar**.

   O Visual Studio instala a versão mais recente do pacote Microsoft. CodeAnalyzers. FxCopAnalyzers. Os assemblies aparecem em **Gerenciador de soluções** em **referências** > **analisadores**.

   ![Nó de analisadores no Gerenciador de Soluções](media/solution-explorer-analyzers-node.png)

Se você estiver usando uma versão mais antiga do Visual Studio 2019, instale o pacote usando o [console do Gerenciador de pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou a [interface do usuário do Gerenciador de pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

::: moniker-end

::: moniker range="vs-2017"

1. [Determine qual versão do pacote do analisador](#fxcopanalyzers-package-versions) instalar, com base na sua versão do Visual Studio.

2. Instale o pacote no Visual Studio usando o [console do Gerenciador de pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou a [interface do usuário do Gerenciador de pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > A página nuget.org para cada pacote do analisador mostra o comando a ser colado no **console do Gerenciador de pacotes**. Há até mesmo um botão útil para copiar o texto na área de transferência.
   >
   > ![Página NuGet.org mostrando o comando do console do Gerenciador de pacotes](media/nuget-package-manager-command.png)

   Os assemblies do analisador são instalados e aparecem em **Gerenciador de soluções** em **referências** > **analisadores**.

::: moniker-end

### <a name="custom-installation"></a>Instalação personalizada

Para instalação personalizada, por exemplo, para especificar uma versão diferente do pacote, selecione o botão de reticências (...) na página de propriedades de análise de código do projeto. Esse botão abre o Gerenciador de pacotes NuGet com "Microsoft. CodeAnalysis. FxCopAnalyzers" como a cadeia de caracteres de pesquisa.

![Instalar pacote de analisadores do FxCop personalizado na página de propriedades no Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Determine [qual versão do pacote do analisador](#fxcopanalyzers-package-versions) instalar, com base na sua versão do Visual Studio. Você também pode instalar o pacote da [interface do usuário do Gerenciador de pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

### <a name="fxcopanalyzers-package-versions"></a>Versões do pacote FxCopAnalyzers

Use as diretrizes a seguir para determinar qual versão do pacote de analisadores do FxCop instalar para sua versão do Visual Studio:

| Versão do Visual Studio | Versão do pacote do FxCop Analyzer |
| - | - |
| Visual Studio 2019 (todas as versões)<br />Visual Studio 2017 versão 15,8 e posterior | [latest](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 versão 15,5 a 15,7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 versão 15,3 a 15,4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 versão 15,0 a 15,2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 atualização 2 e 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Atualização 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

No Visual Studio 2017 versão 15,5 e posterior, você pode instalar a extensão do [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) que contém todos os analisadores do FxCop para projetos gerenciados.

1. No Visual Studio, selecione **ferramentas** > **extensões e atualizações**.

   A caixa de diálogo **Extensões e Atualizações** é aberta.

   > [!NOTE]
   > Como alternativa, baixe a extensão diretamente do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. Expanda **online** no painel esquerdo e, em seguida, selecione **Visual Studio Marketplace**.

3. Na caixa de pesquisa, digite "análise de código" e procure a extensão **Microsoft Code analysis 2017** .

   ![Extensão do Microsoft Code Analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

A extensão do [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) contém todos os analisadores do FxCop para projetos gerenciados. Para instalar esta extensão:

1. No Visual Studio, selecione **extensões** > **gerenciar extensões**.

   A caixa de diálogo **gerenciar extensões** é aberta.

   > [!NOTE]
   > Como alternativa, baixe a extensão diretamente do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. Expanda **online** no painel esquerdo e, em seguida, selecione **Visual Studio Marketplace**.

3. Na caixa de pesquisa, digite "análise de código" e procure a extensão **Microsoft Code analysis 2019** .

   ![Extensão do Microsoft Code Analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Selecione **Baixar**.

   A extensão é baixada.

5. Selecione **OK** para fechar a caixa de diálogo e feche todas as instâncias do Visual Studio para iniciar o **instalador VSIX**.

   A caixa de diálogo **instalador do VSIX** é aberta.

   ::: moniker range="vs-2017"

   ![Instalador do VSIX para análise de código da Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Selecione **Modificar** para iniciar a instalação.

   Após um ou dois minutos, a instalação é concluída.

7. Selecione **fechar**e abra o Visual Studio novamente.

::: moniker range="vs-2017"

Se você quiser verificar se a extensão está instalada, selecione **ferramentas** > **extensões e atualizações**. Na caixa de diálogo **extensões e atualizações** , selecione a categoria **instalado** à esquerda e, em seguida, procure a extensão por nome.

::: moniker-end

::: moniker range=">=vs-2019"

Se você quiser verificar se a extensão está instalada, selecione **extensões** > **gerenciar extensões**. Na caixa de diálogo **gerenciar extensões** , selecione a categoria **instalado** à esquerda e, em seguida, procure a extensão por nome.

::: moniker-end

## <a name="see-also"></a>Veja também

- [Visão geral dos analisadores de código no Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Usar analisadores de código no Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrar da análise herdada para analisadores de código](../code-quality/fxcop-analyzers.yml)
