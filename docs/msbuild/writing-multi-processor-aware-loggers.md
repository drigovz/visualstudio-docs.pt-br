---
title: Escrevendo agentes com reconhecimento de multiprocessador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 886e012b026ef17b512a7e134d080382744783ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630741"
---
# <a name="write-multi-processor-aware-loggers"></a>Escrever agentes com reconhecimento de multiprocessador

A capacidade do MSBuild de tirar proveito de vários processadores pode diminuir o tempo de construção do projeto, mas também adiciona complexidade para construir registro de eventos. Em um ambiente de processador único, eventos, erros, avisos e mensagens chegam ao agente de uma maneira previsível e sequencial. No entanto, em um ambiente com vários processadores, eventos de origens diferentes podem chegar ao mesmo tempo ou fora de sequência. Para fornecer isso, o MSBuild fornece um logger com reconhecimento de vários processadores e um novo modelo de registro e permite que você crie "loggers de encaminhamento" personalizados.

## <a name="multi-processor-logging-challenges"></a>Desafios de registro em log de multiprocessador

 Quando você constrói um ou mais projetos em um sistema multiprocessador ou multinúcleo, os eventos de compilação do MSBuild para todos os projetos são gerados ao mesmo tempo. Uma avalanche de mensagens de eventos pode chegar ao agente ao mesmo tempo ou fora de sequência. Como um logger Do MSBuild 2.0 não foi projetado para lidar com essa situação, ele pode sobrecarregar o logger e causar tempos de compilação aumentados, saída de logger incorreta ou até mesmo uma compilação quebrada. Para resolver esses problemas, o logger (a partir do MSBuild 3.5) pode processar eventos fora de seqüência e correlacionar eventos e suas fontes.

 Você pode melhorar a eficiência de registro em log ainda mais criando um agente personalizado de encaminhamento. Um agente personalizado de encaminhamento atua como um filtro, permitindo que você escolha, antes de criar, somente os eventos que você deseja monitorar. Quando você usa um agente personalizado de encaminhamento, eventos indesejados não podem sobrecarregar o agente, truncar os logs ou reduzir os tempos de build.

## <a name="multi-processor-logging-models"></a>Modelos de registro em log de multiprocessador

 Para fornecer problemas de compilação relacionados a vários processadores, o MSBuild oferece suporte a dois modelos de registro, central e distribuído.

### <a name="central-logging-model"></a>Modelo de log central

 No modelo de registro em log central, uma única instância de *MSBuild.exe* age como o "nó central" e as instâncias filho do nó central ("nós secundários") são anexadas ao nó central para ajudar na execução de tarefas de build.

 ![Modelo de Madeireiro Central](../msbuild/media/centralnode.png "CentralNode")

 Agentes de vários tipos anexados ao nó central são conhecidos como "agentes centrais". Apenas uma instância de cada tipo de agente pode ser anexada ao nó central ao mesmo tempo.

 Quando ocorre um build, os nós secundários encaminham os eventos de build para o nó central. O nó central encaminha todos os seus eventos e também os de nós secundários, para um ou mais dos agentes centrais anexados. Os agentes, em seguida, criam arquivos de log que são baseados nos dados de entrada.

 Embora é necessário implementar somente o <xref:Microsoft.Build.Framework.ILogger> pelo agente central, é recomendável que você implemente também <xref:Microsoft.Build.Framework.INodeLogger> para que o agente central inicialize com o número de nós que participam do build. A sobrecarga do método <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> a seguir invoca quando o mecanismo inicializa o agente.

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

 Qualquer agente pré-existente com base em <xref:Microsoft.Build.Framework.ILogger> pode atuar como agente central e pode ser anexado ao build. No entanto, agentes centrais escritos sem suporte explícito para cenários de registro em log de multiprocessador e eventos fora de ordem podem quebrar um build ou produzir saída sem sentido.

### <a name="distributed-logging-model"></a>Modelo de log distribuído

 No modelo de registro em log central, muito tráfego de mensagens de entrada pode sobrecarregar o nó central, por exemplo, ao criar vários projetos ao mesmo tempo. Isso pode enfatizar os recursos do sistema e diminuir o desempenho do build. Para aliviar esse problema, o MSBuild suporta um modelo de registro distribuído.

 ![Modelo de registro distribuído](../msbuild/media/distnode.png "DistNode")

 O modelo de registro em log distribuído estende o modelo de registro em log central, permitindo que você crie um agente de encaminhamento.

#### <a name="forwarding-loggers"></a>Agentes de encaminhamento

 Um agente de encaminhamento é um agente secundário leve que tem um filtro de evento que anexa um nó secundário e recebe eventos de build de entrada desse nó. Ele filtra os eventos de entrada e encaminha apenas os que você especifica para o nó central. Isso reduz o tráfego de mensagem que é enviado para o nó central e melhora o desempenho geral do build.

 Há duas maneiras de usar o registro em log distribuído:

- Personalize o agente de encaminhamento pré-fabricado denominado <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>.

- Escrever seu próprio agente de encaminhamento personalizado.

Você pode modificar o ConfigurableForwardingLogger para atender às suas necessidades. Para fazer isso, chame o agente na linha de comando usando *MSBuild.exe* e liste os eventos de build que você deseja que o agente encaminhe para o nó central.

Como alternativa, você pode criar um agente de encaminhamento personalizado. Ao criar um agente de encaminhamento personalizado, você pode ajustar o comportamento do agente. No entanto, criar um agente de encaminhamento personalizado é mais complexo do que apenas personalizar o ConfigurableForwardingLogger. Para saber mais, confira [Criando agentes de encaminhamento](../msbuild/creating-forwarding-loggers.md).

## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Como usar o ConfigurableForwardingLogger para registro em log distribuído simples

 Para anexar um ConfigurableForwardingLogger ou um agente de encaminhamento personalizado, use a opção `-distributedlogger` (`-dl` para a forma abreviada) em um build de linha de comando *MSBuild.exe*. O formato para especificar os nomes dos tipos de agente e classes é o mesmo que para a opção `-logger`, exceto em casos em que um agente distribuído tenha sempre duas classes de registro em log em vez de uma, o agente de encaminhamento e o agente central. Este é um exemplo de como anexar um agente de encaminhamento personalizado chamado XMLForwardingLogger.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral
```

> [!NOTE]
> Um asterisco (*) deve separar os dois nomes de agentes na opção `-dl`.

 Usar o ConfigurávelForwardingLogger é como usar qualquer outro logger (como descrito na [Obtenção de logs de compilação),](../msbuild/obtaining-build-logs-with-msbuild.md)exceto que você anexa o logger ConfigurávelForwardingLogger em vez do logger típico do MSBuild e especifica como parâmetros os eventos que deseja que o ConfigurávelForwardingLogger passe para o nó central.

 Por exemplo, se você quiser ser notificado somente quando um build começar e terminar, e quando ocorrer um erro, você terá que passar `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT` e `ERROREVENT` como parâmetros. Vários parâmetros podem ser passados, separando-os com ponto e vírgula. A seguir está um exemplo de como usar o ConfigurableForwardingLogger para encaminhar apenas os eventos `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT` e `ERROREVENT`.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT
```

 A seguir está uma lista dos parâmetros do ConfigurableForwardingLogger disponíveis.

|Parâmetros do ConfigurableForwardingLogger|
| - |
|BUILDSTARTEDEVENT|
|BUILDFINISHEDEVENT|
|PROJECTSTARTEDEVENT|
|PROJECTFINISHEDEVENT|
|TARGETSTARTEDEVENT|
|TARGETFINISHEDEVENT|
|TASKSTARTEDEVENT|
|TASKFINISHEDEVENT|
|ERROREVENT|
|WARNINGEVENT|
|HIGHMESSAGEEVENT|
|NORMALMESSAGEEVENT|
|LOWMESSAGEEVENT|
|CUSTOMEVENT|
|COMMANDLINE|
|PERFORMANCESUMMARY|
|NOSUMMARY|
|SHOWCOMMANDLINE|

## <a name="see-also"></a>Confira também

- [Como criar agentes de encaminhamento](../msbuild/creating-forwarding-loggers.md)