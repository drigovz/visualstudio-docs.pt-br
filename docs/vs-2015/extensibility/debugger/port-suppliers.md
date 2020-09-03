---
title: Fornecedores de porta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153701"
---
# <a name="port-suppliers"></a>Fornecedores de porta
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos da arquitetura do depurador, um **fornecedor de porta**:  
  
- Está contido em um servidor e fornece portas na solicitação para esse servidor.  
  
- Pode adicionar e remover portas do servidor que a contém.  
  
- Pode enumerar todas as portas que ele forneceu para o servidor.  
  
- É representado por uma interface [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , que é registrada com o Visual Studio por meio do registro. Essa interface pode ser obtida chamando [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornece um fornecedor de porta padrão e uma porta padrão. Se uma porta personalizada precisar ser implementada, um fornecedor de porta personalizado também precisará ser implementado para fornecer essas portas personalizadas.  
  
## <a name="see-also"></a>Consulte Também  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Porta](../../extensibility/debugger/ports.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
