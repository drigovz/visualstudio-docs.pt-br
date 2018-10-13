---
title: 'Idiaenumsymbols:: clone | Microsoft Docs'
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
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ca7bcd94cba05611ed576a14d54e48017b34e4c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201507"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSymbols** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ppenum  
 [out] Retorna um [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) objeto que contém uma duplicata do enumerador. Os símbolos não são duplicados, apenas o enumerador.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



