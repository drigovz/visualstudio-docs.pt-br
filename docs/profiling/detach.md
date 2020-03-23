---
title: Desanexar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b151e3ede34d0c8fa3a863d7a4e7474431ae6f4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777384"
---
# <a name="detach"></a>Desanexar
A opção de **desanexar** VSPerfCmd.exe desconecta o criador de perfil de todos os processos ou dos processos especificados se nenhum for especificado. A criação de perfil deve ter sido inicializada usando o método de amostragem.

 A criação de perfil que foi iniciada com as opções **Iniciar** ou o **Anexar** pode ser desconectada com **Desanexar**. O criador de perfil pode ser reconectado usando os comandos **Anexar** subsequentes.

 **Desanexar** não fecha o arquivo de dados de criação de perfil. Use a opção **Desligamento** para finalizar a criação de perfil e fechar o arquivo de dados.

> [!NOTE]
> Se a opção **Iniciar** foi especificada com a opção **Crosssession**, todas as chamadas para **VSPerfCmd /Attach** ou **VSPerfCmd /Detach** também devem especificar **Crosssession**.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>parâmetros
 `PIDs|ProcessNames``PID` - O identificador numérico do sistema de um ou mais processos.

 `ProcessNames` - o nome do processo. Se estiver executando várias instâncias do processo nomeado, os resultados serão imprevisíveis.

 Separe vários processos com vírgulas.

 Se nenhum processo for especificado, o criador de perfil será desanexado de todos os processos com perfil.

## <a name="valid-options"></a>Opções válidas
 As seguintes opções **VSPerfCmd** podem ser combinadas com a opção **Anexar** em uma única linha de comando.

 **Crosssession** Habilita aplicativos de criação de perfil em sessões que não seja a sessão de logon. Necessário se a opção **Iniciar** foi especificada com a opção **Crosssession**.

## <a name="example"></a>Exemplo
 Neste exemplo, o comando **Desanexar** suspende a criação de perfil e o comando **Desligamento** fecha o arquivo de dados do criador de perfil.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Confira também
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
