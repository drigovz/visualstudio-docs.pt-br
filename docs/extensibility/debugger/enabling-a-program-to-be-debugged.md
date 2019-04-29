---
title: Habilitar um programa a ser depurado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f301de66421ef1327b86d900305cb4ecbfb5623
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889688"
---
# <a name="enable-a-program-to-be-debugged"></a>Habilitar um programa a ser depurado
Antes de seu mecanismo de depuração (DES) pode depurar um programa, você deve primeiro iniciar o DE ou anexá-lo a um programa existente.

## <a name="in-this-section"></a>Nesta seção
 [Obter uma porta](../../extensibility/debugger/getting-a-port.md) discute como obter uma porta, como a primeira etapa para habilitar um programa a ser depurado.

 [Registrar o programa](../../extensibility/debugger/registering-the-program.md) explica a próxima etapa na habilitação de um programa a ser depurado: registrá-lo com a porta. Depois de registrado, o programa pode ser depurado pelo processo de anexação ou a depuração just-in-time (JIT).

 [Anexar ao programa](../../extensibility/debugger/attaching-to-the-program.md) explica a próxima etapa: anexar o depurador ao programa.

 [Com base em inicialização anexando](../../extensibility/debugger/launch-based-attachment.md) descreve com base em inicialização anexo a um programa, que é automático durante a inicialização, o SDM.

 [Enviar os eventos necessários](../../extensibility/debugger/sending-the-required-events.md) percorre os eventos necessários durante a criação de um mecanismo de depuração (DE) e anexá-lo a um programa.

## <a name="related-sections"></a>Seções relacionadas
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) define um mecanismo de depuração (DE) e descreve serviços implementados por meio DE interfaces e como eles podem causar o depurador para fazer a transição entre os modos operacionais diferentes.