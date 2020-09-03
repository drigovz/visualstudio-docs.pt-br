---
title: Criar exibições personalizadas de objetos gerenciados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb5b56404c7ddc99b7999b47cf3c2a899f915efd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72578051"
---
# <a name="create-custom-views-of-managed-objects"></a>Criar exibições personalizadas de objetos gerenciados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode personalizar o modo como o Visual Studio exibe tipos de dados nas janelas variáveis do depurador.  
  
## <a name="attributes"></a>Atributos  
 No C# e no Visual Basic, você pode adicionar expansões para dados personalizados usando <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 No código do [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], o Visual Basic não dá suporte ao atributo DebuggerBrowsable. Essa restrição é removida em versões mais recentes do .NET Framework.  
  
## <a name="visualizers"></a>Visualizadores  
 Você pode escrever um visualizador para exibir qualquer tipo de dados gerenciados. Para obter mais informações, consulte [How to: Write a Visualizer](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Código nativo  
 Para o código nativo, você pode adicionar expansões de tipo de dados personalizados ao arquivo autoexp.dat, que está localizado no diretório Arquivos de Programas\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. As instruções sobre como escrever regras de `autoexp` estão localizadas no próprio arquivo.  
  
> [!CAUTION]
> A estrutura desse arquivo e a sintaxe de regras de autoexp podem ser alteradas de uma versão do Visual Studio para a seguinte.  
  
 As exibições de tipo nativo também podem ser personalizadas para gravar um suplemento do avaliador de expressão. Para obter mais informações, consulte [exemplo de EEAddIn: depuração do avaliador de expressões de depurador](https://msdn.microsoft.com/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Consulte Também  
 [Usando o atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Janelas Watch e QuickWatch](../debugger/watch-and-quickwatch-windows.md)   
 [Melhorando a depuração com os atributos de exibição do depurador](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
