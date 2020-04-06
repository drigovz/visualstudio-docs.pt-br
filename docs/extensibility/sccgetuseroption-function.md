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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc7b68df3331c1240ad833048940e656da034ccf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700684"
---
# <a name="sccgetuseroption-function"></a>Função SccGetUserOption
Esta função recupera uma variedade de opções específicas do usuário.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>parâmetros
 pContext

[em] O ponteiro de contexto plug-in de controle de origem.

 nOpção

[em] Opção para recuperar (consulte Observações para possíveis opções).

 lpVal

[fora] Valor associado à opção.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A opção foi recuperada com sucesso.|
|SCC_E_OPNOTSUPPORTED|A opção não é suportada.|
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado.|

## <a name="remarks"></a>Comentários
 As seguintes opções são suportadas por este comando:

|Opção de Usuário|Descrição|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se o usuário quer verificar a versão local dos arquivos. `lpVal`é atribuído `SCC_USEROPT_COLV_YES` (o usuário quer verificar `SCC_USEROPT_COLV_NO`arquivos locais) ou .|

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [Códigos de erro](../extensibility/error-codes.md)
