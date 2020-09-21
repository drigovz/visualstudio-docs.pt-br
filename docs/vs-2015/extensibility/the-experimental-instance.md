---
title: A instância experimental | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ee3c1ef0aed082a0e4e0fb519c744fda376fc8e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838360"
---
# <a name="the-experimental-instance"></a>A instância experimental
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para proteger seu ambiente de desenvolvimento do Visual Studio de aplicativos não testados que podem alterá-lo, o VSSDK fornece um espaço experimental que você pode usar para experimentar. Você desenvolve novos aplicativos usando o Visual Studio como de costume, mas os executa usando essa instância experimental.  
  
 Cada aplicativo que tem um pacote VSIX inicia a instância experimental do Visual Studio no modo de depuração.  
  
 Se você quiser iniciar a instância experimental do Visual Studio fora de uma solução específica, execute o seguinte comando na janela de comando:  
  
 Exp. de *\<Visual studio installation path>* /RootSuffix "\Common7\IDE\devenv.exe"  
  
> [!NOTE]
> A instância experimental é gravada no registro nos `<version number>Exp` nós e `<version number>Exp_Config` . Por exemplo, a área de registro experimental do Visual Studio 2015 é  
>   
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` e `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Recomendamos que você execute sua extensão na instância experimental enquanto estiver desenvolvendo. Quando você implanta a extensão, ela é executada na instância de desenvolvimento. Para obter mais informações sobre como registrar aplicativos, consulte [registrando VSPackages](../extensibility/internals/registering-vspackages.md).
