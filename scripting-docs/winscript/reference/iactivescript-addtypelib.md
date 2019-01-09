---
title: IActiveScript::AddTypeLib | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 695edbd6f5356959785e54dc38f28b68c8c0400e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092534"
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