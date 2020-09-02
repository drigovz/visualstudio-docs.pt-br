---
title: Nós de programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a06be4ef0a69ec173f171ba202f1f479448b1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153655"
---
# <a name="program-nodes"></a>Nós de programa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos da arquitetura do depurador, um **nó de programa**:  
  
- É uma descrição leve de um programa.  
  
- Pode se identificar e o processo em que ele está sendo executado, e pode ser anexado a, ser desanexado e descrever o mecanismo de depuração (DE) que o criou, se houver.  
  
- É representado por uma interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , normalmente criada por uma ou uma porta. Nós de programa são adicionados a uma porta chamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando um nó de programa é adicionado a uma porta, ele é adicionado ao processo que contém o programa que esse nó de programa representa.  
  
  Um pouco depois que uma sessão de depuração é iniciada, dependendo da implementação do pacote de depuração, os nós de programa são usados para criar programas correspondentes. Quando um processo é consultado para seus programas, os programas são enumerados, um para cada nó de programa.  
  
  Antes que um programa seja anexado ao, o IDE precisa apenas de uma descrição leve do programa. Essas informações podem ser obtidas no nó do programa. Depois que o programa é anexado ao, o IDE precisa exibir informações mais detalhadas, como uma lista de todos os threads em execução no programa. Essas informações são obtidas do próprio programa.  
  
## <a name="see-also"></a>Consulte Também  
 [Suplementa](../../extensibility/debugger/programs.md)   
 [Processar](../../extensibility/debugger/processes.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
