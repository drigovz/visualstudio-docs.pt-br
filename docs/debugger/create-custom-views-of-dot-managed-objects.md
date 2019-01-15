---
title: Criar exibições personalizadas de objetos gerenciados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 389deb0b6504ca5c7a3716399429f176e5dc7870
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861430"
---
# <a name="create-custom-views-of-managed-objects"></a>Criar exibições personalizadas de objetos gerenciados
Você pode personalizar o modo como o Visual Studio exibe tipos de dados nas janelas variáveis do depurador.  
  
## <a name="attributes"></a>Atributos  
 No C# e no Visual Basic, você pode adicionar expansões para dados personalizados usando <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 No código do [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], o Visual Basic não dá suporte ao atributo DebuggerBrowsable. Essa restrição é removida em versões mais recentes do .NET Framework.  
  
## <a name="visualizers"></a>Visualizadores  
 Você pode escrever um visualizador para exibir qualquer tipo de dados gerenciados. Para obter mais informações, confira [Como: Escrever um visualizador](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
## <a name="native-code"></a>Código nativo  
 Para o código nativo, você pode adicionar expansões de tipo de dados personalizados ao arquivo autoexp.dat, que está localizado no diretório Arquivos de Programas\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. As instruções sobre como escrever regras de `autoexp` estão localizadas no próprio arquivo.  
  
> [!CAUTION]
>  A estrutura desse arquivo e a sintaxe de regras de autoexp podem ser alteradas de uma versão do Visual Studio para a seguinte.  
  
 As exibições de tipo nativo também podem ser personalizadas para gravar um suplemento do avaliador de expressão. Para obter mais informações, consulte [EEAddIn Sample: Depuração de expressão de suplemento do avaliador](https://msdn.microsoft.com/library/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Consulte também  
 [Usando o atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Janelas Inspeção e QuickWatch](../debugger/watch-and-quickwatch-windows.md)   
 [Aprimorando a depuração com os atributos de exibição do depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)