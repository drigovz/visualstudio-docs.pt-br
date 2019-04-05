---
title: Instalar VSPackages com o Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d5b22479996bca6ee69c1334d79f012024b865d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926782"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalando VSPackages com o Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Integrando o VSPackage em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] requer mais do que apenas copiar arquivos para um computador do usuário. Instalador do VSPackage deve instalar o VSPackage e seus arquivos dependentes e registre-se e integrá-los em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. O VSPackage pode tirar proveito dos recursos de integração como exibir um ícone no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] inicial da tela e a caixa de diálogo sobre.  
  
 Arquivos do Microsoft Windows Installer são a maneira recomendada para distribuir seu VSPackages. Pacotes do Windows Installer de fácil de usar podem ser executados em qualquer sistema operacional do Windows com suporte pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Para obter mais informações, consulte [Windows Installer](http://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Noções básicas do Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Fornece uma visão geral do Windows Installer.  
  
 [Cenários de configuração do VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Discute as diferentes maneiras que você pode dar suporte a instalações lado a lado de seu os VSPackages e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Criar um pacote do Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Fornece uma visão geral das etapas comuns instaladores seguem para instalar corretamente e integrar os VSPackages em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Detectar os requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md)  
 Descreve como um instalador pode detectar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e seus componentes e cancelar a instalação se VSPackage requisitos não forem atendidos.  
  
 [Gerenciamento de componente](../../extensibility/internals/component-management.md)  
 Discute como desenvolver um instalador que manterá a integridade de versões anteriores do produto.  
  
 [Escolher o diretório de instalação para um VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Resume as opções para localizar os VSPackages.  
  
 [Registrar o VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Discute como os VSPackages são registrados no momento da instalação e por que o auto-registro é uma má ideia.  
  
 [Implantar tipos de projeto](../../extensibility/internals/deploying-project-types.md)  
 Discute como usar o novo agregador de tipo de projeto para tipos de projeto de código gerenciado.  
  
 [Como: Gerar informações de registro para um instalador](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Explica como usar RegPkg.exe para gerar um manifesto de registro para um VSPackage gerenciado.  
  
 [Comandos que devem ser executados após a instalação](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Explica como executar comandos de pós-instalação para integrar os VSPackages em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Desinstalar um VSPackage com o Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Descreve as etapas que o instalador deve executar quando os usuários desinstalarem o VSPackage.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Instalando VSPackages](../../misc/installing-vspackages.md)  
 Discute como compilar e instalar VSPackages e como dar suporte a usuários que estão executando várias versões de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ao mesmo tempo.
