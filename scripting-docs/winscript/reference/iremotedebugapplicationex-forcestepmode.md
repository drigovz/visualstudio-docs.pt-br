---
title: IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:ForceStepMode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:ForceStepMode
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 771c17fdb8f2bea77959bc53b8d98fd10399a142
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094751"
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode
Força o depurador em modo de etapa única.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ForceStepMode(  
   IRemoteDebugApplicationThread*  pStepThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStepThread`  
 [in] Thread para o Monitor de depuração do processo para a etapa. Se for null, o PDM limpa seu thread passo a passo.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Interface IRemoteDebugApplicationEx](http://msdn.microsoft.com/en-us/2f65fa67-06b7-4053-8945-22383ab66343)