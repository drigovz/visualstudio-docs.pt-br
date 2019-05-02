---
title: IDebugSyncOperation::InProgressAbort | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a794ea70d6d2fe937afb311e6961d53f22bd7ac2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004838"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Cancela uma operação em andamento em outro thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|A operação não pode ser cancelada.|  
|`E_ABORT`|Não foi possível concluir a operação.|  
  
## <a name="remarks"></a>Comentários  
 O Gerenciador de depuração do processo chama esse método de dentro do thread depurador para cancelar uma operação que está em andamento em outro thread.  
  
 Se o `InProgressAbort` método não é possível concluir a operação, ele retorna `E_ABORT` assim que possível. Esse método pode retornar `E_NOTIMPL` se a operação não pode ser cancelada.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)