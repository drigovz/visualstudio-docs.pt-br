---
title: Função SccInitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700636"
---
# <a name="sccinitialize-function"></a>Função SccInitialize
Essa função inicializa o plug-in de controle de origem e fornece recursos e limites para o ambiente de desenvolvimento integrado (IDE).

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>parâmetros
 `ppvContext`

[em] O plug-in de controle de origem pode colocar um ponteiro em sua estrutura de contexto aqui.

 `hWnd`

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 `lpCallerName`

[em] O nome do programa chamando o plug-in de controle de origem.

 `lpSccName`

[dentro, fora] O buffer onde o plug-in de controle de `SCC_NAME_LEN`origem coloca seu próprio nome (para não exceder ).

 `lpSccCaps`

[fora] Retorna os sinalizadores de capacidade do plug-in de controle de origem.

 `lpAuxPathLabel`

[dentro, fora] O buffer onde o plug-in de controle `lpAuxProjPath` de origem coloca uma string que descreve o parâmetro retornado pelo `SCC_AUXLABEL_LEN` [SccOpenProject](../extensibility/sccopenproject-function.md) e pelo [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (para não exceder ).

 `pnCheckoutCommentLen`

[fora] Retorna o comprimento máximo permitido para um comentário de checkout.

 `pnCommentLen`

[fora] Retorna o comprimento máximo permitido para outros comentários.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A inicialização do controle de origem foi bem sucedida.|
|SCC_E_INITIALIZEFAILED|O sistema não pôde ser inicializado.|
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar a operação especificada.|
|SCC_E_NONSPECFICERROR|Falha não específica; o sistema de controle de origem não foi inicializado.|

## <a name="remarks"></a>Comentários
 O IDE chama essa função quando ele carrega pela primeira vez o plug-in de controle de origem. Ele permite que o IDE passe certas informações, como o nome do chamador, para o plug-in. O IDE também recebe de volta certas informações, como o comprimento máximo permitido para comentários e as capacidades do plug-in.

 Os `ppvContext` pontos `NULL` apontam para um ponteiro. O plug-in de controle de origem pode alocar uma estrutura `ppvContext`para uso próprio e armazenar um ponteiro para essa estrutura em . O IDE passará este ponteiro para todas as outras funções da API VSSCI, permitindo que o plug-in tenha informações de contexto disponíveis sem recorrer ao armazenamento global e para suportar várias instâncias do plug-in. Esta estrutura deve ser desalocada quando o [SccUninitialize](../extensibility/sccuninitialize-function.md) é chamado.

 Os `lpCallerName` `lpSccName` parâmetros permitem que o IDE e o plug-in de controle de origem troquenomes. Esses nomes podem ser usados simplesmente para distinguir entre várias instâncias, ou podem realmente aparecer em menus ou caixas de diálogo.

 O `lpAuxPathLabel` parâmetro é uma string usada como comentário para identificar o caminho do projeto auxiliar armazenado no arquivo da solução e passado para o plug-in de controle de origem em uma chamada para o [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]usa a string "SourceSafe Project:"; outros plug-ins de controle de origem devem abster-se de usar esta seqüência específica.

 O `lpSccCaps` parâmetro dá ao plug-in de controle de origem um lugar para armazenar bitflags indicando as capacidades do plug-in. (Para obter uma lista completa de bitflags de capacidade, consulte [Sinalizadores de capacidade](../extensibility/capability-flags.md)). Por exemplo, se o plug-in planeja gravar resultados em uma função de retorno de chamada fornecida pelo chamador, o plug-in definirá o bit de capacidade SCC_CAP_TEXTOUT. Isso sinalizaria o IDE para criar uma janela para resultados de controle de versão.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Sinalizadores de capacidade](../extensibility/capability-flags.md)
