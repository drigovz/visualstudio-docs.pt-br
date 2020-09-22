---
title: Como depurar um mecanismo de depuração personalizado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7e710cec4536a5a1327580e56c60cb23ca36f4c
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2020
ms.locfileid: "90838407"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Como depurar um mecanismo de depuração personalizado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um tipo de projeto inicia o mecanismo de depuração (DE) do <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> método. Isso significa que o DE é iniciado sob o controle da instância de controle do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tipo de projeto. No entanto, essa instância do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] não pode depurar o de. O que vem a seguir são as etapas para permitir que você depure seus personalizados DE.  
  
> [!NOTE]
> : No procedimento "Depurando um mecanismo de depuração personalizado", você deve aguardar até que o seja iniciado antes de poder anexá-lo. Se você posicionar uma caixa de mensagem perto do início do que aparece quando o DE começa, você pode anexar nesse ponto e, em seguida, desmarcar a caixa de mensagem para continuar. Dessa forma, você pode capturar todos os eventos.  
  
> [!WARNING]
> Você deve ter a depuração remota instalada antes de tentar os procedimentos a seguir. Consulte [depuração remota](../../debugger/remote-debugging.md) para obter detalhes.  
  
### <a name="debugging-a-custom-debug-engine"></a>Depurando um mecanismo de depuração personalizado  
  
1. Inicie o msvsmon.exe, o monitor de depuração remota.  
  
2. No menu **ferramentas** no msvsmon.exe, selecione **Opções** para abrir a caixa de diálogo **Opções** .  
  
3. Selecione a opção "sem autenticação" e clique em **OK**.  
  
4. Inicie uma instância do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e abra seu projeto de personalização.  
  
5. Inicie uma segunda instância do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e abra seu projeto personalizado que inicia o de (para desenvolvimento), normalmente, no hive experimental do registro que é configurado quando o VSIP é instalado).  
  
6. Na segunda instância do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , carregue um arquivo de origem do projeto personalizado e inicie o programa a ser depurado. Aguarde alguns instantes para permitir que o seja carregado ou aguarde até que um ponto de interrupção seja atingido.  
  
7. Na primeira instância de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (com o de seu projeto), selecione **anexar ao processo** no menu **depurar** .  
  
8. Na caixa de diálogo **anexar ao processo** , altere o **transporte** para **remoto (somente nativo sem autenticação)**.  
  
9. Altere o **qualificador** para o nome do seu computador (Observação: há um histórico de entradas, portanto, você precisa digitar esse nome apenas uma vez).  
  
10. Na lista **processos disponíveis** , selecione a instância de de que está em execução e clique no botão **anexar** .  
  
11. Depois que os símbolos forem carregados em seu de, coloque os pontos de interrupção em seu DE código.  
  
12. Toda vez que você parar e reiniciar o processo de depuração, repita as etapas de 6 a 10.  
  
### <a name="debugging-a-custom-project-type"></a>Depurando um tipo de projeto personalizado  
  
1. Inicie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no hive do registro normal e carregue o projeto de tipo de projeto (isto é, a origem para o tipo de projeto, não uma instanciação do tipo de projeto).  
  
2. Abra as propriedades do projeto e vá para a página de **depuração** . Para o **comando**, digite o caminho para o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (por padrão, é *[unidade]* \Arquivos de Programas\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3. Para os **argumentos de comando**, digite `/rootsuffix exp` para o hive experimental do registro (criado quando o VSIP foi instalado).  
  
4. Clique em **OK** para aceitar as alterações.  
  
5. Inicie o tipo de projeto pressionando F5. Isso abrirá uma segunda instância do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
6. Neste ponto, você pode inserir pontos de interrupção no código-fonte do tipo de projeto.  
  
7. Na segunda instância do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , carregue ou crie uma nova instância do tipo de projeto. Durante a carga ou a criação, seus pontos de interrupção podem ser atingidos.  
  
8. Depurar o tipo de projeto.  
  
9. Se você optar por depurar o processo de inicialização de um, você poderá executar as etapas no procedimento "Depurando um mecanismo de depuração personalizado" para anexar ao DE depois que ele for iniciado. Isso fornecerá três instâncias de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] execução: uma para a origem do tipo de projeto, uma segunda para o tipo de projeto instanciado e uma terceira anexada a de seu.  
  
## <a name="see-also"></a>Consulte Também  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
