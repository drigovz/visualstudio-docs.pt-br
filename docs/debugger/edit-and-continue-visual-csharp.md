---
title: Editar e continuar (Visual C#) | Microsoft Docs
description: Editar e continuar está disponível para projetos do Visual C#. Saiba quais edições têm suporte e como pode controlar se, e quando, suas edições são aplicadas.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 375e1db598f925a193def159203ccb7e5c5fdf05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871852"
---
# <a name="edit-and-continue-visual-c"></a>Editar e continuar (Visual C#)
 Com a função Editar e Continuar no C#, é possível fazer alterações em seu código no modo de interrupção durante a depuração. As alterações podem ser aplicadas sem precisar interromper e reiniciar a sessão de depuração. No modo de execução, o editor de origem é somente leitura.

 Editar e Continuar dá suporte à maioria das alterações que você talvez queira fazer durante uma sessão de depuração, mas há algumas exceções. Para obter mais informações, consulte [alterações de código com suporte (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Editar e continuar tem suporte no UWP no Windows 10 e aplicativos x86 e x64 direcionados para a área de trabalho .NET Framework 4,6 ou versões posteriores (o .NET Framework é apenas uma versão da área de trabalho).

 > [!NOTE]
 > Aplicativos e plataformas sem suporte incluem o Silverlight 5 e o Windows 8.1.

 Quando Editar e Continuar estiver habilitado, as alterações com suporte são aplicadas automaticamente quando você usa um comando de execução do depurador, tal como **Continuar**, **Etapa** ou **Definir Próxima Instrução**, ou executa uma avaliação de função em uma janela de depuração.

 Para obter mais informações, consulte [como: usar editar e continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Consulte também
- [Como usar Editar e Continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Alterações de código com suporte (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Escrever e depurar o código XAML em execução com o Hot recarregamento de XAML no Visual Studio](../xaml-tools/xaml-hot-reload.md)
