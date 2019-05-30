---
title: Depurar máquinas de virtuais do Azure do ASP.NET e conjuntos de dimensionamento
description: Saiba como configurar o snappoints e exibir instantâneos com o Depurador de Instantâneos.
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
ms.openlocfilehash: 38cf8b5c2af174b026c507fc5c668f826707adf3
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263355"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Depurar aplicativos ASP.NET dinâmicos em máquinas virtuais do Azure e conjuntos de dimensionamento de máquinas virtuais do Azure usando o Depurador de Instantâneos

O Depurador de Instantâneos tira um instantâneo de seus aplicativos em produção quando o código no qual você está interessado é executado. Para instruir o depurador a tirar um instantâneo, defina snappoints e logpoints em seu código. O depurador permite ver exatamente o que deu errado sem afetar o tráfego do seu aplicativo de produção. O Depurador de Instantâneo pode ajudar a reduzir drasticamente o tempo que leva para resolver problemas que ocorrem em ambientes de produção.

Snappoints e logpoints são semelhantes aos pontos de interrupção. Porém, ao contrário dos pontos de interrupção, os snappoints não interrompem o aplicativo quando atingidos. Normalmente, a captura de um instantâneo em um snappoint leva 10 a 20 milissegundos.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Iniciar o Depurador de Instantâneos
> * Definir um snappoint e exibir um instantâneo
> * Definir um logpoint

## <a name="prerequisites"></a>Pré-requisitos

* Depurador de instantâneos para máquinas virtuais do Azure (VM) e conjuntos de dimensionamento de máquina Virtual do Azure só está disponível para o Visual Studio 2019 Enterprise ou superior com o **carga de trabalho de desenvolvimento do Azure**. (Na guia **Componentes individuais**,é possível encontrá-lo em **Depuração e testes** > **Depurador de instantâneos**).

    Se ainda não estiver instalado, instale [Visual Studio Enterprise de 2019](https://visualstudio.microsoft.com/vs/).

* Coleta de instantâneo está disponível para os seguintes aplicativos web do Azure conjuntos de dimensionamento de máquinas virtuais Machines\Virtual:
  * Aplicativos ASP.NET em execução no .NET Framework 4.6.1 ou posterior.
  * Aplicativos ASP.NET Core em execução no .NET Core 2.0 ou posterior no Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Abra seu projeto e iniciar o Depurador de Instantâneos

1. Abra o projeto em que você gostaria de fazer a depuração de instantâneos.

    > [!IMPORTANT]
    > A depuração de instantâneo, você precisará abrir o *mesma versão do código-fonte* que é publicado para o serviço do Azure Virtual Machine\Virtual máquina conjunto de dimensionamento.

1. Escolha **Depurar > Anexar Depurador de Instantâneos...** . Selecione uma conta de armazenamento do Azure e o Azure Virtual Machine\Virtual máquina conjunto de dimensionamento de seu aplicativo web é implantado em e, em seguida, clique em **Attach**.

      ![Iniciar o depurador de instantâneos no menu Depurar](../debugger/media/snapshot-debug-menu-attach.png)

      ![Selecionar recurso do Azure](../debugger/media/snapshot-select-azure-resource-vm.png) 

    > [!IMPORTANT]
    > Na primeira vez que você selecionar **Anexar Depurador de Instantâneos** para sua VM, o IIS será reiniciado automaticamente.
    > Na primeira vez que você seleciona **anexar o depurador de instantâneo** para seus conjuntos de dimensionamento de máquina Virtual, requer a atualização manual de cada instância dos conjuntos de escala de máquina Virtual.

    Os metadados para os **Módulos** não serão ativados inicialmente; navegue até o aplicativo Web, e o botão **Iniciar Coleção** ficará ativo. O Visual Studio agora está no modo de depuração de instantâneos.

   ![Modo de depuração de instantâneos](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > A extensão de site do Application Insights também dá suporte à depuração de instantâneos. Se você encontrar uma mensagem de erro "extensão de site desatualizada", veja [dicas de solução de problemas e problemas conhecidos da depuração de instantâneos](../debugger/debug-live-azure-apps-troubleshooting.md) para atualizar os detalhes.
    > Para VMSS o usuário é necessário para atualizar manualmente as instâncias em seus conjuntos de dimensionamento de máquina Virtual depois de anexar o depurador de instantâneo pela primeira vez.

   O **módulos** janela mostra quando todos os módulos de tem carregado para o Azure Virtual Machine\Virtual máquina conjunto de dimensionamento (escolher **Depurar > Windows > módulos** para abrir essa janela).

   ![Verificar a janela Módulos](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Definir um snappoint

1. No editor de códigos, clique na medianiz esquerda ao lado de uma linha de código de seu interesse para definir um snappoint. Verifique se esse é o código que você sabe que será executado.

   ![Definir um snappoint](../debugger/media/snapshot-set-snappoint.png)

1. Clique em **Iniciar Coleção** para ativar o snappoint.

   ![Ativar o snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Não é possível depurar ao exibir um instantâneo, mas você pode colocar vários snappoints em seu código para seguir a execução em diferentes linhas de código. Se você tiver vários snappoints em seu código, o Depurador de Instantâneos garantirá que os instantâneos correspondentes sejam da mesma sessão do usuário final. O Depurador de Instantâneos fará isso mesmo se houver muitos usuários acessando seu aplicativo.

## <a name="take-a-snapshot"></a>Capturar um instantâneo

Quando um snappoint é ativado, ele captura um instantâneo sempre que a linha de código em que o snappoint se encontra é executada. Essa execução pode ser causada por uma solicitação real em seu servidor. Para forçar o snappoint a ser atingido, vá para a exibição de navegador do seu site e realize as ações necessárias que fazem com que o snappoint seja atingido.

## <a name="inspect-snapshot-data"></a>Inspecionar dados de instantâneo

1. Quando o snappoint for atingido, um instantâneo será exibido na janela de Ferramentas de Diagnóstico. Para abrir essa janela, escolha **Depurar > Janelas > Mostrar Ferramentas de Diagnóstico**.

   ![Abrir um snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Clique duas vezes o snappoint para abrir o instantâneo no editor de códigos.

   ![Inspecionar dados de instantâneo](../debugger/media/snapshot-inspect-data.png)

   Nessa exibição, você pode passar o mouse sobre as variáveis para exibir DataTips; use as janelas **Locais**, **Inspeções** e **Pilha de Chamadas** e também avalie expressões.

    O site em si ainda fica ativo, e os usuários finais não são afetados. Apenas um instantâneo é capturado por snappoint por padrão: após a captura de um instantâneo, o snappoint é desativado. Se você quiser capturar outro instantâneo no snappoint, poderá ativar o snappoint novamente clicando em **Atualizar Coleção**.

Você também pode adicionar mais snappoints ao seu aplicativo e ativá-los com o botão **Atualizar Coleção**.

**Precisa de ajuda?** Consulte as páginas [Solução de problemas e problemas conhecidos](../debugger/debug-live-azure-apps-troubleshooting.md) e [Perguntas frequentes sobre depuração de instantâneo](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Definir um snappoint condicional

Se você tiver dificuldades para recriar um estado específico em seu aplicativo, considere se o uso de um snappoint condicional pode ajudar. Os snappoints condicionais ajudam a evitar a captura de um instantâneo até que o aplicativo entre em um estado desejado, como quando uma variável tem um valor específico que você deseja inspecionar. É possível definir condições usando expressões, filtros ou contagens de ocorrências.

#### <a name="to-create-a-conditional-snappoint"></a>Para criar um snappoint condicional

1. Clique com o botão direito do mouse em um ícone de snappoint (a bola vazada) e escolha **Configurações**.

   ![Escolha Configurações](../debugger/media/snapshot-snappoint-settings.png)

1. Na janela de configurações de snappoint, digite uma expressão.

   ![Digitar uma expressão](../debugger/media/snapshot-snappoint-conditions.png)

   Na ilustração anterior, o instantâneo é criado para o snappoint somente quando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Definir um logpoint

Além de tirar um instantâneo quando um snappoint é atingido, também é possível configurar um snappoint para registrar uma mensagem em log (ou seja, criar um logpoint). Você pode definir logpoints sem a necessidade de reimplantar o aplicativo. Logpoints são executados virtualmente e não causam impacto ou efeitos colaterais ao seu aplicativo em execução.

#### <a name="to-create-a-logpoint"></a>Para criar um logpoint

1. Clique com o botão direito em um ícone de snappoint (o hexágono azul) e escolha **Configurações**.

1. Na janela de configurações de snappoint, selecione **Ações**.

    ![Criar um logpoint](../debugger/media/snapshot-logpoint.png)

1. No campo **Mensagem**, você pode inserir a nova mensagem de log para registrar em log. Você também pode avaliar variáveis na sua mensagem de log colocando-as entre chaves.

    Se você escolher **Enviar para a Janela de Saída**, quando o logpoint for atingido, a mensagem será exibida na janela de Ferramentas de Diagnóstico.

    ![Dados de logpoint na janela Ferramentas de Diagnóstico](../debugger/media/snapshot-logpoint-output.png)

    Se você escolher **Enviar para log do aplicativo**, quando o logpoint for atingido, a mensagem será exibida em qualquer lugar em que você possa ver mensagens de `System.Diagnostics.Trace` (ou `ILogger` no .NET Core), como [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como usar o Depurador de Instantâneos para Máquinas Virtuais e Conjuntos de Dimensionamento de Máquinas Virtuais do Azure. Talvez você queira ler mais detalhes sobre esse recurso.

> [!div class="nextstepaction"]
> [Perguntas frequentes sobre depuração de instantâneos](../debugger/debug-live-azure-apps-faq.md)
