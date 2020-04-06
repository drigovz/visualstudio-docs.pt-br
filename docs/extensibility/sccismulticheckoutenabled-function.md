---
title: SccIsMultiCheckoutEnabled Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700577"
---
# <a name="sccismulticheckoutenabled-function"></a>Função SccIsMultiCheckoutEnabled
Esta função verifica se o plug-in de controle de origem permite vários checkouts em um arquivo.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>parâmetros
 pContext

[em] A estrutura de contexto plug-in de controle de origem.

 pbMultiCheckout

[fora] Especifica se vários checkouts estão habilitados para este projeto (não zero significa que vários checkouts são suportados).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O cheque foi bem sucedido.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 O IDE faz duas verificações para determinar se os arquivos podem ser verificados simultaneamente por mais de um usuário. Primeiro, o sistema de controle de origem deve suportar vários checkouts. O plug-in de controle de origem pode especificar esse recurso durante a inicialização especificando o `SCC_CAP_MULTICHECKOUT`. Depois disso, como uma segunda verificação, o IDE chama essa função para determinar se o projeto atual suporta ou não vários checkouts. Se vários checkouts forem suportados para o projeto selecionado, `pbMultiCheckout` o plug-in reameda um código de sucesso e definirá como não zero (`TRUE`) ou `FALSE`.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
