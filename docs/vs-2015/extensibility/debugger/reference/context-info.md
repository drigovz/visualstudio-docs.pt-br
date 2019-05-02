---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4e8c1b438cd2fa2721e81f055695e5836c26d12
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928409"
---
# <a name="contextinfo"></a>CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa estrutura descreve um contexto de memória ou o contexto de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Membros  
 dwFields  
 Uma combinação de sinalizadores de ele [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumeração que especifica quais campos são preenchidos<strong>.</strong>  
  
 bstrModuleUrl  
 O nome do módulo no qual o contexto está localizado.  
  
 bstrFunction  
 O nome da função onde se encontra o contexto.  
  
 posFunctionOffset  
 Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura que identifica o deslocamento de linha e coluna da função associada com o contexto de código.  
  
 bstrAddress  
 O endereço no código onde se encontra o contexto determinado.  
  
 bstrAddressOffset  
 O deslocamento do endereço no código onde se encontra o contexto determinado.  
  
 bstrAddressAbsolute  
 O endereço absoluto na memória onde se encontra o contexto determinado.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é retornada de uma chamada para o [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) método.  
  
 Um uso típico para esta estrutura é suportados uma **memória** janela de depuração.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
