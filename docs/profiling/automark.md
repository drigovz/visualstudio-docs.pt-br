---
title: AutoMark | Microsoft Docs
description: Use a opção automarcar para especificar o intervalo de tempo entre os eventos de coleta de dados do contador de desempenho do Windows. Use-o com a opção WinCounter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3712246256618debfb8d85ebfb0c273511eb9558
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901087"
---
# <a name="automark"></a>AutoMark
A opção **AutoMark** especifica o número de milésimos de segundos entre a coleção de eventos de contador de desempenho de software do Windows. Contadores de desempenho do Windows são especificados na opção **WinCounter**.

 Apenas uma opção **AutoMark** pode ser especificada na linha de comando. Observe que o intervalo de amostragem de **WinCounter** especificado por **AutoMark** é independente do intervalo de amostragem principal.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds
```

#### <a name="parameters"></a>Parâmetros
 `Milliseconds` Especifica o número de milésimos de segundos entre coleções de eventos do contador de desempenho do Windows.

## <a name="required-options"></a>Opções obrigatórias
 **WinCounter:** `Path` Especifica o contador de desempenho do Windows a ser coletado. Quando você estiver usando o método de instrumentação, vários contadores do Windows podem ser especificados. Quando você estiver usando o método de amostragem, apenas um contador de software pode ser especificado. A opção **WinCounter** deve ser especificada em uma linha de comando que contém a opção **Iniciar**.

## <a name="example"></a>Exemplo
 Neste exemplo, um intervalo de amostragem de 1000 milésimos de segundos é definido para dois contadores de desempenho do Windows.

```cmd
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Confira também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
