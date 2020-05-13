---
title: Função SccGetCommandOptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeefa26422476ca40e782df3ff35eee9d429a149
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700827"
---
# <a name="sccgetcommandoptions-function"></a>Função SccGetCommandOptions
Esta função solicita ao usuário opções avançadas para um determinado comando.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 Icommand

[em] O comando para o qual são solicitadas opções avançadas (consulte [código de comando](../extensibility/command-code-enumerator.md) para possíveis valores).

 ppvOptions

[em] A estrutura de opções (também pode ser `NULL`).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Sucesso.|
|SCC_I_ADV_SUPPORT|O plug-in de controle de origem suporta opções avançadas para o comando.|
|SCC_I_OPERATIONCANCELED|O usuário cancelou a caixa de diálogo **Opções** do plug-in de controle de origem.|
|SCC_E_OPTNOTSUPPORTED|O plug-in de controle de origem não suporta esta operação.|
|SCC_E_ISCHECKEDOUT|Não é possível executar esta operação em um arquivo que está atualmente verificado.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 O IDE chama essa função `ppvOptions` = `NULL` pela primeira vez para determinar se o plug-in de controle de origem suporta o recurso de opções avançadas para o comando especificado. Se o plug-in suportar o recurso para esse comando, o IDE chamará essa função novamente quando o usuário solicitar opções avançadas (geralmente `NULL` implementadas como um botão **Avançado** em uma caixa de diálogo) e fornece um ponteiro não-NULL para `ppvOptions` que aponta para um ponteiro. O plug-in armazena todas as opções avançadas especificadas pelo usuário `ppvOptions`em uma estrutura privada e retorna um ponteiro para essa estrutura em . Essa estrutura é então passada para todas as outras funções de API plug-in de controle de fonte que precisam saber sobre ela, incluindo chamadas subseqüentes para a `SccGetCommandOptions` função.

 Um exemplo pode ajudar a esclarecer essa situação.

 Um usuário escolhe o comando **Obter** e o IDE exibe uma caixa de diálogo **Obter.** O IDE `SccGetCommandOptions` chama `iCommand` a `SCC_COMMAND_GET` função `ppvOptions` com `NULL`set para e definido para . Isso é interpretado pelo plug-in de controle de origem como a pergunta: "Você tem alguma opção avançada para este comando?" Se o plug-in retornar, `SCC_I_ADV_SUPPORT`o IDE exibirá um botão **Avançado** na caixa de diálogo **Obter.**

 Na primeira vez que o usuário clica no `SccGetCommandOptions` botão **Avançado,** o IDE novamente `NULL` chama a função, desta vez com um não-que`NULL``ppvOptions` aponta para um ponteiro. O plug-in exibe sua própria caixa de diálogo **Get Options,** solicita informações ao usuário, coloca essas `ppvOptions`informações em sua própria estrutura e retorna um ponteiro para essa estrutura em .

 Se o usuário clicar em **Avançado** novamente na mesma `SccGetCommandOptions` caixa de `ppvOptions`diálogo, o IDE chamará a função novamente sem alterar, para que a estrutura seja transmitida de volta para o plug-in. Isso permite que o plug-in reinicialize sua caixa de diálogo para os valores que o usuário havia definido anteriormente. O plug-in modifica a estrutura no lugar antes de retornar.

 Finalmente, quando o usuário clica em **OK** na caixa de diálogo **Obter** do IDE, o `ppvOptions` IDE chama o [SccGet](../extensibility/sccget-function.md), passando a estrutura retornada que contém as opções avançadas.

> [!NOTE]
> O `SCC_COMMAND_OPTIONS` comando é usado quando o IDE exibe uma caixa de diálogo **Opções** que permite ao usuário definir preferências que controlam como a integração funciona. Se o plug-in de controle de origem quiser fornecer sua própria caixa de diálogo de preferências, ele poderá exibi-lo a partir de um botão **Avançado** na caixa de diálogo preferências do IDE. O plug-in é o único responsável por obter e persistir essas informações; o IDE não o usa ou o modifica.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [Código de comando](../extensibility/command-code-enumerator.md)
