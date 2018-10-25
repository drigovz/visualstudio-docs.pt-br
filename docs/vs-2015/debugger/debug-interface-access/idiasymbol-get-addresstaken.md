---
title: 'Idiasymbol:: Get_addresstaken | Microsoft Docs'
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
- IDiaSymbol::get_addressTaken method
ms.assetid: 0d366188-f5e1-4226-b392-58c09539d097
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b23aa524c026e115e50b94f58b68463a68f67a94
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825875"
---
# <a name="idiasymbolgetaddresstaken"></a>IDiaSymbol::get_addressTaken
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera um sinalizador que indica se o outro símbolo faz referência ao endereço desse símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_addressTaken (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 [out] Retorna `TRUE` se outro símbolo faz referência a esse endereço; caso contrário, retornará `FALSE`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir `B` referências `A`. Portanto, o símbolo `A`do `get_addressTaken` retorno do método `TRUE`.  
  
```cpp#  
int A  = 0;  
int* B = &A;  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descrição|  
|-----------------|-----------------|  
|Cabeçalho:|dia2.h|  
|Versão:|DIA SDK v7.0|  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



