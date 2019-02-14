---
title: IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27bf39aea5b095860f9e5aebf864abb4df6bf86d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54964386"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Determina se é okey procurar um arquivo. PDB no diretório de depuração do original.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Qualquer código de retorno diferente de `S_OK` impede procurando um arquivo. PDB no diretório de depuração do original. O diretório de depuração original é o caminho para o arquivo de símbolo compilado no executável quando a depuração está ativada. Esse caminho não é necessariamente o mesmo que o caminho onde o executável existe.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)