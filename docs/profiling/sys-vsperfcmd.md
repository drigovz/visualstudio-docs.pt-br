---
title: Sys (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 435393ac536eb70f2f3f6d38b16eaab645848704
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778174"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
A opção *VSPerfCmd.exe* **Sys** define o evento de criação de perfil que é amostrado para eventos de chamada do sistema (chamadas de função do aplicativo perfilado para o sistema operacional) e altera opcionalmente o número de chamadas do sistema em um intervalo de amostragem a partir do padrão de 10.

 **Sys** só pode ser usada em uma linha de comando que também contém a opção de **Inicialização** ou **Anexar**.

 Por padrão, o evento de amostragem do criador de perfil é definido como ciclos de relógio do processador e o intervalo de amostragem é definido como 10.000.000. As opções **Temporizador**, **PF**, **Sys** e **Contador** permitem que você defina o intervalo de amostragem e o evento de amostragem. A opção **GC** coleta dados da memória do .NET em cada alocação e evento de coleta de lixo. Apenas uma dessas opções pode ser especificada em uma linha de comando.

 O evento de amostragem e o intervalo de amostragem só podem ser definidos na primeira linha de comando que contém uma opção **Inicialização** ou **Anexar**.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>parâmetros
 `Events` Um valor inteiro que especifica o número de eventos de falha do sistema em um intervalo de amostragem. Caso `Events` não seja especificado, o intervalo é definido como 10.

## <a name="required-options"></a>Opções obrigatórias
 **Sys** requer uma das opções a seguir.

 **Inicialização:** `AppName` Inicia o profiler e `AppName`o aplicativo especificado por .

 **Anexa:** `PID` Anexa o profiler ao processo `PID`especificado por .

## <a name="invalid-options"></a>Opções inválidas
 As opções a seguir não podem ser especificadas na mesma linha de comando de **Sys**.

 **PF****[ :**`Events`] Define o evento de amostragem como `Events`falhas de página e define opcionalmente o intervalo de amostragem para . O intervalo de PF padrão é 10.

 **Temporizador**[**:**`Cycles`] Define o evento de amostragem `Cycles`para ciclos de relógio do processador e define opcionalmente o intervalo de amostragem para . O intervalo do temporizador padrão é 10.000.000.

 **Contador:** `Name``,Reload`[`,FriendlyName`] Define o evento de amostragem `Name` para o contador `Reload`de desempenho da CPU especificado e define o intervalo de amostragem para .

 **GC**[**:**{**Alocação**&#124;**Tempo de vida**}] coleta dados de memória do .NET. Por padrão **(Alocação),** os dados são coletados em todos os eventos de alocação de memória. Quando o parâmetro **Tempo de Vida** é especificado, os dados também são coletados em todos os eventos de coleta de lixo.

## <a name="example"></a>Exemplo
 Este exemplo demonstra como configurar o criador de perfil do evento de amostragem para chamadas do sistema e como definir o intervalo de amostragem de 20 chamadas por amostra.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Confira também
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
