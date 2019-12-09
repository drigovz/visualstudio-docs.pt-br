---
title: 'IDebugApplication110:: CallableWaitForHandles | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575082"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Aguarda que qualquer um dos identificadores especificados seja sinalizado enquanto permite que chamadas entre threads sejam postadas nesse thread. Esse método deve ser chamado a partir do thread do depurador.  
  
> [!IMPORTANT]
> A [interface IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) é implementada pelo PDM v 11.0 e superior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `handleCount`  
 O número de identificadores a serem esperados.  
  
 `pHandles`  
 O conjunto de identificadores a serem esperados.  
  
 `pIndex`  
 Quando o valor HRESULT é S_OK, o índice em `pHandles` para o identificador que foi sinalizado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplication110 Interface](../../winscript/reference/idebugapplication110-interface.md)