---
title: Função SccCheckin | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ba512642e1a63d9d39856f96194d717583d44f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701177"
---
# <a name="scccheckin-function"></a>Função SccCheckin
Esta função verifica arquivos previamente verificados no sistema de controle de origem, armazenando as alterações e criando uma nova versão. Esta função é chamada com uma contagem e uma matriz de nomes dos arquivos a serem verificados.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in SCC pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 nArquivos

[em] Número de arquivos selecionados para serem verificados.

 lpFileNames

[em] Matriz de nomes de caminhos locais totalmente qualificados de arquivos a serem verificados.

 lpComment

[em] Comentário a ser aplicado a cada um dos arquivos selecionados que estão sendo verificados. Este parâmetro `NULL` é se o plug-in de controle de origem deve solicitar um comentário.

 fOpções

[em] Bandeiras de comando, 0 ou `SCC_KEEP_CHECKEDOUT`.

 pvOpções

[em] Opções específicas de plug-in SCC.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O arquivo foi verificado com sucesso.|
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle de código fonte.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica. O arquivo não foi verificado.|
|SCC_E_NOTCHECKEDOUT|O usuário não checou o arquivo, então não pode fazer o check-in.|
|SCC_E_CHECKINCONFLICT|O check-in não pôde ser realizado porque:<br /><br /> - Outro usuário fez `bAutoReconcile` check-in na frente e foi falso.<br /><br /> -ou-<br /><br /> - A fusão automática não pode ser feita (por exemplo, quando os arquivos são binários).|
|SCC_E_VERIFYMERGE|O arquivo foi mesclado automaticamente, mas não foi verificado na verificação pendente do usuário.|
|SCC_E_FIXMERGE|O arquivo foi mesclado automaticamente, mas não foi verificado devido a um conflito de mesclagem que deve ser resolvido manualmente.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|
|SCC_E_FILENOTEXIST|O arquivo local não foi encontrado.|

## <a name="remarks"></a>Comentários
 O comentário se aplica a todos os arquivos que estão sendo verificados. O argumento de `null` comentário pode ser uma string, nesse caso o plug-in de controle de origem pode solicitar ao usuário uma seqüência de comentários para cada arquivo.

 O `fOptions` argumento pode ser dado um valor do `SCC_KEEP_CHECKEDOUT` sinalizador para indicar a intenção do usuário de verificar o arquivo e verificar novamente.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
