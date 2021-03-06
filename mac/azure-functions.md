---
title: Introdução ao Azure Functions
description: Introdução ao Azure Functions no Visual Studio para Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.topic: how-to
ms.openlocfilehash: f3c1c528e9201c66bc566f9867f8325c653700b9
ms.sourcegitcommit: f915322d60182143da7036893d2941bc200cf439
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94575535"
---
# <a name="introduction-to-azure-functions"></a>Introdução ao Azure Functions

Azure Functions é uma maneira de criar e executar trechos orientados a eventos de código – funções – – na nuvem, sem precisar provisionar ou gerenciar explicitamente a infraestrutura. Para obter mais informações sobre o Azure Functions, consulte a [Documentação do Azure Functions](/azure/azure-functions/).

## <a name="requirements"></a>Requisitos

As ferramentas do Azure Functions estão incluídas no **Visual Studio para Mac 7.5** e posterior.

Para criar e implantar funções, você também precisa de uma assinatura do Azure. Se você não tiver uma conta do Azure, poderá se inscrever hoje gratuitamente e receber 12 meses de serviços populares gratuitos, $200 de crédito gratuito e mais de 25 serviços sempre gratuitos-> [https://azure.com/free](https://azure.com/free/dotnet) .

## <a name="creating-your-first-azure-functions-project"></a>Criando seu primeiro projeto do Azure Functions

1. Em Visual Studio para Mac, selecione **arquivo > nova solução**.
2. Na caixa de diálogo Novo Projeto, selecione o modelo do Azure Functions em **Nuvem > Geral** e clique em **Próximo** :

    ![Caixa de diálogo novo projeto mostrando Azure Functions opção](media/azure-functions-image1.png)

3. Selecione o modelo do Azure Functions inicial que você deseja usar, insira seu nome de função e clique em **Próximo**.

    ![Caixa de diálogo novo projeto mostrando modelos de Azure Functions](media/azure-functions-image2.png)

    > [!TIP]
    > Embora os modelos (CLI) e o Azure Functions Runtime em pacote sejam mantidos tão atualizados quanto possível, eles inevitavelmente ficam desatualizados. Ao criar um projeto do Functions, o Visual Studio para Mac verificará se há atualizações para a CLI e notificará você conforme mostrado na imagem abaixo. Basta clicar no botão para baixar os modelos atualizados.
    > ![Caixa de diálogo novo projeto mostrando Azure Functions atualizações estão disponíveis](media/azure-functions-update.png)

    Dependendo do tipo de função que você selecionar, a próxima página solicitará que você insira detalhes como direitos de acesso, conforme ilustrado na imagem a seguir:

    ![Caixa de diálogo Novo Projeto mostrando uma opção adicional](media/azure-functions-image3.png)

    Para obter mais informações sobre os diferentes tipos de modelos do Azure Functions e as propriedades de associação necessárias para configurar cada modelo, consulte a seção [Modelos de função disponíveis](#available-function-templates). Neste exemplo, estamos usando um gatilho HTTP com direitos de acesso definidos como anônimos.

4. Depois de definir os parâmetros, escolha o local para o projeto e clique em **Criar**.

O Visual Studio para Mac cria um projeto .NET Standard com uma função padrão incluída. Ela também inclui referências de NuGet a uma variedade de pacotes do **AzureWebJobs** , bem como ao pacote **Newtonsoft.Json**.

![Editor do Visual Studio para Mac exibindo uma nova função do Azure do modelo](media/azure-functions-newproj.png)

O novo projeto contém os seguintes arquivos:

* **nome-da-sua-função.cs** – essa classe contém o código clichê para a função que você selecionou. Ela contém um atributo **FunctionName** com o nome da função e um atributo de gatilho que especifica o que dispara a função (por exemplo, uma solicitação HTTP). Para obter mais informações sobre o método de função, consulte o artigo [Referência do desenvolvedor de C# do Azure Functions](/azure/azure-functions/functions-dotnet-class-library).
* **host.json** – Este arquivo descreve as opções de configuração global para o host de funções. Para ver um arquivo de exemplo e obter informações sobre as configurações disponíveis para esse arquivo, consulte a [Referência de host.json para o Azure Functions](/azure/azure-functions/functions-host-json).
* **local.settings.json** – Este arquivo contém todas as configurações para executar funções localmente. Essas configurações são usadas pelas Ferramentas Básicas do Azure Functions. Para saber mais, confira [Arquivo de configurações locais](/azure/azure-functions/functions-run-local#local-settings-file) no tópico Ferramentas Básicas do Azure Functions.

Agora que criou um novo projeto do Azure Functions no Visual Studio para Mac, você pode testar a função disparada por HTTP padrão do computador local.

## <a name="testing-the-function-locally"></a>Testando a função localmente

Com o suporte para Azure Functions no Visual Studio para Mac, você pode testar e depurar sua função no computador de desenvolvimento local.

1. Para testar a função localmente, pressione o botão **Executar** no Visual Studio para Mac:

    ![Botão Iniciar depuração no Visual Studio para Mac](media/azure-functions-run.png)

1. Executar o projeto inicia a depuração local na função do Azure e abre uma nova janela do Terminal, conforme ilustrado na imagem a seguir:

    ![Janela do Terminal mostrando a saída da função](media/azure-functions-terminal.png)

    Copie a URL da saída.

3. Cole a URL para a solicitação HTTP na barra de endereços do navegador. Adicione a cadeia de caracteres de consulta `?name=<yourname>` ao final da URL e execute a solicitação. A imagem a seguir mostra a resposta no navegador para a solicitação GET local retornada pela função:

    ![Solicitação HTTP no navegador](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Adicionar outra função ao seu projeto

Modelos de função permitem que você crie rapidamente novas funções usando os gatilhos e modelos mais comuns. Para criar outro tipo de função, faça o seguinte:

1. Para adicionar uma nova função, clique com o botão direito do mouse no nome do projeto e selecione **Adicionar > Adicionar Função...** :

    ![Ação de contexto para adicionar nova função](media/azure-functions-addnew.png)

2. Na caixa de diálogo **Nova Função do Azure** , selecione a função de que precisa:

    ![Caixa de diálogo Nova Função do Azure](media/azure-functions-image4.png)

    Uma lista dos modelos de função do Azure é fornecida na seção [Modelos de função disponíveis](#available-function-templates).

Você pode usar o procedimento acima para adicionar mais funções a seu projeto de aplicativo de funções. Cada função no projeto pode ter um gatilho diferente, mas uma função deve ter apenas um gatilho. Para obter mais informações, consulte [Azure Functions os conceitos de gatilhos e associações](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Publicar no Azure

1. Clique com o botão direito do mouse no nome do projeto e selecione **publicar > publicar no Azure** :  ![ menu de contexto com publicar > publicar no Azure... opção realçada](media/azure-functions-image5.png)
2. Se você já conectou conta do Azure ao Visual Studio para Mac, uma lista de serviços de aplicativo disponíveis é exibida. Se você ainda não tiver feito logon, será solicitado que o faça.
3. Na caixa de diálogo **Publicar no Serviço de Aplicativo do Azure** , você pode selecionar um serviço de aplicativo existente ou crie um novo clicando em **Novo**.
4. Na caixa de diálogo **criar novo serviço de aplicativo** , insira suas configurações:  ![ caixa de diálogo novo serviço de aplicativo, com campos para nome do serviço, assinatura, grupo de recursos e configurações do plano de serviço.](media/azure-functions-image7.png)

    |Setting  |Descrição  |
    |---------|---------|
    |**Nome do serviço de aplicativo**|Um nome exclusivo que identifica seu novo aplicativo de funções.|
    |**Assinatura**|A assinatura do Azure a utilizar.|
    |**[Grupo de Recursos](/azure/azure-resource-manager/resource-group-overview)**|Nome do grupo de recursos no qual criar o seu aplicativo de funções. Escolha **+** criar um novo grupo de recursos.|
    |**[Plano de Serviço](/azure/azure-functions/functions-scale)**|Escolha um plano existente ou crie um personalizado. Escolha um local em uma região perto de você ou perto de outros serviços acessados pelas funções.|

5. Crie em **Próximo** para criar uma conta de armazenamento. Uma conta de armazenamento do Azure é requerida pelo runtime do Functions. Clique em **Personalizado** para criar uma conta de armazenamento de uso geral ou use uma já existente:

    ![Caixa de diálogo novo serviço de aplicativo com prompt para o nome da conta de armazenamento.](media/azure-functions-image8.png)

6. Clique em **Criar** para criar um aplicativo de função e recursos relacionados no Azure com essas configurações e implantar seu código de projeto de função.

7. Uma caixa de diálogo será exibida durante a publicação solicitando a você "Atualizar a versão do Functions no Azure". Clique em **Sim** :

    ![Solicitação solicitando "atualizar as configurações do aplicativo do Azure para corresponder à versão das funções locais?" com opções Sim e não.](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>Configurações do aplicativo de funções

As configurações que você adicionou no local.settings.json também devem ser adicionadas ao aplicativo de funções no Azure. Essas configurações não são carregadas automaticamente quando você publicar o projeto.

Para acessar as configurações do aplicativo, vá para o portal do Azure em [https://ms.portal.azure.com/](https://ms.portal.azure.com/) . Em **Aplicativos do Functions** , selecione **Aplicativos de Funções** e realce o nome da função:

![menu do azure functions](media/azure-functions-image9.png)

Na guia **Visão geral** , selecione **Configurações do aplicativo** em **Recursos configurados** :

![Guia Visão geral da função do azure](media/azure-functions-image10.png)

Desse ponto em diante, você pode definir as configurações do aplicativo para o aplicativo de funções, no qual você pode adicionar novas configurações do aplicativo ou modificar as existentes:

![área de configurações do aplicativo do portal do Azure](media/azure-functions-image11.png)

`FUNCTIONS_EXTENSION_VERSION` é uma configuração importante que talvez você precise definir. Ao publicar no Visual Studio para Mac, esse valor deve ser definido como **beta**.

## <a name="available-function-templates"></a>Modelos de função disponíveis

- **Gatilho do GitHub** – Responda a eventos que ocorrerem em seus repositórios do GitHub. Para obter mais informações, consulte o [Artigo do Azure Functions sobre o GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function)
  - Autor de comentários do GitHub – Esta função será executada quando receber um webhook do GitHub para uma solicitação de pull ou emissão e adicionará um comentário.
  - WebHook do GitHub – Esta função será executada sempre que receber um webhook do GitHub.

- **HTTP** – Dispare a execução de seu código usando uma solicitação HTTP. Há modelos explícitos para os gatilhos HTTP a seguir:
  - Gatilho Http
  - Http GET CRUD
  - Http POST CRUD
  - Gatilho Http com parâmetros

- **Temporizador** – Execute a limpeza ou outras tarefas em lote seguindo um cronograma predefinido. Esse modelo tem dois campos: um nome e um cronograma, que é uma expressão CRON de seis campos. Para obter mais informações, consulte o [artigo Azure Functions no tempo](/azure/azure-functions/functions-create-scheduled-function)

- **Gatilho de fila** – Esta é uma função que responderá às mensagens conforme elas chegarem na fila do Armazenamento do Azure. Além do nome da função, esse modelo tem um **Caminho** (o nome da fila da qual a mensagem será lida) e uma **Conexão** da conta de armazenamento (o nome da configuração de aplicativo que contém a cadeia de conexão da conta de armazenamento). Para obter mais informações, consulte o [artigo Azure Functions sobre armazenamento de filas](/azure/azure-functions/functions-create-storage-queue-triggered-function).

- **Gatilho de blob** – Processe blobs do Armazenamento do Azure quando eles forem adicionados a um contêiner. Além do nome da função, esse modelo também tem uma propriedade de conexão e de caminho. A propriedade de caminho é o caminho em sua conta de armazenamento que o gatilho monitorará. A conta de conexão é o nome da configuração do aplicativo que contém a cadeia de conexão da sua conta de armazenamento. Para obter mais informações, consulte o [artigo Azure Functions armazenamento de BLOBs](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **WebHook genérico** – É uma função simples que será executada sempre que receber uma solicitação de qualquer serviço que dá suporte a webhooks. Para obter mais informações, consulte o [artigo Azure Functions sobre WebHooks genéricos](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Orquestração de Funções Duráveis** – Funções Duráveis permitem que você escreva funções com estado em um ambiente sem servidor. A extensão gerencia estado, pontos de verificação e reinicializações para você. Para obter mais informações, consulte os guias de Azure Functions sobre [funções duráveis](/azure/azure-functions/durable-functions-overview).

- **Redimensionador de imagem** – Esta função cria imagens redimensionadas sempre que um blob é adicionado a um contêiner. O modelo usa a cadeia de conexão e o caminho para o gatilho, uma saída de imagem pequena e uma saída de imagem média.

- **Token SAS** – Esta função gera um token SAS para um determinado contêiner do Armazenamento do Azure e um nome de blob. Além do nome da função, esse modelo também tem uma propriedade de conexão e de caminho. A propriedade de caminho é o caminho em sua conta de armazenamento que o gatilho monitorará. A conta de conexão é o nome da configuração do aplicativo que contém a cadeia de conexão da sua conta de armazenamento. Os **Direitos de acesso** também precisam ser definidos. O nível de autorização controla se a função requer uma chave de API e qual chave usar; A função usa uma chave de função; O administrador usa sua chave de acesso da conta. Para obter mais informações, consulte o exemplo de [Função do Azure em C# para gerar tokens SAS](https://github.com/Azure-Samples/functions-dotnet-sas-token/).
