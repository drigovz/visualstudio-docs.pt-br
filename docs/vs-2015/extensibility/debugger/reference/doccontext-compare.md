---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6d0fd8cff2f352c8ede674be64062a738c1f3d02
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924814"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica os critérios para comparar dois contextos de documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Membros  
 DOCCONTEXT_EQUAL  
 Localize o contexto do documento primeiro na lista que é igual para o contexto do documento de destino.  
  
 DOCCONTEXT_LESS_THAN  
 Localize o contexto do documento primeiro na lista que é menor que o contexto do documento de destino.  
  
 DOCCONTEXT_GREATER_THAN  
 Localize o contexto do documento primeiro na lista que é maior que o contexto do documento de destino.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Localize o contexto do documento primeiro na lista que está no mesmo documento que o contexto do documento de destino.  
  
## <a name="remarks"></a>Comentários  
 Passado como um argumento para o [comparar](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) método.  
  
 Esses valores são usados para especificar um critério de comparação para localizar o contexto do documento primeiro em uma lista. Um contexto de documento é dada uma lista de contextos de documento para comparar a próprio em relação a por meio de `IDebugDocumentContext2::Compare` método. O contexto do documento primeiro na lista para o qual o operador de comparação é `true` , em seguida, será retornado.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
