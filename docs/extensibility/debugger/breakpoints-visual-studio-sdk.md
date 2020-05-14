---
title: Pontos de interrupção (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739197"
---
# <a name="breakpoints-visual-studio-sdk"></a>Pontos de interrupção (SDK do Visual Studio)
Existem três tipos de pontos de interrupção: pendente, vinculado e erro.

 **Um ponto de ruptura pendente:**

- É uma abstração que contém todas as informações necessárias para vincular um ponto de ruptura a um ou mais contextos de código em um ou mais programas. Cada vez que um programa sendo depurado causa código para carregar, o mecanismo de depuração verifica todos os pontos de interrupção pendentes para ver se eles podem ser vinculados.

   Um ponto de interrupção pendente em si nunca se liga ao código, mas sim coleta e é dito para conter todos os pontos de interrupção vinculados que ele gera.

- É representado por uma interface [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

  **Um ponto de ruptura vinculado:**

- É uma abstração para um ponto de ruptura associado ou vinculado a um único contexto de código. Cada ponto de ruptura vinculado é gerado em resposta a um ponto de ruptura pendente. Um ponto de ruptura pendente pode, no entanto, gerar mais de um ponto de ruptura vinculado.

   Quando o código é descarregado, um ponto de ruptura vinculado pode ser desvinculado e descartado.

- É representado por uma interface [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

  **Um ponto de quebra de erro:**

- É uma abstração para descrever um erro na tentativa de vincular um ponto de ruptura pendente a um contexto de código. Um ponto de ruptura de erro descreve um erro de localização ou na própria expressão de ponto de ruptura. Para obter mais informações, consulte [Pontos de interrupção de Vinculação](../../extensibility/debugger/binding-breakpoints.md).

   O erro de ponto de partida pode ser um erro ou um aviso.

- É representado por uma interface [IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

## <a name="see-also"></a>Confira também
- [Programas](../../extensibility/debugger/programs.md)
- [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md)
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
