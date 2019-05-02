---
title: Função SccGetUserOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b237ded8ac0d22500986a9d390834147f24a2c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433182"
---
# <a name="sccgetuseroption-function"></a>Função SccGetUserOption
Essa função recupera uma variedade de opções específicas do usuário.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parâmetros
 pContext

[in] O ponteiro de contexto de plug-in de controle do código-fonte.

 nOption

[in] Opção de recuperação (consulte comentários para obter possíveis opções).

 lpVal

[out] Valor associado com a opção.

## <a name="return-value"></a>Valor de retorno
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Opção foi recuperada com êxito.|
|SCC_E_OPNOTSUPPORTED|Não há suporte para a opção.|
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado.|

## <a name="remarks"></a>Comentários
 As opções a seguir têm suporte por este comando:

|Opção de usuário|Descrição|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se o usuário deseja fazer check-out da versão local dos arquivos. `lpVal` é atribuída `SCC_USEROPT_COLV_YES` (o usuário deseja fazer check-out de arquivos locais) ou `SCC_USEROPT_COLV_NO`.|

## <a name="see-also"></a>Consulte também
- [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [Códigos de erro](../extensibility/error-codes.md)