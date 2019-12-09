---
title: Desinstalando um VSPackage com o Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8e92937e848d124c18dc91b9bdfa0f020f27f20
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722126"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Desinstalando um VSPackage com o Windows Installer
Para a maior parte, Windows Installer pode desinstalar seu VSPackage apenas por "desfazer" o que era para instalar o VSPackage. As ações personalizadas discutidas em [comandos que devem ser executadas após a instalação](../../extensibility/internals/commands-that-must-be-run-after-installation.md) do também devem ser executadas após uma desinstalação. Como as chamadas para devenv. exe ocorrem logo antes da ação InstallFinalize padrão para instalação e desinstalação, as entradas de tabela CustomAction e InstallExecuteSequence servem para ambos os casos.

> [!NOTE]
> Execute `devenv /setup` depois de desinstalar um pacote MSI.

 Como regra geral, se você adicionar ações personalizadas a um pacote de Windows Installer, deverá lidar com essas ações durante a desinstalação e a reversão. Se você adicionar ações personalizadas para registrar automaticamente seu VSPackage, por exemplo, você deve adicionar ações personalizadas para cancelar o registro também.

> [!NOTE]
> É possível que um usuário instale o VSPackage e, em seguida, desinstale as versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] com as quais ele está integrado. Você pode ajudar a garantir que a desinstalação do seu VSPackage funcione nesse cenário, eliminando ações personalizadas que executam código com dependências em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="handling-launch-conditions-at-uninstall-time"></a>Manipulando condições de inicialização no momento da desinstalação
 A ação padrão LaunchConditions lê as linhas da tabela LaunchCondition para mostrar mensagens de erro se as condições não forem atendidas. Como as condições de inicialização são geralmente usadas para garantir que os requisitos do sistema sejam atendidos, geralmente você pode ignorar condições de inicialização durante a desinstalação adicionando a condição, `NOT Installed`, à linha LaunchConditions da tabela LaunchCondition.

 Uma alternativa é adicionar `OR Installed` para iniciar condições que não são importantes durante a desinstalação. Isso garante que a condição sempre será verdadeira durante a desinstalação e, portanto, não exibirá a mensagem de erro de condição de inicialização.

> [!NOTE]
> `Installed` é a propriedade Windows Installer conjuntos quando detecta que seu VSPackage já foi instalado no sistema.

## <a name="see-also"></a>Consulte também
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Detectar os requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md)