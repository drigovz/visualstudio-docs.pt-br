---
title: Noções sobre configurações de build
description: Saiba como você precisa de configurações de compilação quando precisa criar seus projetos com configurações diferentes no Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c6037bd6ed3b7899ff00bce202df7707356683a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971395"
---
# <a name="understand-build-configurations"></a>Noções sobre configurações de build

Você precisará de configurações de compilação quando precisar compilar seus projetos com configurações diferentes. Por exemplo, **debug** e **Release** são configurações e opções de compilador diferentes são usadas adequadamente ao criá-las.  Uma configuração está ativa e é indicada na barra de comandos na parte superior do IDE.

![Configuração ativa](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Configurações de build no Visual Studio para Mac](/visualstudio/mac/configurations).

A configuração e o controle de plataforma onde os arquivos de saída criados são armazenados. Normalmente, quando o Visual Studio cria seu projeto, a saída é colocada em uma subpasta do projeto chamada com a configuração ativa (por exemplo, *bin/Debug/x86*), mas você pode alterá-la.

Você pode criar suas próprias configurações de compilação no nível da solução e do projeto. A configuração da solução determina quais projetos são incluídos na compilação quando essa configuração está ativa. Somente os projetos especificados na configuração da solução ativa serão criados. Se várias plataformas de destino forem selecionadas no Configuration Manager, todos os projetos que se aplicam a essa plataforma serão criados. A configuração do projeto determina quais configurações de compilação e opções de compilador são usadas quando você cria o projeto.

Para criar, selecionar, modificar ou excluir uma configuração, é possível usar o **Configuration Manager**. Para abri-lo, na barra de menus, escolha **criar**  >  **Configuration Manager** ou apenas digite **configuração** na caixa de pesquisa. Também é possível usar a lista **Configurações de Solução** na barra de ferramentas **Padrão** para selecionar uma configuração ou para abrir o **Configuration Manager**.

![Configuration Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Se você não encontrar as definições de configuração da solução na barra de ferramentas e não puder acessar o **Configuration Manager**, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] as configurações de desenvolvimento poderão ser aplicadas. Para obter mais informações, consulte [como: gerenciar configurações com Visual Basic configurações de desenvolvedor aplicadas](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Por padrão, as configurações de **depuração** e **versão** são incluídas em projetos que são criados usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelos. Uma configuração de **depuração** dá suporte à depuração de um aplicativo, e uma configuração de **versão** cria uma versão do aplicativo que pode ser implantada. Para saber mais, consulte [Como definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md). Também é possível criar configurações de solução e de projeto personalizadas. Para obter mais informações, consulte [como: criar e editar configurações](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Configurações da solução

Uma configuração de solução especifica como os projetos na solução devem ser criados e implantados. Para modificar uma configuração de solução ou definir uma nova, no **Configuration Manager**, em **Configuração da solução ativa**, escolha **Editar** ou **Novo**.

Cada entrada na caixa **Contextos do Projeto** em uma configuração de solução representa um projeto na solução. Para cada combinação de **Configuração da solução ativa** e **Plataforma da solução ativa**, é possível definir como cada projeto é usado. (Para obter mais informações sobre as plataformas de solução, consulte [Noções básicas sobre plataformas de build](../ide/understanding-build-platforms.md).)

Quando você define uma nova configuração de solução e marca a caixa de seleção **Criar novas configurações de projeto**, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] atribui automaticamente a nova configuração a todos os projetos. Da mesma forma, quando você define uma nova plataforma de solução e marca a caixa de seleção **Criar novas plataformas de projeto**, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] atribui automaticamente a nova plataforma a todos os projetos. Além disso, se você adicionar um projeto que define como destino uma nova plataforma, o Visual Studio adiciona essa plataforma à lista de plataformas de solução e a atribui a todos os projetos. Ainda é possível modificar as configurações para cada projeto.

A configuração da solução ativa também fornece contexto ao IDE. Por exemplo, se você estiver trabalhando em um projeto e a configuração especificar que ele será criado para um dispositivo móvel, a **Caixa de Ferramentas** exibirá apenas os itens que podem ser usados em um projeto de dispositivo móvel.

## <a name="project-configurations"></a>Configurações de projeto

A configuração e a plataforma para as quais um projeto se destina são usadas em conjunto para especificar as configurações de compilação e as opções de compilador a serem usadas quando ele é compilado. Um projeto pode ter configurações diferentes para cada combinação de configuração e plataforma. Para modificar as propriedades de um projeto, abra o menu de atalho do projeto no **Gerenciador de soluções** e, em seguida, escolha **Propriedades**.  Na parte superior da guia **Build** do designer de projeto, escolha uma configuração ativa para editar suas configurações de compilação.

![Configurações do designer de projeto](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Criando várias configurações

Quando você cria uma solução usando o comando **Compilar**  >  **compilação de solução** , o Visual Studio cria apenas a configuração ativa. Todos os projetos especificados na configuração da solução são criados e a única configuração de projeto criada é aquela especificada na configuração da solução ativa e na plataforma de solução ativa, que é mostrada na barra de ferramentas no Visual Studio. Por exemplo, **debug** e **x86**. Outras configurações e plataformas definidas não são criadas.

Se você quiser criar várias configurações e plataformas em uma ação, poderá usar a opção **Compilar**  >  **lote Build** no Visual Studio. Para acessar esse recurso, pressione **Ctrl** + **Q** para abrir a caixa de pesquisa e digite `Batch build` . A compilação em lotes não está disponível para todos os tipos de projeto. Consulte [como: Compilar várias configurações simultaneamente](how-to-build-multiple-configurations-simultaneously.md).

## <a name="how-visual-studio-assigns-project-configurations"></a>Como o Visual Studio atribui configurações de projeto

Quando você define uma nova configuração de solução e não copia as configurações de uma já existente, o Visual Studio usa os seguintes critérios para atribuir configurações de projeto padrão. Os critérios são avaliados na ordem mostrada.

1. Se um projeto tiver um nome de configuração *\<configuration name> \<platform name>*() que corresponda exatamente ao nome da nova configuração de solução, essa configuração será atribuída. Nomes de configuração não diferenciam maiúsculas de minúsculas.

1. Se o projeto tiver um nome de configuração no qual a parte configuração-nome corresponda à nova configuração de solução, essa configuração será atribuída, independentemente se a parte da plataforma for correspondente ou não.

1. Se ainda não houver correspondência, a primeira configuração listada no projeto será atribuída.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Como o Visual Studio atribui configurações de solução

Quando você cria uma configuração de projeto (no **Configuration Manager**, escolhendo **Novo** no menu suspenso na coluna **Configuração** desse projeto) e marca a caixa de seleção **Criar novas configurações de solução** o Visual Studio procura uma configuração de solução com nome semelhante para compilar o projeto em cada plataforma à que ele dá suporte. Em alguns casos, o Visual Studio renomeia as configurações de solução existentes ou define novas configurações.

O Visual Studio usa os seguintes critérios para atribuir configurações de solução.

- Se uma configuração de projeto não especificar uma plataforma ou especificar apenas uma delas, então a configuração de solução cujo nome corresponder ao da nova configuração de projeto será localizada ou adicionada. O nome padrão dessa configuração de solução não inclui um nome de plataforma; Ele assume o formulário *\<project configuration name>* .

- Se um projeto der suporte a várias plataformas, uma configuração de solução será localizada ou adicionada para cada plataforma com suporte. O nome de cada configuração de solução inclui o nome de configuração do projeto e o nome da plataforma e tem *\<project configuration name> \<platform name>* o formulário.

## <a name="see-also"></a>Confira também

- [Passo a passo: Criar um aplicativo](../ide/walkthrough-building-an-application.md)
- [Compilar e criar](../ide/compiling-and-building-in-visual-studio.md)
- [Soluções e projetos](../ide/solutions-and-projects-in-visual-studio.md)
- [Referência de build do C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Noções básicas sobre plataformas de Build](understanding-build-platforms.md)
- [Configurações de build (Visual Studio para Mac)](/visualstudio/mac/configurations)
