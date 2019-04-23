---
title: Instalar analisadores do Roslyn
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1afeb6f75648ce2ab1687fa9262ab28b658b0d70
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077804"
---
# <a name="install-net-compiler-platform-analyzers"></a>Instalar analisadores do .NET Compiler Platform

O Visual Studio inclui um conjunto principal de plataforma do compilador .NET (*Roslyn*) analisadores. Esses analisadores estão sempre ativados. Você pode instalar outros analisadores como pacotes NuGet ou como extensões do Visual Studio no *VSIX* arquivos.

## <a name="to-install-nuget-analyzer-packages"></a>Para instalar os pacotes do NuGet analyzer

1. Localize o pacote de analisador que você deseja instalar em www.nuget.org.

   Por exemplo, você talvez queira [instalar os analisadores FxCop Microsoft](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) para verificar seu código para problemas de segurança e desempenho, entre outros. Ou, instale [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/) para procurar problemas de estilo na Base de código.

2. Instale o pacote no Visual Studio, usando o [Package Manager Console](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) ou o [UI Gerenciador de pacotes](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > A página www.nuget.org para cada pacote de analisador mostra o comando Colar na **Package Manager Console**. Há até mesmo um botão útil para copiar o texto na área de transferência.

   Os assemblies do analisador são instalados e aparecem na **Gerenciador de soluções** sob **referências** > **analisadores**.

## <a name="to-install-vsix-analyzers"></a>Para instalar analisadores VSIX

::: moniker range="vs-2017"

1. No Visual Studio, selecione **ferramentas** > **extensões e atualizações**.

   A caixa de diálogo **Extensões e Atualizações** é aberta.

   > [!NOTE]
   > Como alternativa, você pode localizar e baixar a extensão de analisador diretamente a partir [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

::: moniker range=">=vs-2019"

1. No Visual Studio, selecione **extensões** > **gerenciar extensões**.

   O **gerenciar extensões** caixa de diálogo é aberta.

   > [!NOTE]
   > Como alternativa, você pode localizar e baixar a extensão de analisador diretamente a partir [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker-end

2. Expandir **Online** no painel esquerdo e, em seguida, selecione **Visual Studio Marketplace**.

3. Na caixa de pesquisa, digite o nome da extensão do analisador que você deseja instalar. Por exemplo, você talvez queira [instalar os analisadores FxCop Microsoft](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix) para verificar seu código para problemas de segurança e desempenho, entre outros.

4. Selecione **baixar**.

   A extensão é baixada.

5. Selecione **Okey** para fechar a caixa de diálogo e, em seguida, feche todas as instâncias do Visual Studio para iniciar o **instalador do VSIX**.

   O **instalador do VSIX** caixa de diálogo é aberta.

   ![Instalador do VSIX para análise de código da Microsoft](media/vsix-installer-code-analysis.png)

6. Selecione **modificar** para iniciar a instalação.

7. Depois de um ou dois minutos, a instalação for concluída. Selecione **Fechar**.

8. Abra o Visual Studio novamente.

::: moniker range="vs-2017"

Se você deseja verificar se a extensão é instalada, selecione **ferramentas** > **extensões e atualizações**. No **extensões e atualizações** caixa de diálogo, selecione o **instalado** categoria à esquerda e, em seguida, pesquise a extensão pelo nome.

::: moniker-end

::: moniker range=">=vs-2019"

Se você deseja verificar se a extensão é instalada, selecione **extensões** > **gerenciar extensões**. No **gerenciar extensões** caixa de diálogo, selecione o **instalado** categoria à esquerda e, em seguida, pesquise a extensão pelo nome.

::: moniker-end

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Usar Analisadores do Roslyn no Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores de Roslyn no Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Instalar analisadores do FxCop](../code-quality/install-fxcop-analyzers.md)