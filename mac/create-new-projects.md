---
title: Criando novos Projetos e Soluções
description: Este artigo descreve como criar projetos e soluções no Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2020
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 7ee9b23f9ede12a353f6c6fdc0f578d7f78a772c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493288"
---
# <a name="create-a-new-project"></a>Criar um novo projeto

## <a name="opening-the-project-creation-dialog"></a>Como abrir a caixa de diálogo de criação do projeto

Há várias maneiras de criar um projeto no Visual Studio para Mac. Quando você abre o Visual Studio para Mac pela primeira vez, a janela iniciar é mostrada. A partir daqui, você pode escolher **novo** , que leva você para a tela de criação do projeto.

> [!TIP]
> Além disso, na janela iniciar, você também pode abrir e Pesquisar projetos e soluções recentes. Abra também os projetos recentes acessando a barra de menus e escolhendo **Arquivo > Soluções Recentes**

![Iniciar janela com criar novo projeto](media/first-run-project.png)

Se o Visual Studio para Mac já estiver aberto com uma solução carregada, crie uma solução acessando a barra de menus e escolhendo **Arquivo > Nova Solução**. A criação de uma nova solução dessa maneira fecha a solução que já está carregada.

## <a name="creating-a-new-project"></a>Criando um novo projeto

A caixa de diálogo **Novo Projeto** , por padrão, mostrará os modelos usados recentemente classificados pelos *usados mais recentemente*.

Caso você não deseje usar um modelo recente, escolha um nas categorias à esquerda da caixa de diálogo. Cada categoria contém vários modelos de projeto para sua escolha. Ao clicar em um tipo de projeto, você poderá ver uma descrição no lado direito da tela.

![Tela do novo projeto](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Como configurar o novo projeto

Depois que você escolher um modelo de projeto, as telas a seguir orientarão você em todas as etapas de configuração necessárias para configurar o projeto; isso pode variar por tipo de projeto.

Todos os projetos exigem um novo projeto, juntamente com um local para armazenar os arquivos. Se o projeto fizer parte de uma nova solução, em vez de adicioná-lo a uma solução existente, um nome de solução também será necessário.

Opcionalmente, neste estágio, você também pode configurar opções de controle do código-fonte do Git. A imagem a seguir é um exemplo da etapa de configuração final de um projeto .NET Core:

![Como configurar um novo projeto](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Como adicionar projetos adicionais a uma solução

Você pode adicionar mais projetos a uma solução clicando com o botão direito do mouse na solução na **janela da solução** e escolhendo **Adicionar > adicionar novo projeto** ou **Adicionar > adicionar um projeto existente**.

A adição de um novo projeto orientará você pela criação do projeto, conforme mostrado em [Como configurar o novo projeto](#configuring-your-new-project).

A opção de adicionar um projeto existente permitirá que você procure um projeto existente no computador e adicione-o à solução.

## <a name="see-also"></a>Confira também

- [Criar soluções e projetos (Visual Studio no Windows)](/visualstudio/ide/creating-solutions-and-projects)
