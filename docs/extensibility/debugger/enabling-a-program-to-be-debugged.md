---
title: Habilitando um programa a ser depurado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738898"
---
# <a name="enable-a-program-to-be-debugged"></a>Permitir que um programa seja depurado
Antes que seu motor de depuração (DE) possa depurar um programa, você deve primeiro iniciar o DE ou anexá-lo a um programa existente.

## <a name="in-this-section"></a>Nesta seção
 [Obter uma porta](../../extensibility/debugger/getting-a-port.md) Discute como obter uma porta como o primeiro passo para permitir que um programa seja depurado.

 [Registre o programa](../../extensibility/debugger/registering-the-program.md) Explica o próximo passo para habilitar um programa a ser depurado: registrá-lo na porta. Uma vez registrado, o programa pode ser depurado pelo processo de anexação ou depuração just-in-time (JIT).

 [Anexar ao programa](../../extensibility/debugger/attaching-to-the-program.md) Explica o próximo passo: anexar o depurador ao programa.

 [Anexação baseada em lançamento](../../extensibility/debugger/launch-based-attachment.md) Descreve o anexo baseado em lançamento a um programa, que é automático após o lançamento pelo SDM.

 [Envie os eventos necessários](../../extensibility/debugger/sending-the-required-events.md) Passos sobre os eventos necessários ao criar um mecanismo de depuração (DE) e anexá-lo a um programa.

## <a name="related-sections"></a>Seções relacionadas
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) Define um mecanismo de depuração (DE) e descreve os serviços implementados através das interfaces DE e como eles podem fazer com que o depurador transite entre diferentes modos operacionais.
