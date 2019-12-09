---
title: 'IApplicationDebugger:: CreateInstanceAtDebugger | Microsoft Docs'
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
ms.openlocfilehash: c15dc5d9b36a718ed41813bac46bc4b9415eb853
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577883"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Permite a criação de objetos no processo do depurador por código que está fora do processo para o depurador.  
  
> [!IMPORTANT]
> Esse método não deve ser implementado, pois permite que um código não confiável Crie objetos arbitrários em um thread de depurador confiável.  
  
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
 no Identificador de classe (CLSID) do objeto a ser criado.  
  
 `pUnkOuter`  
 no Se `NULL`, o objeto não será criado como parte de uma agregação. Caso contrário, `pUnkOuter` é um ponteiro para a interface de `IUnknown` do objeto de agregação (o `IUnknown` de controle).  
  
 `dwClsContext`  
 no Contexto para execução do código executável. Os valores são obtidos do `CLSCTX` de enumeração.  
  
 `riid`  
 no O identificador de interface usado para se comunicar com o objeto.  
  
 `ppvObject`  
 fora Endereço da variável de ponteiro que recebe o ponteiro de interface solicitado em `riid`. Após o retorno bem-sucedido, * `ppvObject` conterá o ponteiro de interface solicitado. Após a falha, \* `ppvObject` contém `NULL`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método delega para `CoCreateInstance`.  
  
 O método não está implementado no momento.  
  
## <a name="see-also"></a>Consulte também  
 [IApplicationDebugger Interface](../../winscript/reference/iapplicationdebugger-interface.md)