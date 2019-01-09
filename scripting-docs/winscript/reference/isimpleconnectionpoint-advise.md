---
title: ISimpleConnectionPoint::Advise | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3c0ea37e6fabb051458a11c4838061126bd98bf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091735"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Estabelece uma conexão entre o objeto de ponto de conexão simples e o coletor do cliente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdisp`  
 [in] Ponteiro para o `IDispatch` interface no cliente do coletor de aviso. O coletor do cliente recebe chamadas de saída do ponto de conexão simples.  
  
 `pdwCookie`  
 [out] Ponteiro para um token retornado que identifica exclusivamente essa conexão. O chamador usa esse token posteriormente para excluir a conexão, passando-o para o `ISimpleConnectionPoint::Unadvise` método. Se a conexão não foi estabelecida com êxito, esse valor é zero.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método estabelece uma conexão entre o objeto de ponto de conexão simples e o coletor do cliente.  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)