---
title: IDispatchEx::GetNameSpaceParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1abe2a880e12d6a4a3c1dfda32d30722525858f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000830"
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
Recupera a interface para o pai do namespace de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppunk`  
 Endereço de um `IUnknown` ponteiro de interface que recebe a interface do namespace pai.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se tiver êxito ou caso contrário, um código de erro definido pelo OLE.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)