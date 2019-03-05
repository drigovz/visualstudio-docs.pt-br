---
title: Solucionar problemas de descoberta de modelo no Visual Studio | Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9ae6220ac38de7bf2edc7b5c305ecb377a46f18
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57323994"
---
# <a name="troubleshooting-template-installation"></a>Instalação do modelo de solução de problemas

Se você tiver problemas ao implantar seus modelos de projeto ou item, você pode habilitar o log de diagnóstico.

::: moniker range="vs-2017"

1. Crie um arquivo pkgdef na *Common7\IDE\CommonExtensions* pasta para a instalação. Por exemplo, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Crie um arquivo pkgdef na *Common7\IDE\CommonExtensions* pasta para a instalação. Por exemplo, *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Adicione o seguinte ao arquivo pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Abra uma [Prompt de comando do desenvolvedor](/dotnet/framework/tools/developer-command-prompt-for-vs) para sua instalação e execução `devenv /updateConfiguration`.

::: moniker range="vs-2017"

4. Inicie o Visual Studio e inicie as caixas de diálogo New Project e o novo Item para inicializar a ambas as árvores do modelo.

   O log de modelo agora aparece na **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid corresponde à ID da instalação da sua instância do Visual Studio). A inicialização de cada árvore modelo acrescenta as entradas nesse log.

::: moniker-end

::: moniker range=">=vs-2019"

4. Inicie o Visual Studio e inicie as caixas de diálogo New Project e o novo Item para inicializar a ambas as árvores do modelo.

   O log de modelo agora aparece na **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid corresponde à ID da instalação da sua instância do Visual Studio). A inicialização de cada árvore modelo acrescenta as entradas nesse log.

::: moniker-end

O arquivo de log contém as seguintes colunas:

- **FullPathToTemplate**, que tem os seguintes valores:

    - 1 para implantação baseada em manifesto

    - 0 para implantação baseada em disco

- **TemplateFileName**

- Outras propriedades de modelo

> [!NOTE]
> Para desabilitar o registro em log, remova o arquivo pkgdef ou alterar o valor de `EnableTemplateDiscoveryLog` à `dword:00000000`e, em seguida, execute `devenv /updateConfiguration` novamente.

## <a name="see-also"></a>Consulte também

- [Criando modelos personalizados de projeto e de item](creating-custom-project-and-item-templates.md)