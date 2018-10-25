---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
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
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cf9a8cfde8ea909759d573c336247720979ae2a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916082"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cria uma ID exclusiva para essa propriedade para garantir que ele seja exclusivo entre todas as outras propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado quando o Gerenciador de sessão de depuração quer ter certeza de que essa propriedade é identificada exclusivamente entre todas as outras propriedades. O mecanismo de depuração (DES) dá suporte a esse método, a menos que as propriedades que ele lida com são identificadas já exclusivamente. Se o DE não oferece suporte a esse método, ele retorna `E_NOTIMPL`.  
  
 Qualquer ID exclusiva é criada com `CreateObjectID` é destruído quando o [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) é chamado de método; isso também sinaliza o término da necessidade de identificando exclusivamente esta propriedade.  
  
> [!NOTE]
>  Não há nenhum método para recuperar essa ID exclusiva, portanto, o DE pode fazer o que quiser para IDs exclusivas quando o `CreateObjectID` método é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)

