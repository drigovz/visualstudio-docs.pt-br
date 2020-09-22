---
title: IDiaSymbol::get_slot | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_slot method
ms.assetid: 97e405b8-483f-4da0-91e7-ca4d88251ecd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b668d11c48185d8daac5d8b17ff8848e5f9c1fd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838468"
---
# <a name="idiasymbolget_slot"></a>IDiaSymbol::get_slot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o número de slot do local. Use quando a [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md) for `LocIsSlot` .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_slot (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna o número do slot do local.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
> Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md)
