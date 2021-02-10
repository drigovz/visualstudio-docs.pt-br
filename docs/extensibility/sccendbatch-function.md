---
title: Função SccEndBatch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 85d49fcd9920c442aa1736f1fb0f3e46ccd4eba0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943043"
---
# <a name="sccendbatch-function"></a>Função SccEndBatch
Essa função conclui um lote de operações de controle do código-fonte. Esses lotes não podem ser aninhados.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parâmetros
 Nenhum.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O lote de operações foi concluído com êxito.|
|SCC_E_UNKNOWNERROR|Falha não específica.|

## <a name="remarks"></a>Comentários
 Os lotes de controle do código-fonte são usados para executar as mesmas operações de controle do código-fonte em vários projetos ou em vários contextos. Os lotes podem ser usados para eliminar caixas de diálogo redundantes da experiência do usuário durante uma operação em lote. O [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e a `SccEndBatch` função são usados como um par para indicar o início e o fim de uma operação. Eles não podem ser aninhados.

## <a name="see-also"></a>Confira também
- [Funções da API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
