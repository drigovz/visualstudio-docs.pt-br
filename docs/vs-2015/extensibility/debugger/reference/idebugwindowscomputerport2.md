---
title: IDebugWindowsComputerPort2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugWindowsComputerPort2 interface
ms.assetid: 25f327b8-0303-4268-88d1-74df630436aa
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd11e57c8e2ec03da1dcfa9ff76b3b3ec2ded5e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149313"
---
# <a name="idebugwindowscomputerport2"></a>IDebugWindowsComputerPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Permite consultar informações sobre o computador de destino.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugWindowsComputerPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 Essa interface é implementada por objetos de porta do Gerenciador de depuração de sessão.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugWindowsComputerPort2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)|Recupera informações sobre o computador no qual o depurador está em execução.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
