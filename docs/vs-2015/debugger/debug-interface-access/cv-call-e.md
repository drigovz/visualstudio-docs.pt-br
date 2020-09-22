---
title: CV_call_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd1ee4c024894e5752277a5000d37745c88c4ac6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838523"
---
# <a name="cv_call_e"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica a Convenção de chamada para uma função.  
  
> [!NOTE]
> Somente os valores de enumeração mais comuns são documentados aqui. A enumeração completa está disponível no arquivo de cabeçalho cvconst. h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Elementos  
 CV_CALL_NEAR_C  
 Especifica uma Convenção de chamada de função usando um push próximo da direita para a esquerda. A função de chamada limpa a pilha.  
  
 CV_CALL_NEAR_FAST  
 Especifica uma Convenção de chamada de função usando um push próximo da esquerda para a direita com registros. A função chamada usa a soma dos bytes de parâmetro para limpar a pilha.  
  
 CV_CALL_NEAR_STD  
 Especifica uma Convenção de chamada de função usando uma chamada quase padrão (Push da direita para a esquerda).  
  
 CV_CALL_NEAR_SYS  
 Especifica uma Convenção de chamada de função usando uma chamada do sistema próxima.  
  
 CV_CALL_THISCALL  
 Especifica uma Convenção de chamada de função usando `this` Call ( `this` ponteiro passado no registro).  
  
 CV_CALL_CLRCALL  
 Especifica uma Convenção de chamada de função usada pelo CLR (Common Language Runtime) (também conhecido como Convenção de chamada de código gerenciado).  
  
## <a name="remarks"></a>Comentários  
 Os valores nessa enumeração são retornados por uma chamada para o método [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst. h  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
