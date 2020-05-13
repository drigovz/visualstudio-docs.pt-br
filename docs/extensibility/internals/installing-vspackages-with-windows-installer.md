---
title: Instalando pacotes VS com instalador do Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707457"
---
# <a name="installing-vspackages-with-windows-installer"></a>Instalando VSPackages com o Windows Installer
Integrar seu VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] em requer mais do que apenas copiar arquivos no computador de um usuário. O instalador do VSPackage deve instalar o VSPackage e seus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]arquivos dependentes e registrá-los e integrá-los em . O VSPackage pode aproveitar os recursos de integração, como exibir um ícone na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tela de respingo e na caixa de diálogo Sobre.

 Os arquivos do Microsoft Windows Installer são a maneira recomendada de distribuir seus VSPackages. Pacotes fáceis de usar do Windows Installer podem ser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]executados em qualquer sistema operacional Windows suportado por . Para obter mais informações, consulte [o Instalador do Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).

## <a name="in-this-section"></a>Nesta seção
- [Noções básicas do Windows Installer](../../extensibility/internals/windows-installer-basics.md)

 Fornece uma visão geral do Instalador do Windows.

- [Cenários de instalação do VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Discute diferentes maneiras de suportar instalações lado a lado [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de seus VSPackages e .

- [Criação de um pacote do Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Fornece uma visão geral das etapas típicas que os instaladores seguem para instalar e integrar corretamente vsPackages em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Detecção de requisitos do sistema](../../extensibility/internals/detecting-system-requirements.md)

 Descreve como um instalador [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pode detectar e seus componentes e cancelar a configuração se os requisitos do VSPackage não forem atendidos.

- [Gerenciamento de componentes](../../extensibility/internals/component-management.md)

 Discute como desenvolver um instalador que manterá a integridade das versões anteriores do produto.

- [Escolhendo o diretório de instalação de um VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Resume as opções para localizar VSPackages.

- [Registro do VSPackage](../../extensibility/internals/vspackage-registration.md)

 Discute como os VSPackages são registrados no momento da instalação e por que o auto-registro é uma má ideia.

- [Tipos de projeto de implantação](../../extensibility/internals/deploying-project-types.md)

 Discute como usar o novo agregador do tipo projeto para tipos de projeto de código gerenciado.

- [Como gerar informações de registro para um instalador](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Explica como usar o RegPkg.exe para gerar um manifesto de registro para um VSPackage gerenciado.

- [Comandos que precisam ser executados após a instalação](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Explica como executar comandos pós-instalação para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]integrar VSPackages em .

- [Desinstalando um VSPackage com o Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Descreve as etapas que o instalador deve executar quando os usuários desinstalam o VSPackage.
