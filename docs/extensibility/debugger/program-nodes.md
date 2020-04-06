---
title: Nódulos do programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738222"
---
# <a name="program-nodes"></a>Nódulos do programa
Na arquitetura dedepurador, um *nó de programa*:

- É uma descrição leve de um programa.

- Pode identificar-se e o processo em que está sendo executado. Um nó de programa pode ser anexado, ser separado e descrever o mecanismo de depuração (DE) que o criou, se houver.

- É representado por uma interface [IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) normalmente criada por um DE ou porto. Os nós do programa são adicionados a uma porta [chamando-o de AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando um nó de programa é adicionado a uma porta, ele é adicionado ao processo que contém o programa que este nó de programa representa.

  Algum tempo após o início de uma sessão de depuração, dependendo da implementação do pacote de depuração, os nós do programa são usados para criar programas correspondentes. Quando um processo é questionado para seus programas, os programas são enumerados, um para cada nó do programa.

  Antes de um programa ser anexado, o IDE precisa apenas de uma descrição leve do programa. Essas informações podem ser obtidas do nó do programa. Uma vez que o programa é anexado, o IDE exibe informações mais detalhadas, como uma lista de todos os segmentos em execução no programa. Essas informações são obtidas do próprio programa.

## <a name="see-also"></a>Confira também
- [Programas](../../extensibility/debugger/programs.md)
- [Processos](../../extensibility/debugger/processes.md)
- [Motor de depuração](../../extensibility/debugger/debug-engine.md)
- [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
