---
title: 'IDebugProgramPublisher2:: UnpublishProgram | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 05efc566cec0e7e885b16a4bb7c7e7d6256ac7b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146274"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Torna um programa indisponível para ser depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDebuggeeInterface`  
 no Uma `IUnknown` interface para o programa. Esse é o mesmo valor fornecido para o método [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) e identifica exclusivamente o programa que está sendo removido (ou seja, é usado como um cookie).  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Para disponibilizar um programa para os mecanismos de depuração e o Gerenciador de depuração de sessão, use o método [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
