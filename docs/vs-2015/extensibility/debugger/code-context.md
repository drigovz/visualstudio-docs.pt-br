---
title: Contexto de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d59a4c79cb21386fa6f6e7031404aeb0b435b3b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197368"
---
# <a name="code-context"></a>Contexto de código
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuração, um **contexto de código**:  
  
- Fornece uma abstração de uma posição no código, como conhecido pelo mecanismo DE depuração (DE). Para a maioria das arquiteturas de tempo de execução hoje, um contexto de código pode ser considerado como um endereço no fluxo de instruções de um programa. Para linguagens não tradicionais, em que o código não pode ser representado por instruções, um contexto de código pode ser representado por outros meios.  
  
- Descreve a posição atual no fluxo de execução do programa que está sendo depurado.  
  
- Existe somente quando um programa é interrompido em um ponto de interrupção.  
  
- Tem um contexto de documento associado.  
  
- É implementado por uma interface [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [Contexto do documento](../../extensibility/debugger/document-context.md)   
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)
