---
title: IDiaSession::findSymbolByToken | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByToken method
ms.assetid: 3c92149c-6eef-454f-86be-66e89557b9e6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d42be946db927603412670d30e2f4c9a1cab43fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144770"
---
# <a name="idiasessionfindsymbolbytoken"></a>IDiaSession::findSymbolByToken
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o símbolo que contém um token de metadados especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT findSymbolByToken (   
   ULONG        token,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `token`  
 no Especifica o token.  
  
 `symtag`  
 no Tipo de símbolo a ser encontrado. Os valores são obtidos da enumeração de [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .  
  
 `ppSymbol`  
 fora Retorna um objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o símbolo recuperado.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="example"></a>Exemplo  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByToken( token, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
