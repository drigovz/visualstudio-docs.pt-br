---
title: Adicionando serviços móveis usando serviços conectados
description: Adicionar Serviços Móveis usando a caixa de diálogo Adicionar Serviços Conectados do Visual Studio
documentationcenter: na
author: ghogen
manager: jillfra
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 0a8f6fab3c8f30834a467e2ad98843b16a9245b4
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916706"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Adicionando Serviços Móveis usando os serviços conectados do Visual Studio
Com o Visual Studio 2015, você pode se conectar a Serviços Móveis do Azure usando a caixa de diálogo **Adicionar Serviço Conectado** . Você pode conectar de qualquer aplicativo de cliente C#, qualquer aplicativo JavaScript ou aplicativo Cordova de plataforma cruzada. Uma vez conectado, você pode criar e acessar dados, criar APIs personalizados e trabalhos programados ou adicionar suporte ou notificações por push.  A operação de serviços conectados adiciona todas as referências apropriadas e o código de conexão. Você também pode aproveitar o suporte interno para autenticação com uma variedade de esquemas de identidade populares, como o AD do Azure, Facebook, Twitter e contas da Microsoft.

## <a name="supported-project-types"></a>Tipos de projeto com suporte
> [!NOTE]
> No Visual Studio 2015, não há suporte para adição de Serviços Móveis do Azure a projetos Windows Universal (Windows 10) usando a caixa de diálogo Adicionar Serviços Conectados. É possível adicionar Serviços Móveis do Azure instalando os pacotes adequados usando o Gerenciador de Pacotes NuGet para seu projeto.
>
>

Você pode usar a caixa de diálogo Serviços Conectados para se conectar a Serviços Móveis do Azure nos tipos de projeto a seguir.

* Projetos de aplicativo Windows 8.1 Store, Phone e Universal para .NET
* Projetos de aplicativo Windows 8.1 Store, Phone e Universal para JavaScript
* Projetos criados usando o Visual Studio Tools para Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Conectar-se aos Serviços Móveis do Azure usando a caixa de diálogo Adicionar Serviços Conectados
1. Certifique-se de ter uma conta do Azure. Se não tiver uma conta do Azure, você poderá assinar uma versão de [avaliação gratuita](https://azure.microsoft.com/pricing/free-trial/).
2. Abra a caixa de diálogo **Adicionar Serviços Conectados** .

   * Para aplicativos .NET, abra o projeto no Visual Studio, abra o menu de contexto do nó **Referências** no Gerenciador de Soluções e escolha **Adicionar Serviço Conectado**

        ![Conectar-se ao Serviço Móvel do Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Para projetos de aplicativo Apache Cordova, abra o projeto no Visual Studio, abra o menu de contexto do nó do projeto no Gerenciador de Soluções e escolha **Adicionar Serviço Conectado**.
3. Na caixa de diálogo **Adicionar Serviço Conectado**, escolha **Serviços Móveis do Azure** e escolha o botão **Configurar**. Você será solicitado a fazer logon no Azure, se ainda não o fez.

    ![Adicionando um Serviço Móvel do Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. Na caixa de diálogo **Serviços Móveis do Azure** , escolha um serviço móvel existente, se houver. Se você precisar criar um novo serviço móvel do Azure, siga o procedimento abaixo para fazer isso. Caso contrário, pule para a próxima etapa.

    Para criar uma nova conta de serviço móvel:

   1. Escolha o link **Criar serviço** na parte inferior da caixa de diálogo.
       ![Adicionar novo serviço conectado móvel](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Na caixa de diálogo **Criar Serviço Móvel**, você pode escolher um serviço móvel de back-end JavaScript ou um serviço móvel de back-end .NET na lista suspensa **Runtime**.

       ![Criando um serviço móvel](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Um serviço de back-end JavaScript é simples e eficiente. Se você criar um serviço móvel de back-end JavaScript, o código de JavaScript do lado do servidor é armazenado na nuvem, mas você pode editar scripts de servidor usando o Gerenciador de Servidores, ou o portal de gerenciamento do Azure.

       Um serviço móvel back-end do .NET fornece a toda a potência e a flexibilidade da API Web e do Entity Framework. Se você criar um serviço móvel back-end do .NET, um projeto será criado e adicionado à sua solução.
   3. Escolha a **Região** onde deseja o serviço móvel e insira um nome de usuário e uma senha para o servidor.
   4. Depois de inserir todas as informações necessárias, escolha o botão **Criar** para criar o serviço móvel.
   5. O novo serviço móvel deve aparecer na lista de serviço, na caixa de diálogo **Serviços Móveis do Azure** . Escolha o novo serviço móvel na lista e escolha o botão **Adicionar** para adicionar o serviço ao seu projeto.
5. Revise a página de introdução exibida e descubra como seu projeto foi modificado. Uma página de Introdução será exibida no navegador sempre que você adicionar um serviço conectado. Você pode revisar as próximas etapas sugeridas e exemplos de código ou alternar para a página O que aconteceu para ver quais referências foram adicionadas ao seu projeto e como o seu código e arquivos de configuração foram modificados.
6. Usando os exemplos de código como guia, comece a escrever o código para acessar seu serviço móvel!

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}
Faça perguntas e obtenha ajuda:

* [Fórum do MSDN: Serviços Móveis do Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Serviços Móveis do Azure no Blog da equipe do Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Serviços Móveis do Azure em azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Documentação dos Serviços Móveis do Azure em azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
