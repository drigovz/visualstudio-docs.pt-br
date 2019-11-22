---
title: Adicionando serviços móveis usando serviços conectados
description: Adicionar serviços móveis usando a caixa de diálogo Adicionar serviços conectados do Visual Studio
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
ms.openlocfilehash: 4f84970daea03904d4642317cf6097beb07be7f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300191"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Adicionando serviços móveis usando os serviços conectados do Visual Studio
Com o Visual Studio 2015, você pode se conectar aos serviços móveis do Azure usando a caixa de diálogo **Adicionar serviço conectado** . Você pode se conectar de C# qualquer aplicativo cliente, qualquer aplicativo JavaScript ou aplicativo Cordova de plataforma cruzada. Depois de se conectar, você pode criar e acessar dados, criar APIs personalizadas e trabalhos agendados ou adicionar suporte para notificações por push.  A operação de serviços conectados adiciona todas as referências e o código de conexão apropriados. Você também pode aproveitar o suporte interno para autenticação com uma variedade de esquemas de identidade populares, como contas do Azure AD, Facebook, Twitter e Microsoft.

## <a name="supported-project-types"></a>Tipos de projeto com suporte
> [!NOTE]
> No Visual Studio 2015, não há suporte para a adição de serviços móveis do Azure a projetos do Windows universal (Windows 10) usando a caixa de diálogo Adicionar serviços conectados. Você pode adicionar os serviços móveis do Azure instalando os pacotes apropriados usando o Gerenciador de pacotes NuGet para seu projeto.
>
>

Você pode usar a caixa de diálogo serviços conectados para se conectar aos serviços móveis do Azure nos seguintes tipos de projeto.

* Projetos .NET Windows 8.1 Store, Phone e universal app
* JavaScript Windows 8.1 armazenamento, telefone e projetos de aplicativo universal
* Projetos criados usando Ferramentas do Visual Studio para Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Conectar-se aos serviços móveis do Azure usando a caixa de diálogo Adicionar serviços conectados
1. Verifique se você tem uma conta do Azure. Se você não tiver uma conta do Azure, poderá se inscrever para uma [avaliação gratuita](https://go.microsoft.com/fwlink/?LinkId=518146).
2. Abra a caixa de diálogo **Adicionar serviços conectados** .

   * Para aplicativos .NET, abra o projeto no Visual Studio, abra o menu de contexto do nó **referências** em Gerenciador de soluções e, em seguida, escolha **Adicionar serviço conectado**

        ![Conectando-se ao serviço móvel do Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Para Apache Cordova projetos de aplicativo, abra o projeto no Visual Studio, abra o menu de contexto do nó do projeto no Gerenciador de Soluções e, em seguida, escolha **Adicionar serviço conectado**.
3. Na caixa de diálogo **Adicionar serviço conectado** , escolha **serviços móveis do Azure**e, em seguida, escolha o botão **Configurar** . Você pode ser solicitado a fazer logon no Azure se ainda não tiver feito isso.

    ![Adicionando um serviço móvel do Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. Na caixa de diálogo **serviços móveis do Azure** , escolha um serviço móvel existente se você tiver um. Se você precisar criar um novo serviço móvel do Azure, siga o procedimento abaixo para fazer isso. Caso contrário, pule para a próxima etapa.

    Para criar uma nova conta de serviço móvel:

   1. Escolha o link **Criar serviço** na parte inferior da caixa de diálogo.
       ![adicionar novo serviço conectado móvel](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. Na caixa de diálogo **Criar serviço móvel** , você pode escolher um serviço móvel de back-end JavaScript ou um serviço móvel de back-end do .net na lista suspensa **tempo de execução** .

       ![Criando um serviço móvel](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Um serviço de back-end JavaScript é simples e poderoso. Se você criar um serviço móvel de back-end JavaScript, o código JavaScript do lado do servidor será armazenado na nuvem, mas você poderá editar scripts de servidor usando Gerenciador de Servidores ou o portal de gerenciamento do Azure.

       Um serviço móvel de back-end do .NET oferece todo o poder e a flexibilidade da API Web e Entity Framework. Se você criar um serviço móvel de back-end do .NET, um projeto será criado para você e adicionado à sua solução.
   3. Escolha a **região** onde você deseja o serviço móvel e insira um nome de usuário e uma senha para o servidor.
   4. Depois de inserir todas as informações necessárias, escolha o botão **criar** para criar o serviço móvel.
   5. O novo serviço móvel deve aparecer na lista de serviços na caixa de diálogo **serviços móveis do Azure** . Escolha o novo serviço móvel na lista e, em seguida, escolha o botão **Adicionar** para adicionar o serviço ao seu projeto.
5. Examine a página de introdução que aparece e descubra como o projeto foi modificado. Uma página Introdução aparece em seu navegador sempre que você adiciona um serviço conectado. Você pode examinar as próximas etapas sugeridas e os exemplos de código, ou alternar para a página o que aconteceu para ver quais referências foram adicionadas ao seu projeto e como seus arquivos de código e de configuração foram modificados.
6. Usando os exemplos de código como guia, comece a escrever código para acessar seu serviço móvel!

## <a name="how-your-project-is-modified"></a>Como o projeto é modificado
Como o Visual Studio modifica seu projeto depende do tipo de projeto. Para C# aplicativos cliente, consulte [o que aconteceu C# – projetos](https://go.microsoft.com/fwlink/p/?LinkId=513119). Para aplicativos cliente JavaScript, consulte [o que aconteceu – projetos JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=513120). Para aplicativos Cordova, consulte [o que aconteceu – projetos Cordova](https://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Próximas etapas
Faça perguntas e Obtenha ajuda:

* [Fórum do MSDN: serviços móveis do Azure](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Serviços móveis do Azure no blog da equipe de Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Serviços móveis do Azure em azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Documentação dos serviços móveis do Azure em azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
