---
title: Desinstalar um VSPackage com o Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6175b89db774598463d1f8ffaa03057ecb50a69b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441193"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Desinstalando um VSPackage com o Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Na maior parte, o Windows Installer pode desinstalar o VSPackage apenas por "Desfazer" o que fazia para instalar o VSPackage. As ações personalizadas discutidos [comandos que deve ser executado após a instalação](../../extensibility/internals/commands-that-must-be-run-after-installation.md) deve ser executado após a desinstalação também. Como as chamadas para devenv.exe ocorrerem logo antes da ação padrão de InstallFinalize para instalação e desinstalação, as entradas da tabela CustomAction e InstallExecuteSequence atender a ambos os casos.  
  
> [!NOTE]
> Executar `devenv /setup` depois de desinstalar um pacote MSI.  
  
 Como regra geral, se você adicionar ações personalizadas a um pacote do Windows Installer, você deve tratar essas ações durante a reversão e desinstalação. Se você adicionar ações personalizadas para se registrar o VSPackage, por exemplo, você deve adicionar ações personalizadas para cancelar o registro, muito.  
  
> [!NOTE]
> É possível que um usuário instalar o VSPackage e, em seguida, desinstalar as versões do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] com o qual ele está integrado. Você pode ajudar a garantir que a desinstalação do VSPackage funciona nesse cenário, eliminando as ações personalizadas que executam código com dependências no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Manipulação de condições de inicialização no momento da desinstalação  
 A ação padrão de LaunchConditions lê as linhas da tabela para mostrar o erro LaunchCondition mensagens se as condições não forem atendidas. Conforme as condições de inicialização geralmente são usadas para garantir que os requisitos de sistema são atendidos, você geralmente pode ignorar condições de inicialização durante a desinstalação, adicionando a condição, `NOT Installed`, à linha da tabela LaunchCondition LaunchConditions.  
  
 Uma alternativa é adicionar `OR Installed` para iniciar as condições que não são importantes durante a desinstalação. Isso garante que a condição sempre será true durante a desinstalação e, portanto, não exibirá a mensagem de erro de condição de inicialização.  
  
> [!NOTE]
> `Installed` é a propriedade que instalador do Windows define quando ele detecta que o VSPackage já foi instalado no sistema.  
  
## <a name="see-also"></a>Consulte também  
 [Windows Installer](http://msdn.microsoft.com/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Detectar os requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md)
