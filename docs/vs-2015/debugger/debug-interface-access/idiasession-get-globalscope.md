---
title: IDiaSession::get_globalScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_globalScope method
ms.assetid: 75d128a8-3dce-40ed-b392-de3fdda041b7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b2b7b67ca3943f84a270873dfbdeb9b353b4e7e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145072"
---
# <a name="idiasessionget_globalscope"></a>IDiaSession::get_globalScope
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera uma referência ao escopo global.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_globalScope (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna um objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o escopo global.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
