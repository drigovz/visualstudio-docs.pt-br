---
title: Lançamento de um Programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf638e0c96c7df1de2650260427a972a07efce23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738484"
---
# <a name="launch-a-program"></a>Lançar um programa
Os usuários que desejam depurar um programa podem pressionar **F5** para executar o depurador a partir do IDE. Isso começa uma série de eventos que resultam na conexão do IDE a um mecanismo de depuração (DE), que por sua vez está conectado, ou conectado, ao programa da seguinte forma:

1. O IDE primeiro chama o pacote do projeto para obter as configurações ativas de depuração do projeto da solução. As configurações incluem o diretório inicial, as variáveis de ambiente, a porta em que o programa será executado e o DE para usar para criar o programa, se especificado. Essas configurações são passadas para o pacote de depuração.

2. Se um DE for especificado, o DE chamará o sistema operacional para iniciar o programa. Como conseqüência do lançamento do programa, o ambiente de tempo de execução do programa carrega. Por exemplo, se um programa for escrito no MSIL, o tempo de execução do idioma comum será invocado para executar o programa.

    -ou-

    Se um DE não for especificado, a porta liga para o sistema operacional para iniciar o programa, o que faz com que o ambiente de tempo de execução do programa seja carregado.

   > [!NOTE]
   > Se um DE for usado para lançar um programa, é provável que o mesmo DE seja anexado ao programa.

3. Dependendo se o DE ou a porta lançaram o programa, o DE ou o ambiente de tempo de execução criam uma descrição do programa, ou nó, e notificam a porta que o programa está executando.

   > [!NOTE]
   > Recomenda-se que o ambiente de tempo de execução crie o nó do programa, pois o nó do programa é uma representação leve de um programa que pode ser depurado. Não há necessidade de carregar um DE inteiro apenas para criar e registrar um nó de programa. Se o DE foi projetado para ser executado no processo do IDE, mas nenhum IDE está realmente em execução, precisa haver um componente que possa adicionar um nó de programa à porta.

   O programa recém-criado, juntamente com quaisquer outros programas, relacionados ou não relacionados, lançados ou anexados a partir do mesmo IDE, compõem uma sessão de depuração.

   Programáticamente, quando o usuário pressiona [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pela primeira vez **f5**, 's debug package chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> pacote de projeto (que <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> está associado ao tipo de programa que está sendo lançado) através do método, que por sua vez preenche uma estrutura com as configurações ativas de depuração do projeto da solução. Esta estrutura é passada de volta para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> pacote de depuração através de uma chamada para o método. O pacote de depuração instancia o Session Debug Manager (SDM), que inicia o programa sendo depurado e quaisquer mecanismos de depuração associados.

   Um dos argumentos passados para o SDM é o GUID do DE a ser usado para lançar o programa.

   Se o DE `GUID_NULL`GUID não for, o SDM co-cria o DE e, em seguida, chama seu método [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para iniciar o programa. Por exemplo, se um programa for `IDebugEngineLaunch2::LaunchSuspended` escrito `CreateProcess` em `ResumeThread` código nativo, provavelmente chamará e (funções Win32) para executar o programa.

   Como conseqüência do lançamento do programa, o ambiente de tempo de execução do programa é carregado. O DE ou o ambiente de tempo de execução criam uma interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) para descrever o programa e passam essa interface para [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) para notificar a porta que o programa está executando.

   Se `GUID_NULL` for aprovada, a porta lança o programa. Uma vez que o programa está sendo `IDebugProgramNode2` executado, o ambiente de `IDebugPortNotify2::AddProgramNode`tempo de execução cria uma interface para descrever o programa e passa-o para . Isso notifica a porta que o programa está executando. Em seguida, o SDM anexa o mecanismo de depuração ao programa de execução.

## <a name="in-this-section"></a>Nesta seção
 [Notificando a porta](../../extensibility/debugger/notifying-the-port.md) Explica o que acontece depois que um programa é lançado e a porta é notificada.

 [Anexando após um lançamento](../../extensibility/debugger/attaching-after-a-launch.md) Documentos quando a sessão de depuração estiver pronta para anexar o DE ao programa.

## <a name="related-sections"></a>Seções relacionadas
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md) Contém links para várias tarefas de depuração, como o lançamento de um programa e a avaliação de expressões.
