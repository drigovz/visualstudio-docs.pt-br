---
title: Trabalhando com Git
description: Usando o Git no Visual Studio para Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: dc865ec593f53149d9c004f252015def32325d18
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616171"
---
# <a name="working-with-git"></a>Trabalhando com Git

O Git é um sistema de controle de versão distribuído que permite que as equipes trabalhem nos mesmos documentos simultaneamente. Isso significa que há um servidor central que contém todos os arquivos, mas quando um repositório passar por check-out nessa fonte central, todo o repositório será clonado para o computador local.

As seções a seguir explorarão como o Git pode ser usado para controle de versão no Visual Studio para Mac.

## <a name="git-version-control-menu"></a>Menu de controle de versão do Git

A imagem a seguir ilustra as opções fornecidas pelo Visual Studio para Mac pelo item de menu de Controle de Versão:

![Item de menu de Controle de Versão](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Push e Pull

Push e pull são duas das ações mais usadas no Git. Para sincronizar as alterações que outras pessoas fizeram no repositório remoto, você deverá **Efetuar pull** de lá. Isso é feito no Visual Studio para Mac selecionando **Controle de versão > Atualizar solução**.

Depois de atualizar, examinar e confirmar seus arquivos, você deverá **Efetuar push** neles para o repositório remoto a fim de permitir que outros usuários acessem suas alterações. Isso é feito no Visual Studio para Mac selecionando **Controle de versão > Efetuar push nas alterações**. Isso exibirá a caixa de diálogo de Push, permitindo que você exiba as alterações confirmadas e selecione o branch para o qual o push será efetuado:

![Caixa de diálogo mostrando o branch de confirmação](media/version-control-gitPush.png)

Você também poderá Confirmar e Efetuar push nas alterações ao mesmo tempo por meio da caixa de diálogo Confirmar:

![Opção que mostra como confirmar e efetuar push ao mesmo tempo.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Acusar, Registrar em log e Mesclar

Na parte inferior da janela são exibidas cinco guias, conforme ilustrado abaixo:

![Guias de Controle de versão](media/version-control-gitTabs.png)

Elas permitem executar as seguintes ações:

* **Código-fonte** – Exibe o arquivo de código-fonte.
* **Alterações** – Exibe a alteração no código entre o arquivo local e o arquivo de base. Você também pode comparar versões diferentes do arquivo em diferentes hashes:

    ![Guia Alterações](media/version-control-gitChange.png)

* **Acusar** – Exibe o nome do usuário associado a cada seção de código.
* **Registrar em log** – Exibe todas as confirmações, horas, datas, mensagens e usuários que são responsáveis pelo arquivo:

    ![Guia Log](media/version-control-gitLog.png)

* **Mesclar** – Pode ser usado em caso de conflito de mesclagem ao confirmar seu trabalho. Mostra uma representação visual das alterações feitas por você e por outros desenvolvedores, permitindo que você combine as duas seções de código corretamente.

## <a name="switching-branches"></a>Alternar os branches

Por padrão, a primeira ramificação criada em um repositório é conhecida como a ramificação **principal** . Não há tecnicamente nada diferente entre a ramificação principal e qualquer outra, mas a ramificação principal é aquela que costuma ser considerada em equipes de desenvolvimento como o Branch ' Live ' ou ' Production '.

Uma linha independente de desenvolvimento pode ser criada por ramificação fora do principal (ou de qualquer outra ramificação, para esse assunto). Isso fornece uma nova versão da ramificação principal em um ponto no tempo, permitindo o desenvolvimento independentemente do que é "Live". É comum usar branches dessa forma para recursos no desenvolvimento de software

Os usuários podem criar tantos branches quanto desejarem para cada repositório, porém é recomendado que, após terminar de usar um branch, ele seja excluído para manter o repositório organizado.

Branches são exibidos no Visual Studio para Mac navegando para **Controle de versão > Gerenciar branches e remotos...**:

![Exibição Branches](media/version-control-gitBranch2.png)

Alterne para outro branch selecionando-o na lista e pressionando o botão **Alternar para o branch**.

Para criar um novo branch, selecione o botão **Novo** na caixa de diálogo Configuração de repositório Git. Digite o nome do novo branch:

![Criar um novo branch](media/version-control-gitBranch.png)

Você também pode definir um branch remoto como seu branch de _acompanhamento_. Leia mais sobre o acompanhamento de branches na [Documentação do Git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Consulte o Branch atual na janela da solução, ao lado do nome do projeto:

 ![Branch atual exibido na janela de solução](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Revisar e confirmar

Para examinar as alterações nos arquivos, use as guias Alterações, Acusar, Registro em log e Mesclar em cada documento, ilustrado anteriormente neste tópico.

Examine todas as alterações no seu projeto navegando para o item de menu **Controle de versão > Examinar solução e confirmar**:

![Exibição Examinar código](media/version-control-gitReviewCommit.png)

Isso permite exibir todas as alterações em cada arquivo de um projeto com a opção de Reverter, Criar um Patch ou Confirmar.

Para confirmar um arquivo para o repositório remoto, pressione **confirmar**, insira uma mensagem de confirmação e confirme com o botão confirmar:

![Confirmando um arquivo](media/version-control-gitCommit.png)

Depois de ter confirmado suas alterações, efetue push nelas para o repositório remoto para permitir que outros usuários possam vê-los.

## <a name="related-video"></a>Vídeo relacionados

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Confira também

* [Compartilhar seu código com o Visual Studio 2017 e o GIT do Azure Repos](/azure/devops/repos/git/share-your-code-in-git-vs-2017)
