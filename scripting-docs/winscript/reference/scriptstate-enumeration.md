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
ms.openlocfilehash: d66d119c80c2b089c3d8a75a8e95d7095e9f9797
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238797"
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
  
|Valor|Estado de script|  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|O script acabou de ser criado, mas ainda não foi inicializado usando uma `IPersist*` interface e [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) .|  
|SCRIPTSTATE_INITIALIZED|O script foi inicializado, mas não está em execução (conectando-se a outros objetos ou eventos de coletor) ou executando qualquer código. O código pode ser consultado para execução chamando o método [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md) .|  
|SCRIPTSTATE_STARTED|O script pode executar código, mas ainda não está coletando os eventos de objetos adicionados pelo método [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|SCRIPTSTATE_CONNECTED|O script é carregado e conectado para eventos de coletor.|  
|SCRIPTSTATE_DISCONNECTED|O script é carregado e tem um estado de execução de tempo de execução, mas está temporariamente desconectado dos eventos de coletor.|  
|SCRIPTSTATE_CLOSED|O script foi fechado. O mecanismo de script não funciona e retorna erros para a maioria dos métodos.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e códigos de erro do script ativo](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)