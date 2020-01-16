---
title: Usar permissões | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa01cb77e8a003438721984da13f46de350104ea
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918988"
---
# <a name="user-permissions-and-visual-studio"></a>Permissões de usuário e Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Por motivos de segurança, você deve executar o Visual Studio como um usuário normal sempre que possível.

> [!WARNING]
> Você deve se certificar de não compilar, iniciar ou depurar qualquer solução do Visual Studio que não venha de uma pessoa de confiança ou de uma localidade confiável.

 Você pode fazer quase tudo no IDE do Visual Studio como um usuário normal, mas precisa de permissões de administrador para concluir as seguintes tarefas:

|Área|Tarefa|Para obter mais informações|
|----------|----------|--------------------------|
|Instalação|Instalar o Visual Studio.|[Instalação do Visual Studio 2015](../install/install-visual-studio-2015.md)|
||Atualizar de uma edição de avaliação do Visual Studio.|[Como: atualizar a partir de uma edição de avaliação do Visual Studio](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||Instalar, atualizar ou remover conteúdo da Ajuda local.|[Instalar e gerenciar o conteúdo local](../ide/install-and-manage-local-content.md)|
|Tipos de aplicativo|Desenvolver soluções do SharePoint 2010.|[Requisitos para desenvolver soluções do SharePoint](https://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||Adquirir uma licença de desenvolvedor da [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|[Obter uma licença da desenvolvedor (Aplicativos da Windows Store)](https://msdn.microsoft.com/library/windows/apps/hh974578.aspx)|
|Caixa de Ferramentas|Adicionar controles COM clássicos à **Caixa de Ferramentas**.|[Usando a caixa de ferramentas](../ide/using-the-toolbox.md)|
|Suplementos|Instalar e usar suplementos escritos usando COM clássico no IDE.|[Criando suplementos e assistentes](https://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Compilação|Usar eventos pós-compilação que registram um componente.|[Noções básicas sobre etapas e eventos de build personalizados](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||Incluir uma etapa de registro ao criar projetos do C++.|[Noções básicas sobre etapas e eventos compilação personalizada](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|Depuração|Depurar aplicativos que são executados com permissões elevadas.|[Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)|
||Depurar aplicativos que são executados em uma conta de usuário diferente, como sites do ASP.NET.|[Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Depurar na zona de aplicativos de navegador XAML (XBAP).|[Host do WPF (PresentationHost.exe)](https://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||Usar o emulador para depurar projetos de serviço de nuvem do Microsoft Azure.|[Depurando um serviço de nuvem no Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)|
||Configurar um firewall para depuração remota.|[Configurar as ferramentas remotas no dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|Ferramentas de desempenho|Criar perfil de um aplicativo.|[Guia do iniciante à criação de perfil de desempenho](../profiling/beginners-guide-to-performance-profiling.md)|
|Implantação|Implantar um aplicativo Web para o IIS (Serviços de Informações da Internet) em um computador local.|[Implantar um aplicativo Web ASP.NET em um provedor de hospedagem usando o Visual Studio ou o Visual Web Developer: implantação no IIS como um ambiente de teste](https://www.asp.net/web-forms/tutorials/deployment/deployment-to-a-hosting-provider/Deployment-to-a-Hosting-Provider-Deploying-to-IIS-as-a-Test-Environment-5-of-12)|
|Fornecendo comentários à Microsoft|Alterar como participar do Programa de Experiência do Usuário do Visual Studio.|[Como: Enviar comentários](../misc/how-to-send-feedback-about-visual-studio.md)|

## <a name="running-visual-studio-as-an-administrator"></a>Executando o Visual Studio como um administrador
 Você pode iniciar o Visual Studio com permissões administrativas toda vez que iniciar o IDE ou pode modificar o atalho do aplicativo para sempre ser executado com permissões administrativas. Para obter mais informações, consulte a Ajuda do Windows.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8includeswin8-mdmd-includewin81includeswin81-mdmd-includewinserver8includeswinserver8-mdmd-or-includewinblue_server_2includeswinblue-server-2-mdmd"></a>Para executar o Visual Studio com permissões administrativas no [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[win81](../includes/win81-md.md)], [!INCLUDE[winserver8](../includes/winserver8-md.md)] ou [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]

1. Na tela **Inicial**, digite **Visual Studio**. Você deve ver a versão (ou versões) do Visual Studio que está instalado.

2. Selecione a versão do Visual Studio que deseja iniciar e exiba o menu de atalho (ele aparece na parte inferior da tela). Escolha **Executar como administrador**.

     Quando o Visual Studio for iniciado, **(Administrador)** será exibido após o nome do produto na barra de título.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7includeswin7-mdmd-or-includewinsvr08_r2includeswinsvr08-r2-mdmd"></a>Para executar o Visual Studio com permissões administrativas no [!INCLUDE[win7](../includes/win7-md.md)] ou [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]

1. No menu **Iniciar**, escolha **Todos os Programas**.

2. No **Microsoft Visual Studio**, na pasta *Versão*, selecione a **Versão** do *Visual Studio*, abra o menu de atalho e escolha **Executar como administrador**.

     Quando o Visual Studio for iniciado, **(Administrador)** será exibido após o nome do produto na barra de título.

## <a name="see-also"></a>Consulte também
 [Portabilidade, migração e atualização de projetos do Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Como instalar o Visual Studio 2015](../install/install-visual-studio-2015.md)
