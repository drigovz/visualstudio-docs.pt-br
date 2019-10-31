---
title: Criar exibições personalizadas de objetos gerenciados | Microsoft Docs
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f5247a56667f5715d9f155c662eb333967878d71
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188641"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Criar exibições personalizadas de objetos gerenciados (C#, F#Visual Basic C++,,/CLI)
Você pode personalizar o modo como o Visual Studio exibe tipos de dados nas janelas variáveis do depurador.

## <a name="attributes"></a>Atributos

No C#, Visual Basic, F#e C++ (C++somente código/CLI), você pode adicionar expansões para dados personalizados usando <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

No código .NET Framework 2,0, Visual Basic não oferece suporte ao atributo DebuggerBrowsable. Essa limitação é removida em versões mais recentes do .NET.

## <a name="visualizers"></a>Visualizadores

Você pode escrever um visualizador para exibir qualquer tipo de dados gerenciados. Para obter mais informações, consulte [How to: Write a Visualizer](create-custom-visualizers-of-data.md).

> [!NOTE]
> Para C++ o código, você pode adicionar expansões de tipo de dados personalizadas usando a estrutura Natvis, conforme descrito em [criar exibições personalizadas de C++ objetos no depurador](create-custom-views-of-native-objects.md).

## <a name="see-also"></a>Consulte também

- [Diga ao depurador o que mostrar usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Informe ao depurador que tipo mostrar usando o atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Janelas Inspeção e Inspeção Rápida](../debugger/watch-and-quickwatch-windows.md)
- [Aprimorando a depuração com os atributos de exibição do depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
