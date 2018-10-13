---
title: 'Idiasymbol:: Get_interruptreturn | Microsoft Docs'
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
- IDiaSymbol::get_interruptReturn method
ms.assetid: 9665da6c-4cc0-41d7-b2e2-0d9e50174cf8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e3d8dc49761dcbf5dee8eeb2814874cb62bf702
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232564"
---
# <a name="idiasymbolgetinterruptreturn"></a>IDiaSymbol::get_interruptReturn
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera um sinalizador que especifica se a função contém um retorno de instrução de interrupção (por exemplo, X86 código assembly `iret`).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT get_interruptReturn(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pFlag`  
 [out] Retorna `TRUE` se a função tem um retorno de instrução de interrupção; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descrição|  
|-----------------|-----------------|  
|Cabeçalho:|dia2.h|  
|Versão:|V DIA SDK 8.0|  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



