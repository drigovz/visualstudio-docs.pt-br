---
title: Programas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9070b33c7522cdc13fd6217956fcab72cd83f8d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153637"
---
# <a name="programs"></a>Programas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos da arquitetura do depurador, um **programa**:  
  
- É um contêiner para um conjunto de threads e um conjunto de módulos. Um programa não tem uma única analogia no sistema operacional Windows.  
  
     Um programa é um tipo de subprocesso. Por exemplo, quando você está depurando um site da Web, um script pode ser visto como um programa. Enquanto um script é executado no processo do mecanismo de script, independentemente de outros scripts, ele também tem seu próprio conjunto de threads. Um mecanismo DE depuração (DE) é anexado a um programa e não a um processo ou a um thread.  
  
- Pode se identificar e o processo em que ele está sendo executado, e pode ser anexado a, ser desanexado e descrever o que o criou, se houver. Um programa pode executar, parar, continuar e ser encerrado.  
  
- Pode enumerar todos os seus threads. Um programa também pode fornecer seu próprio fluxo de desmontagem e pode enumerar todos os contextos de código de uma determinada posição de documento.  
  
- É representado por uma interface [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , criada antes de o programa ser anexado ou como parte do processo de anexo, dependendo da implementação. Quando uma porta enumera os programas de um processo, cada programa é criado de acordo com uma interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) correspondente passada como um argumento para [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Embora os mecanismos de depuração também criem `IDebugProgram2` interfaces para representar programas, esses programas não são criados de acordo com um nó de programa. As `IDebugProgramNode2` interfaces criadas por um de são usadas para depuração real, enquanto aquelas criadas por uma porta são usadas apenas para descobrir quais programas estão sendo executados em um processo.  
  
## <a name="see-also"></a>Consulte Também  
 [Processar](../../extensibility/debugger/processes.md)   
 [Nós de programa](../../extensibility/debugger/program-nodes.md)   
 [Módulos](../../extensibility/debugger/modules.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Posição do documento](../../extensibility/debugger/document-position.md)   
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
