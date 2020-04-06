---
title: Descoberta de modelo de solução de solucionar problemas no Visual Studio | Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698929"
---
# <a name="troubleshooting-template-installation"></a>Instalação do modelo de solução de problemas

Se você encontrar problemas para implantar seus modelos de projeto ou itens, você pode habilitar o registro de diagnóstico.

::: moniker range="vs-2017"

1. Crie um arquivo pkgdef na pasta *Common7\IDE\CommonExtensions* para sua instalação. Por exemplo, *C:\Arquivos de programa (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Crie um arquivo pkgdef na pasta *Common7\IDE\CommonExtensions* para sua instalação. Por exemplo, *C:\Arquivos de programa (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Adicione o seguinte ao arquivo pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Abra um prompt de comando `devenv /updateConfiguration`do [desenvolvedor](/dotnet/framework/tools/developer-command-prompt-for-vs) para sua instalação e execução .

::: moniker range="vs-2017"

4. Abra o Visual Studio e lance as caixas de diálogo Novo Projeto e Novo Item para inicializar ambas as árvores de modelo.

   O log de modelo agora aparece em **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid corresponde ao ID de instalação da sua instância do Visual Studio). Cada modelo de inicialização da árvore anexa entradas a este log.

::: moniker-end

::: moniker range=">=vs-2019"

4. Abra o Visual Studio e lance o **Create a new project** and New **Item** dialog boxes para inicializar ambas as árvores de modelo.

   O log de modelo agora aparece em **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid corresponde ao ID de instalação da sua instância do Visual Studio). Cada modelo de inicialização da árvore anexa entradas a este log.

::: moniker-end

O arquivo de registro contém as seguintes colunas:

- **FullPathToTemplate**, que tem os seguintes valores:

  - 1 para implantação baseada em manifesto

  - 0 para implantação baseada em disco

- **Nome do arquivo do modelo**

- Outras propriedades do modelo

> [!NOTE]
> Para desativar o registro, remova o arquivo pkgdef `EnableTemplateDiscoveryLog` `dword:00000000`ou altere `devenv /updateConfiguration` o valor de para , e depois seja executado novamente.

## <a name="see-also"></a>Confira também

- [Criando modelos personalizados de projetos e itens](creating-custom-project-and-item-templates.md)
