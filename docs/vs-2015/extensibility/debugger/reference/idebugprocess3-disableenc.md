---
title: IDebugProcess3::D isableENC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0db9eb44b8074a5c5e3b35a5a5dadcf04f37fb2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838463"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método desabilita explicitamente editar e continuar neste processo (e todos os programas que ele contém). Um fornecedor de porta personalizada sempre deve retornar `E_NOTIMPL` .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `reason`  
 no Um valor da enumeração [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro.  
  
> [!NOTE]
> Um fornecedor de porta personalizada sempre deve retornar `E_NOTIMPL` .  
  
## <a name="remarks"></a>Comentários  
 Depois que editar e continuar estiver desabilitado para um processo, ele poderá ser habilitado novamente apenas reiniciando o processo.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
