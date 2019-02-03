---
title: IDiaSession::findFileById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c97df0a5c860fa27fdc136164b9fea79f58fa26
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042134"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Recupera um arquivo de origem pelo identificador de arquivo de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `uniqueId`  
 [in] Especifica o identificador de arquivo de origem.  
  
 `ppResult`  
 [out] Retorna um [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) recuperado do objeto que representa o arquivo de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O identificador de arquivo de origem é um valor exclusivo usado internamente para o DIA SDK para tornar exclusiva a todos os arquivos de origem. Esse método normalmente é usada internamente para o DIA SDK.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)