---
title: A Instância Experimental | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699033"
---
# <a name="the-experimental-instance"></a>A instância experimental
Para proteger seu ambiente de desenvolvimento do Visual Studio de aplicativos não testados que podem alterá-lo, o VSSDK fornece um espaço experimental que você pode usar para experimentar. Você desenvolve novos aplicativos usando o Visual Studio como de costume, mas você executá-los usando esta instância experimental.

 Cada aplicativo que tem um pacote VSIX lança a instância experimental do Visual Studio no modo de depuração.

 Se você quiser iniciar a instância experimental do Visual Studio fora de uma solução específica, execute o seguinte comando na janela de comando:

 "*\<Caminho de instalação do estúdio visual>* \Common7\IDE\devenv.exe" /RootSuffix Exp

> [!NOTE]
> A instância experimental é escrita `<version number>Exp` no `<version number>Exp_Config` registro sob os nós e nós. Por exemplo, a área de registro experimental do Visual Studio 2015 é
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Recomendamos que você execute sua extensão na instância experimental enquanto estiver desenvolvendo-a. Quando você implanta a extensão, ela é executada na instância de desenvolvimento. Para obter mais informações sobre como registrar aplicativos, consulte [Registrando VSPackages](../extensibility/internals/registering-vspackages.md).
