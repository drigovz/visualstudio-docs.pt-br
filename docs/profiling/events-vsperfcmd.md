---
title: Eventos (VSPerfCmd) | Microsoft Docs
description: Controle o log do ETW (rastreamento de eventos para Windows) usando a opção eventos na ferramenta de linha de comando VSPerfCmd.exe. Examine os parâmetros de sintaxe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1ec92cae275d9f73f24f983905bc0013950e9d37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899565"
---
# <a name="events-vsperfcmd"></a>Eventos (VSPerfCmd)
A opção *VSPerfCmd.exe* **Events** controla o log do ETW (rastreamento de eventos para Windows). Os dados ETW são salvos em um arquivo .etl separado do arquivo de dados do criador de perfil. Os dados podem ser exibidos em um relatório usando o comando [VSPerfReport](../profiling/vsperfreport.md) /summary:etw.

 A opção **Eventos** pode ser chamada a qualquer momento antes do comando **Shutdown** do VSPerfCmd ser chamado para interromper a criação de perfil.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parâmetros
 **On**&#124;**Off** Inicia ou interrompe a coleta de dados de evento.

 `Guid` O GUID do controle de provedor.

 `ProviderName` O nome do provedor que está registrado no WMI (Instrumentação de Gerenciamento do Windows).

 `Flags` Um valor de sinalizadores hexadecimais prefixados com "0x" que é definido pelo provedor de eventos.

 `Level` Especifica o volume de dados coletado. `Level` é definido pelo provedor de eventos.

 A opção **Eventos** compreende as seguintes palavras-chave kernel como nomes de provedor:

 **Processo** Eventos de processo

 **Thread** Eventos de thread

 **Imagem** Eventos de carregamento e descarregamento de imagens

 **Disco** Eventos de E/S de disco

 **Arquivo** Eventos de E/S de arquivo

 **Falhas graves** Falhas de página graves

 **Falha de página** Falhas de página lógicas

 **Rede** Eventos de rede

 **Registro** Eventos de acesso ao Registro

 Observe que o Kernel Provider só pode ser habilitado. Ele não pode ser desabilitado, nem seus sinalizadores podem ser modificados, até que o monitor seja desligado.

## <a name="remarks"></a>Comentários

> [!NOTE]
> Quando eventos CLR ETW estiverem habilitados, os dados de inicialização adicional também serão coletados no relatório de Exibição de Rastreamento. Para excluir eventos de inicialização daqueles que aparecem no relatório, use o seguinte comando:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Se você não excluir os eventos de inicialização, como tais eventos não são listados no arquivo MOF (Managed Object Format), eles aparecerão como GUIDs no relatório. Para obter mais informações, confira esta página no site da Microsoft: [Arquivo de formato MOF (Managed Object Format) de exemplo](https://msdn.microsoft.com/library/default.aspx).

## <a name="see-also"></a>Confira também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
