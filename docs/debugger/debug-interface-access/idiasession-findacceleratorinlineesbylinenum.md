---
title: IDiaSession::findAcceleratorInlineesByLinenum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d963763f341430c92810fe811144212d2cc522e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999711"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Retorna uma enumeração de símbolos para quadros embutidos que correspondem ao local de origem especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `parent`  
 [in] Um `IDiaSymbol` que corresponde à função de stub do acelerador que precisa ser pesquisado.  
  
 `file`  
 [in] O `IDiaSourceFile` de local de origem.  
  
 `linenum`  
 [in] O número de linha de local de origem.  
  
 `colnum`  
 [in] O número da coluna do local de origem.  
  
 `ppResult`  
 [out] Um ponteiro para um `IDiaEnumLineNumbers` ponteiro de interface que é inicializado com o resultado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)