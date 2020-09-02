---
title: 'IDebugDocument2:: GetName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09456b20faf4d5f5ea09baa55e0a7fd78a19a95c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186650"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o nome do documento em uma de várias formas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `gnType`  
 no Um valor da enumeração [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) que determina o tipo de nome a ser retornado.  
  
 `pbstrFileName`  
 fora Retorna uma cadeia de caracteres que contém o nome do documento.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método pode, por exemplo, retornar o nome do documento como um título ou um nome de arquivo ou até mesmo parte de um nome de arquivo.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
