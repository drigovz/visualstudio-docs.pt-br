---
title: Incluindo um pacote NuGet no projeto
description: Este documento abrange como incluir um pacote NuGet em um projeto usando o Visual Studio para Mac. Ele explica a descoberta e download de um pacote, apresentando também os recursos de integração do IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74127199"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Instale e gerencie pacotes NuGet no Visual Studio para Mac

A UI do NuGet Package Manager no Visual Studio for Mac permite que você instale, desinstale e atualize facilmente pacotes NuGet em projetos e soluções. Você pode pesquisar e adicionar pacotes aos seus projetos .NET Core, ASP.NET Core e Xamarin.

Este artigo descreve como incluir um pacote NuGet em um projeto e demonstra a cadeia de ferramentas que facilita esse processo.

Para uma introdução ao uso do NuGet no Visual Studio para Mac, consulte [Quickstart: Instale e use um pacote no Visual Studio para Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Encontrar e instalar um pacote

1. Com um projeto aberto no Visual Studio para Mac, clique com o botão direito do mouse na pasta **Dependências** **(Pacotes** se estiver usando um projeto Xamarin) no **Solution Pad** e selecione **Gerenciar pacotes NuGet...**.

    ![Ação de contexto Adicionar novo pacote NuGet](media/nuget-walkthrough-packages-menu.png)

2. Isso inicia a janela **Gerenciar pacotes NuGet.** Certifique-se de que a queda de origem no `nuget.org`canto superior esquerdo da caixa de diálogo está definida para , de modo que você esteja pesquisando o repositório central do pacote NuGet.

    ![Listar pacotes NuGet](media/nuget-walkthrough-add-packages1.png)

3. Use a caixa de pesquisa no canto superior direito para localizar um pacote específico, como por exemplo `EntityFramework`. Quando você encontrar um pacote que deseja usar, selecione-o e clique no botão **Adicionar pacote** para iniciar a instalação.

    ![Adicionar o pacote NuGet entityframework](media/nuget-walkthrough-add-packages2.png)

4. Depois que o pacote for baixado, ele será adicionado ao seu projeto. A solução mudará dependendo do tipo de projeto que você está editando:

    **Projetos Xamarin**
    * O nó **Referências** conterá uma lista de todos os assemblies que fazem parte de um pacote NuGet.
    * O nó **Pacotes** exibe cada pacote NuGet que você baixou. Você pode atualizar ou remover um pacote da lista.
    
    **.NET Projetos principais**

    * O **nó Dependências > NuGet** exibe cada pacote NuGet que você baixou. Você pode atualizar ou remover um pacote da lista.

## <a name="using-nuget-packages"></a>Usando pacotes NuGet

Depois que o pacote NuGet for adicionado e as referências de projeto forem atualizadas, você poderá programar as APIs como faria com qualquer referência de projeto.

Verifique se você adicionou as diretivas `using` necessárias na parte superior do arquivo:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Atualizando pacotes

As atualizações de pacotes podem ser feitas de uma só vez, clicando com o botão direito do mouse no nó **Dependências** **(Nó de pacotes** para projetos Xamarin) ou individualmente em cada pacote. Quando uma nova versão de um pacote NuGet ![estiver disponível, um ícone de atualização aparecerá seta para cima com círculo](media/nuget-walkthrough-update-icon.png).

Clique com o botão direito do mouse em **Dependências** para acessar o menu de contexto e escolha **Atualizar** para atualizar todos os pacotes:

![Menu Pacotes](media/nuget-walkthrough-packages-menu-update.png)

* **Gerenciar pacotes NuGet** - Abre a janela para adicionar mais pacotes ao projeto.
* **Atualizar** – Verifica o servidor de origem de cada pacote e baixa as versões mais recentes.
* **Restaurar** – Baixa todos os pacotes ausentes (sem atualizar os pacotes existentes para as versões mais recentes).

As opções Atualizar e Restaurar também estão disponíveis no nível da Solução, afetando todos os projetos na solução.

### <a name="locating-outdated-packages"></a>Localizando pacotes desatualizados
A partir do bloco de soluções, você pode ver qual versão de um pacote está instalada no momento e clicar com o botão direito do mouse no pacote para atualizar.

![Menu de pacotes com as opções para Atualizar, Remover, Atualizar](media/nuget-walkthrough-PackageMenu.png)

Você também verá uma notificação ao lado do nome do pacote quando uma nova versão de um pacote estiver disponível, para que você possa decidir se deseja atualizá-lo.

![Notificação mostrada quando uma nova versão do pacote está disponível](media/nuget-walkthrough-package-update-available.png)

No menu mostrado, você tem duas opções:

* **Atualizar** – Verifica o servidor de origem e baixa uma versão mais recente (se houver).
* **Remover** – Remove o pacote desse projeto e os assemblies relevantes das Referências do projeto.

## <a name="manage-packages-for-the-solution"></a>Gerenciar pacotes para a solução

O gerenciamento de pacotes para uma solução é um meio conveniente de trabalhar com vários projetos ao mesmo tempo.

1. Clique com o botão direito do mouse na solução e **selecione Gerenciar pacotes NuGet...**:

    ![Gerenciar Pacotes do NuGet para a solução](media/nuget-walkthrough-manage-packages-solution.png)

1. Ao gerenciar pacotes para a solução, a interface do usuário possibilita selecionar os projetos afetados pelas operações:

    ![Seletor de projeto ao gerenciar pacotes para a solução](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Guia Consolidar

Ao trabalhar em uma solução com vários projetos, é considerado uma prática recomendada para garantir que em qualquer lugar que você use o mesmo pacote NuGet em cada projeto, você também está usando o mesmo número de versão desse pacote. Visual Studio for Mac ajuda a tornar isso mais fácil, fornecendo uma guia **Consolidate** na interface do gerente de pacotes quando você optar por gerenciar pacotes para uma solução. Usando esta guia, você pode facilmente ver onde pacotes com números de versão distintos são usados por diferentes projetos na solução:

![Guia Consolidar da interface do usuário do Gerenciador de Pacotes](media/nuget-walkthrough-consolidate-tab.png)

Neste exemplo, o projeto NuGetDemo está usando o Microsoft.EntityFrameworkCore 2.20, enquanto o NuGetDemo.Shared está usando o Microsoft.EntityFrameworkCore 2.2.6. Para consolidar as versões de pacote, faça o seguinte:

- Selecione os projetos a atualizar na lista de projetos.
- Selecione a versão a ser usada em todos esses projetos na lista **Nova Versão,** como Microsoft.EntityFrameworkCore 3.0.0.
- Selecione o botão **Consolidar pacote.**

O Gerenciador de Pacotes instala a versão de pacote selecionada em todos os projetos selecionados e, após isso, o pacote não aparece mais na guia **Consolidar**.

## <a name="adding-package-sources"></a>Adicionando origens de pacotes

Os pacotes disponíveis para instalação são inicialmente recuperados de nuget.org. No entanto, você pode adicionar outros locais de pacote ao Visual Studio para Mac. Isso pode ser útil para testar seus próprios pacotes NuGet em desenvolvimento ou para usar um servidor NuGet privado dentro de sua empresa ou organização.

No Visual Studio for Mac, navegue até **o Visual Studio > Preferências > NuGet > Sources** para visualizar e editar a lista de fontes de pacotes. Observe que as origens podem ser um servidor remoto (especificado por uma URL) ou um diretório local.

![Origens dos pacotes](media/nuget-walkthrough-PackageSource.png)

Clique em **Adicionar** para configurar uma nova origem. Insira um nome amigável e a URL (ou caminho de arquivo) para a origem do pacote. Se a origem for um servidor Web seguro, insira também o nome de usuário e a senha, caso contrário, deixe essas entradas em branco:

![Adicionar origens de pacotes](media/nuget-walkthrough-PackageSource2.png)

É possível selecionar diferentes origens ao procurar pacotes:

![Adicionar origens de pacotes](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Controle de versão

A documentação do NuGet aborda como [usar NuGet sem confirmar pacotes no controle do código-fonte](/nuget/consume-packages/packages-and-source-control). Se você preferir não armazenar binários e informações não usadas no controle do código-fonte, configure o Visual Studio para Mac para restaurar automaticamente os pacotes do servidor. Isso significa que, quando um desenvolvedor recuperar o projeto do controle do código-fonte pela primeira vez, o Visual Studio para Mac baixará e instalará os pacotes necessários automaticamente.

![Restaurar os pacotes automaticamente](media/nuget-walkthrough-AutoRestore.png)

Consulte a documentação do controle do código-fonte específico para ver detalhes sobre como excluir o diretório `packages` do rastreamento.

## <a name="related-video"></a>Vídeo relacionados

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Confira também

* [Instalar e usar um pacote no Visual Studio (no Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
