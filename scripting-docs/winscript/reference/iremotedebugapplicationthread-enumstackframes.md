---
title: IRemoteDebugApplicationThread::EnumStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.EnumStackFrames
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::EnumStackFrames
ms.assetid: 605ce83d-43d2-47ea-b066-ec8f0da50ca6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96ca35779ea9f113fc96e485f028f1e74058990a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149215"
---
# <a name="iremotedebugapplicationthreadenumstackframes"></a>IRemoteDebugApplicationThread::EnumStackFrames
Retorna um enumerador para os quadros de pilha associado a esse thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppedsf`  
 [out] Um enumerador para os quadros de pilha associado a esse thread.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método deve ser chamado de dentro de um ponto de interrupção. O enumerador de quadro de pilha deve retornar os quadros começando do topo da pilha, começando com o quadro mais recentemente enviados por push.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)