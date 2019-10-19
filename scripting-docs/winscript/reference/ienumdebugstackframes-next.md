---
title: 'IEnumDebugStackFrames:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17261f8ba9b2957d33ed7019c16f2e1423b6b42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575545"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
Recupera um número especificado de segmentos na sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 no O número de segmentos a serem recuperados.  
  
 `prgdsfd`  
 fora Retorna uma matriz de interfaces `DebugStackFrameDescriptor` que representa os segmentos que estão sendo recuperados.  
  
 `pceltFetched`  
 fora O número real de segmentos buscados pelo enumerador.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método recupera um número especificado de segmentos na sequência de enumeração.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IEnumDebugStackFrames](../../winscript/reference/ienumdebugstackframes-interface.md)  
 [DebugStackFrameDescriptor Structure](../../winscript/reference/debugstackframedescriptor-structure.md)