---
title: Função SccDirDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701009"
---
# <a name="sccdirdiff-function"></a>Função SccDirDiff
Esta função exibe as diferenças entre o diretório local atual no disco cliente e o projeto correspondente sob controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>parâmetros
 pContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 lpDirName

[em] Caminho totalmente qualificado para o diretório local para o qual mostrar uma diferença visual.

 dwFlags

[em] Bandeiras de comando (ver seção Observações).

 pvOpções

[em] Opções específicas de plug-in de controle de origem.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O diretório em disco é o mesmo do projeto no controle de código fonte.|
|SCC_I_FILESDIFFER|O diretório em disco é diferente do projeto no controle de código fonte.|
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|
|SCC_E_FILENOTCONTROLLED|O diretório não está sob controle de código fonte.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha inespecífica.|
|SCC_E_FILENOTEXIST|O diretório local não foi encontrado.|

## <a name="remarks"></a>Comentários
 Esta função é usada para instruir o plug-in de controle de origem a exibir ao usuário uma lista de alterações em um diretório especificado. O plug-in abre sua própria janela, em um formato de sua escolha, para exibir as diferenças entre o diretório do usuário no disco e o projeto correspondente sob controle de versão.

 Se um plug-in suportar a comparação de diretórios, ele deve suportar a comparação de diretórios em uma base de nome de arquivo, mesmo que as opções "quick-diff" não sejam suportadas.

|`dwFlags`|Interpretação|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|Comparação insensível a casos (pode ser usada para difusão rápida ou visual).|
|SCC_DIFF_IGNORESPACE|Ignora o espaço em branco (pode ser usado para difusão rápida ou visual).|
|SCC_DIFF_QD_CONTENTS|Se suportado pelo plug-in de controle de origem, compara silenciosamente o diretório, byte byte.|
|SCC_DIFF_QD_CHECKSUM|Se suportado por plug-in, compara silenciosamente o diretório através de um checkum, ou, se não for suportado, volta para SCC_DIFF_QD_CONTENTS.|
|SCC_DIFF_QD_TIME|Se suportado por plug-in, compara silenciosamente o diretório através de seu carimbo de data e hora, ou, se não for suportado, recua sobre SCC_DIFF_QD_CHECKSUM ou SCC_DIFF_QD_CONTENTS.|

> [!NOTE]
> Esta função usa os mesmos sinalizadores de comando do [SccDiff](../extensibility/sccdiff-function.md). No entanto, um plug-in de controle de origem pode optar por não suportar a operação "quick-diff" para diretórios.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
