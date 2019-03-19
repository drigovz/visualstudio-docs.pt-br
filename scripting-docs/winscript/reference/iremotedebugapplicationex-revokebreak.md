---
title: IRemoteDebugApplicationEx:RevokeBreak | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:RevokeBreak
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:RevokeBreak
ms.assetid: 1f077860-0a39-4ec9-b676-ae0712819c7b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0992eb5637434ccdf0dbf4fa6e436c87ae3fdd6c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148172"
---
# <a name="iremotedebugapplicationexrevokebreak"></a>IRemoteDebugApplicationEx:RevokeBreak

Revoga um comando de interrupção.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT RevokeBreak( );
```

### <a name="parameters"></a>Parâmetros

nenhuma.

## <a name="return-value"></a>Valor de retorno

O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.

|Valor|Descrição|
|-----------|-----------------|
|`S_OK`|O método foi bem-sucedido.|

## <a name="see-also"></a>Consulte também

- [Interface IRemoteDebugApplicationEx](iremotedebugapplicationex-interface.md)