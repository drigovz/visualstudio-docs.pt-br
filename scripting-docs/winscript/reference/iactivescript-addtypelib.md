---
title: IActiveScript::AddTypeLib | Microsoft Docs
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
ms.openlocfilehash: c4943d1305c2f25de4eec9e782949a66827de879
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144869"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Adiciona uma biblioteca de tipos para o espaço para nome para o script. Isso é semelhante ao `#include` diretiva em C/C++. Ele permite que um conjunto de itens predefinidos, como definições de classe, `typedefs`e constantes a ser adicionado ao ambiente de tempo de execução disponível para o script nomeadas.  
  
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
 [in] CLSID da biblioteca de tipos para adicionar.  
  
 `dwMaj`  
 [in] Número de versão principal.  
  
 `dwMin`  
 [in] Número de versão secundária.  
  
 `dwFlags`  
 [in] Sinalizadores de opção. Pode ser o seguinte:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|A biblioteca de tipos descreve um controle ActiveX usado pelo host.|  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
|`TYPE_E_CANTLOADLIBRARY`|Não foi possível carregar a biblioteca de tipos especificada.|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)