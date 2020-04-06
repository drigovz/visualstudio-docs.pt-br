---
title: Função SccQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700474"
---
# <a name="sccqueryinfo-function"></a>Função SccQueryInfo
Esta função obtém informações de status para um conjunto de arquivos selecionados sob controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 nArquivos

[em] Número de arquivos especificados na `lpFileNames` matriz `lpStatus` e no comprimento da matriz.

 lpFileNames

[em] Uma série de nomes de arquivos a serem consultados.

 lpStatus

[dentro, fora] Uma matriz na qual o plug-in de controle de origem retorna os sinalizadores de status para cada arquivo. Para obter mais informações, consulte [File Status Code](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A consulta foi bem sucedida.|
|SCC_E_ACCESSFAILURE|Houve um problema com o acesso ao sistema de controle de origem, provavelmente causado por problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_PROJNOTOPEN|O projeto não está aberto sob controle de código.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 Se `lpFileName` for uma seqüência de string vazia, no momento não há informações de status para atualizar. Caso contrário, é o nome completo do caminho do arquivo para o qual as informações de status podem ter sido alteradas.

 A matriz de retorno pode `SCC_STATUS_xxxx` ser uma máscara de bits. Para obter mais informações, consulte [File Status Code](../extensibility/file-status-code-enumerator.md). Um sistema de controle de origem pode não suportar todos os tipos de bits. Por exemplo, `SCC_STATUS_OUTOFDATE` se não for oferecido, a broca simplesmente não está definida.

 Ao usar esta função para verificar `MSSCCI` arquivos, observe os seguintes requisitos de status:

- `SCC_STATUS_OUTBYUSER`é definido quando o usuário atual checou o arquivo.

- `SCC_STATUS_CHECKEDOUT`não pode `SCC_STATUS_OUTBYUSER` ser definido a menos que esteja definido.

- `SCC_STATUS_CHECKEDOUT`só é definido quando o arquivo é verificado no diretório de trabalho designado.

- Se o arquivo for verificado pelo usuário atual em um diretório `SCC_STATUS_OUTBYUSER` diferente do `SCC_STATUS_CHECKEDOUT` diretório de trabalho, será definido, mas não é.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [Código de status do arquivo](../extensibility/file-status-code-enumerator.md)
