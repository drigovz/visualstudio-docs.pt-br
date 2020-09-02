---
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e1af059cf4319c18b8f8bb63e7b50ec3d2822e93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568428"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém os bytes de atributos personalizados, dado o nome do atributo personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszCustomAttributeName`  
 no Uma cadeia de caracteres que contém o nome do atributo personalizado a ser pesquisado.  
  
 `ppBlob`  
 [entrada, saída] Uma matriz que é preenchida com os bytes do atributo personalizado.  
  
 `pdwLen`  
 [entrada, saída] Especifica o número máximo de bytes a serem retornados na `ppBlob` matriz e retorna o número de bytes gravados na matriz.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK ou retornará S_FALSE se o atributo personalizado não existir. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Defina o `ppBlob` parâmetro como um valor nulo para retornar o número de bytes de atributos disponíveis. Em seguida, aloque uma matriz e passe essa matriz no para o `ppBlob` parâmetro.  
  
 Os bytes de atributo representam os dados brutos do atributo personalizado.  
  
 Se os `ppBlob` `pdwLen` parâmetros e forem definidos como um valor nulo, esse método poderá ser usado para determinar se o atributo personalizado simplesmente existe. No entanto, uma alternativa mais fácil é chamar o método [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
