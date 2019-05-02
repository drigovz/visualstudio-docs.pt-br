---
title: IDebugApplication110::SynchronousCallInMainThread | Microsoft Docs
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
ms.openlocfilehash: d98f28f441096886c9ef7f26e63d876455a264e7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446368"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
Faz uma chamada síncrona no thread principal.  
  
> [!IMPORTANT]
> [Interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) é implementada pelo PDM v11.0 e maior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pptc`  
 O [IDebugThreadCall Interface](../../winscript/reference/idebugthreadcall-interface.md) objeto a ser chamado.  
  
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