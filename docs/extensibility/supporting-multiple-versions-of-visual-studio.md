---
title: Suporte a múltiplas versões do Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699482"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Suporte a várias versões do Visual Studio
O termo *lado a lado* significa que você pode instalar e manter várias versões de um produto no mesmo computador. Para VSPackages, isso significa que um usuário pode ter várias versões do Visual Studio instaladas no mesmo computador. No entanto, você não pode ter versões lado a lado de seus VSPackages carregados em uma única versão do Visual Studio.

 Antes de tornar seu VSPackage capaz de ser carregado em versões lado a lado do Visual Studio, considere o seguinte:

- Você deve determinar qual estratégia de implementação lado a lado você deseja seguir.

   Para obter mais informações, consulte [Escolhendo Entre PACOTES VS compartilhados e versões](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Seus formatos de solução e arquivo de projeto devem se encaixar em sua estratégia de implementação.

   Para obter mais informações, consulte [Atualizar projetos personalizados](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) e [registrar extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- O instalador deve lidar com sua estratégia de implementação para que os componentes em versão, e também componentes compartilhados em todas as versões, sejam instalados e registrados corretamente.

   Para obter mais informações, consulte [Instalar pacotes VS com o Instalador do Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) e também o gerenciamento de [componentes.](../extensibility/internals/component-management.md)

  > [!NOTE]
  > A instalação de uma versão do Visual Studio também instala uma versão correspondente do .NET Framework. Por exemplo, a instalação do Visual Studio 2010 e do Visual Studio 2012 no mesmo computador também instala as versões 4.0 e 4.5 do .NET Framework, respectivamente.

## <a name="in-this-section"></a>Nesta seção
- [Escolhendo entre vspackages compartilhados e versados](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Explica como resolver problemas lado a lado em seu VSPackage.

- [Registrando extensões de nome](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) de arquivo para implantações lado a lado Descreve como o VSPackage pode registrar associações de arquivos em um cenário lado a lado.

## <a name="related-sections"></a>Seções relacionadas
- [Instalando VSPackages com o Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
