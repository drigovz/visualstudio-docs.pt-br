---
title: Instalar analisadores do FxCop
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b5cb0fa5985cbc923713330289d7f83ed1fd954e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551097"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Instalar analisadores do FxCop no Visual Studio

A Microsoft criou um conjunto de analisadores, chamado [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), que contém as regras mais importantes do "FxCop" da análise herdada. Esses analisadores verificam o código em busca de problemas de segurança, desempenho e design, entre outros.

Você pode instalar esses analisadores do FxCop como um pacote NuGet ou como uma extensão VSIX para o Visual Studio. Para saber mais sobre os prós e contras de cada [um, consulte pacote NuGet versus Extensão](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)do VSIX.

## <a name="to-install-fxcop-analyzers-as-a-nuget-package"></a>Para instalar os analisadores do FxCop como um pacote NuGet

1. [Determine qual versão do pacote](#fxcopanalyzers-package-versions) do analisador instalar, com base na sua versão do Visual Studio.

2. Instale o pacote no Visual Studio usando o console do [Gerenciador de pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou a [interface do usuário do Gerenciador de pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > A página nuget.org para cada pacote do analisador mostra o comando a ser colado no **console do Gerenciador de pacotes**. Há até mesmo um botão útil para copiar o texto na área de transferência.
   >
   > ![Página NuGet.org mostrando o comando do console do Gerenciador de pacotes](media/nuget-package-manager-command.png)

   Os assemblies do analisador são instalados e aparecem em **Gerenciador de soluções** em**analisadores**de **referências** > .

   ![Nó de analisadores no Gerenciador de Soluções](media/solution-explorer-analyzers-node.png)

### <a name="fxcopanalyzers-package-versions"></a>Versões do pacote FxCopAnalyzers

Use as diretrizes a seguir para determinar qual versão do pacote de analisadores do FxCop instalar para sua versão do Visual Studio:

| Versão do Visual Studio | Versão do pacote do FxCop Analyzer |
| - | - |
| Visual Studio 2019 (todas as versões)<br />Visual Studio 2017 versão 15,8 e posterior | [2.9.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.3) |
| Visual Studio 2017 versão 15,5 a 15,7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 versão 15,3 a 15,4 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 versão 15,0 a 15,2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 atualização 2 e 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Atualização 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="to-install-fxcop-analyzers-as-a-vsix"></a>Para instalar os analisadores do FxCop como um VSIX

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

4. Selecione **baixar**.

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

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores de código no Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Usar analisadores de código no Visual Studio](../code-quality/use-roslyn-analyzers.md)
- [Migrar da análise herdada para analisadores de código](../code-quality/fxcop-analyzers.yml)
