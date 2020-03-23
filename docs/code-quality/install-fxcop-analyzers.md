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
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508765"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Instale analisadores FxCop no Visual Studio

A Microsoft criou um conjunto de analisadores, chamado [Microsoft.CodeAnalysis.FxCopAnalyzers,](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)que contém as regras mais importantes do "FxCop" a partir da análise de legados. Esses analisadores verificam seu código para problemas de segurança, desempenho e design, entre outros.

Você pode instalar esses analisadores FxCop como um pacote NuGet ou como uma extensão VSIX para o Visual Studio. Para saber mais sobre os prós e contras de cada um, consulte [o pacote NuGet vs. extensão VSIX](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>Pacote NuGet

::: moniker range=">=vs-2019"

No Visual Studio 2019 versão 16.3 e posterior, você pode instalar o pacote [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet diretamente da página de propriedades de análise de código do projeto:

1. Clique com o botão direito do mouse no nó do projeto no **Solution Explorer,** selecione **Propriedades**e selecione a guia **Análise de código.**

   ![Instale o pacote de analisadores FxCop da página de propriedades no Visual Studio](media/install-fxcop-properties-page.png)

2. Selecione **Instalar**.

   O Visual Studio instala a versão mais recente do pacote Microsoft.CodeAnalysis.FxCopAnalyzers. Os conjuntos aparecem no **Solution Explorer** em **Analyzers** > **de referências**.

   ![Nó de analisadores no Solution Explorer](media/solution-explorer-analyzers-node.png)

Se você estiver usando uma versão mais antiga do Visual Studio 2019, instale o pacote usando o [Console do Gerenciador de Pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou a UI do [Gerenciador de pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

::: moniker-end

::: moniker range="vs-2017"

1. [Determine qual versão do pacote analisador](#fxcopanalyzers-package-versions) instalar, com base na sua versão do Visual Studio.

2. Instale o pacote no Visual Studio usando o [Console do Gerenciador de Pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou a IU do [Gerenciador de pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > A página nuget.org para cada pacote analisador mostra o comando para colar no **Console do Gerenciador de Pacotes**. Há até um botão útil para copiar o texto para a área de transferência.
   >
   > ![NuGet.org página mostrando o comando Package Manager Console](media/nuget-package-manager-command.png)

   Os conjuntos de analisadores são instalados e aparecem no **Solution Explorer** em **Analyzers** > **de referências**.

::: moniker-end

### <a name="custom-installation"></a>Instalação personalizada

Para instalação personalizada, por exemplo, para especificar uma versão diferente do pacote, selecione o botão ellipsis (...) na página de propriedades de Análise de Código do projeto. Este botão abre o gerenciador de pacotes NuGet com "Microsoft.CodeAnalysis.FxCopAnalyzers" como a seqüência de pesquisa.

![Instale o pacote de analisadores FxCop personalizado da página de propriedades no Visual Studio](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Determine [qual versão do pacote analisador](#fxcopanalyzers-package-versions) instalar, com base na sua versão do Visual Studio. Você também pode instalar o pacote a partir da [ida e outra do Gerenciador](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)de pacotes .

### <a name="fxcopanalyzers-package-versions"></a>Versões do pacote FxCopAnalyzers

Use as seguintes diretrizes para determinar qual versão do pacote de analisadores FxCop instalará para sua versão do Visual Studio:

| Versão do Visual Studio | Versão do pacote do analisador FxCop |
| - | - |
| Visual Studio 2019 (todas as versões)<br />Visual Studio 2017 versão 15.8 e posterior | [Últimas](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 versão 15.5 a 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 versão 15.3 a 15.4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 versão 15.0 a 15.2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 atualização 2 e 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Atualização 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>Vsix

::: moniker range="vs-2017"

No Visual Studio 2017 versão 15.5 e posterior, você pode instalar a extensão [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) que contém todos os analisadores FxCop para projetos gerenciados.

1. No Visual Studio, selecione **Extensões e Atualizações de** **Ferramentas** > .

   A caixa de diálogo **Extensões e Atualizações** é aberta.

   > [!NOTE]
   > Alternativamente, baixe a extensão diretamente do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

2. ExpandA **o Online** no painel esquerdo e selecione **Visual Studio Marketplace**.

3. Na caixa de pesquisa, digite "análise de código", e procure a extensão **Microsoft Code Analysis 2017.**

   ![Extensão microsoft code analysis 2017](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

A extensão [Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) contém todos os analisadores FxCop para projetos gerenciados. Para instalar esta extensão:

1. No Visual Studio, selecione **Extensões** > **Gerenciar extensões**.

   A caixa de diálogo **Gerenciar extensões** é aberta.

   > [!NOTE]
   > Alternativamente, baixe a extensão diretamente do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019).

2. ExpandA **o Online** no painel esquerdo e selecione **Visual Studio Marketplace**.

3. Na caixa de pesquisa, digite "análise de código", e procure a extensão **Microsoft Code Analysis 2019.**

   ![Extensão microsoft code analysis 2019](media/manage-extensions-code-analysis.png)

::: moniker-end

4. Selecione **Baixar**.

   A extensão é baixada.

5. Selecione **OK** para fechar a caixa de diálogo e, em seguida, feche todas as instâncias do Visual Studio para iniciar o **VSIX Installer**.

   A caixa de diálogo **VSIX Installer** é aberta.

   ::: moniker range="vs-2017"

   ![Instalador VSIX para Análise de Código Microsoft](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Selecione **Modificar** para iniciar a instalação.

   Depois de um minuto ou dois, a instalação é concluída.

7. Selecione **Fechar**e abra o Visual Studio novamente.

::: moniker range="vs-2017"

Se você quiser verificar se a extensão está instalada, selecione**Extensões e Atualizações de** **Ferramentas** > . Na caixa de diálogo **Extensões e Atualizações,** selecione a categoria **Instalado** à esquerda e procure a extensão por nome.

::: moniker-end

::: moniker range=">=vs-2019"

Se você quiser verificar se a extensão está instalada, selecione **Extensões** > **Gerenciar extensões**. Na caixa de diálogo **Gerenciar extensões,** selecione a categoria **Instalado** à esquerda e, em seguida, procure a extensão por nome.

::: moniker-end

## <a name="see-also"></a>Confira também

- [Visão geral dos analisadores de código no Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Usar analisadores de código no Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrar da análise de legado para analisadores de código](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
