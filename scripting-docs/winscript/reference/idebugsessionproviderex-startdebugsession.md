---
title: 'IDebugSessionProviderEx: StartDebugSession | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSessionProviderEx:StartDebugSession
apilocation:
- scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfe26265d56b2179feeac2a9802940258074b1c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574307"
---
# <a name="idebugsessionproviderexstartdebugsession"></a>IDebugSessionProviderEx:StartDebugSession
Inicia uma sessão de depuração com o aplicativo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pda`  
 no Especifica o aplicativo de depuração.  
  
 `fQuery`  
 no Verdadeiro indica uma consulta.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método inicia uma sessão de depuração com o aplicativo especificado. O depurador deve chamar `IRemoteDebugApplication::ConnectDebugger` antes de retornar dessa chamada.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugSessionProviderEx](../../winscript/reference/idebugsessionproviderex-interface.md)  
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)