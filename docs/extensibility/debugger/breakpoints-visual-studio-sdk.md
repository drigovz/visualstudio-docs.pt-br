---
title: Pontos de interrupção (SDK do Visual Studio) | Microsoft Docs
description: 'Saiba mais sobre os três tipos de pontos de interrupção: pendente, associado e erro. Este artigo lista as interfaces usadas para implementar os tipos.'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8d266bb97b6d3086a8f5b74100f5821a5cfca3af
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914446"
---
# <a name="breakpoints-visual-studio-sdk"></a>Pontos de interrupção (SDK do Visual Studio)
Há três tipos de pontos de interrupção: pendente, associado e erro.

 **Um ponto de interrupção pendente:**

- É uma abstração que contém todas as informações necessárias para associar um ponto de interrupção a um ou mais contextos de código em um ou mais programas. Cada vez que um programa sendo depurado faz com que o código seja carregado, o mecanismo de depuração verifica todos os pontos de interrupção pendentes para ver se eles podem ser associados.

   Um ponto de interrupção pendente nunca é associado ao código, mas, em vez disso, ele coleta e diz que contém todos os pontos de interrupção associados que ele gera.

- É representado por uma interface [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

  **Um ponto de interrupção associado:**

- É uma abstração para um ponto de interrupção associado a ou associado a um único contexto de código. Cada ponto de interrupção associado é gerado em resposta a um ponto de interrupção pendente. No entanto, um ponto de interrupção pendente pode gerar mais de um ponto de interrupção associado.

   Quando o código é descarregado, um ponto de interrupção associado pode ser desassociado e descartado.

- É representado por uma interface [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

  **Um ponto de interrupção de erro:**

- É uma abstração para descrever um erro ao tentar associar um ponto de interrupção pendente a um contexto de código. Um ponto de interrupção de erro descreve um erro no local ou na própria expressão de ponto de interrupção. Para obter mais informações, consulte [pontos de interrupção de ligação](../../extensibility/debugger/binding-breakpoints.md).

   O erro de ponto de interrupção pode ser um erro ou um aviso.

- É representado por uma interface [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

## <a name="see-also"></a>Confira também
- [Programas](../../extensibility/debugger/programs.md)
- [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
