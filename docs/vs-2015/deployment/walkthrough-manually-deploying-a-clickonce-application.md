---
title: 'Walkthrough: Implantando manualmente um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e1099eaf8d766088612abbb399bdf004e6378e4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294682"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Instruções passo a passo: implantando um aplicativo ClickOnce manualmente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você não puder usar o Visual Studio para implantar seu aplicativo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ou se precisar usar recursos avançados de implantação, como a implantação de aplicativo confiável, deverá usar a ferramenta de linha de comando Mage. exe para criar seus manifestos [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Este tutorial descreve como criar uma implantação de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] usando a versão de linha de comando (Mage. exe) ou a versão gráfica (MageUI. exe) do Manifest Generation and Editing Tool.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Este tutorial tem alguns pré-requisitos e opções que você precisa escolher antes de criar uma implantação.  
  
- Instale o Mage. exe e o MageUI. exe.  
  
     O Mage. exe e o MageUI. exe fazem parte do [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Você deve ter o [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] instalado ou a versão do [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] incluída com o Visual Studio. Para obter mais informações, consulte [SDK do Windows](https://go.microsoft.com/fwlink/?LinkId=158044) no msdn.  
  
- Forneça um aplicativo para implantar.  
  
     Este tutorial pressupõe que você tenha um aplicativo do Windows que você está pronto para implantar. Esse aplicativo será chamado de AppToDeploy.  
  
- Determine como a implantação será distribuída.  
  
     As opções de distribuição incluem: Web, compartilhamento de arquivos ou CD. Para obter mais informações, consulte [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
- Determine se o aplicativo requer um nível elevado de confiança.  
  
     Se seu aplicativo exigir confiança total — por exemplo, acesso completo ao sistema do usuário — você pode usar a opção `-TrustLevel` de Mage. exe para definir isso. Se você quiser definir um conjunto de permissões personalizado para seu aplicativo, poderá copiar a seção de permissão da Internet ou da intranet de outro manifesto, modificá-la para atender às suas necessidades e adicioná-la ao manifesto do aplicativo usando um editor de texto ou MageUI. exe. Para saber mais, veja [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
- Obtenha um certificado Authenticode.  
  
     Você deve assinar sua implantação com um certificado Authenticode. Você pode gerar um certificado de teste usando as ferramentas do Visual Studio, MageUI. exe ou MakeCert. exe e Pvk2Pfx. exe, ou pode obter um certificado de uma autoridade de certificação (CA). Se você optar por usar a implantação de aplicativo confiável, também deverá executar uma instalação única do certificado em todos os computadores cliente. Para saber mais, veja [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    > Você também pode assinar sua implantação com um certificado CNG que pode ser obtido de uma autoridade de certificação.  
  
- Certifique-se de que o aplicativo não tenha um manifesto com informações de UAC.  
  
     Você precisa determinar se seu aplicativo contém um manifesto com informações de controle de conta de usuário (UAC), como um elemento `<dependentAssembly>`. Para examinar um manifesto do aplicativo, você pode usar o utilitário [Sigcheck](https://go.microsoft.com/fwlink/?LinkId=158035) do Windows Sysinternals.  
  
     Se seu aplicativo contiver um manifesto com detalhes do UAC, você deverá compilá-lo novamente sem as informações do UAC. Para um C# projeto no Visual Studio, abra as propriedades do projeto e selecione a guia aplicativo. Na lista suspensa **manifesto** , selecione **criar aplicativo sem um manifesto**. Para um projeto Visual Basic no Visual Studio, abra as propriedades do projeto, selecione a guia aplicativo e clique em **exibir configurações de UAC**. No arquivo de manifesto aberto, remova todos os elementos dentro do único elemento `<asmv1:assembly>`.  
  
- Determine se o aplicativo requer pré-requisitos no computador cliente.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos implantados do Visual Studio podem incluir um bootstrapper de instalação de pré-requisito (Setup. exe) com sua implantação. Este tutorial cria os dois manifestos necessários para uma implantação de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Você pode criar um bootstrapper de pré-requisito usando a [tarefa GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Para implantar um aplicativo com a ferramenta de linha de comando Mage. exe  
  
1. Crie um diretório onde você armazenará seus [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] arquivos de implantação.  
  
2. No diretório de implantação que você acabou de criar, crie um subdiretório de versão. Se esta for a primeira vez que você está implantando o aplicativo, nomeie o subdiretório de versão **1.0.0.0**.  
  
    > [!NOTE]
    > A versão da sua implantação pode ser distinta da versão do seu aplicativo.  
  
3. Copie todos os arquivos do aplicativo para o subdiretório da versão, incluindo arquivos executáveis, assemblies, recursos e arquivos de dados. Se necessário, você pode criar subdiretórios adicionais que contenham arquivos adicionais.  
  
4. Abra o prompt de comando do [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] ou do Visual Studio e altere para o subdiretório da versão.  
  
5. Crie o manifesto do aplicativo com uma chamada para Mage. exe. A instrução a seguir cria um manifesto de aplicativo para o código compilado para ser executado no processador Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    > Certifique-se de incluir o ponto (.) após a opção `-FromDirectory`, que indica o diretório atual. Se você não incluir o ponto, deverá especificar o caminho para os arquivos do aplicativo.  
  
6. Assine o manifesto do aplicativo com seu certificado Authenticode. Substitua *MyCert. pfx* pelo caminho para o arquivo de certificado. Substitua *passwd* pela senha do seu arquivo de certificado.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Para assinar o manifesto do aplicativo com um certificado CNG, use o seguinte. Substitua *cngCert. pfx* pelo caminho para o arquivo de certificado.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7. Altere para a raiz do diretório de implantação.  
  
8. Gere o manifesto de implantação com uma chamada para Mage. exe. Por padrão, o Mage. exe marcará sua implantação do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] como um aplicativo instalado, para que possa ser executado online e offline. Para disponibilizar o aplicativo somente quando o usuário estiver online, use a opção `-Install` com um valor de `false`. Se você usar o padrão, e os usuários instalarem seu aplicativo de um site ou compartilhamento de arquivos, certifique-se de que o valor da opção `-ProviderUrl` aponte para o local do manifesto do aplicativo no servidor Web ou compartilhamento.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Assine o manifesto de implantação com seu certificado de Authenticode ou CNG.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     ou  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Copie todos os arquivos no diretório de implantação para o destino ou a mídia de implantação. Pode ser uma pasta em um site da Web ou site FTP, um compartilhamento de arquivos ou um CD-ROM.  
  
11. Forneça aos usuários a URL, UNC ou mídia física necessária para instalar o aplicativo. Se você fornecer uma URL ou um UNC, deverá dar aos usuários o caminho completo para o manifesto de implantação. Por exemplo, se AppToDeploy for implantado em http://webserver01/ no diretório AppToDeploy, o caminho de URL completo será http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Para implantar um aplicativo com a ferramenta gráfica MageUI. exe  
  
1. Crie um diretório onde você armazenará seus [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] arquivos de implantação.  
  
2. No diretório de implantação que você acabou de criar, crie um subdiretório de versão. Se esta for a primeira vez que você está implantando o aplicativo, nomeie o subdiretório de versão **1.0.0.0**.  
  
    > [!NOTE]
    > A versão da sua implantação é provavelmente distinta da versão do seu aplicativo.  
  
3. Copie todos os arquivos do aplicativo para o subdiretório da versão, incluindo arquivos executáveis, assemblies, recursos e arquivos de dados. Se necessário, você pode criar subdiretórios adicionais que contenham arquivos adicionais.  
  
4. Inicie a ferramenta gráfica MageUI. exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5. Crie um novo manifesto de aplicativo selecionando **arquivo**, **novo**, **manifesto do aplicativo** no menu.  
  
6. Na guia **nome** padrão, digite o nome e o número de versão dessa implantação. Especifique também o **processador** para o qual seu aplicativo é criado, como x86.  
  
7. Selecione a guia **arquivos** e clique no botão de reticências ( **...** ) ao lado da caixa de texto **diretório de aplicativo** . Uma caixa de diálogo Procurar pasta é exibida.  
  
8. Selecione o subdiretório da versão que contém os arquivos do aplicativo e clique em **OK**.  
  
9. Se você for implantar do Serviços de Informações da Internet (IIS), marque a caixa de seleção **ao preencher adicionar a extensão. Deploy a qualquer arquivo que não tenha** essa marca.  
  
10. Clique no botão **popular** para adicionar todos os seus arquivos de aplicativo à lista de arquivos. Se seu aplicativo contiver mais de um arquivo executável, marque o arquivo executável principal para essa implantação como o aplicativo de inicialização selecionando **ponto de entrada** na lista suspensa **tipo de arquivo** . (Se seu aplicativo contiver apenas um arquivo executável, o MageUI. exe o marcará para você.)  
  
11. Selecione a guia **permissões necessárias** e selecione o nível de confiança que você precisa que seu aplicativo declare. O padrão é **FullTrust**, que será adequado para a maioria dos aplicativos.  
  
12. Selecione **arquivo**, **salvar como** no menu. Uma caixa de diálogo opções de assinatura é exibida solicitando que você assine o manifesto do aplicativo.  
  
13. Se você tiver um certificado armazenado como um arquivo no sistema de arquivos, use a opção **entrar com o arquivo de certificado** e selecione o certificado do sistema de arquivos usando o botão de reticências ( **...** ). Em seguida, digite a senha do certificado.  
  
     - ou -  
  
     Se o certificado for mantido em um repositório de certificados acessível do seu computador, selecione a opção **assinar com o certificado armazenado** e selecione o certificado na lista fornecida.  
  
14. Clique em **OK** para assinar o manifesto do aplicativo. A caixa de diálogo Salvar como é exibida.  
  
15. Na caixa de diálogo Salvar como, especifique o diretório da versão e clique em **salvar**.  
  
16. Selecione **arquivo**, **novo**, **manifesto de implantação** no menu para criar seu manifesto de implantação.  
  
17. Na guia **nome** , especifique um nome e um número de versão para essa implantação (**1.0.0.0** neste exemplo). Especifique também o **processador** para o qual seu aplicativo é criado, como x86.  
  
18. Selecione a guia **Descrição** e especifique os valores para o **Editor** e o **produto**. (**Produto** é o nome dado ao seu aplicativo no menu Iniciar do Windows quando o aplicativo é instalado em um computador cliente para uso offline.)  
  
19. Selecione a guia **Opções de implantação** e, na caixa de texto local de **início** , especifique o local do manifesto do aplicativo no servidor Web ou compartilhamento. Por exemplo, \\\myServer\myShare\AppToDeploy.application.  
  
20. Se você adicionou a extensão. Deploy em uma etapa anterior, selecione também **usar. implantar extensão de nome de arquivo** aqui.  
  
21. Selecione a guia **Opções de atualização** e especifique com que frequência você deseja que esse aplicativo seja atualizado. Se seu aplicativo usar <xref:System.Deployment.Application.UpdateCheckInfo> para verificar se há atualizações em si, desmarque a caixa de seleção **este aplicativo deve verificar** se há atualizações.  
  
22. Selecione a guia **referência de aplicativo** e clique no botão **selecionar manifesto** . Será exibida uma caixa de diálogo aberta.  
  
23. Selecione o manifesto do aplicativo que você criou anteriormente e clique em **abrir**.  
  
24. Selecione **arquivo**, **salvar como** no menu. Uma caixa de diálogo opções de assinatura é exibida solicitando que você assine o manifesto de implantação.  
  
25. Se você tiver um certificado armazenado como um arquivo no sistema de arquivos, use a opção **entrar com o arquivo de certificado** e selecione o certificado do sistema de arquivos usando o botão de reticências ( **...** ). Em seguida, digite a senha do certificado.  
  
     - ou -  
  
     Se o certificado for mantido em um repositório de certificados acessível do seu computador, selecione a opção **assinar com o certificado armazenado** e selecione o certificado na lista fornecida.  
  
26. Clique em **OK** para assinar seu manifesto de implantação. A caixa de diálogo Salvar como é exibida.  
  
27. Na caixa de diálogo **salvar como** , mova um diretório para cima até a raiz de sua implantação e clique em **salvar**.  
  
28. Copie todos os arquivos no diretório de implantação para o destino ou a mídia de implantação. Pode ser uma pasta em um site da Web ou site FTP, um compartilhamento de arquivos ou um CD-ROM.  
  
29. Forneça aos usuários a URL, UNC ou mídia física necessária para instalar o aplicativo. Se você fornecer uma URL ou um UNC, deverá dar aos usuários o caminho completo do manifesto de implantação. Por exemplo, se AppToDeploy for implantado em http://webserver01/ no diretório AppToDeploy, o caminho de URL completo será http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Próximas etapas  
 Quando você precisar implantar uma nova versão do aplicativo, crie um novo diretório chamado após a nova versão — por exemplo, 1.0.0.1 — e copie os novos arquivos de aplicativo para o novo diretório. Em seguida, você precisa seguir as etapas anteriores para criar e assinar um novo manifesto de aplicativo e atualizar e assinar o manifesto de implantação. Tenha cuidado para especificar a mesma versão mais alta nas chamadas de `-New` e `–Update` de Mage. exe, pois [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] apenas atualiza as versões superiores, com o inteiro mais significativo mais importante. Se você tiver usado o MageUI. exe, poderá atualizar o manifesto de implantação abrindo-o, selecionando a guia **referência do aplicativo** , clicando no botão **selecionar manifesto** e, em seguida, selecionando o manifesto do aplicativo atualizado.  
  
## <a name="see-also"></a>Consulte também  
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest Generation and Editing Tool, Cliente Gráfico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
   de [manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)  
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
