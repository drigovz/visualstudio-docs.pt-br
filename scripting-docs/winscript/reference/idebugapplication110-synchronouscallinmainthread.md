---
title: 'IDebugApplication110:: SynchronousCallInMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::SynchronousCallInMainThread
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db2b94d51cc5c9a65355aae7405fb162f564e0cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573645"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
Faz uma chamada síncrona no thread principal.  
  
> [!IMPORTANT]
> A [interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) é implementada pelo PDM v 11.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pptc`  
 O objeto de [interface IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md) a ser chamado.  
  
 `dwParam1`  
 O primeiro parâmetro da chamada.  
  
 `dwParam1`  
 O primeiro parâmetro da chamada.  
  
 `dwParam2`  
 O segundo parâmetro da chamada.  
  
 `dwParam3`  
 O terceiro parâmetro da chamada.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplication110 Interface](../../winscript/reference/idebugapplication110-interface.md)