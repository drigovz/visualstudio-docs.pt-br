---
title: Função SccAdd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23a6226b0d3cc2441a509c16b2e4672a766f3329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701309"
---
# <a name="sccadd-function"></a>Função SccAdd
Esta função adiciona novos arquivos ao sistema de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccAdd(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG*     pfOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 nArquivos

[em] Número de arquivos selecionados para serem adicionados `lpFileNames` ao projeto atual, conforme dado na matriz.

 lpFileNames

[em] Matriz de nomes locais totalmente qualificados de arquivos a serem adicionados.

 lpComment

[em] O comentário a ser aplicado a todos os arquivos que estão sendo adicionados.

 pfOpções

[em] Matriz de sinalizadores de comando, fornecidas por arquivo.

 pvOpções

[em] Opções específicas de plug-in de controle de origem.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A operação de adição foi bem sucedida.|
|SCC_E_FILEALREADYEXISTS|O arquivo selecionado já está sob controle de origem.|
|SCC_E_TYPENOTSUPPORTED|O tipo do arquivo (por exemplo, binário) não é suportado pelo sistema de controle de origem.|
|SCC_E_OPNOTSUPPORTED|O sistema de controle de origem não suporta esta operação.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_NONSPECIFICERROR|Falha não específica; adicionar não realizado.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|
|SCC_E_FILENOTEXIST|O arquivo local não foi encontrado.|

## <a name="remarks"></a>Comentários
 Os `fOptions` usuais são substituídos `pfOptions`aqui `LONG` por uma matriz, com uma especificação de opção por arquivo. Isso porque o tipo de arquivo pode variar de arquivo para arquivo.

> [!NOTE]
> É inválido especificar `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` ambos e opções para o mesmo arquivo, mas é válido especificar nenhum dos dois. A configuração também `SCC_FILETYPE_AUTO`não é a mesma que a configuração, nesse caso, o plug-in de controle de origem detecta automaticamente o tipo de arquivo.

 Abaixo está a lista de `pfOptions` bandeiras usadas na matriz:

|Opção|Valor|Significado|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|O plug-in de controle de origem deve detectar o tipo de arquivo.|
|SCC_FILETYPE_TEXT|0x01|Indica um arquivo de texto ASCII.|
|SCC_FILETYPE_BINARY|0x02|Indica um tipo de arquivo diferente do texto ASCII.|
|SCC_ADD_STORELATEST|0x04|Armazena apenas a última cópia do arquivo, sem deltas.|
|SCC_FILETYPE_TEXT_ANSI|0x08|Trata o arquivo como texto ANSI.|
|SCC_FILETYPE_UTF8|0x10|Trata o arquivo como texto Unicode no formato UTF8.|
|SCC_FILETYPE_UTF16LE|0x20|Trata o arquivo como texto Unicode no formato UTF16 Little Endian.|
|SCC_FILETYPE_UTF16BE|0x40|Trata o arquivo como texto Unicode no formato UTF16 Big Endian.|

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
