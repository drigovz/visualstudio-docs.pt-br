---
title: Implantação do ClickOnce no Windows Vista | Microsoft Docs
description: Saiba como o Visual Studio gera o manifesto do UAC externo para o ClickOnce e Registration-Free aplicativos COM, que exigem um manifesto externo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2e09225339a87c55c31d27d26b129e199385e99
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383073"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Implantação do ClickOnce no Windows Vista

A criação de aplicativos no Visual Studio para controle de conta de usuário (UAC) no Windows Vista normalmente gera um manifesto incorporado, codificado como dados XML binários no arquivo executável do aplicativo.  O ClickOnce e Registration-Free aplicativos COM exigem um manifesto externo, portanto, o Visual Studio gera um arquivo para esses projetos que contêm os dados do UAC em vez de um manifesto incorporado. Para implantações do ClickOnce e Registration-Free COM, o Visual Studio usa informações de um arquivo chamado *app. manifest* para gerar informações externas do manifesto do UAC. Para todos os outros casos, o Visual Studio insere os dados do UAC no arquivo executável do aplicativo.

O Visual Studio fornece as seguintes opções para a geração de manifesto:

- Use um manifesto inserido. Insira dados do UAC no arquivo executável do aplicativo e execute como um usuário normal.

   Essa é a configuração padrão (a menos que você use o ClickOnce). Essa configuração dá suporte à maneira normal em que o Visual Studio opera no Windows Vista, com a geração de um manifesto interno e externo usando o `AsInvoker` .

- Use um manifesto externo. Gere um manifesto externo usando o *app. manifest*.

   Isso gera apenas o manifesto externo usando as informações em *app. manifest*. Quando você publica um aplicativo usando ClickOnce ou Registration-Free COM, o Visual Studio adiciona o *app. manifest* ao projeto e, em seguida, adiciona essa opção.

- Não use nenhum manifesto. Crie o aplicativo sem um manifesto.

   Essa abordagem também é conhecida como *virtualização*. Use esta opção para compatibilidade com aplicativos existentes de versões anteriores do Visual Studio.

  As novas propriedades estão disponíveis na página **aplicativo** do designer de projeto (somente para projetos do Visual C#) e no formato de arquivo de projeto do MSBuild.

  O método para configurar a geração de manifesto do UAC no IDE do Visual Studio difere dependendo do tipo de projeto (Visual C# ou Visual Basic).

  * Para obter informações sobre como configurar projetos do Visual C# para geração de manifesto, consulte [página do aplicativo, designer de projeto (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Para obter informações sobre como configurar projetos de Visual Basic para geração de manifesto, consulte [página de aplicativo, designer de projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Confira também
- [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Permissões de usuário e Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)