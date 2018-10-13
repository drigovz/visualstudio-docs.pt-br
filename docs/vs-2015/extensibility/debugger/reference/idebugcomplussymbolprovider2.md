---
title: IDebugComPlusSymbolProvider2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6aed363d7f3571fa26d291858ce63ba654afaec1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186219"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Representa um provedor de símbolo COM+ com métodos que são específicos para o código gerenciado e estende o **IDebugComPlusSymbolProvider**[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider  
```  
  
## <a name="methods"></a>Métodos  
 Além dos métodos na [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface, essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Determina se o método especificado tem informações de linha.|  
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Recupera um tipo de dado seu nome.|  
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Recupera um tipo de dado seu token.|  
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Determina se o endereço de depuração especificada é um ponto de sequência.|  
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Cargas de depurar símbolos usando o método de retorno de chamada especificados.|  
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|Carregar símbolos de depuração de um fluxo de dados que recebe o **ICorDebugModule** objeto.|  
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|Cargas de dado de símbolos de depuração a **ICorDebugModule** objeto.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

