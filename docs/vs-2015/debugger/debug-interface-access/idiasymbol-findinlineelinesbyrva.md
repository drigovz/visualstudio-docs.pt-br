---
title: IDiaSymbol::findInlineeLinesByRVA | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: ac108db1-9dbf-4dc4-bf48-159ca8d3725c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1cf8c53f236102ada34272d06b789d04683fa73c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849782"
---
# <a name="idiasymbolfindinlineelinesbyrva"></a>IDiaSymbol::findInlineeLinesByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera uma enumeração que permite que um cliente iterar por meio das informações de número de linha de todas as funções que são embutidas, diretamente ou indiretamente, nesse símbolo no endereço relativo virtual (RVA) especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT findInlineeLinesByRVA (    DWORD                 rva,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rva`  
 [in] Especifica o endereço como um RVA.  
  
 `length`  
 [in] Especifica o intervalo de endereços, no número de bytes, para cobrir com essa consulta.  
  
 `ppResult`  
 [out] Mantém um `IDiaEnumLineNumbers` objeto que contém a lista de números de linha são recuperadas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)



