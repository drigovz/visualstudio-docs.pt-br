---
title: Desinstalando um VSPackage com o Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6cdf9023512f4225e2a8edcadcf589cb61547e24
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011808"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Desinstalando um VSPackage com o Windows Installer
Para a maior parte, Windows Installer pode desinstalar seu VSPackage apenas por "desfazer" o que era para instalar o VSPackage. As ações personalizadas discutidas em [comandos que devem ser executadas após a instalação](../../extensibility/internals/commands-that-must-be-run-after-installation.md) do também devem ser executadas após uma desinstalação. Como as chamadas para devenv.exe ocorrem pouco antes da ação padrão InstallFinalize para instalação e desinstalação, as entradas de tabela CustomAction e InstallExecuteSequence servem para ambos os casos.

> [!NOTE]
> Execute `devenv /setup` depois de desinstalar um pacote MSI.

 Como regra geral, se você adicionar ações personalizadas a um pacote de Windows Installer, deverá lidar com essas ações durante a desinstalação e a reversão. Se você adicionar ações personalizadas para registrar automaticamente seu VSPackage, por exemplo, você deve adicionar ações personalizadas para cancelar o registro também.

> [!NOTE]
> É possível que um usuário instale o VSPackage e, em seguida, desinstale as versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] com as quais ele está integrado. Você pode ajudar a garantir que a desinstalação do seu VSPackage funcione nesse cenário, eliminando ações personalizadas que executam código com dependências no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Manipulando condições de inicialização no momento da desinstalação
 A ação padrão LaunchConditions lê as linhas da tabela LaunchCondition para mostrar mensagens de erro se as condições não forem atendidas. Como as condições de inicialização são geralmente usadas para garantir que os requisitos do sistema sejam atendidos, geralmente você pode ignorar condições de inicialização durante a desinstalação adicionando a condição, `NOT Installed` , à linha LaunchConditions da tabela LaunchCondition.

 Uma alternativa é adicionar `OR Installed` às condições de inicialização que não são importantes durante a desinstalação. Isso garante que a condição sempre será verdadeira durante a desinstalação e, portanto, não exibirá a mensagem de erro de condição de inicialização.

> [!NOTE]
> `Installed` é a propriedade Windows Installer define quando detecta que seu VSPackage já foi instalado no sistema.

## <a name="see-also"></a>Veja também
- [Windows Installer](/previous-versions/ee231230(v=vs.100))
- [Detecção de requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md)