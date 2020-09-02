---
title: Vincular elementos de modelo e itens de trabalho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee4fea9e3fb1d5b4d27b1d520ac2ab036747f73d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657626"
---
# <a name="link-model-elements-and-work-items"></a>Vincular elementos de modelo e itens de trabalho
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rastreie tarefas, casos de teste, bugs, requisitos, problemas e outros trabalhos relacionados ao seu modelo vinculando elementos de modelo no Visual Studio e itens de trabalho em Team Foundation Server ou Visual Studio Team Services. Anexe documentos a itens de trabalho vinculados para associá-los a elementos de modelo.

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Você deve usar Team Explorer para criar e abrir links. Verifique se o projeto e os diagramas de modelagem têm controle de versão de forma que outras pessoas possam abrir diagramas vinculados.

 Por exemplo, é possível vincular:

- Um item de trabalho de histórico do usuário e um diagrama de atividade para mostrar como realizar o histórico como uma sequência de operações

- Um caso de uso em um diagrama de caso de uso e em itens de trabalho de caso de teste para verificar se o caso uso está implementado corretamente

- Um atributo em uma classe em um diagrama de classes UML e em um item de trabalho de bug para mostrar um erro na implementação do atributo

- Um componente em um diagrama de componente e em um item de trabalho de tarefa para acompanhar o desenvolvimento do componente. Essa tarefa costuma ser dividida em tarefas menores

  É possível vincular itens de trabalho a qualquer elemento selecionado em diagramas de modelagem ou no Gerenciador de Modelos UML, como estes itens:

- Todos os elementos em modelo UML como, por exemplo, classes UML, linhas da vida, casos de uso, subsistemas, atividades, nós de objeto, componentes, interfaces

- Todas as relações em modelos UML como, por exemplo, associações, generalizações, dependências, fluxos, mensagens

- Partes de elementos como, por exemplo, os atributos e as operações de classes, as ocorrências de execução das linhas de vida, os PINs de entrada e saída das atividades, além das partes e das portas de componentes

- Camadas e dependências de camada

- Comentários e links de comentário

- Diagramas. Para selecionar um diagrama, escolha uma parte em branco do diagrama.

> [!WARNING]
> Você já deve estar conectado ao SCC (controle de código-fonte) do TFS para criar ou vincular a um item de trabalho. Se você tentar abrir uma conexão com um outro TFS SCC, o Visual Studio fechará a solução atual automaticamente. Verifique se você já está conectado ao SCC apropriado antes de tentar criar ou vincular a um item de trabalho. Em versões posteriores do Visual Studio, os comandos de menu não estarão disponíveis se você não estiver conectado a um SCC.

- [Conectar-se a um projeto de equipe](#ConnectTFS)

- [Vincular um elemento de modelo a um novo item de trabalho](#LinkNew)

- [Vincular um elemento de modelo a um item de trabalho existente](#LinkExisting)

- [Vincular itens de trabalho a um elemento de modelo](#OpenWorkItem)

- [Exibir elementos de modelo a um item de trabalho](#ViewLinkedModels)

- [Excluir links entre elementos de modelo e itens de trabalho](#RemoveLinks)

- [Solução de problemas](#Troubleshooting)

## <a name="connect-to-a-team-project"></a><a name="ConnectTFS"></a> Conectar-se a um projeto de equipe
 Primeiro, você deve se conectar ao seu projeto de equipe para criar, exibir ou remover links.

1. No menu **equipe** , escolha **gerenciar conexões** para mostrar a janela de Team Explorer.

2. Se o projeto correto não aparecer, em Team Explorer, escolha **gerenciar conexões** e, em seguida, escolha **conectar-se ao projeto de equipe**. Em seguida, escolha os projetos corretos ou o servidor, se necessário.

3. Em **Team Explorer**, escolha o projeto no qual você deseja criar, vincular ou exibir itens de trabalho.

## <a name="link-a-model-element-to-a-new-work-item"></a><a name="LinkNew"></a> Vincular um elemento de modelo a um novo item de trabalho

1. Verifique se você está conectado à instância do TFS que deseja usar.

2. No diagrama de modelagem ou no **Gerenciador de modelos UML**, abra o menu de atalho do elemento modelo.

3. Escolha **Criar item de trabalho** e o tipo de item de trabalho que você deseja criar.

4. No formulário do item de trabalho, preencha os campos. Escolha **salvar item de trabalho**.

     O Visual Studio vincula o elemento de modelo ao novo item de trabalho. Um ícone é exibido em ou próximo ao elemento de modelo.

> [!WARNING]
> Você já deve estar conectado ao SCC (controle de código-fonte) do TFS para criar ou vincular a um item de trabalho. Se você tentar abrir uma conexão com um outro TFS SCC, o Visual Studio fechará a solução atual automaticamente. Verifique se você já está conectado ao SCC apropriado antes de tentar criar ou vincular a um item de trabalho. Em versões posteriores do Visual Studio, os comandos de menu não estarão disponíveis se você não estiver conectado a um SCC.

## <a name="link-a-model-element-to-an-existing-work-item"></a><a name="LinkExisting"></a> Vincular um elemento de modelo a um item de trabalho existente
 Ao vincular elementos de modelo a itens de trabalho, comece pelo elemento de modelo, e não pelo item de trabalho.

1. Verifique se você está conectado à instância do TFS que deseja usar.

2. No diagrama de modelagem ou no **Gerenciador de modelos UML**, abra o menu de atalho do elemento modelo. Escolha o **link para o item de trabalho**. Em seguida, selecione seu projeto no campo **projeto** .

3. Escolha um ou mais itens de trabalho para vincular ao elemento de modelo seguindo uma destas etapas:

    - Escolha uma consulta na **consulta salva**.

    - Digite as IDs de um ou mais itens de trabalho, separados por espaços, em **IDs**.

    - Digite uma palavra ou frase no **título contém**.

4. Escolha **Localizar**.

5. Na lista de itens de trabalho, selecione o item de trabalho ou os itens de trabalho que você deseja vincular.

     Quando terminar, a propriedade **itens de trabalho** do elemento modelo mostrará um número maior do que antes. Um ícone também é exibido em ou próximo ao elemento de modelo.

> [!WARNING]
> Você já deve estar conectado ao SCC (controle de código-fonte) do TFS para criar ou vincular a um item de trabalho. Se você tentar abrir uma conexão com um outro TFS SCC, o Visual Studio fechará a solução atual automaticamente. Verifique se você já está conectado ao SCC apropriado antes de tentar criar ou vincular a um item de trabalho. Em versões posteriores do Visual Studio, os comandos de menu não estarão disponíveis se você não estiver conectado a um SCC.

## <a name="view-work-items-linked-to-a-model-element"></a><a name="OpenWorkItem"></a> Exibir itens de trabalho vinculados a um elemento de modelo

1. No **Team Explorer**, verifique se você está conectado ao projeto de equipe onde os itens de trabalho estão vinculados ao elemento de modelo.

2. No diagrama de modelagem ou no **Gerenciador de modelos UML**, abra o menu de atalho do elemento modelo. Escolha **Exibir itens de trabalho** para exibir a lista de itens de trabalho vinculados.

    > [!NOTE]
    > Somente os itens de trabalho do servidor conectado são exibidos. Se você não vir nenhum item de trabalho, verifique se você está conectado ao servidor correto em **Team Explorer**.

## <a name="view-model-elements-linked-to-a-work-item"></a><a name="ViewLinkedModels"></a> Exibir elementos de modelo vinculados a um item de trabalho
 Você pode exibir os diagramas de modelagem e os elementos que estão vinculados a um item de trabalho no Visual Studio Team Services e no Team Foundation Server 2012 ou posterior. Por exemplo, um item de trabalho talvez esteja vinculado a modelos de classe que mostram o design de novas classes que serão implementadas.

1. No **Team Explorer**, verifique se você está conectado ao projeto de equipe em que os elementos de modelo estão vinculados ao item de trabalho.

    > [!NOTE]
    > Só é possível usar o Team Explorer, e não o Team Web Access, para exibir elementos de modelo vinculados. Verifique se o workspace está mapeado para o projeto de modelagem que contém os diagramas ou os elementos de modelagem. Se não tiver um workspace, você deverá criá-lo. Consulte [solução de problemas](#Troubleshooting) e [criar e trabalhar com espaços de trabalho](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).

2. Abra o item de trabalho, escolha **links**. Em **link de modelo**, abra o menu de atalho para o elemento de modelo vinculado. Escolha **Abrir item vinculado**.

     ![Abrir elemento de modelo vinculado de um item de trabalho](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")

## <a name="delete-links-between-model-elements-and-work-items"></a><a name="RemoveLinks"></a> Excluir links entre elementos de modelo e itens de trabalho
 Remova um item de trabalho vinculado com base no elemento de modelo. Isso remove corretamente o link recíproco para esse elemento de modelo do item de trabalho. Do contrário, se você começar pelo item de trabalho, o link recíproco do elemento de modelo para o item de trabalho não será excluído.

1. No diagrama de modelagem ou no **Gerenciador de modelos UML**, abra o menu de atalho do elemento modelo.

2. Escolha **remover itens de trabalho**.

     \- ou –

    1. Escolha **Propriedades**e, em seguida, **itens de trabalho** em que o número de itens de trabalho vinculados é exibido.

    2. Na propriedade **itens de trabalho** , escolha o botão de reticências **[...]**.

        > [!NOTE]
        > Somente itens de trabalho no servidor atual são exibidos. Se a lista estiver vazia, mas o número de itens de trabalho não for zero, verifique se você está conectado ao servidor correto em **Team Explorer**.

3. Em **remover links para itens de trabalho**, desmarque os itens selecionados que você deseja desvincular. Escolha **OK**.

## <a name="troubleshooting"></a><a name="Troubleshooting"></a> Solução de problemas

|**Problema**|**Causa possível**|**Resolução**|
|---------------|------------------------|--------------------|
|Não é possível encontrar o elemento de modelo que você deseja vincular.|O elemento talvez esteja em um diagrama em um projeto de modelagem que esteja em [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Você talvez não tenha um workspace que seja mapeado para o diagrama.|Mapeie o workspace para o projeto e o diagrama de modelagem. Se não tiver um workspace, você deverá criá-lo.<br /><br /> A mensagem de erro exibida para esse problema contém o caminho que é possível usar para mapear o workspace.<br /><br /> Consulte [criar e trabalhar com espaços de trabalho](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|
|Não é possível encontrar o elemento de modelo vinculado.|O elemento vinculado talvez esteja em um diagrama que foi movido, renomeado ou excluído.|1. no item de trabalho, exclua o link para o elemento de modelo.<br />2. Crie um novo link do item de trabalho para o elemento de modelo.|
|O item de trabalho não tem elementos de modelo vinculados esperados.|Um item de trabalho mostra apenas um elemento de camada vinculado caso o vínculo tenha sido criado com base no item de trabalho. A equipe não usa [!INCLUDE[esprscc](../includes/esprscc-md.md)], o caminho local dos diagramas será usado para criar os links. Se o projeto de modelagem e seus diagramas estiverem em [!INCLUDE[esprscc](../includes/esprscc-md.md)], todos os membros da equipe que podem acessar o projeto poderão exibir os elementos vinculados em itens de trabalho.|Tente atualizar o item de trabalho.|
|A exclusão de um link para um elemento de modelo de um item de trabalho não exclui o link do elemento de modelo para o item de trabalho.||Exclua o link para o item de trabalho começando pelo elemento de modelo.|

## <a name="see-also"></a>Consulte Também
 [Editar modelos e diagramas UML](../modeling/edit-uml-models-and-diagrams.md) [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md)
