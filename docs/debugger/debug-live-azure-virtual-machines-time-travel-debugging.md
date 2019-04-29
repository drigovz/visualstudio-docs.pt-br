---
title: Tempo viagem depuração ao vivo ASP.NET máquinas virtuais do Azure
description: Saiba como gravar e reproduzir aplicativos ASP.NET dinâmicos em máquinas virtuais do Azure usando o depurador de instantâneo.
ms.custom: ''
ms.date: 04/11/2019
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
ms.openlocfilehash: 3a81f6aa138b361a44a272ebda3557d27a914c64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854217"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Gravar e reproduzir aplicativos ASP.NET dinâmicos em máquinas virtuais do Azure usando o depurador de instantâneo

A visualização de depuração de viagem de tempo (TTD) no Visual Studio Enterprise oferece a capacidade de registrar um aplicativo Web em execução em uma máquina Virtual do Azure (VM) e, em seguida, com precisão reconstruir e repetir o caminho de execução. TTD integra-se com o depurador de instantâneos e permite a você para retroceder e repetir a cada linha de código qualquer número de vezes que deseja, ajudando você a isolar e identificar problemas que podem ocorrer somente em ambientes de produção.

Capturar uma gravação de TTD não interromperá o aplicativo. No entanto, a gravação de TDD adiciona sobrecarga significativa ao seu processo de execução, deixando ele lento com base em fatores que incluem o tamanho do processo e o número de threads ativos.

Esse recurso está em versão prévia da versão do Visual Studio de 2019 com uma licença ao vivo vá.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Iniciar o depurador de instantâneos com a depuração em tempo de viagem habilitado
> * Defina um snappoint e coletar de um tempo de viagem gravação
> * Inicie a depuração de um tempo de gravação de viagem

## <a name="prerequisites"></a>Pré-requisitos

* Depuração em tempo de viagem para as máquinas virtuais (VM) do Azure só está disponível para o Visual Studio 2019 Enterprise ou superior com o **carga de trabalho de desenvolvimento do Azure**. (Na guia **Componentes individuais**,é possível encontrá-lo em **Depuração e testes** > **Depurador de instantâneos**).

    Se ainda não estiver instalado, instale [Visual Studio Enterprise de 2019](https://visualstudio.microsoft.com/vs/).

* Depuração em tempo de viagem está disponível para os seguintes aplicativos web do Azure VM:
  * Aplicativos do ASP.NET (AMD64) em execução no .NET Framework 4.8 ou posterior.

## <a name="open-your-project-and-start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Abra seu projeto e iniciar o depurador de instantâneos com a depuração em tempo de viagem habilitado

1. Abra o projeto para o qual você gostaria de coletar um tempo de gravação de viagem.

    > [!IMPORTANT]
    > Para iniciar o TTD, você precisará abrir o *mesma versão do código-fonte* que é publicado ao seu serviço de VM do Azure.

1. Escolha **Depurar > Anexar Depurador de Instantâneos...**. Selecione a VM do Azure que seu aplicativo web é implantado e uma conta de armazenamento do Azure. Selecione o **habilitar a depuração em tempo de viagem** opção de visualização e, em seguida, clique em **Attach**.

      ![Selecionar recurso do Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > Na primeira vez que você selecionar **Anexar Depurador de Instantâneos** para sua VM, o IIS será reiniciado automaticamente.

    Os metadados para o **módulos** não for ativado inicialmente. Navegue até o aplicativo web e o **iniciar coleta** botão, em seguida, se torna ativo. O Visual Studio agora está no modo de depuração de instantâneos.

   ![Modo de depuração de instantâneos](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > A extensão de site do Application Insights também dá suporte à depuração de instantâneos. Se você encontrar uma mensagem de erro "extensão de site desatualizada", veja [dicas de solução de problemas e problemas conhecidos da depuração de instantâneos](../debugger/debug-live-azure-apps-troubleshooting.md) para atualizar os detalhes.

   O **módulos** janela mostra quando todos os módulos são carregados para a VM do Azure (escolher **Depurar > Windows > módulos** para abrir essa janela).

   ![Verificar a janela Módulos](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Defina um snappoint e coletar de um tempo de viagem gravação

1. No editor de códigos, clique na medianiz esquerda em um método que você está interessado para definir um snappoint. Verifique se esse é o código que você sabe que será executado.

   ![Definir um snappoint](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Clique com botão direito no ícone de snappoint (a bola vazio) e escolha **ações**. No **configurações de instantâneo** janela, clique no **ação** caixa de seleção. Em seguida, clique o **coletar um rastreamento de viagem de tempo até o final desse método** caixa de seleção.

   ![Coletar um rastreamento de viagem de tempo até o final do método](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Clique em **Iniciar Coleção** para ativar o snappoint.

   ![Ativar o snappoint](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Capturar um instantâneo

Quando um snappoint for ativado, ele captura um instantâneo sempre que executa a linha de código em que o snappoint é colocado. Essa execução pode ser causada por uma solicitação real em seu servidor. Para forçar o snappoint a ser atingido, vá para a exibição de navegador do seu site e realize as ações necessárias que fazem com que o snappoint seja atingido.

## <a name="start-debugging-a-time-travel-recording"></a>Inicie a depuração de um tempo de gravação de viagem

1. Quando o snappoint for atingido, um instantâneo será exibido na janela de Ferramentas de Diagnóstico. Para abrir essa janela, escolha **Depurar > Janelas > Mostrar Ferramentas de Diagnóstico**.

   ![Abrir um snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Clique no link de instantâneo de modo de exibição para abrir a viagem de tempo gravando no editor de códigos.
  
   Você pode executar todas as linhas de código gravado pelo TTD usando o **Continue** e **Inverter continuar** botões. Além disso, o **Debug** barra de ferramentas pode ser usada para **Mostrar próxima instrução**, **intervir**, **Step Over**, **depuração circular**, **Etapa de volta para o**, **percorrer novamente**, **etapa de volta**.

   ![Iniciar a depuração](../debugger/media/time-travel-debugging-step-commands.png)

   Você também pode usar o **Locals**, **inspeções**, e **pilha de chamadas** windows e também avaliar expressões.

   ![Inspecionar dados de instantâneo](../debugger/media/time-travel-debugging-start-debugging.png)

    O site em si ainda está ao vivo e os usuários finais não são afetados por qualquer atividade TTD subsequente. Apenas um instantâneo é capturado por snappoint por padrão: após a captura de um instantâneo, o snappoint é desativado. Se você quiser capturar outro instantâneo no snappoint, poderá ativar o snappoint novamente clicando em **Atualizar Coleção**.

**Precisa de ajuda?** Consulte as páginas [Solução de problemas e problemas conhecidos](../debugger/debug-live-azure-apps-troubleshooting.md) e [Perguntas frequentes sobre depuração de instantâneo](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Definir um snappoint condicional

Se você tiver dificuldades para recriar um estado específico em seu aplicativo, considere se o uso de um snappoint condicional pode ajudar. Snappoints condicional ajuda a que evitar a coleta de um tempo de viagem gravação até que o aplicativo entra em um estado desejado, como quando uma variável tem um valor específico que você deseja inspecionar. [Você pode definir condições de uso de expressões, filtros, ou contagens de ocorrências de](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como coletar uma viagem de tempo gravando para máquinas virtuais do Azure. Você talvez queira ler mais detalhes sobre o depurador de instantâneo.

> [!div class="nextstepaction"]
> [Perguntas frequentes sobre depuração de instantâneos](../debugger/debug-live-azure-apps-faq.md)