---
title: PF | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07ec6d636ec087386fdc9462ae09db55400957a9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778408"
---
# <a name="pf"></a>PF
A opção *VSPerfCmd.exe* **PF** define o evento de criação de perfil que é amostrado para falhas de página e altera opcionalmente o número de falhas de página em um intervalo de amostragem do padrão de 10.

> [!NOTE]
> A **PF** não pode ser usada em sistemas de 64 bits.

A **PF** só pode ser usada em uma linha de comando que também contém a opção de **Inicialização** ou **Anexar**.

 Por padrão, o evento de amostragem é definido como ciclos de relógio do processador não interrompidos e o intervalo de amostragem é definido como 10.000.000. As opções **Temporizador**, **PF**, **Sys** e **Contador** permitem que você defina o intervalo de amostragem e o evento de amostragem. A opção **GC** coleta dados da memória do .NET em cada alocação e evento de coleta de lixo. Apenas uma dessas opções pode ser especificada em uma linha de comando.

 O evento de amostragem e o intervalo de amostragem só podem ser definidos na primeira linha de comando que contém uma opção **Inicialização** ou **Anexar**.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>parâmetros
 `Events` Um valor inteiro que especifica o número de eventos de falha de página em um intervalo de amostragem. Caso `Events` não seja especificado, o intervalo é definido como 10.

## <a name="required-options"></a>Opções obrigatórias
 A **PF** só pode ser especificada em uma linha de comando que contenha uma das opções a seguir.

 **Lançamento:** `AppName` Inicia o profiler e o aplicativo especificado pelo AppName.

 **Anexa:** `PID` Anexa o profiler ao processo especificado pelo AppName.

## <a name="invalid-options"></a>Opções inválidas
 As opções a seguir não podem ser especificadas na mesma linha de comando de **PF**.

 **Temporizador**[**:**`Cycles`] Define o evento de amostragem `Cycles`para ciclos de relógio do processador e define opcionalmente o intervalo de amostragem para . O intervalo do temporizador padrão é 10.000.000.

 **Sys**[**:**`Events`] Define o evento de amostragem para chamadas do aplicativo perfilado para o `Events`kernel do sistema operacional (syscalls) e define opcionalmente o intervalo de amostragem para . O intervalo de Sys padrão é 10.

 **Contador:** `Name``,Reload`[`,FriendlyName`] Define o evento de amostragem `Name` para o contador `Reload`de desempenho da CPU especificado e define o intervalo de amostragem para .

 **GC**[**:**{**Alocação**&#124;**Tempo de vida**}] coleta dados de memória do .NET. Por padrão **(Alocação),** os dados são coletados em todos os eventos de alocação de memória. Quando o parâmetro **Tempo de Vida** é especificado, os dados também são coletados em todos os eventos de coleta de lixo.

## <a name="example"></a>Exemplo
 Este exemplo demonstra como definir o evento de amostragem de criação de perfil como falhas de página e definir o intervalo de amostragem para 20 falhas de página.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Confira também
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
