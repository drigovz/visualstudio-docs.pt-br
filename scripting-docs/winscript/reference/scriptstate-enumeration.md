---
title: Enumeração de SCRIPTstate | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10dd6366e2d0783ec2e9d6bdadc001e9f999901e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575679"
---
# <a name="scriptstate-enumeration"></a>Enumeração SCRIPTSTATE
Especifica o estado de um mecanismo de script. Essa enumeração é usada pelos métodos [IActiveScript:: Getscriptstate](../../winscript/reference/iactivescript-getscriptstate.md) , [IActiveScript:: setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) e [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeração  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|O script acabou de ser criado, mas ainda não foi inicializado usando uma interface `IPersist*` e [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|O script foi inicializado, mas não está em execução (conectando-se a outros objetos ou eventos de coletor) ou executando qualquer código. O código pode ser consultado para execução chamando o método [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) .|  
|SCRIPTSTATE_STARTED|O script pode executar código, mas ainda não está coletando os eventos de objetos adicionados pelo método [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|SCRIPTSTATE_CONNECTED|O script é carregado e conectado para eventos de coletor.|  
|SCRIPTSTATE_DISCONNECTED|O script é carregado e tem um estado de execução de tempo de execução, mas está temporariamente desconectado dos eventos de coletor.|  
|SCRIPTSTATE_CLOSED|O script foi fechado. O mecanismo de script não funciona e retorna erros para a maioria dos métodos.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e códigos de erro do script ativo](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)