---
title: A instância Experimental | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee3c1ef0aed082a0e4e0fb519c744fda376fc8e9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430137"
---
# <a name="the-experimental-instance"></a>A instância experimental
Para proteger seu ambiente de desenvolvimento do Visual Studio de aplicativos não testados que pode alterá-lo, VSSDK fornece um espaço de experimental que você pode usar para fazer experiências. Desenvolver novos aplicativos usando o Visual Studio como de costume, mas você pode executá-los usando essa instância experimental.

 Todos os aplicativos que tem um pacote VSIX inicia a instância experimental do Visual Studio no modo de depuração.

 Se você quiser iniciar a instância experimental do Visual Studio fora de uma solução específica, execute o seguinte comando na janela de comando:

 "*\<Caminho de instalação do visual studio >* \Common7\IDE\devenv.exe" RootSuffix Exp

> [!NOTE]
> A instância experimental é gravada no registro sob o `<version number>Exp` e `<version number>Exp_Config` nós. Por exemplo é a área de registro experimental do Visual Studio 2015
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 É recomendável que você execute sua extensão na instância experimental, enquanto estiver desenvolvendo-o. Quando você implanta a extensão, ele é executado na instância de desenvolvimento. Para obter mais informações sobre como registrar aplicativos, consulte [registrar VSPackages](../extensibility/internals/registering-vspackages.md).