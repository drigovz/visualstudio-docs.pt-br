---
title: Solucionar problemas de descoberta de modelo no Visual Studio | Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba4501662e483af4ae357d75ca55f1a9cbac2329
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017988"
---
# <a name="troubleshooting-template-installation"></a>Instalação do modelo de solução de problemas

Se você tiver problemas ao implantar seus modelos de projeto ou item, você pode habilitar o log de diagnóstico.

1. Crie um arquivo pkgdef na pasta Common7\IDE\CommonExtensions para a instalação (por exemplo, C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) com o seguinte conteúdo:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Abra um Prompt de comando "desenvolvedores" para a instalação por meio de pesquisa na pesquisa do Windows e execute `devenv /updateConfiguration`.

1. Inicie o Visual Studio e inicie as caixas de diálogo New Project e o novo Item para inicializar a ambas as árvores do modelo. O log de modelo agora aparece na **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid corresponde à ID da instalação da sua instância do Visual Studio). A inicialização de cada árvore modelo acrescenta as entradas nesse log.

O arquivo de log contém as seguintes colunas:

- **FullPathToTemplate**, que tem os seguintes valores:

    - 1 para implantação baseada em manifesto

    - 0 para implantação baseada em disco

- **TemplateFileName**

- Outras propriedades de modelo

> [!NOTE]
> Para desabilitar o registro em log, remova o arquivo pkgdef ou alterar o valor de `EnableTemplateDiscoveryLog` à `dword:00000000`e, em seguida, execute `devenv /updateConfiguration` novamente.

## <a name="see-also"></a>Consulte também

[Criando modelos personalizados de projeto e de item](creating-custom-project-and-item-templates.md)