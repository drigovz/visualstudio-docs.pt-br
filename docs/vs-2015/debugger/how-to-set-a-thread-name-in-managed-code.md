---
title: 'Como: definir um nome de thread em código gerenciado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b800fbd2f39d75f110a059c70b87a203eb72e7d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157677"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Como definir um nome de thread no código gerenciado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A nomeação de thread é possível em qualquer edição do Visual Studio. A nomeação de thread é útil para manter o controle de threads na janela **Threads**. Como a janela **threads** não está disponível nas edições Visual Studio Express, a nomenclatura de thread tem pouco utilidade nas Express Editions.  
  
 Para definir um nome do thread no código gerenciado, use a propriedade <xref:System.Threading.Thread.Name%2A>.  
  
## <a name="example"></a>Exemplo  
  
```  
Public Class Needle  
    ' This method will be called when the thread is started.  
    Sub Baz()  
        Console.WriteLine("Needle Baz is running on another thread")  
    End Sub  
End Class  
  
Sub Main()  
    Console.WriteLine("Thread Simple Sample")  
    Dim oNeedle As New Needle()  
   ' Create a Thread object.   
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)  
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Depurar aplicativos multissegmentados](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como definir um nome de thread em código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)
