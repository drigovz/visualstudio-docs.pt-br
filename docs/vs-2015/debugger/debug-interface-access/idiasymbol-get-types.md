---
title: IDiaSymbol::get_types | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 813dcd692669d823548e52ce6bb7eccc9546de61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838707"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera uma matriz de tipos específicos do compilador para este símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cTypes`  
 no Tamanho do buffer para armazenar os dados.  
  
 `pcTypes`  
 fora Retorna o número de tipos gravados ou, se o `types` parâmetro for `NULL` , o número total de tipos disponíveis.  
  
 `types[]`  
 fora Uma matriz que deve ser preenchida com os objetos [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representam todos os tipos desse símbolo.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
> Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
