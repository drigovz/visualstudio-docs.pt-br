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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4a54193b23015135b6112655fe48d79d3de74e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943147"
---
# <a name="scccloseproject-function"></a>Função SccCloseProject
Essa função fecha um projeto, marcando o final de uma sessão específica.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parâmetros
 pvContext a estrutura de contexto do plug-in de controle do código-fonte.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O projeto foi fechado com êxito.|
|SCC_E_PROJNOTOPEN|Nenhum projeto está aberto no momento.|
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|
|SCC_E_NONSPECIFICERROR|Falha não específica.|

## <a name="remarks"></a>Comentários
 O [SccOpenProject](../extensibility/sccopenproject-function.md) é sempre chamado antes dessa função. Uma chamada para essa função é seguida por uma chamada para a `SccOpenProject` função ou [SccUninitialize](../extensibility/sccuninitialize-function.md), que termina a conexão com o sistema de controle do código-fonte completamente.

## <a name="see-also"></a>Confira também
- [Funções da API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
