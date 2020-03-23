---
title: Noções sobre configurações de build
ms.date: 01/20/2020
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a37d4fa5dc92253b94dc64590c9df5fec7703ceb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904159"
---
# <a name="understand-build-configurations"></a>Noções sobre configurações de build

Você precisa de configurações de compilação quando precisa construir seus projetos com configurações diferentes. Por exemplo, **Debug** e **Release** são configurações e diferentes opções de compiladores são usadas de acordo ao construí-las.  Uma configuração está ativa e é indicada na barra de comando na parte superior do IDE.

![Configuração ativa](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Configurações de build no Visual Studio para Mac](/visualstudio/mac/configurations).

A configuração e o controle da plataforma onde os arquivos de saída incorporados são armazenados. Normalmente, quando o Visual Studio constrói seu projeto, a saída é colocada em uma subpasta de projeto nomeada com a configuração ativa (por exemplo, *bin/Debug/x86),* mas você pode alterá-la.

Você pode criar suas próprias configurações de compilação no nível de solução e projeto. A configuração da solução determina quais projetos estão incluídos na compilação quando essa configuração estiver ativa. Somente serão construídos os projetos especificados na configuração da solução ativa. Se várias plataformas de destino forem selecionadas no Gerenciador de Configuração, todos os projetos que se aplicam a essa plataforma serão construídos. A configuração do projeto determina quais configurações de compilação e opções de compilador são usadas quando você constrói o projeto.

Para criar, selecionar, modificar ou excluir uma configuração, é possível usar o **Configuration Manager**. Para abri-lo, na barra de menus, escolha **Build** > **Configuration Manager**ou apenas digite **Configuração** na caixa de pesquisa. Também é possível usar a lista **Configurações de Solução** na barra de ferramentas **Padrão** para selecionar uma configuração ou para abrir o **Configuration Manager**.

![Configuration Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Se você não conseguir encontrar configurações de configuração de solução na [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] barra de ferramentas e não conseguir acessar o **Gerenciador de configuração,** as configurações de desenvolvimento podem ser aplicadas. Para obter mais informações, consulte [Como gerenciar configurações com configurações de desenvolvedor Visual Basic aplicadas](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Por padrão, as configurações **Debug** e **Release** são [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] incluídas em projetos criados usando modelos. Uma configuração **de Debug** suporta a depuração de um aplicativo, e uma configuração **de Versão** cria uma versão do aplicativo que pode ser implantada. Para saber mais, consulte [Como definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md). Também é possível criar configurações de solução e de projeto personalizadas. Para obter mais informações, [consulte Como: Criar e editar configurações](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Configurações da solução

Uma configuração de solução especifica como os projetos na solução devem ser criados e implantados. Para modificar uma configuração de solução ou definir uma nova, no **Configuration Manager**, em **Configuração da solução ativa**, escolha **Editar** ou **Novo**.

Cada entrada na caixa **Contextos do Projeto** em uma configuração de solução representa um projeto na solução. Para cada combinação de **Configuração da solução ativa** e **Plataforma da solução ativa**, é possível definir como cada projeto é usado. (Para obter mais informações sobre as plataformas de solução, consulte [Noções básicas sobre plataformas de build](../ide/understanding-build-platforms.md).)

Quando você define uma nova configuração de solução e marca a caixa de seleção **Criar novas configurações de projeto**, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] atribui automaticamente a nova configuração a todos os projetos. Da mesma forma, quando você define uma nova plataforma de solução e marca a caixa de seleção **Criar novas plataformas de projeto**, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] atribui automaticamente a nova plataforma a todos os projetos. Além disso, se você adicionar um projeto que define como destino uma nova plataforma, o Visual Studio adiciona essa plataforma à lista de plataformas de solução e a atribui a todos os projetos. Ainda é possível modificar as configurações para cada projeto.

A configuração da solução ativa também fornece contexto ao IDE. Por exemplo, se você estiver trabalhando em um projeto e a configuração especificar que ele será criado para um dispositivo móvel, a **Caixa de Ferramentas** exibirá apenas os itens que podem ser usados em um projeto de dispositivo móvel.

## <a name="project-configurations"></a>Configurações de projeto

A configuração e a plataforma que um projeto visa são usadas em conjunto para especificar as configurações de compilação e opções de compilador para usar quando for construída. Um projeto pode ter configurações diferentes para cada combinação de configuração e plataforma. Para modificar as propriedades de um projeto, abra o menu de atalho para o projeto no **Solution Explorer**e escolha **Propriedades**.  Na parte superior da guia **Build** do designer de projeto, escolha uma configuração ativa para editar suas configurações de compilação.

![Configurações do project designer](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Construindo múltiplas configurações

Quando você constrói uma solução usando o comando **Build** > **Build Solution,** o Visual Studio só constrói a configuração ativa. Todos os projetos especificados nessa configuração de solução são construídos, e a única configuração do projeto que foi construída é aquela especificada na configuração ativa da solução e na plataforma de solução ativa, que é mostrada na barra de ferramentas do Visual Studio. Por exemplo, **Debug** e **x86**. Outras configurações e plataformas definidas não são construídas.

Se você quiser construir várias configurações e plataformas em uma ação, você pode usar a opção **Build** > **Batch Build** no Visual Studio. Para acessar esse recurso, **pressione Ctrl**+**Q** `Batch build`para abrir a caixa de pesquisa e digite . A compilação em lote não está disponível para todos os tipos de projeto. [Veja Como: Construir várias configurações simultaneamente](how-to-build-multiple-configurations-simultaneously.md).

## <a name="how-visual-studio-assigns-project-configurations"></a>Como o Visual Studio atribui configurações de projeto

Quando você define uma nova configuração de solução e não copia as configurações de uma já existente, o Visual Studio usa os seguintes critérios para atribuir configurações de projeto padrão. Os critérios são avaliados na ordem mostrada.

1. Se um projeto tiver um nome de*\<configuração (nome \<de configuração> nome *da plataforma>) que corresponda exatamente ao nome da nova configuração da solução, essa configuração será atribuída. Nomes de configuração não diferenciam maiúsculas de minúsculas.

1. Se o projeto tiver um nome de configuração no qual a parte configuração-nome corresponda à nova configuração de solução, essa configuração será atribuída, independentemente se a parte da plataforma for correspondente ou não.

1. Se ainda não houver correspondência, a primeira configuração listada no projeto será atribuída.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Como o Visual Studio atribui configurações de solução

Quando você cria uma configuração de projeto (no **Configuration Manager**, escolhendo **Novo** no menu suspenso na coluna **Configuração** desse projeto) e marca a caixa de seleção **Criar novas configurações de solução** o Visual Studio procura uma configuração de solução com nome semelhante para compilar o projeto em cada plataforma à que ele dá suporte. Em alguns casos, o Visual Studio renomeia as configurações de solução existentes ou define novas configurações.

O Visual Studio usa os seguintes critérios para atribuir configurações de solução.

- Se uma configuração de projeto não especificar uma plataforma ou especificar apenas uma delas, então a configuração de solução cujo nome corresponder ao da nova configuração de projeto será localizada ou adicionada. O nome padrão desta configuração de solução não inclui um nome de plataforma; ele leva o * \<nome de configuração *do projeto de formulário>.

- Se um projeto der suporte a várias plataformas, uma configuração de solução será localizada ou adicionada para cada plataforma com suporte. O nome de cada configuração de solução inclui tanto o nome de configuração do projeto quanto o nome da plataforma, e tem o * \<nome de configuração \< *do projeto de formulário> nome da plataforma>.

## <a name="see-also"></a>Confira também

- [Passo a passo: Criar um aplicativo](../ide/walkthrough-building-an-application.md)
- [Compilação e construção](../ide/compiling-and-building-in-visual-studio.md)
- [Soluções e projetos](../ide/solutions-and-projects-in-visual-studio.md)
- [Referência de build do C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Entendendo plataformas de construção](understanding-build-platforms.md)
- [Configurações de build (Visual Studio para Mac)](/visualstudio/mac/configurations)
