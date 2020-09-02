---
title: IDiaSymbol::get_baseDataOffset | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: bb2ff5ed-9293-4c37-9741-654058b571c5
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7496cb318abdc194ff832d4fbdbaf570e5cc68e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62572864"
---
# <a name="idiasymbolget_basedataoffset"></a>IDiaSymbol::get_baseDataOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o deslocamento de dados base.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT get_baseDataOffset(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Um ponteiro para um `DWORD` que contém o deslocamento de dados base.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
