---
title: Função SccSetOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1adcbb47e9fce7037fe8942326e8836ade51e3eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700304"
---
# <a name="sccsetoption-function"></a>Função SccSetOption
Esta função define opções que controlam o comportamento do plug-in de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 nOpção

[em] A opção que está sendo definida.

 dwVal

[em] Configurações para a opção.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A opção foi definida com sucesso.|
|SCC_I_SHARESUBPROJOK|Retornado `nOption` se `SCC_OPT_SHARESUBPROJ` fosse e o plug-in de controle de origem permite que o IDE defina a pasta de destino.|
|SCC_E_OPNOTSUPPORTED|A opção não foi definida e não deve ser confiada.|

## <a name="remarks"></a>Comentários
 O IDE chama essa função para controlar o comportamento do plug-in de controle de origem. O primeiro parâmetro, `nOption`indica o valor que está sendo `dwVal`definido, enquanto o segundo, indica o que fazer com esse valor. O plug-in armazena essas `pvContext``,` informações associadas a um modo que o IDE deve chamar essa função depois de chamar o [SccInitialize](../extensibility/sccinitialize-function.md) (mas não necessariamente após cada chamada para o [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Resumo das opções e seus valores:

|`nOption`|`dwValue`|Descrição|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Habilita/desativa a fila de eventos em segundo plano.|
|`SCC_OPT_USERDATA`|Valor arbitrário|Especifica um valor de usuário a ser passado para a função de retorno de chamada [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md)|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indica se o IDE atualmente suporta o cancelamento de uma operação.|
|`SCC_OPT_NAMECHANGEPFN`|Ponteiro para a função de retorno de chamada [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Define um ponteiro para uma função de retorno de chamada de mudança de nome.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indica se o IDE permite a verificação manual de seus arquivos (através da interface do usuário de controle de origem) ou se eles devem ser verificados apenas através do plug-in de controle de origem.|
|`SCC_OPT_SHARESUBPROJ`|N/D|Se o plug-in de controle de origem permitir que o IDE especifique a pasta de projeto local, o plug-in retorna `SCC_I_SHARESUBPROJOK`.|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Se `nOption` `SCC_OPT_EVENTQUEUE`for, o IDE está desabilitando (ou reativando) o processamento de fundo. Por exemplo, durante uma compilação, o IDE pode instruir o plug-in de controle de origem a interromper o processamento on-ocioso de qualquer tipo. Após a compilação, ele reativaria o processamento em segundo plano para manter a fila de eventos do plug-in atualizada. Correspondente ao `SCC_OPT_EVENTQUEUE` valor `nOption`de , há `dwVal`dois valores possíveis para , ou seja, `SCC_OPT_EQ_ENABLE` e `SCC_OPT_EQ_DISABLE`.

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Se o `nOption` valor `SCC_OPT_HASCANCELMODE`for, o IDE permite que os usuários cancelem operações longas. A `dwVal` `SCC_OPT_HCM_NO` configuração para (o padrão) indica que o IDE não tem modo de cancelamento. O plug-in de controle de origem deve oferecer seu próprio botão Cancelar se quiser que o usuário possa cancelar. `SCC_OPT_HCM_YES`indica que o IDE fornece a capacidade de cancelar uma operação, de modo que o plug-in SCC não precisa exibir seu próprio botão Cancelar. Se `dwVal` o IDE `SCC_OPT_HCM_YES`for configurado para `SCC_MSG_STATUS` `DOCANCEL` , ele está `lpTextOutProc` preparado para responder e mensagens enviadas para a função de retorno de chamada (ver [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Se o IDE não definir essa variável, o plug-in não deve enviar essas duas mensagens.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Se nOption estiver `SCC_OPT_NAMECHANGEPFN`definido para , e tanto o plug-in de controle de origem quanto o IDE permitirem, o plug-in pode realmente renomear ou mover um arquivo durante uma operação de controle de origem. O `dwVal` será definido como um ponteiro de função do tipo [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Durante uma operação de controle de origem, o plug-in pode chamar essa função, passando em três parâmetros. Estes são o nome antigo (com caminho totalmente qualificado) de um arquivo, o novo nome (com caminho totalmente qualificado) desse arquivo e um ponteiro para informações que têm relevância para o IDE. O IDE envia este último `SccSetOption` `nOption` ponteiro `SCC_OPT_USERDATA`ligando `dwVal` com set para , apontando para os dados. O suporte para esta função é opcional. Um plug-VSSCI que usa essa habilidade deve inicializar seu `NULL`ponteiro de função e variáveis de dados do usuário para , e não deve chamar uma função de renome, a menos que tenha sido dada uma. Deve também estar preparado para manter o valor que foi dado `SccSetOption`ou para alterá-lo em resposta a uma nova chamada para . Isso não acontecerá no meio de uma operação de comando de controle de fonte, mas pode acontecer entre comandos.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Se nOption estiver `SCC_OPT_SCCCHECKOUTONLY`definido para , o IDE está indicando que os arquivos no projeto atualmente aberto nunca devem ser verificados manualmente através da interface de usuário do sistema de controle de origem. Em vez disso, os arquivos devem ser verificados apenas através do plug-in de controle de origem sob controle IDE. Se `dwValue` estiver `SCC_OPT_SCO_NO`definido para , significa que os arquivos devem ser tratados normalmente pelo plug-in e podem ser verificados através da ui de controle de origem. Se `dwValue` estiver `SCC_OPT_SCO_YES`definido como , então apenas o plug-in é permitido verificar arquivos, e a iu do sistema de controle de origem não deve ser invocada. Isto é para situações em que o IDE pode ter "pseudo-arquivos" que fazem sentido verificar apenas através do IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Se`nOption` estiver `SCC_OPT_SHARESUBPROJ`definido para , o IDE está testando se o plug-in de controle de origem pode usar uma pasta local especificada ao adicionar arquivos do controle de origem. O valor `dwVal` do parâmetro não importa neste caso. Se o plug-in permitir que o IDE especifique a pasta de destino local onde os arquivos serão adicionados `SCC_I_SHARESUBPROJOK` do `SccSetOption` controle de origem quando o [SccAddFromScc](../extensibility/sccaddfromscc-function.md) for chamado, então o plug-in deve retornar quando a função for chamada. Em seguida, o `lplpFileNames` IDE `SccAddFromScc` usa o parâmetro da função para passar na pasta de destino. O plug-in usa essa pasta de destino para colocar os arquivos adicionados do controle de origem. Se o plug-in `SCC_I_SHARESUBPROJOK` não `SCC_OPT_SHARESUBPROJ` retornar quando a opção estiver definida, o IDE assumirá que o plug-in é capaz de adicionar arquivos apenas na pasta local atual.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
