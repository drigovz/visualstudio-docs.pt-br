---
title: WaitStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6307dcad45b7e2c8164aa892c4598d577e4ea464
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998960"
---
# <a name="waitstart"></a>WaitStart
A opção WaitStart faz com que o subcomando Start do *VSPerfCmd.exe* seja retornado somente quando o criador de perfil tiver sido inicializado ou o número especificado de segundos tiver decorrido. Por padrão, o comando Start retorna imediatamente. Se o subcomando Start for retornado sem inicializar o criador de perfil, um erro será retornado. Se o número de segundos não for especificado, o comando Start aguardará indefinidamente.

 A opção WaitStart é útil para arquivos de lote a fim de garantir se o criador de perfil foi inicializado.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]
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