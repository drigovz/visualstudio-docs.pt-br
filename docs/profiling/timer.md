---
title: Temporizador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1bed2715421948385a5b7eb1ddbbac064f3288b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778109"
---
# <a name="timer"></a>Timer
A opção *VSPerfCmd.exe* **Timer** define o evento de criação de perfil que é amostrado aos ciclos do relógio do processador e altera opcionalmente o número de ciclos em um intervalo de amostragem do padrão de 10.000.000. Em um processador de 1 GHz (um gigahertz), 10.000.000 ciclos de relógio são aproximadamente 100 amostras por segundo. O número mínimo de ciclos que pode ser especificado é 50.000.

 O **Temporizador** só pode ser usado quando você utiliza o método de criação de perfil de amostragem e em uma linha de comando que também contenha a opção **Inicialização** ou **Anexar**.

 Por padrão, o evento de amostragem do criador de perfil é definido como ciclos de relógio do processador e o intervalo de amostragem é definido como 10.000.000. As opções **Temporizador**, **PF**, **Sys** e **Contador** permitem que você defina o intervalo de amostragem e o evento de amostragem. A opção **GC** coleta dados da memória do .NET em cada alocação e evento de coleta de lixo. Apenas uma dessas opções pode ser especificada em uma linha de comando.

 O evento de amostragem e o intervalo de amostragem só podem ser definidos na primeira linha de comando que contém uma opção **Inicialização** ou **Anexar**.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>parâmetros
 `Cycles` Um valor inteiro que especifica o número de ciclos do relógio do processador em um intervalo de amostragem. Caso `Cycles` não seja especificado, o intervalo é definido como 10.000.000. Especifique o valor sem vírgulas.

## <a name="required-options"></a>Opções obrigatórias
 O **Temporizador** só pode ser especificado em uma linha de comando que contenha uma das opções a seguir.

 **Inicialização:** `AppName` Inicia o profiler e `AppName`o aplicativo especificado por .

 **Anexa:** `PID` Anexa o profiler ao processo especificado pelo`PID`ID do processo ( ).

## <a name="invalid-options"></a>Opções inválidas
 As opções a seguir não podem ser especificadas na mesma linha de comando do **Temporizador**.

 **PF****[ :**`Events`] Define o evento de amostragem como `Events`falhas de página e define opcionalmente o intervalo de amostragem para . O intervalo de PF padrão é 10.

 **Sys**[**:**`Events`] Define o evento de amostragem para `Events`chamadas do sistema operacional e define opcionalmente o intervalo de amostragem para . O intervalo de Sys padrão é 10.

 **Contador**[**:**`Name,Reload,FriendlyName`] Define o evento de `Name` amostragem para o `Reload`contador de desempenho da CPU especificado e define o intervalo de amostragem para .

 **GC**[**:**{**Alocação**&#124;**Tempo de vida**}] coleta dados de memória do .NET. Por padrão **(Alocação),** os dados são coletados em todos os eventos de alocação de memória. Quando o parâmetro **Tempo de Vida** é especificado, os dados também são coletados em todos os eventos de coleta de lixo.

## <a name="example"></a>Exemplo
 Esse exemplo demonstra como definir o intervalo de amostragem da criação de perfil como 1.000.000 ciclos de processador.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Confira também
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
