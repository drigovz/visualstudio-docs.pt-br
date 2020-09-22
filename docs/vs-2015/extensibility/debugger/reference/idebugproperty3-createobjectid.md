---
title: 'IDebugProperty3:: createobjectid | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0035faad9078acd70886d597f039c0d8de5ee12f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838336"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cria uma ID exclusiva para essa propriedade para garantir que ela seja exclusiva entre todas as outras propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado quando o Gerenciador de depuração de sessão deseja certificar-se de que essa propriedade seja identificada exclusivamente entre todas as outras propriedades. O mecanismo de depuração (DE) dá suporte a esse método, a menos que as propriedades com as quais ele lida já estejam identificadas exclusivamente. Se o DE não oferecer suporte a esse método, ele retornará `E_NOTIMPL` .  
  
 Qualquer ID exclusiva criada com `CreateObjectID` é destruída quando o método [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) é chamado; isso também sinaliza o fim da necessidade de identificar exclusivamente essa propriedade.  
  
> [!NOTE]
> Não há nenhum método para recuperar essa ID exclusiva, portanto, o DE pode fazer o que quiser para IDs exclusivas quando o `CreateObjectID` método é chamado.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
