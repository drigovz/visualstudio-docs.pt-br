---
title: Args | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b6d01a95b7e0872d6bb36c6d9f3917bc6a05b3b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779812"
---
# <a name="args"></a>Args
A opção **Args** de VSPerfCmd.exe especifica uma lista de argumentos passados para o aplicativo de destino do subcomando **Launch**.

 **Args** pode ser usado somente quando **Launch** também for especificado na linha de comando. **Args** é opcional quando **Inicialização** for especificado.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>parâmetros
 `Arguments`Uma lista de argumentos para a aplicação de destino do comando **Launch.**

## <a name="required-options"></a>Opções obrigatórias
 **Lançamento:** `AppName` Inicia a aplicação especificada e inicia a criação de perfil com o método de amostragem.

## <a name="example"></a>Exemplo
 O exemplo a seguir usa a opção **Args** para passar argumentos para TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Confira também
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Criação de perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criação de perfil ASP.NET aplicações web](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Serviços de criação de perfil](../profiling/command-line-profiling-of-services.md)
