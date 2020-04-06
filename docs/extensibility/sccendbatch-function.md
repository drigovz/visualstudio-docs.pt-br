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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700916"
---
# <a name="sccendbatch-function"></a>Função SccEndBatch
Esta função conclui um lote de operações de controle de origem. Estes lotes podem não estar aninhados.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>parâmetros
 Nenhum.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Lote de operações concluídacom sucesso.|
|SCC_E_UNKNOWNERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 Os lotes de controle de origem são usados para executar as mesmas operações de controle de origem em vários projetos ou vários contextos. Os lotes podem ser usados para eliminar caixas de diálogo redundantes da experiência do usuário durante uma operação em lote. O [SccBeginBatch](../extensibility/sccbeginbatch-function.md) `SccEndBatch` e a função são usados como um par para indicar o início e o fim de uma operação. Eles não podem ser aninhados.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
