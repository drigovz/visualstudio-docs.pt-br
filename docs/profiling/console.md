---
title: Console | Microsoft Docs
description: Use a opção de console do VSPerfCmd.exe para iniciar o aplicativo especificado em uma nova janela de prompt de comando. Você deve usá-lo com a opção Iniciar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 93c39bfb503bec9858e33b7acf04e0f0433264b9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720898"
---
# <a name="console"></a>Console
A opção **Console** VSPerfCmd.exe inicia o aplicativo especificado em uma nova janela de prompt de comando. O **Console** só pode ser usado com a opção **Iniciar** VSPerfCmd. Se o aplicativo não é um aplicativo de linha de comando, o **Console** não tem nenhum efeito.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Parâmetros
 Nenhum

## <a name="required-options"></a>Opções obrigatórias
 O **Console** só pode ser especificado em uma linha de comando que também tem a opção **Iniciar**.

 **Iniciar:** `AppName` Inicia o criador de perfil e o aplicativo especificado por `AppName` .

## <a name="see-also"></a>Confira também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
