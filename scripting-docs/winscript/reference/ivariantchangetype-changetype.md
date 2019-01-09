---
title: IVariantChangeType::ChangeType | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a02b8a3991ff6d20370cd4a2ea4cd87aa9a1226
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086574"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Usa um valor variant e cria uma nova variante com um tipo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pvarDst`  
 [no, out] Uma variante para conter o valor representado pelo `pvarSrc`, mas com o tipo especificado pelo `vtNew`.  
  
 `pvarSrc`  
 [in] Um valor variant para mudar para um novo tipo.  
  
 `lcid`  
 [in] O contexto de localidade a ser usada ao converter os argumentos para ou de cadeias de caracteres.  
  
 `vtNew`  
 [in] Especifica o tipo para `pvarDst` para se tornar.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O `pvarDst` e `pvarSrc` os argumentos podem ser iguais, caso em que o valor original é substituído. Esse método passa `pvarDst` para o `VariantClear` função e, consequentemente, `pvarDst` deve ser inicializado como um valor válido.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)