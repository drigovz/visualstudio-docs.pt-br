---
title: IDiaSymbol::get_unmodifiedTypeId | Microsoft Docs
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
ms.assetid: 4f7fc73c-f524-4d7a-b378-a9ab99a96104
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cb1849c6c807ffe02e27aadce514fba00e29678
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206629"
---
# <a name="idiasymbolgetunmodifiedtypeid"></a>IDiaSymbol::get_unmodifiedTypeId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera a ID do tipo original (não modificado).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT get_unmodifiedTypeId(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Um ponteiro para um `DWORD` que contém a ID.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



