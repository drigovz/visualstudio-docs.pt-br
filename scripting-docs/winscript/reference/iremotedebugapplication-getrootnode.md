---
title: 'Iremotedebugapplication:: GetRootNode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetRootNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetRootNode
ms.assetid: 6c043aba-1dc5-41de-9711-96cde5e040f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75b398ddac53f2633cbc090f5d49574bd4d94d36
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097767"
---
# <a name="iremotedebugapplicationgetrootnode"></a>IRemoteDebugApplication::GetRootNode
Retorna o nó de aplicativo no qual todos os nós associados ao aplicativo serão adicionados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetRootNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppdanRoot`  
 [out] O nó de aplicativo de depuração sob a qual todos os nós associados ao aplicativo são adicionados.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o nó de aplicativo no qual todos os nós associados ao aplicativo serão adicionados.  
  
## <a name="see-also"></a>Consulte também  
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)