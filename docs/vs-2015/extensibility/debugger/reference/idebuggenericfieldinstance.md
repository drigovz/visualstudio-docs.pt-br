---
title: IDebugGenericFieldInstance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ab9c43e915f2c23dfe5f38ce61beff29949ca0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180806"
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Representa uma instância de um campo para um tipo genérico de código gerenciado.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugGenericFieldInstance : IUnknown  
```  
  
## <a name="methods"></a>Métodos  
 Essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|Recupera os argumentos de parâmetro de tipo para esta instância.|  
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|Retorna o número de argumentos de parâmetro de tipo para esta instância.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
