---
title: 'IActiveScript:: AddTypeLib | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575806"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Adiciona uma biblioteca de tipos ao espaço de nome do script. Isso é semelhante à diretiva `#include` em C/C++. Ele permite que um conjunto de itens predefinidos, como definições de classe, `typedefs` e constantes nomeadas, seja adicionado ao ambiente de tempo de execução disponível para o script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidTypeLib`  
 no CLSID da biblioteca de tipos a ser adicionada.  
  
 `dwMaj`  
 no Número de versão principal.  
  
 `dwMin`  
 no Número de versão secundário.  
  
 `dwFlags`  
 no Sinalizadores de opção. Pode ser o seguinte:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|A biblioteca de tipos descreve um controle ActiveX usado pelo host.|  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
|`TYPE_E_CANTLOADLIBRARY`|Não foi possível carregar a biblioteca de tipos especificada.|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)