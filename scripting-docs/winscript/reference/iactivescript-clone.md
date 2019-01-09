---
title: 'IActiveScript:: clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 084da486d2e5831176130ccd080b9e09a80c9bcc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093659"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clona o mecanismo de script atual (menos qualquer estado de execução atual), retornando um mecanismo de script carregado com nenhum site no thread atual. As propriedades desse novo mecanismo de script serão idênticas às propriedades que do mecanismo de script original seria em se ele foi transferida volta ao estado inicializado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppscript`  
 [out] Endereço de uma variável que recebe um ponteiro para o [IActiveScript](../../winscript/reference/iactivescript.md) interface de mecanismo de script clonado. O host deve criar um site e uma chamada a [IActiveScript:: Setscriptsite](../../winscript/reference/iactivescript-setscriptsite.md) método sobre o novo mecanismo de script antes de estar no estado inicializado e, portanto, utilizável.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_NOTIMPL`|Não há suporte para o método.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
  
## <a name="remarks"></a>Comentários  
 O `IActiveScript::Clone` método é uma otimização das `IPersist*::Save`, `CoCreateInstance`, e `IPersist*::Load`, portanto, o estado do mecanismo de script novo deve ser o mesmo como se o estado do mecanismo de script original foram salvos e carregado em um novo mecanismo de script. Itens nomeados são duplicados no mecanismo de script clonado, mas são esquecidos de ponteiros para objetos específicos para cada item e são obtidos com o [iactivescriptsite:: getItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) método. Isso permite que um modelo de objeto idênticas com pontos de entrada (um modelo de apartment) por thread a ser usado.  
  
 Esse método é usado para hosts de servidor multithread que podem executar várias instâncias do mesmo script. O mecanismo de script pode retornar `E_NOTIMPL`, caso em que o host pode obter o mesmo resultado duplicando o estado persistente e criar uma nova instância do mecanismo de script com um `IPersist*` interface.  
  
 Esse método pode ser chamado de threads não base sem resultando em um balão não base para objetos de host ou o [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)