---
title: GlobalOn e GlobalOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 518f41557809cdeaaae9f9e1ac79e3797a854395
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74776960"
---
# <a name="globalon-and-globaloff"></a>GlobalOn e GlobalOff
As opções *VSPerfCmd.exe* **GlobalOff** e **GlobalOn** pausam e retomam a criação de perfil de todos os processos e threads em uma sessão de criação de perfil de linha de comando.

 Você pode especificar **Globalize** e **GlobalOff** como as únicas opções em uma *VSPerfCmd.exe* linha de comando ou pode incluí-las em linhas de comando que também contêm as opções **Iniciar**, **Iniciar**ou **anexar** .

 **GlobalOn** e **GlobalOff** também podem ser combinados com as opções **ProcessOn**, **ProcessOff**, **ThreadOn** e **ThreadOff**.

 As opções **GlobalOn** e **GlobalOff** interagem com as opções **ProcessOn** e **ProcessOff** que controlam a coleta de dados para um processo especificado e com as opções **ThreadOn** e **ThreadOff** que controlam a coleta de dados para um thread especificado.

 As opções **GlobalOff** e **GlobalOn** também afetam a contagem Global de Iniciar/Parar que é manipulada pelas funções de API do criador de perfil.

- **GlobalOff** imediatamente define a Contagem global de iniciar/parar para 0 e, portanto, fará uma pausa de criação de perfil.

- **GlobalOn** imediatamente define a Contagem global de iniciar/parar para 1 e, portanto, retomará a criação de perfil.

  Confira [APIs de ferramentas de criação de perfil](../profiling/profiling-tools-apis.md) para obter mais informações.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>Parâmetros
 Nenhum

## <a name="valid-options"></a>Opções válidas
 **GlobalOn** e **GlobalOff** podem ser especificados em linhas de comando que também contêm as seguintes opções.

 **Início:** `Method` Inicializa a sessão do criador de perfil de linha de comando e define o método de criação de perfil especificado.

 **Iniciar:** `AppName` Inicia o aplicativo especificado e começa a criação de perfil com o método de amostragem.

 **Anexar:** `PID` Inicia a criação de perfil do processo especificado.

 {**ProcessOff**&#124;**processize**} **:**`PID` Interrompe ou inicia a criação de perfil para o processo especificado.

 {**ThreadOff**&#124;**Threading**} **:**`TID` Interrompe ou inicia a criação de perfil para o processo especificado (somente método de instrumentação).

## <a name="example"></a>Exemplo
 Neste exemplo, as opções **GlobalOff** e **GlobalOn** são usadas para evitar a coleta de dados de criação de perfil para inicialização e desligamento do aplicativo.

```cmd
; Initialize the profiler with profiling stopped.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff
; Start an instrumented application and wait for it to warm up.
; Start profiling.
VSPerfCmd.exe /GlobalOn
; Exercise the application functionality that you want to profile.
; Stop profiling.
VSPerfCmd.exe /GlobalOff
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Confira também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
