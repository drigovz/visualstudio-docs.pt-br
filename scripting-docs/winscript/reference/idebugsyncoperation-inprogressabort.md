---
title: 'IDebugSyncOperation:: InProgressAbort | Microsoft Docs'
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
ms.openlocfilehash: 40974c738c071e52648297ac90a0ab89d9681435
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576663"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Cancela uma operação em andamento em outro thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|A operação não pode ser cancelada.|  
|`E_ABORT`|A operação não pôde ser concluída.|  
  
## <a name="remarks"></a>Comentários  
 O Gerenciador de depuração de processo chama esse método de dentro do thread do depurador para cancelar uma operação em andamento em outro thread.  
  
 Se o método `InProgressAbort` não puder concluir a operação, ele retornará `E_ABORT` assim que possível. Esse método pode retornar `E_NOTIMPL` se a operação não puder ser cancelada.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)