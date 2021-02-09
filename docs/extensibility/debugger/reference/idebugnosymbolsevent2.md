---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0922d6e6e7d7e4ccc162652427e3f8c584580dd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929661"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Sinaliza a interface de usuário do [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador para avisar ao usuário que não foi possível localizar os símbolos para o executável iniciado.

## <a name="syntax"></a>Sintaxe

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Implementado por mecanismos de depuração e consumido pela [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário do depurador.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
