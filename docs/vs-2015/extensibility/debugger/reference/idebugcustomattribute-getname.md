---
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15e02cdd0f1f3e601a37d144c9476877646674c4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872948"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o nome do atributo personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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

