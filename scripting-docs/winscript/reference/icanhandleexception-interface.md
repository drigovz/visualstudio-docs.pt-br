---
title: Interface ICanHandleException | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICanHandleException interface
ms.assetid: 32df7f81-557d-40cf-a844-06a6eaa292f3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 363a52cfeb409d293ba3589b9d869bbc4fdf5918
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150901"
---
# <a name="icanhandleexception-interface"></a>Interface ICanHandleException
Permite que o chamador de um mecanismo de script para especificar quais exceções o chamador identificadores.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos herdados de `IUnknown`, o `ICanHandleException` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[ICanHandleException::CanHandleException](../../winscript/reference/icanhandleexception-canhandleexception.md)|Determina se o chamador do mecanismo de script pode manipular uma exceção especificada.|