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
ms.openlocfilehash: f8faa677e5893c0737bcd89db5567ef7459f6d07
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953219"
---
# <a name="enable-a-program-to-be-debugged"></a>Habilitar um programa a ser depurado
Antes de seu mecanismo de depuração (DES) pode depurar um programa, você deve primeiro iniciar o DE ou anexá-lo a um programa existente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Obter uma porta](../../extensibility/debugger/getting-a-port.md)  
 Discute como obter uma porta como a primeira etapa para habilitar um programa a ser depurado.  
  
 [Registrar o programa](../../extensibility/debugger/registering-the-program.md)  
 Explica a próxima etapa na habilitação de um programa a ser depurado: registrá-lo com a porta. Depois de registrado, o programa pode ser depurado pelo processo de anexação ou a depuração just-in-time (JIT).  
  
 [Anexar ao programa](../../extensibility/debugger/attaching-to-the-program.md)  
 Explica a próxima etapa: anexar o depurador ao programa.  
  
 [Com base em inicialização anexando](../../extensibility/debugger/launch-based-attachment.md)  
 Descreve a inicialização com base em anexo a um programa, que é automático durante a inicialização, o SDM.  
  
 [Enviar os eventos necessários](../../extensibility/debugger/sending-the-required-events.md)  
 Percorre os eventos necessários durante a criação de um mecanismo de depuração (DE) e anexá-lo a um programa.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Define um mecanismo de depuração (DE) e descreve os serviços implementados por meio DE interfaces e como eles podem causar o depurador para fazer a transição entre os modos operacionais diferentes.