---
title: IRemoteDebugApplicationThread::GetApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetApplication
ms.assetid: 9446c7f9-cfa2-408f-98c5-64f549783de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc2e4d542619e214835d3be8354062733ebd5cb8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091488"
---
# <a name="iremotedebugapplicationthreadgetapplication"></a>IRemoteDebugApplicationThread::GetApplication
Retorna o objeto de aplicativo associado a esse thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetApplication(  
   IRemoteDebugApplication**  pprda  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pprda`  
 [out] O objeto de aplicativo associado a esse thread.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o objeto de aplicativo associado a esse thread.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)