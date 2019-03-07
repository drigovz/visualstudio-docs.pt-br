---
title: Interface IDispError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b717ebfe740a9b356513bb0f15e90c629a14e147
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345832"
---
# <a name="idisperror-interface"></a>Interface IDispError
Fornece informações contextuais detalhadas do erro.  
  
> [!NOTE]
>  Essa interface não é implementada.  
  
 Além dos métodos herdados de `IUnknown`, o `IDispError` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Recupera um tipo específico de informações de erro.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Recupera o próximo `IDispError` objeto.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Recupera o código de erro do `IDispError` objeto.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Retorna o identificador programático do dependente de idioma para a classe ou um aplicativo que gerou o erro.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Retorna o caminho do arquivo de Ajuda e a ID do contexto do tópico que explica o erro, se possível.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Retorna uma descrição textual do erro.|