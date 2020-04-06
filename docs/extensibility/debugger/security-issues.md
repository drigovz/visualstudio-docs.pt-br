---
title: Problemas de segurança | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713047"
---
# <a name="security-issues"></a>Problemas de segurança
Para depurar um programa usando o Visual Studio, as únicas permissões necessárias são as mesmas que um desenvolvedor precisa para executar o programa. Isso inclui depuração remota para a maioria das situações. Algumas situações, envolvendo outros serviços, como o Serviço de Informações da Internet, podem exigir um nível mais alto de permissões.

 Enquanto o Visual Studio está em execução, o PDM (Process Debug Manager, gerenciador de depuração) rastreia processos de depuração na máquina local. Remotamente, um programa chamado *msvsmon.exe* é iniciado pelo desenvolvedor para lidar com a depuração remota e disponibilizar o PDM. (*msvsmon.exe* não é um serviço e deve ser iniciado manualmente para permitir a depuração remota naquela máquina.) Quando o Visual Studio (ou *msvsmon.exe)* não está em execução, nenhum processo é rastreado para depuração.

 Um desenvolvedor pode depurar programas que eles começaram sem permissões especiais. O desenvolvedor pode até mesmo depurar processos iniciados por outra pessoa se essa outra pessoa for membro do mesmo grupo de segurança. E, para permitir a depuração remota, é necessário apenas copiar os arquivos necessários para a máquina remota e iniciar *o msvsmon.exe*. Para obter mais informações, consulte [Depuração remota](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Confira também
- [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
- [Gerente de depuração de processos](../../extensibility/debugger/process-debug-manager.md)
- [Depuração remota](../../debugger/remote-debugging.md)
