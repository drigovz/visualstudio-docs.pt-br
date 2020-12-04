---
title: Criar exibições personalizadas de objetos gerenciados | Microsoft Docs
description: O depurador do Visual Studio exibe dados em suas janelas variáveis. Saiba como personalizar como os tipos de dados, incluindo tipos personalizados, são exibidos.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c2248a361837f664b0f78acfe61f6d7588f5258b
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560207"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Criar exibições personalizadas de objetos gerenciados (C#, Visual Basic, F #, C++/CLI)
Você pode personalizar o modo como o Visual Studio exibe tipos de dados nas janelas variáveis do depurador.

## <a name="attributes"></a>Atributos

Em C#, Visual Basic, F # e C++ (somente código C++/CLI), você pode adicionar expansões para dados personalizados usando <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerBrowsableAttribute> .

No código .NET Framework 2,0, Visual Basic não oferece suporte ao atributo DebuggerBrowsable. Essa limitação é removida em versões mais recentes do .NET.

## <a name="visualizers"></a>Visualizadores

Você pode escrever um visualizador para exibir qualquer tipo de dados gerenciados. Para obter mais informações, consulte [How to: Write a Visualizer](create-custom-visualizers-of-data.md).

> [!NOTE]
> Para o código C++, você pode adicionar expansões de tipo de dados personalizadas usando a estrutura Natvis, conforme descrito em [criar exibições personalizadas de objetos C++ no depurador](create-custom-views-of-native-objects.md).

## <a name="see-also"></a>Confira também

- [Diga ao depurador o que mostrar usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Informe ao depurador que tipo mostrar usando o atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Janelas de Inspeção e QuickWatch](../debugger/watch-and-quickwatch-windows.md)
- [Melhorando a depuração com os atributos de exibição do depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
