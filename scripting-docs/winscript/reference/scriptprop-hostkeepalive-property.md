---
title: Propriedade SCRIPTPROP_HOSTKEEPALIVE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724bfcb1ec42617cda4c89269cb0160accafb1a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150199"
---
# <a name="scriptprophostkeepalive-property"></a>Propriedade SCRIPTPROP_HOSTKEEPALIVE
Usado para especificar se o mecanismo de script deve ser mantido totalmente funcional se houver referências pendentes.  
  
 Use [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) para definir essa propriedade como `true`. Se essa propriedade é definida como `true`, o mecanismo de script é mantido completamente funcional, desde que exista pelo menos uma referência pendente para o mecanismo de script ou um `IDispatch` ponteiro para um objeto JavaScript criado usando o script mecanismo. Quando essa propriedade é definida como `true`, você deve fechar não explicitamente ou redefinir o mecanismo de script usando o [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) ou [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) métodos. A versão da última referência a um objeto de script desliga o mecanismo de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Requisitos  
 Essa propriedade é exibida apenas na versão do activscp.idl é instalado com [!INCLUDE[win8](../../javascript/includes/win8-md.md)], com 2707082 KB para o Internet Explorer 8 em [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], ou com 2722913 KB para o Internet Explorer 9 no [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] ou [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].