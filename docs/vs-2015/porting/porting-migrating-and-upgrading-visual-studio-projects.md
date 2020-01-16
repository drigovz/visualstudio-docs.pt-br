---
title: Portar, migrar e atualizar projetos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 3361b04900e549d037338abfba0911b232c9e1bd
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919096"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Portar, migrar e atualizar projetos do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente sobre Visual Studio, confira [Referência de migração e atualização de projeto do Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Quando estiver considerando se deve migrar para uma versão mais recente do Visual Studio, você poderá usar este artigo para descobrir quais soluções, projetos, arquivos e outros ativos criados no Visual Studio 2013, no Visual Studio 2012 ou no Visual Studio 2010 SP1 serão executados sem modificação no Visual Studio 2013 e no Visual Studio 2015. Ou talvez você tenha chegado até esta página por meio de uma mensagem de erro ao tentar abrir um projeto não compatível com a versão do Visual Studio em que você o abriu ou que precise de um SDK ou de uma extensão, como o SDK do Azure para .NET.

Muitos ativos amplamente usados se comportam da mesma forma no Visual Studio 2015, no Visual Studio 2013 e nas duas versões anteriores. Por exemplo, no Visual Studio 2015 é possível abrir um projeto criado no Visual Studio 2013 ou no Visual Studio 2012, alterá-lo e, em seguida, reabri-lo no Visual Studio 2015. Suas alterações serão mantidas e o projeto se comportará da mesma forma que na versão anterior. Isso também vale para muitos ativos que foram criados no Visual Studio 2010 SP1.

Para o Visual Basic, o Visual Studio 2015 não apresentou nenhuma alteração que impedirá a compilação de um aplicativo do Visual Basic criado no Visual Studio 2013. O comportamento em tempo de execução de aplicativos do Visual Basic que são recompilados usando o Visual Studio 2015 não será alterado.

Se usar o Visual Studio 2015 junto com o Visual Studio 2013, Visual Studio 2012 ou Visual Studio 2010 SP1, você poderá criar e modificar projetos e arquivos em qualquer uma das versões. É possível transferir projetos e arquivos entre as versões, desde que você não adicione recursos sem compatibilidade com uma ou mais versões.

## <a name="project"></a> Projetos

A lista a seguir descreve a compatibilidade com o Visual Studio 2015 e o Visual Studio 2013 para projetos criados no Visual Studio 2012 ou no Visual Studio 2010 SP1. Use essa lista para ajudar a determinar se é possível abrir um projeto "no estado em que se encontra" no Visual Studio 2015, no Visual Studio 2013, no Visual Studio 2012 ou no Visual Studio 2010 SP1. Ou ainda se será necessário modificá-lo para garantir a compatibilidade.

|Tipo de projeto|Compatibilidade|
|---------------------|-------------------|
|Aplicativos da Plataforma Universal do Windows|Para instalar as ferramentas para aplicativos universais do Windows, escolha **Personalizar** ou **Modificar** e, em seguida, escolha **Ferramentas de Desenvolvimento de Aplicativos Universais do Windows**.<br /><br /> O desenvolvimento de aplicativos UWP (Plataforma Universal do Windows) para o Windows 10 é compatível somente com o Visual Studio 2015 no Windows 10 ou no [!INCLUDE[win81](../includes/win81-md.md)].|
|Aplicativos da Windows Store|Há suporte para o desenvolvimento de aplicativos da Windows Store, incluindo aplicativos universais destinados a Windows 8.1 e Windows Phone 8.1 no [!INCLUDE[win81](../includes/win81-md.md)] e no Windows 10. Os projetos existentes do [!INCLUDE[win8](../includes/win8-md.md)] podem continuar com suporte, mas não é possível criar projetos do [!INCLUDE[win8](../includes/win8-md.md)]. Os projetos do [!INCLUDE[win81](../includes/win81-md.md)] podem depender apenas de determinados tipos de referência. Para obter mais informações, consulte [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md). **Observação:** projetos do [!INCLUDE[win81](../includes/win81-md.md)] criados usando o Visual Studio 2015 ou o Visual Studio 2013 não podem ser abertos no Visual Studio 2012. Isso ocorre porque os projetos do [!INCLUDE[win81](../includes/win81-md.md)] criados usando o Visual Studio 2015 e o Visual Studio 2013 são destinados a essas versões e o Visual Studio 2012 é compatível somente com os projetos do [!INCLUDE[win8](../includes/win8-md.md)] que são destinados ao [!INCLUDE[win8](../includes/win8-md.md)].|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|É possível criar e usar estes projetos no Visual Studio 2015 e no Visual Studio 2013 após instalar o pacote multiplataforma apropriado. Esses projetos não têm suporte no Visual Studio 2010 SP1.|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|É possível criar e abrir estes projetos no Visual Studio 2015, no Visual Studio 2013 e no Visual Studio 2012, mas não no Visual Studio 2010 SP1.|
|BizTalk|Os projetos do BizTalk Server não são compatíveis com o Visual Studio 2015 ou o Visual Studio 2013.|
|Aplicativo ou biblioteca de classes do Silverlight 4 em C#/Visual Basic|Caso permita que o Visual Studio atualize o projeto automaticamente, será possível abri-lo no Visual Studio 2013 ou no Visual Studio 2012.|
|Formulário da Web ou Windows Form em C#/Visual Basic|É possível abrir o projeto no Visual Studio 2013 e no Visual Studio 2012.|
|Visual Basic 6 e Visual C++ 6|O Visual Studio 2012 e o Visual Studio 2013 não são compatíveis com os aplicativos de depuração criados com o Visual Basic 6 ou o Visual C++ 6. Para depurar esses aplicativos, use as versões anteriores do Visual Studio.|
|Teste de interface do usuário codificado|Caso permita que o Visual Studio atualize o projeto automaticamente, será possível abri-lo no Visual Studio 2013, no Visual Studio 2012 ou no Visual Studio 2010 SP1.|
|F#|Caso permita que o Visual Studio atualize um projeto criado no Visual Studio 2010 SP1, será possível abri-lo no Visual Studio 2013 e no Visual Studio 2012. No entanto, não será possível atualizar um projeto do Silverlight criado em uma versão anterior do Visual Studio para o Visual Studio 2013. Em vez disso, será necessário criar um projeto do Silverlight no Visual Studio 2013 e copiar seu código nele. Os projetos do Silverlight criados no Visual Studio 2013 são destinados ao Silverlight 5.|
|LightSwitch|Caso permita que o Visual Studio atualize o projeto automaticamente, será possível abri-lo somente no Visual Studio 2013.|
|Cache de banco de dados local|O modelo do cache de banco de dados Local e a caixa de diálogo **Configurar a Sincronização de Dados** não estão incluídos no Visual Studio 2013. É possível usar o Visual Studio 2013 para abrir e executar projetos criados no [!INCLUDE[vs2010](../includes/vs2010-md.md)] se o Microsoft Synchronization Services v1.0 estiver instalado. Porém, se desejar atualizá-los no Visual Studio 2013, você precisará fazer todas as alterações manualmente no código. Como alternativa, você pode continuar usando o [!INCLUDE[vs2010](../includes/vs2010-md.md)] para manter e atualizar esses projetos.  Para novos desenvolvimentos, destine o novo modelo de sincronização que é fornecido pelo Microsoft Sync Framework. Para obter informações, confira [Centro de Desenvolvimento do Microsoft Sync Framework](https://msdn.microsoft.com/sync/default)|
|Estrutura Modelo-Exibição-Controlador|O Visual Studio 2010 SP1 é compatível somente com o MVC 2 e o MVC 3. O Visual Studio 2012 é compatível somente com o MVC 3 e o MVC 4. E o Visual Studio 2013 é compatível somente com o MVC 4. Para obter informações sobre como atualizar automaticamente do MVC 2 para o MVC 3, consulte [Atualizador do aplicativo ASP.NET MVC 3](https://aspnet.codeplex.com/releases/view/59008). Para obter informações sobre como atualizar manualmente do MVC 2 para o MVC 3, consulte [Atualizando um projeto ASP.NET MVC 2 para atualização de ferramentas do ASP.NET MVC 3](https://aspnet.codeplex.com/releases/view/59008). Para obter informações sobre como atualizar manualmente do MVC 3 para o MVC 4, consulte [Atualizando um projeto ASP.NET MVC 3 para o ASP.NET MVC 4](/aspnet/whitepapers/mvc4-release-notes). Se seu projeto for destinado para o .NET Framework 3.5 SP1, você deverá redestiná-lo para usar o .NET Framework 4.|
|Modelagem|Se você permitir que o Visual Studio atualize o projeto automaticamente, será possível abri-lo no Visual Studio 2013, Visual Studio 2012 ou Visual Studio 2010 SP1.<br /><br /> Quando o Team Foundation compila um projeto de modelagem, ele tenta validar as camadas no projeto. No Visual Studio 2013, o Team Foundation Build não pode validar as camadas de um projeto de modelagem criado no Visual Studio 2010 SP1. No entanto, no Visual Studio 2010 SP1, o Team Foundation Build pode validar as camadas em um projeto de modelagem criado no Visual Studio 2013.|
|Depuração de MPI/cluster|Caso a mesma versão do runtime ou das ferramentas esteja instalada nos computadores que estão executando o Visual Studio 2013, o Visual Studio 2012 ou o Visual Studio 2010 SP1, será possível abrir esse projeto nas três versões.|
|Instalação MSI (.vdproj)|Este projeto não pode ser aberto no Visual Studio 2013, pois ele não é compatível com esse tipo de projeto. É recomendável usar o InstallShield Limited Edition para Visual Studio (ISLE), uma solução de implantação gratuita que oferece suporte direto à maioria das plataformas Windows e dos runtimes de aplicativo. Você também pode usar o ISLE para importar dados e configurações de projetos do Visual Studio Installer. .|
|Office 2007 VSTO|Caso atualize o projeto para que ele seja destinado ao Office 2013 e ao .NET Framework 4, será possível abri-lo no Visual Studio 2013, no Visual Studio 2012 ou no Visual Studio 2010 SP1.|
|Office 2010 VSTO|Caso o projeto seja destinado ao .NET Framework 4, será possível abri-lo no Visual Studio 2013, no Visual Studio 2012 e no Visual Studio 2010 SP1. Todos outros projetos exigem uma atualização unidirecional.|
|Aplicativos avançados da Internet|Caso atualize o projeto, será possível abri-lo no Visual Studio 2013, no Visual Studio 2012 e no Visual Studio 2010 SP1.|
|SharePoint 2007|Este projeto não pode ser aberto no Visual Studio 2013. No entanto, caso atualize o projeto manualmente para o SharePoint 2010, será possível abri-lo no Visual Studio 2013, no Visual Studio 2012 e no Visual Studio 2010 SP1. Para saber mais de como atualizar o SharePoint 2007, confira [Migrar do SharePoint 2007 para o SharePoint 2010 para profissionais de TI](https://channel9.msdn.com/Blogs/matthijs/Migrating-from-SharePoint-2007-to-SharePoint-2010-for-the-IT-Pro) e [Ferramenta de migração do SharePoint Enterprise Search para o SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)).|
|SharePoint 2010|É possível abrir o projeto no Visual Studio 2013, no Visual Studio 2012 e no Visual Studio 2010 SP1.|
|SketchFlow|Caso permita que o Visual Studio atualize o projeto para o WPF 4.5 ou o Silverlight 5, será possível abri-lo no Visual Studio 2012 e no Visual Studio 2013.|
|Banco de dados do [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)]|É possível abrir o projeto no Visual Studio 2013, no Visual Studio 2012 e no Visual Studio 2010 SP1. Se você tiver um arquivo de banco de dados (.mdf) criado em uma versão anterior do SQL Server, será preciso atualizá-lo para o [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] para poder usá-lo com o SQL Server Express LocalDB, mas o banco de dados não será mais compatível com versões anteriores do SQL Server. Caso não faça a atualização, será possível continuar trabalhando com o banco de dados no Visual Studio 2013 instalando e usando o [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] no mesmo computador. Para saber mais, confira [Atualizar arquivos .mdf](../data-tools/upgrade-dot-mdf-files.md).|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|Caso o [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express esteja instalado nos computadores que estão executando o Visual Studio 2013, o Visual Studio 2012 e o Visual Studio 2010 SP1, será possível abrir o projeto nas três versões.|
|Projeto de Relatório do SQL Server|É possível abrir o projeto no Visual Studio 2013 e no Visual Studio 2012. Apenas para o modo local (isto é, quando não conectado ao SQL Server), você não obterá a experiência em tempo de design para controles associados ao visualizador no [!INCLUDE[vs2010](../includes/vs2010-md.md)], mas o projeto funcionará corretamente no runtime. **Cuidado:** caso adicione um recurso específico do Visual Studio 2013, o esquema de relatório será atualizado automaticamente e não será mais possível abrir o projeto no Visual Studio 2012.|
|Testes de unidade|É possível usar o [!INCLUDE[TCMext](../includes/tcmext-md.md)] no Visual Studio 2013, no Visual Studio 2012 e no Visual Studio 2010 SP1 para abrir os testes criados em qualquer uma dessas versões.|
|Visual C++|É possível usar o Visual Studio 2013 para abrir um projeto C++ criado no Visual Studio 2012 ou no Visual Studio 2010 SP1. Caso deseje usar o ambiente de compilação do Visual Studio 2013 para compilar um projeto criado no Visual Studio 2012, será necessário ter as duas versões do Visual Studio instaladas no mesmo computador. Para obter mais informações, confira [Como: atualizar projetos do Visual C++ para o Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) e [Guia de portabilidade e atualização do Visual C++](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb).|
|Visual Studio 2010 Web|Caso permita que o Visual Studio atualize o projeto automaticamente, será possível abri-lo no Visual Studio 2013, no Visual Studio 2012 e no Visual Studio 2010 SP1.|
|Banco de dados do Visual Studio 2010 (.dbproj)|Caso converta o projeto em um projeto de banco de dados do SQL Server Data Tools, será possível abri-lo no Visual Studio 2013. No entanto, o Visual Studio 2013 não é compatível com estes artefatos:<br /><br /> –    testes de unidade<br />–    planos de geração de dados<br />–    arquivos de comparação de dados<br />–    extensões de regra personalizada para análise de código estático<br />–    server.sqlsettings<br />–    arquivos .sqlcmd<br />–    extensões de implantação personalizada<br />–    projetos parciais (.files)<br /><br /> Se você instalar o SQL Server Data Tools, será possível abrir o projeto no Visual Studio 2010 SP1 após a conversão. Para saber mais, confira [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx).|
|Visual Database Tools do Visual Studio 2010|É possível abrir esse projeto no Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1.|
|Visual Studio Lab Management|É possível usar o [!INCLUDE[TCMext](../includes/tcmext-md.md)], o Visual Studio 2013, o Visual Studio 2012 e o Visual Studio 2010 SP1 para abrir ambientes criados em qualquer uma dessas versões. No entanto, a versão do Microsoft Test Manager deve corresponder à versão do Team Foundation Server para que você possa criar ambientes.|
|Macro do Visual Studio|Este projeto não pode ser aberto no Visual Studio 2013, pois ele não é compatível com o tipo de projeto.|
|SDK/VSIX do Visual Studio|Depois de atualizar um projeto do SDK do Visual Studio para o Visual Studio 2013, ele não poderá ser aberto no Visual Studio 2012. Para obter mais informações, confira [Como: Migrar projetos de extensibilidade para o Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md).|
|Ferramentas do Microsoft Azure para Visual Studio|Caso esteja usando as Ferramentas do Microsoft Azure para o Visual Studio versão 2.1, será possível abrir o projeto no Visual Studio 2013, no Visual Studio 2012 e no Visual Studio 2010 SP1. Para projetos destinados a versões anteriores, caso permita que o Visual Studio atualize o projeto para a versão 2.1, será possível abri-lo no Visual Studio 2013, no Visual Studio 2012 e no Visual Studio 2010 SP1.|
|Windows Communication Foundation, Windows Presentation Foundation|É possível abrir esse projeto no Visual Studio 2013, Visual Studio 2012 e Visual Studio 2010 SP1.|
|Windows Mobile|Este projeto não pode ser aberto no Visual Studio 2013, pois ele não é compatível com o tipo de projeto.|
|Windows Phone 7,1|Caso permita que o Visual Studio atualize o projeto para o Windows Phone 8.0, será possível abri-lo no Visual Studio 2012 e no Visual Studio 2013.|
|Outros|É possível abrir a maioria dos outros tipos de projetos no Visual Studio 2012, no Visual Studio 2013 e no Visual Studio 2010 SP1.|
|Sites do FrontPage|Este projeto não pode ser aberto no Visual Studio 2013, pois ele não é compatível com o tipo de projeto.|
|Biblioteca de Classes Portátil|Se você permitir que o Visual Studio atualize o projeto automaticamente, será possível abri-lo no Visual Studio 2013, Visual Studio 2012 ou Visual Studio 2010 SP1.<br /><br /> –    Os projetos direcionados ao Silverlight 4 serão direcionados ao Silverlight 5.<br />–    Os projetos direcionados ao Windows Phone 7.0 ou ao Windows Phone 7.5 serão direcionados ao Windows Phone 8.<br />–    Os projetos direcionados ao Xbox 360 não serão mais direcionados ao Xbox 360.|
|Projetos do Azure, como projetos de serviços de nuvem (extensão .ccproj) e projetos do Azure Resource Manager (Projetos de Implantação em Nuvem) com a extensão .deployproj|Para abrir esses tipos de projetos, primeiro instale o [SDK do Azure para .NET](https://azure.microsoft.com/downloads/) e, em seguida, abra o projeto.|

## <a name="troubleshooting-project-compatibility-issues"></a>Solucionando problemas de compatibilidade de projeto
 Veja a seguir algumas ações que poderão ser realizadas quando não for possível abrir um projeto no Visual Studio 2015 ou no Visual Studio 2013:

- Caso tente abrir um projeto que não seja compatível com o Visual Studio 2015 ou o Visual Studio 2013 e para o qual a versão associada do Visual Studio não esteja instalada, uma mensagem poderá ser exibida informando que o tipo de projeto não é compatível. Além disso, o tipo de projeto poderá ser listado na caixa de diálogo **Examinar Alterações de Projeto e de Solução** em **Projetos incompatíveis**. Para resolver esse problema, abra a página de programas e recursos no **Painel de Controle** do Windows, selecione **Visual Studio** e, em seguida, escolha **Alterar**, **Reparar**. Em seguida, você pode instalar a versão ausente.

- Se você tentar abrir um projeto para um aplicativo da área de trabalho no [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)], ocorrerá um erro, e uma destas mensagens será exibida: "Esta edição do Visual Studio oferece suporte somente a aplicativos do [!INCLUDE[win81](../includes/win81-md.md)]" ou "Este projeto é incompatível com a edição atual do Visual Studio". O [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] está restrito ao desenvolvimento, ao teste e à implantação dos aplicativos da Windows Store destinados ao Windows 8.1. Para abrir um projeto de aplicativo da área de trabalho, você deve usar uma edição do Visual Studio que ofereça suporte a esse tipo de projeto.

   Para obter mais informações sobre as edições do Visual Studio, confira [Produtos do Microsoft Visual Studio](https://visualstudio.microsoft.com/products/)

- Se você tentar abrir um projeto de aplicativo da Windows Store no [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop, ocorrerá um erro. Não é possível usar o [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop para criar aplicativos da Windows Store. Se desejar compilar aplicativos da Windows Store, você também poderá instalar o [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]. Ou, para desenvolver aplicativos para todas as plataformas da Microsoft e da Web, tente o Visual Studio Professional 2013.

- Caso um projeto exija recursos específicos do Visual Studio 2013, ele não poderá ser aberto em uma versão anterior.

- Caso esteja usando o Visual Studio 2012 e deseja abrir um projeto criado no Visual Studio 2013, talvez seja possível personalizar o sistema do projeto para incorporar os recursos do Visual Studio 2013. Para saber mais sobre como isso, confira [Habilitar o reconhecimento de versão em projetos personalizados](../misc/making-custom-projects-version-aware.md).

  Para obter informações adicionais de solução de problemas, confira o artigo da base de dados de conhecimento [Compatibilidade do Visual Studio 2013](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview).

## <a name="file"></a> Arquivos

A lista a seguir identifica se o Visual Studio 2013 é compatível com cada tipo de arquivo, se é possível abrir o arquivo no Visual Studio 2012 e no Visual Studio 2010 SP1, além de mostrar se é necessário modificá-lo para garantir a compatibilidade.

|Tipo de arquivo|Compatibilidade|
|------------------|-------------------|
|AppManifest, Inbrowsersettings, OutOfBrowserSettings (arquivos .xml)|É possível abrir estes arquivos no Visual Studio 2012, no Visual Studio 2013 e no Visual Studio 2010 SP1.|
|Esquemas de arquivo simples do BizTalk|É possível adicionar estes esquemas a um projeto do BizTalk 2013 no Visual Studio 2013. Para usar o Visual Studio 2013 com projetos do BizTalk 2010 que têm esquemas de arquivo simples, instale o BizTalk 2013 em um computador que tenha o Visual Studio 2013. Na primeira vez em que abrir o projeto do BizTalk 2010, ele será atualizado automaticamente para o sistema de projeto do BizTalk 2013 ou do Visual Studio 2013.|
|Arquivos de definição de relatório do cliente (.rdlc)|É possível abrir estes arquivos no Visual Studio 2013 e o esquema será atualizado automaticamente caso adicione os recursos e controles do Visual Studio 2013.|
|Conjunto de regras da análise de código|É possível abrir estes arquivos no Visual Studio 2012, no Visual Studio 2013 e no Visual Studio 2010 SP1.|
|Arquivos de pacote de aplicativos de camada de dados|É possível abrir estes arquivos no Visual Studio 2013 caso estejam na versão 2.0 ou na versão 2.5.|
|Arquivos de despejo do depurador|É possível abrir estes arquivos no Visual Studio 2012, no Visual Studio 2013 e no Visual Studio 2010 SP1.|
|Arquivos de diagrama DGML|É possível abrir estes arquivos no Visual Studio 2012, no Visual Studio 2013 e no Visual Studio 2010 SP1 sem alterar o arquivo.|
|Arquivos EDMX (Modelo de Dados de Entidade)|No Visual Studio 2013, será possível abrir um arquivo EDMX destinado ao .NET Framework 4.5 ou ao .NET Framework 4 sem fazer alterações no arquivo.|
|Arquivos de relatório do Criador de Perfil|É possível abrir arquivos de relatório do Profiler (.vsp, .vsps, .psess e .vspf) no Visual Studio 2012 e no Visual Studio 2013. Um arquivo .vspx não pode ser aberto no Visual Studio 2010 SP1.|
|Arquivo de solução (.suo)|É possível usar o Visual Studio 2013 para abrir um arquivo de solução criado no Visual Studio 2012 ou no Visual Studio 2010 SP1|
|SQL Server Compact Edition|O Visual Studio 2013 não é compatível com o SQL Server Compact Edition.|
|Arquivos SQLX|Para abrir estes arquivos no Visual Studio 2013, será necessário executar uma atualização unidirecional, implantar o arquivo .sqlx na versão de destino do Visual Studio e recompilar o arquivo no formato .dacpac.|
|Arquivos de log do IntelliTrace do [!INCLUDE[vs2010](../includes/vs2010-md.md)]|É possível abrir estes arquivos no Visual Studio 2012, no Visual Studio 2013 e no Visual Studio 2010 SP1.|
|Arquivos JavaScript Memory Analyzer (.diagsession)|Os arquivos criados por versões anteriores do Visual Studio poderão ser exibidos no Visual Studio 2013. No entanto, dependendo das informações coletadas, os arquivos criados no Visual Studio 2013 podem não abrir no Visual Studio 2012 ou no Visual Studio 2010 SP1.|

## <a name="integration"></a> Ativos de integração

Você poderá encontrar problemas de compatibilidade se usar clientes e servidores de versões diferentes do Visual Studio Team Foundation Server.

|Tipo de integração|Compatibilidade|
|-------------------------|-------------------|
|Análise do Código e Meu Trabalho|Os recursos Análise do Código e Meu Trabalho não funcionarão se você conectar um cliente do [!INCLUDE[esprfound](../includes/esprfound-md.md)] ao [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)].|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|Não é possível usar um ambiente de 64 bits, como o MSBuild ou [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] para compilar aplicativos do [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] que são criados no [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)].|

## <a name="see-also"></a>Veja também

- [Tornando projetos personalizados com reconhecimento de versão](../misc/making-custom-projects-version-aware.md)
