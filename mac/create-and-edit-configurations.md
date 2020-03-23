---
title: Criando e Editando Configurações de Build
description: Este artigo descreve como criar configurações de build no Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.openlocfilehash: 26f6e25bfe1284fc31bcd484b905bf5d75c2ba15
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128432"
---
# <a name="creating-and-editing-build-configurations"></a>Criando e editando configurações de build

As configurações de build dão um controle preciso sobre uma compilação que permite criar configurações para atender a diferentes situações de teste e distribuição. Você pode criar configurações de construção para projetos individuais ou em toda a solução.

Você pode criar novas configurações e editar as existentes para projetos e soluções usando o diálogo Opções de Projeto.

>[!NOTE]
>Este tópico se aplica ao Visual Studio para Mac. Para o Visual Studio no Windows, [consulte Como: Criar e editar configurações](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Criando uma configuração de construção de projeto

Para criar uma configuração de compilação de projeto, siga estas etapas:

1. Clique com botão direito do mouse no nó do projeto e selecione **Opções**. Você também pode clicar duas vezes no nó do projeto para trazer à tona a caixa de diálogo Opções de projeto.

2. Na caixa de diálogo Opções do Projeto, selecione **Compilar > Configurações**:

    ![Gerenciador de configurações nas opções do projeto](media/create-and-edit-configurations-image2.png)

3. Selecione **Adicionar** para criar uma nova configuração. Você também pode copiar qualquer uma das configurações existentes.

Depois de criar a configuração, você pode usar a seção **Build** nas Opções de Projeto para adaptar propriedades apropriadas à sua configuração:

![Configurar opções de build](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Criando uma configuração de build da solução

Para criar uma configuração de compilação de soluções, siga estas etapas:

1. Clique com o botão direito do mouse no nó da solução e selecione **Opções**. Você também pode clicar duas vezes no nó de solução para trazer à tona a caixa de diálogo Opções de solução.

2. Na caixa de diálogo Opções da Solução, selecione **Compilar > Configurações**:

    ![Gerenciador de configurações nas opções da solução](media/create-and-edit-configurations-image1.png)

3. Selecione **Adicionar** para criar uma nova configuração. Você também pode copiar qualquer uma das configurações existentes.

Depois de criar a configuração, você pode usar a seção **Construir** da caixa de diálogo Opções de projeto para cada um de seus projetos para adaptar propriedades apropriadas à sua configuração:

![Configurar opções de build](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Renomeando uma configuração de compilação

Para renomear uma configuração, selecione-a na lista de configuração navegando para **criar configurações >** nas opções de projeto ou solução:

![lista de configurações](media/create-and-edit-configurations-image4.png)

Selecione o botão **Renomear**.

![renomear caixa de diálogo](media/create-and-edit-configurations-image5.png)

Em seguida, clique em **OK** para confirmar.

## <a name="related-video"></a>Vídeo relacionados

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Confira também

- [Criar e editar configurações de build (Visual Studio no Windows)](/visualstudio/ide/how-to-create-and-edit-configurations)