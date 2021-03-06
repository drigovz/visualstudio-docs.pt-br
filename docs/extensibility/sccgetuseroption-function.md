---
title: Função SccGetUserOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e4bc3e4bf6acef8ff8de1cdcecb2596dcf6d86e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844548"
---
# <a name="sccgetuseroption-function"></a>Função SccGetUserOption
Essa função recupera uma variedade de opções específicas do usuário.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parâmetros
 pContext

no O ponteiro de contexto do plug-in de controle do código-fonte.

 nOption

no Opção para recuperar (consulte comentários para as opções possíveis).

 lpVal

fora Valor associado à opção.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A opção foi recuperada com êxito.|
|SCC_E_OPNOTSUPPORTED|Não há suporte para a opção.|
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado.|

## <a name="remarks"></a>Comentários
 As opções a seguir são suportadas por este comando:

|Opção de usuário|Descrição|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se o usuário deseja fazer check-out da versão local dos arquivos. `lpVal` é atribuído `SCC_USEROPT_COLV_YES` (o usuário deseja fazer check-out de arquivos locais) ou `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Consulte também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [Códigos de Erro](../extensibility/error-codes.md)
