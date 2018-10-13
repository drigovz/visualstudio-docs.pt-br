---
title: IDiaSymbol::get_numberOfRegisterIndices | Microsoft Docs
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
ms.assetid: 1ec8b8ea-e423-4327-8dc0-a390e6e3ffb0
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 798a21bc0308e7f478f09cbd52754b81f21802e3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49174046"
---
# <a name="idiasymbolgetnumberofregisterindices"></a>IDiaSymbol::get_numberOfRegisterIndices
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o número de índices de registro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT get_numberOfRegisterIndices(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Um ponteiro para um `DWORD` que contém o número de índices de registro.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



