---
title: Função SccCloseProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71df385bc0cf42c2437abfd117c2f84bda5b5432
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701056"
---
# <a name="scccloseproject-function"></a>Função SccCloseProject
Esta função fecha um projeto, marcando o final de uma sessão específica.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>parâmetros
 pvContext A estrutura de contexto plug-in de controle de origem.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O projeto foi fechado com sucesso.|
|SCC_E_PROJNOTOPEN|Nenhum projeto está aberto no momento.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 O [SccOpenProject](../extensibility/sccopenproject-function.md) é sempre chamado antes desta função. Uma chamada para esta função é seguida `SccOpenProject` por uma chamada para a função ou para o [SccUninitialize](../extensibility/sccuninitialize-function.md), que termina a conexão ao sistema de controle de origem completamente.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
