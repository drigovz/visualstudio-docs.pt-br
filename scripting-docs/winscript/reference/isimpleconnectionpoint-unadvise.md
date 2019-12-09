---
title: 'ISimpleConnectionPoint:: Unadvise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e00c172fd33eb0ccf27aaf28e0e2f692c1a353ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571754"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Encerra uma conexão de consultoria estabelecida anteriormente por meio de `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwCookie`  
 no Token da conexão a ser encerrado, conforme retornado de `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Quando uma conexão de consultoria é encerrada, o ponto de conexão chama o método `Release` no ponteiro que foi salvo para a conexão durante o método `ISimpleConnectionPoint::Advise`. Essa chamada inverte a `AddRef` que foi executada durante a `ISimpleConnectionPoint::Advise` quando o ponto de conexão chama o `QueryInterface` do coletor de consultoria.  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)