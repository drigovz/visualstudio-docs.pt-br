---
title: Função SccGetEvents | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700815"
---
# <a name="sccgetevents-function"></a>Função SccGetEvents
Esta função recupera um evento de status enfileirado.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 Lpfilename

[dentro, fora] Buffer onde o plug-in de controle de origem coloca o nome do arquivo retornado (até _MAX_PATH caracteres).

 lpStatus

[dentro, fora] Retorna código de status (consulte [Código de status de arquivo](../extensibility/file-status-code-enumerator.md) para possíveis valores).

 pnEventsRemaining

[dentro, fora] Retorna número de entradas deixadas na fila após esta chamada. Se esse número for grande, o chamador pode decidir ligar para o [SccQueryInfo](../extensibility/sccqueryinfo-function.md) para obter todas as informações de uma só vez.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Obter eventos bem sucedidos.|
|SCC_E_OPNOTSUPPORTED|Não há suporte para essa função.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 Esta função é chamada durante o processamento ocioso para ver se houve alguma atualização de status para arquivos sob controle de origem. O plug-in de controle de origem mantém o status de todos os arquivos que ele conhece e sempre que uma mudança de status é notada pelo plug-in, o status e o arquivo associado são armazenados em uma fila. Quando `SccGetEvents` é chamado, o elemento superior da fila é recuperado e devolvido. Esta função é restrita para retornar apenas informações previamente armazenadas em cache e deve ter uma reviravolta muito rápida (ou seja, sem leitura do disco ou pedindo ao sistema de controle de origem o status); caso contrário, o desempenho do IDE pode começar a se degradar.

 Se não houver atualização de status para relatar, o plug-in de `lpFileName`controle de origem armazena uma seqüência vazia no buffer apontado por . Caso contrário, o plug-in armazena o nome completo do caminho do arquivo para o qual as informações de status foram alteradas e retorna o código de status apropriado (um dos valores detalhados no [código de status do arquivo).](../extensibility/file-status-code-enumerator.md)

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [Código de status de arquivo](../extensibility/file-status-code-enumerator.md)
