---
title: Função SccHistory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734afefd97e61867076d487acbcf67f10f54e672
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700660"
---
# <a name="scchistory-function"></a>Função SccHistory
Esta função exibe o histórico dos arquivos especificados.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>parâmetros
 `pvContext`

[em] A estrutura de contexto plug-in de controle de origem.

 `hWnd`

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 `nFiles`

[em] Número de arquivos especificados na `lpFileName` matriz.

 `lpFileName`

[em] Matriz de nomes de arquivos totalmente qualificados.

 `fOptions`

[em] Bandeiras de comando (atualmente não utilizadas).

 `pvOptions`

[em] Opções específicas de plug-in de controle de origem.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O histórico da versão foi obtido com sucesso.|
|SCC_I_RELOADFILE|O sistema de controle de origem realmente modificou o arquivo em disco enquanto buscava o histórico (por exemplo, obtendo uma versão antiga dele), então o IDE deve recarregar esse arquivo.|
|SCC_E_FILENOTCONTROLLED|O arquivo não está sob controle de origem.|
|SCC_E_OPNOTSUPPORTED|O sistema de controle de origem não suporta esta operação.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_PROJNOTOPEN|O projeto não foi aberto.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica. O histórico do arquivo não pôde ser obtido.|

## <a name="remarks"></a>Comentários
 O plug-in de controle de origem pode exibir sua própria `hWnd` caixa de diálogo para mostrar o histórico de cada arquivo, usando como janela pai. Alternativamente, a função de retorno de chamada de saída de texto opcional fornecida ao [SccOpenProject](../extensibility/sccopenproject-function.md) pode ser usada, se for suportada.

 Observe que, em certas circunstâncias, o arquivo examinado pode mudar durante a execução desta chamada. Por exemplo, [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] o comando histórico dá ao usuário a chance de obter uma versão antiga do arquivo. Nesse caso, o plug-in de `SCC_I_RELOAD` controle de origem retorna para avisar o IDE de que ele precisa recarregar o arquivo.

> [!NOTE]
> Se o plug-in de controle de origem não suportar essa função para uma matriz de arquivos, apenas o histórico do arquivo do primeiro arquivo pode ser exibido.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
