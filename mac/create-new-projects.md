---
title: Criando novos Projetos e Soluções
description: Este artigo descreve como criar projetos e soluções no Visual Studio para Mac
author: conceptdev
ms.author: crdun
ms.date: 04/02/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: ae69c71b3b70e950bc0b58b1c34335f3a52529df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62983603"
---
# <a name="creating-new-projects-and-solutions"></a>Criando novos Projetos e Soluções

## <a name="creating-new-projects-and-solutions-from-a-template"></a>Criando novos Projetos e Soluções com base em um modelo

Soluções podem ser criadas a qualquer momento usando um modelo predefinido. Começando com o Visual Studio 2019 para Mac, escolha **Novo** da janela de início. Como alternativa, navegue até  **Arquivo > Nova Solução**. Selecione as plataformas necessárias e, em seguida, o modelo necessário:

![Criar novas Soluções](media/projects-and-solutions-image0.png)

Isso criará uma solução que pode conter um ou vários projetos, dependendo do tipo de modelo escolhido.

É possível navegar pelo gerenciador de soluções usando as ações de contexto ou a barra de menus.

Para adicionar um novo Projeto à solução, clique com o botão direito no nome da Solução e selecione **Adicionar > Adicionar novo projeto** para exibir a caixa de diálogo Novo projeto:

![Adicionar um novo projeto](media/projects-and-solutions-image4.png)

Esse método para adicionar novos projetos pode ser usado para aproveitar os recursos de compartilhamento de código do Xamarin. Adicionar um Projeto Compartilhado ou um modelo de Biblioteca Portátil a uma Solução existente fornece uma maneira de conter qualquer lógica de plataforma cruzada que pode ser usada em todos os outros projetos em uma solução. Para obter mais informações sobre como compilar aplicativos de plataforma cruzada, consulte o [guia relevante](https://developer.xamarin.com/guides/cross-platform/application_fundamentals/code-sharing/).

## <a name="opening-recent-solutions"></a>Abrindo soluções recentes.

A janela de início do Visual Studio exibe uma lista de projetos recentes nos quais você tem trabalhado:

![Seção de soluções recentes na página inicial](media/create-new-projects-recent.png)

Você pode filtrar essa lista usando a Caixa de filtro ou remover itens individuais da lista.

## <a name="see-also"></a>Consulte também

- [Criar soluções e projetos (Visual Studio no Windows)](/visualstudio/ide/creating-solutions-and-projects)