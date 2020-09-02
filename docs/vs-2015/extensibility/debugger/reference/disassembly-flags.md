---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d48fcf9dd941194b56e2c794ad7f5673f8e58421
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159305"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica os sinalizadores para desmontagem.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Membros  
 DF_DOCUMENTCHANGE  
 Indica que essa instrução está em um documento diferente do anterior.  
  
 DF_DISABLED  
 Indica que esta instrução não será executada.  
  
 DF_INSTRUCTION_ACTIVE  
 Indica que essa instrução é uma das próximas instruções a serem executadas (pode haver mais de uma).  
  
 DF_DATA  
 Indica que essa instrução é realmente dados (não código).  
  
 DF_HASSOURCE  
 Indica que esta instrução tem fonte. Algumas instruções, como criação de perfil ou código de coleta de lixo, não têm origem correspondente.  
  
 DF_DOCUMENT_CHECKSUM  
 Indica que `bstrDocumentUrl` o campo contém dados de soma de verificação após a URL do documento. Consulte a seção comentários da estrutura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) para saber como os dados de soma de verificação são armazenados.  
  
## <a name="remarks"></a>Comentários  
 Usado como o `dwFlags` membro da estrutura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) .  
  
 Esses sinalizadores podem ser combinados com uma operadora de bits `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
