---
title: Servidores (SDK do Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ed2ce924b22827a82a67664e3e473f0930a87e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199402"
---
# <a name="servers-visual-studio-sdk"></a>Servidores (SDK do Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos da arquitetura do depurador, um **servidor**:  
  
- É um contêiner de portas e fornecedores de porta e é usado para comunicar portas e fornecedores de porta para o SDM (Gerenciador de depuração de sessão) e os mecanismos de depuração.  
  
- Pode se identificar por nome e enumerar suas portas e fornecedores de porta.  
  
- É representado por uma interface [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , que é implementada pelo Visual Studio (uma instância de um servidor para cada instância do Visual Studio em execução).  
  
## <a name="see-also"></a>Consulte Também  
 [Porta](../../extensibility/debugger/ports.md)   
 [Fornecedores de porta](../../extensibility/debugger/port-suppliers.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
