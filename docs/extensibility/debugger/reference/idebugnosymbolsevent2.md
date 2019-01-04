---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 179d8a95bc54db90a98311626b34c3e17b68f7f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873113"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Sinaliza o [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] da interface do usuário para avisar o usuário que símbolos não pôde ser localizados para o executável iniciado do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Implementado por mecanismos de depuração e consumido pelo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] da interface do usuário do depurador.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll