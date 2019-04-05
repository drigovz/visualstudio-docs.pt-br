---
title: Habilitar um programa a ser depurado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0f0331430a1cc625dee2a7029742fd62d67fb56
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928446"
---
# <a name="enabling-a-program-to-be-debugged"></a>Habilitando um programa a ser depurado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Define um mecanismo de depuração (DE) e descreve os serviços implementados por meio DE interfaces e como eles podem causar o depurador para fazer a transição entre os modos operacionais diferentes.
