---
title: Gerenciando propriedades de solução e projeto
description: Este artigo descreve como gerenciar as propriedades de projetos e soluções no Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 0c3277df3be22658acf85a4f0607ed9ad0308b5c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492991"
---
# <a name="managing-project-and-solution-properties"></a>Gerenciando propriedades de solução e projeto

## <a name="project-options"></a>Opções do projeto

As opções de projeto são específicas para cada projeto e afetam como ele é escrito, criado e executado. Ao contrário das preferências de Visual Studio para Mac que são configurações específicas do usuário, as opções de projeto são armazenadas no arquivo de projeto (. csproj), para que outros desenvolvedores possam compilar e executar o projeto corretamente. Ter opções de projeto específicas permite que vários desenvolvedores trabalhem no mesmo documento sem comprometer a formatação do arquivo.

Para abrir as opções do projeto no Visual Studio para Mac, clique duas vezes no nome do projeto ou clique com o botão direito do mouse para abrir o menu de contexto e selecione **Opções** :

![Opção no menu de contexto](media/projects-and-solutions-image2.png)

As opções editáveis incluem opções para compilar, executar e definir o código-fonte e o controle de versão.

As opções do projeto são organizadas em cinco categorias diferentes:

* **Geral** – as informações do projeto como Nome, Descrição e Namespace Padrão são definidas aqui, bem como o Local do projeto.
* **Build** -usado para definir ou alterar perfis PCL para bibliotecas de classes portáteis. Ele também permite definir comandos, configurações e opções do compilador personalizados. O caminho de saída e o nome de assembly também pode ser definidos aqui.
* **Execute** -usado para criar configurações de execução personalizadas em uma base por projeto.
* **Código-fonte** -controla a formatação de vários tipos de arquivo e convenções de nomenclatura diferentes. Você também pode definir as políticas de nomenclatura e os estilos de cabeçalho padrão aqui.
* **Controle de versão** – opções para definir o estilo de mensagens de confirmação ao usar o controle de versão com seu projeto.

Cada projeto pode conter as opções específicas do projeto, dependendo da plataforma. Por exemplo, um projeto do Xamarin.Android, como o ilustrado na imagem a seguir, tem opções relacionadas ao build do Android (como opções de vinculador) e ao aplicativo (como permissões):

![Opções do Projeto Android](media/projects-and-solutions-image5.png)

O Xamarin.iOS tem opções relacionadas à assinatura do pacote, tais como o perfil de provisionamento necessário a ser usado:

![Opções do Projeto iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opções da Solução

As opções da solução são como as Opções do projeto, mas abrangem todas as Soluções em seu escopo. Elas fornecem uma maneira de definir informações de criador, configurações de build, estilos de formatação de código e controle de versão, e proporcionam uma maneira de atribuir o projeto de inicialização na Solução.  A caixa de diálogo opções de solução pode ser acessada no item de menu **Opções de solução de > de projeto** , no item de menu de contexto **Opções** da solução na janela da solução, ou clicando duas vezes na solução na janela da solução:

![Opções da Solução](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Confira também

* [Gerenciar propriedades do projeto e da solução (Visual Studio no Windows)](/visualstudio/ide/managing-project-and-solution-properties)