---
title: Incluindo um pacote NuGet no projeto
description: Este documento aborda como incluir um pacote NuGet em um projeto usando Visual Studio para Mac. Ele explica a descoberta e download de um pacote, apresentando também os recursos de integração do IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/17/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 22b2e07509403d8e19e3a3e920d45b064c2e51c0
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079517"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Instalar e gerenciar pacotes NuGet no Visual Studio para Mac

A interface do usuário do Gerenciador de pacotes NuGet no Visual Studio para Mac permite que você instale, desinstale e atualize facilmente pacotes NuGet em projetos e soluções. Você pode pesquisar e adicionar pacotes a seus projetos .NET Core, ASP.NET Core e Xamarin.

Este artigo descreve como incluir um pacote NuGet em um projeto e demonstra a cadeia de ferramentas que facilita esse processo.

Para obter uma introdução ao uso do NuGet no Visual Studio para Mac [, consulte início rápido: Instalar e usar um pacote no Visual Studio para Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Localizar e instalar um pacote

1. Com um projeto aberto no Visual Studio para Mac, clique com o botão direito do mouse na pasta **dependências** (pasta**pacotes** se estiver usando um projeto Xamarin) na **painel de soluções** e selecione **adicionar pacotes**.

    ![Ação de contexto Adicionar novo pacote NuGet](media/nuget-walkthrough-PackagesMenu.png)

2. Isso inicia a janela **Adicionar Pacotes**. Verifique se a lista suspensa origem no canto superior esquerdo da caixa de diálogo está definida como `nuget.org`.

    ![Listar pacotes NuGet](media/nuget-walkthrough-AddPackages1.png)

3. Use a caixa de pesquisa no canto superior direito para localizar um pacote específico, como por exemplo `EntityFramework`. Quando você encontrar um pacote que deseja usar, selecione-o e clique no botão **Adicionar pacote** para iniciar a instalação.

    ![Adicionar um pacote NuGet do Azure](media/nuget-walkthrough-AddPackages2.png)

4. Depois que o pacote for baixado, ele será adicionado ao seu projeto. A solução será alterada dependendo do tipo de projeto que você está editando:

    **Projetos do Xamarin**
    * O nó **Referências** conterá uma lista de todos os assemblies que fazem parte de um pacote NuGet.
    * O nó **Pacotes** exibe cada pacote NuGet que você baixou. Você pode atualizar ou remover um pacote da lista.
    
    **Projetos do .NET Core**

    As **dependências > nó NuGet** exibe cada pacote NuGet que você baixou. Você pode atualizar ou remover um pacote da lista.

## <a name="using-nuget-packages"></a>Usando pacotes NuGet

Depois que o pacote NuGet for adicionado e as referências de projeto forem atualizadas, você poderá programar as APIs como faria com qualquer referência de projeto.

Verifique se você adicionou as diretivas `using` necessárias na parte superior do arquivo:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Atualizando pacotes

As atualizações de pacote podem ser feitas de uma só vez, clicando com o botão direito do mouse no nó de **dependências** (ou no nó **pacotes** para projetos do Xamarin) ou individualmente em cada componente.

Clique com o botão direito do mouse em **dependências** para acessar o menu de contexto:

![Menu Pacotes](media/nuget-walkthrough-PackagesMenu.png)

* **Gerenciar pacotes NuGet** – abre a janela para adicionar mais pacotes ao projeto.
* **Atualizar** – Verifica o servidor de origem de cada pacote e baixa as versões mais recentes.
* **Restaurar** – Baixa todos os pacotes ausentes (sem atualizar os pacotes existentes para as versões mais recentes).

As opções Atualizar e Restaurar também estão disponíveis no nível da Solução, afetando todos os projetos na solução.

No painel de solução, você pode exibir qual versão de um pacote está instalada no momento e clicar com o botão direito do mouse no pacote a ser atualizado.

![Menu pacotes com as opções para atualizar, remover, atualizar](media/nuget-walkthrough-PackageMenu.png)

Você também verá uma notificação ao lado do nome do pacote quando uma nova versão de um pacote estiver disponível, para que você possa decidir se talvez queira atualizá-la.

![Notificação mostrada quando uma nova versão de pacote está disponível](media/nuget-walkthrough-package-update-available.png)

No menu mostrado, você tem duas opções:

* **Atualizar** – Verifica o servidor de origem e baixa uma versão mais recente (se houver).
* **Remover** – Remove o pacote desse projeto e os assemblies relevantes das Referências do projeto.

## <a name="adding-package-sources"></a>Adicionando origens de pacotes

Os pacotes disponíveis para instalação são recuperados inicialmente de nuget.org. No entanto, você pode adicionar outros locais de pacotes para o Visual Studio para Mac. Isso pode ser útil para testar seus próprios pacotes NuGet em desenvolvimento ou para usar um servidor NuGet privado dentro de sua empresa ou organização.

No Visual Studio para Mac, navegue até **Visual Studio > Preferências > NuGet > Origens** para exibir e editar a lista de origens de pacote. Observe que as origens podem ser um servidor remoto (especificado por uma URL) ou um diretório local.

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

## <a name="see-also"></a>Consulte também

* [Instalar e usar um pacote no Visual Studio (no Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
