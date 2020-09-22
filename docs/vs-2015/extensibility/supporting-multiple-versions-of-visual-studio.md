---
title: Suporte a várias versões do Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f4393a88a689e2a923291ada37a9b6d85718db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838270"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Suporte a várias versões do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O termo de *lado a lado* significa que você pode instalar e manter várias versões de um produto no mesmo computador. Para VSPackages, isso significa que um usuário pode ter várias versões do Visual Studio instaladas no mesmo computador. No entanto, você não pode ter versões lado a lado de seu VSPackages carregadas em uma única versão do Visual Studio.

 Antes de tornar o VSPackage capaz de ser carregado em versões lado a lado do Visual Studio, considere o seguinte:

- Você deve determinar qual estratégia de implementação lado a lado você deseja seguir.

     Para obter mais informações, consulte [escolhendo entre VSPackages compartilhadas e com controle de versão](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Seus formatos de arquivo de solução e de projeto devem se ajustar à sua estratégia de implementação.

     Para obter mais informações, consulte [Atualizando projetos personalizados](../misc/upgrading-custom-projects.md) e [registrando extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- O instalador deve lidar com sua estratégia de implementação para que os componentes com controle de versão, e também os componentes compartilhados em todas as versões, sejam corretamente instalados e registrados.

     Para obter mais informações, consulte [instalando o VSPackages com Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e também [Gerenciamento de componentes](../extensibility/internals/component-management.md).

    > [!NOTE]
    > A instalação de uma versão do Visual Studio também instala uma versão correspondente do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Por exemplo, a instalação do Visual Studio 2010 e do Visual Studio 2012 no mesmo computador também instala as versões 4,0 e 4,5 do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , respectivamente.

## <a name="in-this-section"></a>Nesta seção
 [Escolhendo entre VSPackages compartilhadas e com controle de versão](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Explica como resolver problemas lado a lado no seu VSPackage.

 [Registrando extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Descreve como seu VSPackage pode registrar associações de arquivo em um cenário lado a lado.

## <a name="related-sections"></a>Seções relacionadas
 [Instalando o VSPackages](../misc/installing-vspackages.md) Discute como criar e instalar o VSPackages e como dar suporte a usuários que executam várias versões do Visual Studio ao mesmo tempo.
