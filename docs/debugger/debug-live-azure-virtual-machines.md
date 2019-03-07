---
title: Depuração do ASP.NET Azure máquinas virtuais e conjuntos de dimensionamento de máquina virtual do Azure
description: Saiba como configurar o snappoints e exibir instantâneos com o depurador de instantâneo.
ms.custom: ''
ms.date: 02/06/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 608745fc2c96836163e1406abda6869d52b1da1b
ms.sourcegitcommit: 62149c96de0811415e99bb1e0194e76c320e1a1e
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "57007261"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Depurar aplicativos ASP.NET dinâmicos em máquinas virtuais do Azure e conjuntos de dimensionamento de máquina virtual do Azure usando o depurador de instantâneo

O depurador de instantâneo tira um instantâneo de seus aplicativos em produção, quando o código que você está interessado é executado. Para instruir o depurador a tirar um instantâneo, defina snappoints e logpoints em seu código. O depurador permite ver exatamente o que deu errado sem afetar o tráfego do seu aplicativo de produção. O Depurador de Instantâneo pode ajudar a reduzir drasticamente o tempo que leva para resolver problemas que ocorrem em ambientes de produção.

Snappoints e logpoints são semelhantes aos pontos de interrupção, mas ao contrário de pontos de interrupção, snappoints não interrompem o aplicativo quando atingidos. Normalmente, capturando um instantâneo em um snappoint leva 10 a 20 milissegundos.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Inicie o depurador de instantâneo
> * Defina um snappoint e exibir um instantâneo
> * Defina um logpoint

## <a name="prerequisites"></a>Pré-requisitos

* Depurador de instantâneos para máquinas virtuais do Azure (VM) e conjuntos de dimensionamento de máquina Virtual do Azure (VMSS) só está disponível para visualização do Visual Studio 2019 Enterprise ou superior com o **carga de trabalho de desenvolvimento do Azure**. (Sob o **componentes individuais** guia, você encontrá-lo sob **depuração e testes** > **depurador de instantâneo**.)

    Se ainda não estiver instalado, instale [versão prévia do Visual Studio Enterprise de 2019](https://visualstudio.microsoft.com/vs/preview/).

* Coleta de instantâneo está disponível para os seguintes aplicativos web do Azure VM/VMSS:
  * Aplicativos ASP.NET em execução no .NET Framework 4.6.1 ou posterior.
  * Aplicativos ASP.NET Core em execução no .NET Core 2.0 ou posterior no Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Abra seu projeto e iniciar o depurador de instantâneo

1. Abra o projeto que você gostaria de depuração de instantâneo.

    > [!IMPORTANT]
    > A depuração de instantâneo, você precisará abrir o *mesma versão do código-fonte* que é publicado ao seu serviço VM/VMSS do Azure.

1. Anexe o depurador de instantâneo. Você pode usar um dos vários métodos diferentes:

    * Escolha **Depurar > Anexar depurador de instantâneos...** . Selecione o VM/VMSS do Azure seu aplicativo web é implantado e uma conta de armazenamento do Azure e, em seguida, clique em **Attach**.

      ![Iniciar o depurador de instantâneo no menu Depurar](../debugger/media/snapshot-debug-menu-attach.png)

    * Clique com botão direito no seu projeto e selecione **Publish**e, em seguida, na página de publicação. clique em **Anexar depurador de instantâneo**. Selecione o VM/VMSS do Azure seu aplicativo web é implantado e uma conta de armazenamento do Azure e, em seguida, clique em **Attach**.
    ![Iniciar o depurador de instantâneo da página de publicação](../debugger/media/snapshot-publish-attach.png)

    * Na depuração de destino menu suspenso, selecione **depurador de instantâneo**, aperte **F5** e se necessário selecionar o VM/VMSS do Azure seu aplicativo web é implantado e o armazenamento do Azure da conta e, em seguida, clique em  **Anexar**.
    ![Iniciar o depurador de instantâneo no menu suspenso F5](../debugger/media/snapshot-F5-dropdown-attach.png)

    * Usando o Gerenciador de nuvem (**exibição > Gerenciador de nuvem**), o VM/VMSS do Azure seu aplicativo web é implantado com o botão direito e selecione uma conta de armazenamento do Azure e, em seguida, clique em **Anexar depurador de instantâneo**.

      ![Iniciar o depurador de instantâneo do Cloud Explorer](../debugger/media/snapshot-launch.png)

    > [!IMPORTANT]
    > Na primeira vez que você seleciona **anexar o depurador de instantâneo** para sua VM, o IIS será reiniciado automaticamente.
    > Na primeira vez que você seleciona **anexar o depurador de instantâneo** para sua VMSS, exigem a atualização manual de cada instância do VMSS.

    Os metadados para o **módulos** inicialmente não será possível ativar, navegue até o aplicativo web e o **iniciar coleta** botão se tornará ativo. Visual Studio agora está no modo de depuração de instantâneo.

    > [!NOTE]
    > A extensão de site do Application Insights também dá suporte à depuração de instantâneo. Se você encontrar uma mensagem de erro "desatualizados da extensão de site", consulte [solução de problemas e problemas conhecidos para depuração de instantâneo](../debugger/debug-live-azure-apps-troubleshooting.md) para atualizar os detalhes.
    > Para VMSS o usuário é necessário para atualizar manualmente as instâncias em suas VMSS depois de anexar o depurador de instantâneo pela primeira vez.

   ![Modo de depuração de instantâneo](../debugger/media/snapshot-message.png)

   O **módulos** janela mostra quando todos os módulos têm carregadas para o Azure VM/VMSS (escolher **Depurar > Windows > módulos** para abrir essa janela).

   ![Verifique a janela módulos](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Defina um snappoint

1. No editor de códigos, clique na medianiz esquerda ao lado de uma linha de código que você está interessado para definir um snappoint. Verifique se que ele é o código que você sabe que será executado.

   ![Defina um snappoint](../debugger/media/snapshot-set-snappoint.png)

1. Clique em **iniciar coleta** para ativar o snappoint.

   ![Ativar o snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Você não pode depurar ao exibir um instantâneo, mas você pode colocar vários snappoints em seu código a seguir execução em diferentes linhas de código. Se você tiver vários snappoints em seu código, o depurador de instantâneo garante que os instantâneos correspondentes são da mesma sessão do usuário final. O depurador de instantâneo faz isso, mesmo se houver muitos usuários acessando seu aplicativo.

## <a name="take-a-snapshot"></a>Tirar um instantâneo

Quando um snappoint for ativado, ele irá capturar um instantâneo sempre que executa a linha de código em que o snappoint é colocado. Essa execução pode ser causada por uma solicitação real em seu servidor. Para forçar o snappoint participar, vá para a exibição de navegador do seu site e executar quaisquer ações necessárias que fazem com que seu snappoint seja atingido.

## <a name="inspect-snapshot-data"></a>Inspecione os dados de instantâneo

1. Quando o snappoint for atingido, um instantâneo é exibida na janela de ferramentas de diagnóstico. Para abrir essa janela, escolha **Depurar > Windows > Mostrar ferramentas de diagnóstico**.

   ![Abra um snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Clique duas vezes o snappoint para abrir o instantâneo no editor de códigos.

   ![Inspecione os dados de instantâneo](../debugger/media/snapshot-inspect-data.png)

   Nessa exibição, você pode passar o mouse sobre as variáveis para exibir os DataTips, use o **Locals**, **inspeções**, e **pilha de chamadas** windows e também avaliar expressões.

    O site em si ainda está ao vivo e os usuários finais não são afetados. Apenas um instantâneo é capturado por snappoint por padrão: após um instantâneo captura o snappoint seja desligada. Se você quiser capturar outro instantâneo no snappoint, você pode ativar o snappoint novamente clicando **atualizar coleção**.

Você também pode adicionar mais snappoints ao seu aplicativo e ligá-los com o **atualizar coleção** botão.

**Precisa de ajuda?** Consulte a [problemas conhecidos e solução de problemas](../debugger/debug-live-azure-apps-troubleshooting.md) e [perguntas frequentes sobre depuração de instantâneo](../debugger/debug-live-azure-apps-faq.md) páginas.

## <a name="set-a-conditional-snappoint"></a>Defina um snappoint condicional

Se você tiver dificuldades recriar um estado específico em seu aplicativo, considere se o uso de um snappoint condicional pode ajudar. Snappoints condicional ajuda a que evitar tirar um instantâneo, até que o aplicativo entra em um estado desejado, como quando uma variável tem um valor específico que você deseja inspecionar. Você pode definir condições de uso de expressões, filtros, ou contagens de ocorrências.

#### <a name="to-create-a-conditional-snappoint"></a>Para criar um snappoint condicional

1. Um ícone de snappoint (a bola vazado) com o botão direito e escolha **configurações**.

   ![Escolha Configurações](../debugger/media/snapshot-snappoint-settings.png)

1. Na janela de configurações de snappoint, digite uma expressão.

   ![Digite uma expressão](../debugger/media/snapshot-snappoint-conditions.png)

   Na ilustração anterior, o instantâneo é criado somente para o snappoint quando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Defina um logpoint

Além de gerar um instantâneo quando um snappoint for atingido, você também pode configurar um snappoint para registrar em log uma mensagem (ou seja, criar um logpoint). Você pode definir logpoints sem a necessidade de reimplantar o aplicativo. Logpoints são executados virtualmente e fazer com que nenhum impacto ou efeitos colaterais para seu aplicativo em execução.

#### <a name="to-create-a-logpoint"></a>Para criar um logpoint

1. Um ícone de snappoint (o azul hexágono) com o botão direito e escolha **configurações**.

1. Na janela de configurações de snappoint, selecione **ações**.

    ![Criar um logpoint](../debugger/media/snapshot-logpoint.png)

1. No **mensagem** campo, você pode inserir a nova mensagem de log para registrar em log. Você também pode avaliar variáveis na sua mensagem de log, colocando-os entre chaves.

    Se você escolher **enviar para a janela de saída**, quando o logpoint for atingido, a mensagem será exibida na janela de ferramentas de diagnóstico.

    ![Logpoint dados na janela diagsession](../debugger/media/snapshot-logpoint-output.png)

    Se você escolher **enviar para log de aplicativo**, quando o logpoint for atingido, a mensagem será exibida em qualquer lugar que você pode ver mensagens de `System.Diagnostics.Trace` (ou `ILogger` no .NET Core), como [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como usar o depurador de instantâneos de máquinas virtuais do Azure e conjuntos de dimensionamento de máquina Virtual do Azure. Você talvez queira ler mais detalhes sobre esse recurso.

> [!div class="nextstepaction"]
> [Perguntas frequentes sobre depuração de instantâneos](../debugger/debug-live-azure-apps-faq.md)