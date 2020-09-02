---
title: Implantação do ClickOnce no Windows Vista | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675468"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Implantação do ClickOnce no Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A criação de aplicativos no Visual Studio para controle de conta de usuário (UAC) no Windows Vista normalmente gera um manifesto incorporado, codificado como dados XML binários no arquivo executável do aplicativo. Como o ClickOnce e os aplicativos COM sem registro exigem um manifesto externo, o Visual Studio gera um arquivo para esses tipos de projetos que contêm os dados do UAC em vez de um manifesto incorporado. Por padrão, o Visual Studio usa informações de um arquivo chamado App. manifest para gerar informações externas do manifesto do UAC (para implantação COM ClickOnce e sem registro) ou para incorporá-las no arquivo executável do aplicativo (para todos os outros casos). O Visual Studio fornece as seguintes opções para a geração de manifesto:  
  
- Use um manifesto inserido. Insira dados do UAC no arquivo executável do aplicativo e execute como usuário normal.  
  
   Essa é a configuração padrão (a menos que você use o ClickOnce). Essa configuração dará suporte à maneira normal em que o Visual Studio opera no Windows Vista; ou seja, a geração de um manifesto interno e externo, usando `AsInvoker` .  
  
- Use um manifesto externo. Gere um manifesto externo usando o app. manifest.  
  
   Isso gera apenas o manifesto externo usando as informações em app. manifest. Quando você publica um aplicativo usando o ClickOnce ou o COM sem registro, o Visual Studio adiciona o app. manifest ao projeto e adiciona essa opção.  
  
- Não use nenhum manifesto. Crie o aplicativo sem um manifesto.  
  
   Essa abordagem também é conhecida como *virtualização*. Use esta opção para compatibilidade com aplicativos existentes de versões anteriores do Visual Studio.  
  
  As novas propriedades estão disponíveis na página **aplicativo** do designer de projeto (somente para projetos do Visual C#) e no formato de arquivo de projeto do MSBuild.  
  
  Observe que o método para configurar a geração de manifesto do UAC no IDE do Visual Studio difere dependendo do tipo de projeto (Visual C# e Visual Basic).  
  
  Para obter informações sobre como configurar projetos do Visual C# para geração de manifesto, consulte [página do aplicativo, designer de projeto (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Para obter informações sobre como configurar projetos de Visual Basic para geração de manifesto, consulte [página de aplicativo, designer de projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Permissões de usuário e Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Página de aplicativo, designer de projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
