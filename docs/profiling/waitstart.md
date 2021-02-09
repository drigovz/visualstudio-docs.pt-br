---
title: WaitStart | Microsoft Docs
description: Saiba que a opção WaitStart faz com que o subcomando VSPerfCmd.exe iniciar seja retornado somente quando o criador de perfil tiver sido inicializado ou quando o número especificado de segundos tiver passado.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b883ae215854994918419fb311d94ad921989740
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911481"
---
# <a name="waitstart"></a>WaitStart
A opção WaitStart faz com que o subcomando Start do *VSPerfCmd.exe* seja retornado somente quando o criador de perfil tiver sido inicializado ou o número especificado de segundos tiver decorrido. Por padrão, o comando Start retorna imediatamente. Se o subcomando Start for retornado sem inicializar o criador de perfil, um erro será retornado. Se o número de segundos não for especificado, o comando Start aguardará indefinidamente.

 A opção WaitStart é útil para arquivos de lote a fim de garantir se o criador de perfil foi inicializado.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parâmetros
 `Seconds` O número de segundos de espera antes do retorno do subcomando Iniciar.

## <a name="required-options"></a>Opções obrigatórias
 A opção WaitStart só pode ser usada com o subcomando Start.

 **Saída:** `filename` Especifica o nome do arquivo de saída.

## <a name="remarks"></a>Comentários

## <a name="example"></a>Exemplo
 Neste exemplo de arquivo em lotes, o comando Start aguardará 5 segundos para inicializar o criador de perfil.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5
if not %errorlevel% 0 goto :error_tag
VSPerfCmd.exe /Launch:TestApp.exe
goto :end
:error_tag
@echo Could not start Profiler!
@echo Error %errorlevel%
:end
```
