---
title: IDiaSymbol::get_guid | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_guid method
ms.assetid: c02a6c92-f406-4646-82e7-3cd005af900e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1dddb9035a73a7d7da281a77760eafb066c4ddd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838276"
---
# <a name="idiasymbolget_guid"></a>IDiaSymbol::get_guid
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o GUID (identificador global exclusivo) do símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_guid (   
   GUID* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna o GUID do símbolo.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` ou código de erro.  
  
> [!NOTE]
> Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descrição|  
|-----------------|-----------------|  
|Cabeçalho:|dia2.h|  
|Versão:|DIA SDK v 7.0|  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
