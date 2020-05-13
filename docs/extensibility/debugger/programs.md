---
title: Programas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738201"
---
# <a name="programs"></a>Programas
Na arquitetura dedepurador, um *programa:*

- É um recipiente para um conjunto de segmentos e um conjunto de módulos. Um programa não tem uma única analogia no sistema operacional Windows.

     Um programa é uma espécie de subprocesso. Por exemplo, quando você está depurando um site, um script pode ser visto como um programa. Enquanto um script é executado no processo de mecanismo de script, independente de outros scripts, ele também tem seu próprio conjunto de threads. Um mecanismo de depuração (DE) é anexado a um programa, e não a um processo ou a um segmento.

- Pode identificar-se e o processo em que está sendo executado. Um programa pode ser anexado, ser desvinculado e descrever o DE que o criou, se houver. Um programa também pode executar, parar, continuar e ser encerrado.

- Pode enumerar todos os seus fios. Um programa também pode fornecer seu próprio fluxo de desmontagem, e pode enumerar todos os contextos de código de uma determinada posição de documento.

- É representado por uma interface [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) criada antes do programa ser anexado, ou como parte do processo de anexação, dependendo da implementação. Quando uma porta enumera os programas de um processo, cada programa é criado de acordo com uma interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) correspondente passada como um argumento para [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Embora os mecanismos `IDebugProgram2` de depuração também criem interfaces para representar programas, esses programas não são criados de acordo com um nó de programa. As `IDebugProgramNode2` interfaces criadas por um DE são usadas para depuração real, enquanto as criadas por uma porta são usadas apenas para descobrir quais programas estão sendo executados em um processo.

## <a name="see-also"></a>Confira também
- [Processos](../../extensibility/debugger/processes.md)
- [Nódulos do programa](../../extensibility/debugger/program-nodes.md)
- [Módulos](../../extensibility/debugger/modules.md)
- [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md)
- [Motor de depuração](../../extensibility/debugger/debug-engine.md)
- [Posição do documento](../../extensibility/debugger/document-position.md)
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
