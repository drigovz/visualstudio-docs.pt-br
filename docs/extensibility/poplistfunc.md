---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c5f8c1683a993915476ff23f1f5d5f2c2aba462
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702069"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Este retorno de chamada é fornecido ao [SccPopulateList](../extensibility/sccpopulatelist-function.md) pelo IDE e é usado pelo plug-in de controle `SccPopulateList` de origem para atualizar uma lista de arquivos ou diretórios (também fornecidos à função).

 Quando um usuário escolhe o comando **Obter** no IDE, o IDE exibe uma caixa de lista de todos os arquivos que o usuário pode obter. Infelizmente, o IDE não sabe a lista exata de todos os arquivos que o usuário pode obter; apenas o plug-in tem essa lista. Se outros usuários adicionaram arquivos ao projeto de controle de código fonte, esses arquivos devem aparecer na lista, mas o IDE não sabe sobre eles. O IDE constrói uma lista dos arquivos que ele acha que o usuário pode obter. Antes de exibir essa lista para o usuário, ele chama o [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` dando ao plug-in de controle de origem a chance de adicionar e excluir arquivos da lista.

## <a name="signature"></a>Assinatura
 O plug-in de controle de origem modifica a lista chamando uma função implementada pelo IDE com o seguinte protótipo:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>parâmetros
 pvCallerData `pvCallerData` O parâmetro passou pelo chamador (o IDE) para o [SccPopulateList](../extensibility/sccpopulatelist-function.md). O plug-in de controle de origem não deve assumir nada sobre o conteúdo deste parâmetro.

 fAddRemove `TRUE`If `lpFileName` é um arquivo que deve ser adicionado à lista de arquivos. Se `FALSE` `lpFileName` , é um arquivo que deve ser excluído da lista de arquivos.

 nStatus Status `lpFileName` of (uma `SCC_STATUS` combinação dos bits; consulte [File Status Code](../extensibility/file-status-code-enumerator.md) for details).

 lpFileName Caminho completo do diretório do nome do arquivo para adicionar ou excluir da lista.

## <a name="return-value"></a>Valor retornado

|Valor|Descrição|
|-----------|-----------------|
|`TRUE`|O plug-in pode continuar chamando esta função.|
|`FALSE`|Houve um problema no lado do IDE (como uma situação fora da memória). O plug-in deve parar de funcionar.|

## <a name="remarks"></a>Comentários
 Para cada arquivo que o plug-in de controle de origem deseja adicionar ou excluir `lpFileName`da lista de arquivos, ele chama essa função, passando no . O `fAddRemove` sinalizador indica um novo arquivo para adicionar à lista ou a um arquivo antigo para excluir. O `nStatus` parâmetro dá o status do arquivo. Quando o plug-in SCC terminar de adicionar e excluir arquivos, ele retorna da chamada [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

> [!NOTE]
> O `SCC_CAP_POPULATELIST` bit de capacidade é necessário para o Visual Studio.

## <a name="see-also"></a>Confira também
- [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Código de status de arquivo](../extensibility/file-status-code-enumerator.md)
