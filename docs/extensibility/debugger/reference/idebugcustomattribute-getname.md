---
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e744839b7f0461249f16afec7c2186adc26e245f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021332"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Obtém o nome do atributo personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bstrName`  
 [out] Retorna uma cadeia de caracteres que contém o nome do atributo personalizado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Nomeado retornado por esse método corresponde ao nome da classe usada para declarar o atributo. Não exatamente, isso pode corresponder ao nome da classe de atributo personalizado em si como o c# permite que o sufixo "Attribute" a ser removido de um nome de atributo personalizado quando ele é usado em uma declaração.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)