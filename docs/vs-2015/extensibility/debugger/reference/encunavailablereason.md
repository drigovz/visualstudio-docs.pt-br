---
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ebdc5518579223a0081f30a0affd3a45e91604e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198767"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Representa os motivos pelos quais **Editar e continuar** não estão disponíveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ENCUN_NONE  
 Nenhum motivo específico pelo qual editar e continuar não está disponível.  
  
 ENCUN_INTEROP  
 Editar e continuar não está disponível durante uma chamada de interoperabilidade.  
  
 ENCUN_SQLCLR  
 Editar e continuar não está disponível durante uma chamada de procedimento SQL que usa o CLR (Common Language Runtime).  
  
 ENCUN_MINIDUMP  
 Editar e continuar não está disponível durante o processamento de um mini-despejo.  
  
 ENCUN_EMBEDDED  
 Editar e continuar não está disponível durante o processamento de código inserido.  
  
 ENCUN_ATTACH  
 Editar e continuar não está disponível porque a sessão foi anexada a, não iniciada pelo, o depurador.  
  
 ENCUN_WIN64  
 Editar e continuar não está disponível durante o processamento do código do Windows de 64 bits.  
  
## <a name="remarks"></a>Comentários  
 Essa enumeração é para uso interno apenas pelo [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] . Os métodos [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) e [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) , conforme implementados por um fornecedor de porta personalizada, sempre devem retornar `E_NOTIMPL` .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. idl  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
