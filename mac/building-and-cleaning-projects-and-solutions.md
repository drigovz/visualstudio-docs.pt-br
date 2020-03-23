---
title: Compilando e Limpando Projetos e Soluções
description: Este artigo descreve como criar um projeto no Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128452"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Compilando e limpando Projetos e Soluções

Siga os passos deste artigo para aprender como construir, reconstruir ou limpar todos os seus projetos em uma solução.

> [!NOTE]
> Este tópico se aplica ao Visual Studio para Mac. Para o Visual Studio no Windows, consulte [Construir e limpar projetos e soluções no Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Para criar, recriar ou limpar uma solução inteira

1. Selecione o nó Solução no **bloco de soluções :**

    ![Selecionando o nó da solução](media/compiling-and-building-image1.png)

2. Selecione o menu **'Construir'** na Barra de Menus e escolha uma das seguintes opções:

    ![selecionando o item de menu criar todos](media/compiling-and-building-image2.png)

    * Escolha **Build All** para compilar os arquivos e componentes dentro do projeto que foram alterados desde a compilação mais recente.

    * Escolha **Reconstruir tudo** para "limpar" a solução e, em seguida, constrói todos os arquivos e componentes do projeto.

    * Escolha **Limpar Tudo** para excluir quaisquer arquivos intermediários e de saída. Com apenas os arquivos de projeto e de componente restantes, novas instâncias dos arquivos de saída e intermediários podem ser criadas.

## <a name="to-build-or-rebuild-a-single-project"></a>Para compilar ou recompilar um único projeto

1. Selecione o projeto no **Solution Pad**.

2. Selecione o menu **Construir** na Barra de Menus.

3. Escolha Build[ProjectName], Rebuild[ProjectName], ou Clean[ProjectName].

## <a name="to-stop-a-build"></a>Para interromper um build

Para parar uma compilação, use uma das seguintes opções:

* Pressione o quadrado vermelho na área de status:

    ![Pressione quadrado vermelho para parar o build](media/compiling-and-building-image3.png)

* Use o item **Stop** no menu **Construir.**

* Pressione **Cmd+Shift+Return**.

## <a name="see-also"></a>Confira também

- [Criar e limpar projetos e soluções (Visual Studio no Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)