---
title: 'IDiaSymbol:: get_isPointerToDataMember | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef17c737-242e-43e8-b7e1-2c3bc58cfcef
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca44d11dfcec717e37a9bc13a2d87f9f5a94ede3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155875"
---
# <a name="idiasymbolget_ispointertodatamember"></a>IDiaSymbol::get_isPointerToDataMember
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica se este símbolo é um ponteiro para um membro de dados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT get_isPointerToDataMember(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Um ponteiro para um `BOOL` que especifica se este símbolo é um ponteiro para um membro de dados.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
