---
title: Status | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bf5e0fdf478e067f61b1d0e259cb1624380e4f02
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778239"
---
# <a name="status"></a>Status
A opção *VSPerfCmd.exe* **Status** exibe informações sobre o estado do profiler e quaisquer processos que estão sendo perfilados.

 A opção **Status** deve ser a única opção especificada na linha de comando. O profiler deve ser inicializado com a opção *VSPerfCmd.exe* **Start** antes que qualquer status possa ser exibido.

## <a name="syntax"></a>Sintaxe

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>parâmetros
 Nenhum

## <a name="remarks"></a>Comentários
 A opção **Status** exibe as seguintes informações de estado para o criador de perfil.

 **Nome do Arquivo de Saída** O caminho e o nome do arquivo de dados do criador de perfil atual.

 **Modo de Coleta** SAMPLE ou TRACE

 **Número Máximo de Processos** O número máximo de processos que podem ser analisados ao mesmo tempo e o número de processos ativos no momento.

 **Número Máximo de Threads** O número máximo de threads que podem ser analisados ao mesmo tempo.

 **Número de Buffers** O número de buffers de memória dedicados à gravação de dados de criação de perfil.

 **Tamanho de Buffers** O tamanho em bytes do buffer de memória.

 A opção **Status** exibe as seguintes informações de estado para cada processo que está atualmente sendo perfilado.

 **Processo** O nome do processo analisado.

 **Identificador do Processo** O identificador do sistema do processo.

 **Número de Threads** O número de threads em execução no momento.

 **Iniciar/Parar Contagem** A contagem do criador de perfil primário interno para controlar a coleta de dados desse processo. A contagem deve ser igual a um para coletar dados. Iniciar/Parar Contagem pode ser manipulada por APIs do criador de perfil e as opções de VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** e **ThreadOff**.

 **Suspender/Retomar Contagem** A contagem do criador de perfil secundário interno para controlar a coleta de dados desse processo. A contagem deve ser menor ou igual a zero para coletar dados. A opção **Suspender/Retomar** contagem pode ser manipulada somente pela APIs do criador de perfil.

 **Usuários com direitos de acesso de monitoramento** Lista os nomes de usuários que têm acesso ao criador de perfil. Usuários adicionais podem ser concedidos acesso por meio da opção VSPerfCmd.exe **Admin**

## <a name="see-also"></a>Confira também
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Aplicativos Autônomos de Perfil](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)
