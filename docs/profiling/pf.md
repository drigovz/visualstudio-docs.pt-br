---
title: PF | Microsoft Docs
description: Saiba como a opção VSPerfCmd.exe PF define o evento de criação de perfil que é amostrado para falhas de página e altera o número de falhas de página em um intervalo de amostragem.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ee20d393a4c18c77dd059bbb78ed67b3c7264aee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957329"
---
# <a name="pf"></a>PF
A opção *VSPerfCmd.exe* **PF** define o evento de criação de perfil que é amostrado para falhas de página e, opcionalmente, altera o número de falhas de página em um intervalo de amostragem a partir do padrão de 10.

> [!NOTE]
> A **PF** não pode ser usada em sistemas de 64 bits.

A **PF** só pode ser usada em uma linha de comando que também contém a opção de **Inicialização** ou **Anexar**.

 Por padrão, o evento de amostragem é definido como ciclos de relógio do processador não interrompidos e o intervalo de amostragem é definido como 10.000.000. As opções **Temporizador**, **PF**, **Sys** e **Contador** permitem que você defina o intervalo de amostragem e o evento de amostragem. A opção **GC** coleta dados da memória do .NET em cada alocação e evento de coleta de lixo. Apenas uma dessas opções pode ser especificada em uma linha de comando.

 O evento de amostragem e o intervalo de amostragem só podem ser definidos na primeira linha de comando que contém uma opção **Inicialização** ou **Anexar**.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Parâmetros
 `Events` Um valor inteiro que especifica o número de eventos de falha de página em um intervalo de amostragem. Caso `Events` não seja especificado, o intervalo é definido como 10.

## <a name="required-options"></a>Opções obrigatórias
 A **PF** só pode ser especificada em uma linha de comando que contenha uma das opções a seguir.

 **Iniciar:** `AppName` Inicia o criador de perfil e o aplicativo especificado por AppName.

 **Anexar:** `PID` Anexa o criador de perfil ao processo especificado por AppName.

## <a name="invalid-options"></a>Opções inválidas
 As opções a seguir não podem ser especificadas na mesma linha de comando de **PF**.

 **Timer**[**:** `Cycles` ] define o evento de amostragem para ciclos de relógio do processador e, opcionalmente, define o intervalo de amostragem como `Cycles` . O intervalo do temporizador padrão é 10.000.000.

 **Sys**[**:** `Events` ] define o evento de amostragem para chamadas do aplicativo de perfil para o kernel do sistema operacional (syscalls) e, opcionalmente, define o intervalo de amostragem como `Events` . O intervalo de Sys padrão é 10.

 **Contador:** `Name` [ `,Reload` [ `,FriendlyName` ]] Define o evento de amostragem para o contador de desempenho de CPU especificado por `Name` e define o intervalo de amostragem como `Reload` .

 **GC**[**:**{**Alocação**&#124;**Tempo de vida**}] coleta dados de memória do .NET. Por padrão (**alocação**), os dados são coletados em cada evento de alocação de memória. Quando o parâmetro **Tempo de Vida** é especificado, os dados também são coletados em todos os eventos de coleta de lixo.

## <a name="example"></a>Exemplo
 Este exemplo demonstra como definir o evento de amostragem de criação de perfil como falhas de página e definir o intervalo de amostragem para 20 falhas de página.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Consulte também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
