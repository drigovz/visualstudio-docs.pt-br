---
title: Desinstalando um VSPackage com o Instalador do Windows | Microsoft Docs
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
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704275"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Desinstalando um VSPackage com o Windows Installer
Na maioria das vezes, o Windows Installer pode desinstalar seu VSPackage apenas "desfazendo" o que fez para instalar o seu VSPackage. As ações [personalizadas discutidas nos comandos que devem ser executados após a instalação](../../extensibility/internals/commands-that-must-be-run-after-installation.md) também devem ser executadas após uma desinstalação. Como as chamadas para devenv.exe ocorrem pouco antes da ação padrão InstallFinalize para instalação e desinstalação, as entradas da tabela CustomAction e InstallExecuteSequence servem a ambos os casos.

> [!NOTE]
> Execute `devenv /setup` depois de desinstalar um pacote MSI.

 Como regra geral, se você adicionar ações personalizadas a um pacote do Windows Installer, você deve lidar com essas ações durante a desinstalação e a reversão. Se você adicionar ações personalizadas para auto-registrar seu VSPackage, por exemplo, você deve adicionar ações personalizadas para desregistrá-lo também.

> [!NOTE]
> É possível que um usuário instale seu VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e, em seguida, desinstale as versões com as quais ele está integrado. Você pode ajudar a garantir que a desinstalação do VSPackage funcione nesse [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]cenário, eliminando ações personalizadas que executam código com dependências .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Lidar com as condições de lançamento no tempo de desinstalação
 A ação padrão LaunchConditions lê as linhas da tabela LaunchCondition para mostrar mensagens de erro se as condições não forem atendidas. Como as condições de lançamento são geralmente usadas para garantir que os requisitos do sistema `NOT Installed`sejam atendidos, você geralmente pode pular as condições de lançamento durante a desinstalação adicionando a condição, à linha LaunchConditions da tabela LaunchCondition.

 Uma alternativa é `OR Installed` adicionar às condições de lançamento que não são importantes durante a desinstalação. Isso garante que a condição será sempre verdadeira durante a desinstalação e, portanto, não exibirá a mensagem de erro da condição de lançamento.

> [!NOTE]
> `Installed`é a propriedade que o Windows Installer define quando detecta que o vsPackage já foi instalado no sistema.

## <a name="see-also"></a>Confira também
- [Instalador do Windows](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Detecção de requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md)
