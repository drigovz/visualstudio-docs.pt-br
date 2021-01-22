---
title: CrossSession | Microsoft Docs
description: Saiba como usar a opção VSPerfCmd.exe CrossSession para permitir que o criador de perfil colete dados de qualquer sessão de console. Você também deve especificar a opção Iniciar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7a20ada8a7ca8d0ca8c34c2c6d730c37cdca09b7
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686201"
---
# <a name="crosssession"></a>CrossSession
A opção *VSPerfCmd.exe* **CrossSession** permite que o criador de perfil colete dados de qualquer sessão de console. A opção **CrossSession** deve ser usada com a opção **Iniciar**.

 Você pode usar a abreviação **CS** no lugar de **CrossSession**.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parâmetros
 Nenhum

## <a name="valid-options"></a>Opções válidas
 Para habilitar a criação de perfil em outra sessão, a opção **CrossSession** deve ser especificada com a opção **Iniciar**. **CrossSession** também deve ser especificado em qualquer comando **Anexar do VSPerfCmd** e **Desanexar** subsequente.

 **Início:** `Method` A opção **Start** Inicializa o criador de perfil para o método de criação de perfil especificado.

 **Attach:** _pid_[**,**_pid_] começa a criação de perfil dos processos especificados.

 **Desanexar**[**:**_PID_[,_PID_]] Interrompe a criação de perfil dos processos especificados.

## <a name="example"></a>Exemplo
 Neste exemplo, a opção **CrossSession** é usada para anexar a um aplicativo que foi iniciado em outra sessão de console.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Consulte também
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
