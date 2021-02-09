---
title: Criando agentes de log de encaminhamento | Microsoft Docs
description: Crie agentes de encaminhamento do MSBuild para melhorar a eficiência do log, permitindo que você escolha os eventos que deseja monitorar ao compilar projetos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ffe175d9ea73640cae1197fe91656d3565525f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901362"
---
# <a name="create-forwarding-loggers"></a>Criar agentes de encaminhamento

Agentes de encaminhamento melhoram a eficiência de log, permitindo que você escolha os eventos que deseja monitorar ao compilar projetos em um sistema com vários processadores. Ao habilitar agentes de encaminhamento, você pode impedir que eventos indesejados sobrecarreguem o agente central, diminuindo o tempo de build e desorganizando o log.

 Para criar um agente de encaminhamento, você pode implementar a interface <xref:Microsoft.Build.Framework.IForwardingLogger> e, em seguida, implementar seus métodos manualmente ou usar a classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> e seus métodos pré-configurados. (O último será suficiente para a maioria dos aplicativos.)

## <a name="register-events-and-respond-to-them"></a>Registrar eventos e responder a eles

 Um agente de encaminhamento reúne informações sobre eventos de build à medida que são relatados pelo mecanismo de build secundária, que é um processo de trabalho criado pelo processo de build principal durante um build em um sistema com vários processadores. Em seguida, o agente de encaminhamento seleciona eventos para encaminhar para o agente central, com base nas instruções que você atribuiu a ele.

 Você deve registrar os agentes de encaminhamento para manipular os eventos que deseja monitorar. Para registrar-se para eventos, os agentes devem substituir o método <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>. Este método agora inclui um parâmetro opcional, `nodecount`, que pode ser definido como o número de processadores no sistema. (Por padrão, o valor é 1.)

 Alguns exemplos de eventos que você pode monitorar são <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> e <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

 Em um ambiente com vários processadores, mensagens de evento, provavelmente, serão recebidas fora de ordem. Portanto, você deve avaliar os eventos usando o manipulador de eventos no agente de encaminhamento e programá-lo para determinar quais eventos passar para o redirecionador para serem encaminhados para o agente central. Para fazer isso, você pode usar a classe <xref:Microsoft.Build.Framework.BuildEventContext>, que está anexada a cada mensagem, para ajudar a identificar eventos que deseja encaminhar e, em seguida, transmitir os nomes de eventos para a classe <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> (ou uma subclasse dela). Quando você usa esse método, nenhuma outra codificação específica é necessária para encaminhar eventos.

## <a name="specify-a-forwarding-logger"></a>Especificar um agente de encaminhamento

 Depois que o agente de log de encaminhamento tiver sido compilado em um assembly, você deverá dizer ao MSBuild para usá-lo durante as compilações. Para fazer isso, use as `-FileLogger` `-FileLoggerParameters` Opções, e `-DistributedFileLogger` junto com *MSBuild.exe*. A `-FileLogger` opção informa *MSBuild.exe* que o agente de log está diretamente anexado. A opção `-DistributedFileLogger` significa que há um arquivo de log por nó. Para definir parâmetros no agente de encaminhamento, use a opção `-FileLoggerParameters`. Para obter mais informações sobre essas e outras opções de *MSBuild.exe* , consulte [referência de linha de comando](../msbuild/msbuild-command-line-reference.md).

## <a name="multi-processor-aware-loggers"></a>Agentes com reconhecimento de multiprocessador

 Quando você cria um projeto em um sistema com vários processadores, as mensagens de build de cada processador não são intercaladas automaticamente em uma sequência unificada. Em vez disso, você deve estabelecer uma prioridade de agrupamento de mensagens usando a classe <xref:Microsoft.Build.Framework.BuildEventContext> que está anexada a cada mensagem. Para obter mais informações sobre o build de multiprocessador, confira [Registrando em log em um ambiente multiprocessador](../msbuild/logging-in-a-multi-processor-environment.md).

## <a name="see-also"></a>Confira também

- [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Agentes de build](../msbuild/build-loggers.md)
- [Registrando em log em um ambiente multiprocessador](../msbuild/logging-in-a-multi-processor-environment.md)