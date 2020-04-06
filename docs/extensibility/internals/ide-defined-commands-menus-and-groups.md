---
title: Comandos, menus e grupos definidos pelo IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707723"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Grupos, menus e comandos definidos pelo IDE
Muitos menus, comandos e grupos de comando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] já estão definidos para uso pelo IDE. Esses comandos também estão disponíveis para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]seu uso quando você estender .

## <a name="finding-environment-defined-commands"></a>Encontrando comandos definidos pelo ambiente
 Os comandos do ambiente são definidos em um conjunto de quatro arquivos .vsct:

- CompartilhadoCmdDef.vsct

- CompartilhadoCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Esses arquivos estão localizados no\\ * \<caminho de instalação do Visual Studio SDK>* \VisualStudioIntegration\Common\Inc . Esses arquivos fornecem as definições e GUIDs dos menus e grupos que você pode usar no arquivo de configuração da tabela de comando (.vsct) do seu VSPackage como recipientes para seus próprios menus, grupos e comandos.

## <a name="in-this-section"></a>Nesta seção
- [GUIDs e IDs de menus do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Dá aos valores GUID e ID dos menus na barra de menus do Visual Studio e dos grupos que eles contêm.

- [GUIDs e IDs de barras de ferramentas do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Dá aos valores GUID e ID de barras de ferramentas no Visual Studio IDE e dos grupos que contêm.

- [GUIDs e IDs de comandos do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Dá aos valores GUID e ID de comandos definidos pelo Visual Studio IDE.

## <a name="see-also"></a>Confira também
- [Arquivos .Vsct (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Comandos definidos pelo IDE para estender sistemas de projeto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
