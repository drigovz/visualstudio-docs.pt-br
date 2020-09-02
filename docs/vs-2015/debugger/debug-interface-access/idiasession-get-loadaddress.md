---
title: IDiaSession::get_loadAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 00ac9345001983aa9829848c4adafae69151d81a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62558275"
---
# <a name="idiasessionget_loadaddress"></a>IDiaSession::get_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o endereço de carregamento do arquivo executável que corresponde aos símbolos neste repositório de símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_loadAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna um endereço virtual (VA) em que um arquivo. exe ou. dll é carregado.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O endereço de carregamento retornado é sempre zero, a menos que especificamente definido usando o método [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
