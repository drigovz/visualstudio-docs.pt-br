---
title: LPTEXTOUTPROC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- LPTEXTOUTPROC
helpviewer_keywords:
- SccMsgDataOnMessage structure
- SccMsgDataOnBeforeGetFile structure
- SccMsgDataIsCancelled structure
- LPTEXTOUTPROC callback function
- SccMsgDataOnAfterGetFile structure
ms.assetid: 2025c969-e3c7-4cf4-a5c5-099d342895ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38c3e8263b9a30058c2de019e5e92160b716aa71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702796"
---
# <a name="lptextoutproc"></a>LPTEXTOUTPROC

Quando o usuário executa uma operação de controle de origem de dentro do ambiente de desenvolvimento integrado (IDE), o plug-in de controle de origem pode querer transmitir mensagens de erro ou status relacionadas à operação. O plug-in pode exibir suas próprias caixas de mensagens para este fim. No entanto, para uma integração mais perfeita, o plug-in pode passar strings para o IDE, que as exibe em sua maneira nativa de exibir informações de status. O mecanismo para `LPTEXTOUTPROC` isso é o ponteiro da função. O IDE implementa essa função (descrita com mais detalhes abaixo) para exibir erro e status.

O IDE passa para o plug-in de controle de `lpTextOutProc` origem um ponteiro de função para esta função, como parâmetro, ao chamar o [SccOpenProject](../extensibility/sccopenproject-function.md). Durante uma operação scc, por exemplo, no meio de uma chamada para o [SccGet](../extensibility/sccget-function.md) envolvendo muitos arquivos, o plug-in pode chamar a `LPTEXTOUTPROC` função, passando periodicamente strings para exibir. O IDE pode exibir essas strings em uma barra de status, em uma janela de saída ou em uma caixa de mensagem separada, conforme apropriado. Opcionalmente, o IDE pode ser capaz de exibir certas mensagens com um botão **Cancelar.** Isso permite que o usuário cancele a operação, e dá ao IDE a capacidade de repassar essas informações para o plug-in.

## <a name="signature"></a>Assinatura
 A função de saída do IDE tem a seguinte assinatura:

```cpp
typedef LONG (*LPTEXTOUTPROC) (
   LPSTR display_string,
   LONG mesg_type
);
```

## <a name="parameters"></a>parâmetros

display_string

Uma seqüência de texto para exibir. Esta corda não deve ser encerrada com um retorno de carruagem ou uma alimentação de linha.

mesg_type

O tipo de mensagem. A tabela a seguir lista os valores suportados para este parâmetro.

|Valor|Descrição|
|-----------|-----------------|
|`SCC_MSG_INFO, SCC_MSG_WARNING, SCC_MSG_ERROR`|A mensagem é considerada Informação, Aviso ou Erro.|
|`SCC_MSG_STATUS`|A mensagem mostra o status e pode ser exibida na barra de status.|
|`SCC_MSG_DOCANCEL`|Enviado sem seqüência de mensagens.|
|`SCC_MSG_STARTCANCEL`|Começa a exibir um botão **Cancelar.**|
|`SCC_MSG_STOPCANCEL`|Pára de exibir um botão **Cancelar.**|
|`SCC_MSG_BACKGROUND_IS_CANCELLED`|Pergunta ao IDE se a operação de fundo `SCC_MSG_RTN_CANCEL` deve ser cancelada: o IDE retorna se a operação foi cancelada; caso contrário, `SCC_MSG_RTN_OK`retorna. O `display_string` parâmetro é lançado como uma estrutura [SccMsgDataIsCancelled,](#LinkSccMsgDataIsCancelled) que é fornecida pelo plug-in de controle de origem.|
|`SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE`|Informa o IDE sobre um arquivo antes de ser recuperado do controle de versão. O `display_string` parâmetro é lançado como uma estrutura [SccMsgDataOnBeforeGetFile,](#LinkSccMsgDataOnBeforeGetFile) que é fornecida pelo plug-in de controle de origem.|
|`SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE`|Informa o IDE sobre um arquivo depois de ter sido recuperado do controle de versão. O `display_string` parâmetro é lançado como uma estrutura [SccMsgDataOnAfterGetFile,](#LinkSccMsgDataOnAfterGetFile) que é fornecida pelo plug-in de controle de origem.|
|`SCC_MSG_BACKGROUND_ON_MESSAGE`|Informa o IDE do status atual de uma operação de fundo. O `display_string` parâmetro é lançado como uma estrutura [SccMsgDataOnMessage,](#LinkSccMsgDataOnMessage) que é fornecida pelo plug-in de controle de origem.|

## <a name="return-value"></a>Valor retornado

|Valor|Descrição|
|-----------|-----------------|
|SCC_MSG_RTN_OK|A seqüência foi exibida ou a operação foi concluída com sucesso.|
|SCC_MSG_RTN_CANCEL|O usuário quer cancelar a operação.|

## <a name="example"></a>Exemplo
 Suponha que o IDE chame o [SccGet](../extensibility/sccget-function.md) com vinte nomes de arquivo. O plug-in de controle de origem quer evitar o cancelamento da operação no meio de um arquivo get. Depois de obter cada `lpTextOutProc`arquivo, ele liga , passando-lhe `SCC_MSG_DOCANCEL` as informações de status em cada arquivo, e envia uma mensagem se ele não tem status para relatar. Se a qualquer momento o plug-in `SCC_MSG_RTN_CANCEL` receber um valor de retorno do IDE, ele cancela a operação get imediatamente, para que não sejam recuperados mais arquivos.

## <a name="structures"></a>Estruturas

### <a name="sccmsgdataiscancelled"></a><a name="LinkSccMsgDataIsCancelled"></a>SccMsgDataIsCancelado

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
} SccMsgDataIsCancelled;
```

 Esta estrutura é `SCC_MSG_BACKGROUND_IS_CANCELLED` enviada com a mensagem. É usado para comunicar a id da operação de fundo que foi cancelada.

### <a name="sccmsgdataonbeforegetfile"></a><a name="LinkSccMsgDataOnBeforeGetFile"></a>SccMsgDataOnBeforeGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
} SccMsgDataOnBeforeGetFile;
```

 Esta estrutura é `SCC_MSG_BACKGROUND_ON_BEFORE_GET_FILE` enviada com a mensagem. Ele é usado para comunicar o nome do arquivo prestes a ser recuperado e o ID da operação de fundo que está fazendo a recuperação.

### <a name="sccmsgdataonaftergetfile"></a><a name="LinkSccMsgDataOnAfterGetFile"></a>SccMsgDataOnAfterGetFile

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szFile;
   SCCRTN sResult;
} SccMsgDataOnAfterGetFile;
```

 Esta estrutura é `SCC_MSG_BACKGROUND_ON_AFTER_GET_FILE` enviada com a mensagem. Ele é usado para comunicar o resultado da recuperação do arquivo especificado, bem como o ID da operação de fundo que fez a recuperação. Consulte os valores de devolução para o [SccGet](../extensibility/sccget-function.md) para o que pode ser dado como resultado.

### <a name="sccmsgdataonmessage"></a><a name="LinkSccMsgDataOnMessage"></a>SccMsgDataOnMessage

```cpp
typedef struct {
   DWORD dwBackgroundOperationID;
   PCSTR szMessage;
   BOOL bIsError;
} SccMsgDataOnMessage;
```

 Esta estrutura é `SCC_MSG_BACKGROUND_ON_MESSAGE` enviada com a mensagem. É usado para comunicar o status atual de uma operação de fundo. O status é expresso como uma string a `bIsError` ser exibida pelo IDE`TRUE` e indica a gravidade da mensagem (para uma mensagem de erro; `FALSE` para um aviso ou para uma mensagem informativa). O ID da operação de fundo que envia o status também é dado.

## <a name="code-example"></a>Exemplo de código
 Aqui está um breve `LPTEXTOUTPROC` exemplo `SCC_MSG_BACKGROUND_ON_MESSAGE` de chamada para enviar a mensagem, mostrando como lançar a estrutura para a chamada.

```cpp
LONG SendStatusMessage(
    LPTEXTOUTPROC pTextOutProc,
    DWORD         dwBackgroundID,
    LPCTSTR       pStatusMsg,
    BOOL          bIsError)
{
    SccMsgDataOnMessage msgData = { 0 };
    LONG                result  = 0;

    msgData.dwBackgroundOperationID = dwBackgroundID;
    msgData.szMessage               = pStatusMsg;
    msgData.bIsError                = bIsError;

    result = pTextOutProc(reinterpret_cast<LPCTSTR>(&msgData), SCC_MSG_BACKGROUND_ON_MESSAGE);
    return result;
}
```

## <a name="see-also"></a>Confira também
- [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
