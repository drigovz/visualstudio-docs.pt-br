---
title: Interface IDebugProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e5e5274e8a3d1c81ce010afc3893b27510a0fad
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348354"
---
# <a name="idebugproperty-interface"></a>Interface IDebugProperty
Usado para descrever qualquer propriedade hierárquica da entidade que está sendo depurada que tem um nome, tipo e valor. Mais comumente, `IDebugProperty` é usado para descrever o resultado da avaliação da expressão, instrução avaliação ou avaliação do registro.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos do `IDebugProperty` Interface.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Obter o `DebugPropertyInfo` que descreve esse `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Obtém as informações estendidas em uma propriedade.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Define o valor de uma propriedade de uma cadeia de caracteres.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Enumera os membros de uma propriedade.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Obtém o pai de uma propriedade.|  
  
## <a name="requirements"></a>Requisitos  
 Header: dbgprop.h