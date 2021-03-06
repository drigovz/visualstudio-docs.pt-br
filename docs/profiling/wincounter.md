---
title: WinCounter | Microsoft Docs
description: Saiba mais sobre a opção WinCounter, especificamente que especifica um contador de desempenho do Windows ou do aplicativo para coletar em intervalos definidos durante a execução do perfil.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: eaa5482ba1bad297fd1cfdf20810ad985b050c25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915936"
---
# <a name="wincounter"></a>WinCounter
A opção **WinCounter** especifica um contador de desempenho do aplicativo ou do Windows para coletar em intervalos definidos durante o perfil de execução. Os contadores de desempenho do aplicativo e do Windows são listados como marcas no arquivo de dados de criação de perfil. Você pode especificar vários contadores de desempenho para coletar em opções separadas.

 Por padrão, os contadores são coletados a cada 500 milissegundos. Use a opção **AutoMark** para especificar um intervalo diferente de coleção.

 Apenas uma opção **AutoMark** é usada. Se várias opções **AutoMark** forem especificadas, a última será usada.

 A opção **WinCounter** só pode ser usada com a opção **Iniciar**.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]
```

#### <a name="parameters"></a>Parâmetros
 `Path` O contador de desempenho do Windows no formato de caminho de contador PDH.

## <a name="required-options"></a>Opções obrigatórias
 A opção **WinCounter** só pode ser usada com a opção **Iniciar**.

 **Início:** `Method` A opção **Start** Inicializa o criador de perfil para o método de criação de perfil especificado.

## <a name="exclusive-options"></a>Opções exclusivas
 A opção **AutoMark** só pode ser usada com a opção **WinCounter**.

 **Marca automática:** `Milliseconds` Especifica o número de milissegundos entre a coleta de dados do contador de desempenho do Windows.

## <a name="example"></a>Exemplo
 No exemplo a seguir, dois contadores de desempenho do Windows são especificados para serem coletados em um intervalo de 1000 milissegundos.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000
```

## <a name="see-also"></a>Consulte também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
