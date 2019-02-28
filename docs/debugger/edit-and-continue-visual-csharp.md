---
title: Editar e continuar (Visual c#) | Microsoft Docs
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 972ad0d772eee9b876f43bc3e2fcd032d4b7e0ab
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685359"
---
# <a name="edit-and-continue-visual-c"></a>Editar e continuar (Visual C#)
 Com a função Editar e Continuar no C#, é possível fazer alterações em seu código no modo de interrupção durante a depuração. As alterações podem ser aplicadas sem precisar interromper e reiniciar a sessão de depuração. No modo de execução, o editor de origem é somente leitura.

 Editar e Continuar dá suporte à maioria das alterações que você talvez queira fazer durante uma sessão de depuração, mas há algumas exceções. Para obter mais informações, consulte [Supported Code Changes (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Editar e continuar é suportada em UWP em x86 e x64 aplicativos destinados ao .NET Framework 4.6 e Windows 10 desktops ou versões posteriores (.NET Framework é apenas uma versão de área de trabalho).

 > [!NOTE]
 > Plataformas e aplicativos sem suporte incluem o ASP.NET 5, o Silverlight 5 e o Windows 8.1.

 Quando Editar e Continuar estiver habilitado, as alterações com suporte são aplicadas automaticamente quando você usa um comando de execução do depurador, tal como **Continuar**, **Etapa** ou **Definir Próxima Instrução**, ou executa uma avaliação de função em uma janela de depuração.

 Para obter mais informações, consulte [como: usar Editar e continuar (c#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Consulte também
- [Como usar Editar e Continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Alterações de código suportadas (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md)