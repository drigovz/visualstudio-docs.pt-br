---
title: Args | Microsoft Docs
description: Use a opção ARGS de VSPerfCmd.exe para passar uma lista de argumentos para o aplicativo de destino do subcomando Launch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ff16d67d0c7168524ff145183f49a662e1f660f0
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205704"
---
# <a name="args"></a>Args
A opção **Args** de VSPerfCmd.exe especifica uma lista de argumentos passados para o aplicativo de destino do subcomando **Launch**.

 **Args** pode ser usado somente quando **Launch** também for especificado na linha de comando. **Args** é opcional quando **Inicialização** for especificado.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parâmetros
 `Arguments` Uma lista de argumentos para o aplicativo de destino do comando de **inicialização** .

## <a name="required-options"></a>Opções obrigatórias
 **Iniciar:** `AppName` Inicia o aplicativo especificado e começa a criação de perfil com o método de amostragem.

## <a name="example"></a>Exemplo
 O exemplo a seguir usa a opção **Args** para passar argumentos para TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Confira também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Criação de perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criação de perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)
