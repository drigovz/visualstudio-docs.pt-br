---
title: IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 601f20c530ec5e275139d1e70d3df58fa88cd715
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147625"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Permite a criação de objetos no processo do depurador pelo código que é out-of-process para o depurador.  
  
> [!IMPORTANT]
>  Esse método não deve ser implementado, pois permite que código não confiável criar objetos arbitrários em um thread do depurador confiável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rclsid`  
 [in] Classe CLSID (identificador) do objeto a ser criado.  
  
 `pUnkOuter`  
 [in] Se `NULL`, o objeto não está sendo criado como parte de uma agregação. Caso contrário, `pUnkOuter` é um ponteiro para o objeto agregado `IUnknown` interface (o controlando `IUnknown`).  
  
 `dwClsContext`  
 [in] Contexto de execução do código executável. Os valores são obtidos da enumeração `CLSCTX`.  
  
 `riid`  
 [in] O identificador de interface usado para se comunicar com o objeto.  
  
 `ppvObject`  
 [out] Endereço da variável de ponteiro que recebe o ponteiro de interface solicitado no `riid`. No retorno bem-sucedido, *`ppvObject` contém o ponteiro de interface solicitado. Em caso de falha, \* `ppvObject` contém `NULL`.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Este método delega ao `CoCreateInstance`.  
  
 O método não está implementado atualmente.  
  
## <a name="see-also"></a>Consulte também  
 [IApplicationDebugger Interface](../../winscript/reference/iapplicationdebugger-interface.md)