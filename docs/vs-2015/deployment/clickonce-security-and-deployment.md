---
title: Segurança do ClickOnce e implantação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 17b906f721bea6e4183575eced962e9ed830cda1
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675454"
---
# <a name="clickonce-security-and-deployment"></a>Segurança e implantação do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] é uma tecnologia de implantação que permite que você crie aplicativos AutoAtualizáveis baseados em Windows que podem ser instalados e executados com interação mínima do usuário. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornece suporte completo para publicar e atualizar aplicativos implantados com a tecnologia ClickOnce, se você tiver desenvolvido seus projetos com o Visual Basic e Visual c#. Para obter informações sobre como implantar aplicativos do Visual C++, consulte [implantação de ClickOnce para aplicativos do Visual C++](https://msdn.microsoft.com/library/9988c546-0936-452c-932f-9c76daa42157).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação supera três grandes problemas na implantação:  
  
- **Dificuldades na atualização de aplicativos.** Com a implantação do Microsoft Windows Installer, sempre que um aplicativo é atualizado, o usuário pode instalar uma atualização, um arquivo msp e aplicá-lo para o produto instalado; com [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação, você pode fornecer atualizações automaticamente. Somente as partes do aplicativo que foram alteradas serão baixadas e, em seguida, o aplicativo atualizado é reinstalado a partir de uma nova pasta lado a lado.  
  
- **Impacto para o computador do usuário.** Com a implantação do Windows Installer, aplicativos quase sempre utilizam componentes compartilhados, com o potencial para conflitos de controle de versão; com [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação, cada aplicativo é independente e não consegue interferir em outros aplicativos.  
  
- **Permissões de segurança.** Implantação do Windows Installer requer permissões administrativas e permite que somente a instalação do usuário limitados; [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação permite que os usuários não administrativos instalar e concede somente as permissões de segurança de acesso do código necessárias para o aplicativo.  
  
  No passado, esses problemas causados, às vezes, os desenvolvedores decidissem criar aplicativos da Web em vez de aplicativos baseados em Windows, sacrificar a uma interface do usuário avançada para facilitar a instalação. Usando os aplicativos implantados usando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], você pode ter o melhor de ambas as tecnologias.  
  
## <a name="what-is-a-clickonce-application"></a>O que é um aplicativo ClickOnce?  
 Um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo é qualquer (. xbap) do Windows Presentation Foundation, Windows Forms (.exe), o aplicativo de console (.exe) ou solução do Office (. dll) publicados usando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tecnologia. Você pode publicar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo de três maneiras diferentes: de uma página da Web, um compartilhamento de arquivos de rede ou mídia como um CD-ROM. Um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo pode ser instalado no computador do usuário final e executar localmente, mesmo quando o computador estiver offline ou pode ser executado em modo somente online sem permanentemente instalar nada no computador do usuário final. Para obter mais informações, consulte [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos podem ser independentes; ele podem verificar novas versões quando elas se tornarem disponíveis e substituem automaticamente qualquer arquivo atualizado. O desenvolvedor pode especificar o comportamento da atualização; um administrador de rede também pode controlar estratégias de atualização, marcando uma atualização como obrigatória, por exemplo. As atualizações podem também ser revertidas para uma versão anterior pelo usuário final ou por um administrador. Para obter mais informações, confira [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Porque [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] os aplicativos são isolados, instalar ou executar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo não pode interromper aplicativos existentes. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos são independentes; cada [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo é instalado para e executar um seguro por usuário, cache por aplicativo. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] os aplicativos executados nas zonas de segurança da Internet ou Intranet. Se necessário, o aplicativo poderá solicitar permissões de segurança elevadas. Para obter mais informações, consulte [Securing ClickOnce Applications](../deployment/securing-clickonce-applications.md) (Protegendo aplicativos ClickOnce).  
  
## <a name="how-clickonce-security-works"></a>Como funciona a segurança do ClickOnce  
 O núcleo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] é baseada em certificados, as políticas de segurança de acesso do código e o prompt de confiança do ClickOnce.  
  
### <a name="certificates"></a>Certificados  
 Certificados Authenticode são usados para verificar a autenticidade do Editor do aplicativo. Ao usar Authenticode para implantação de aplicativos, o ClickOnce ajuda a impedir que um programa prejudicial representando a mesmo como um programa legítimo proveniente de uma fonte confiável e estabelecida. Opcionalmente, certificados também podem ser usados para assinar o aplicativo e manifestos de implantação para provar que os arquivos não foram violados. Para obter mais informações, consulte [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). Certificados também podem ser usados para configurar computadores cliente para ter uma lista de editores confiáveis. Se um aplicativo vier de um fornecedor confiável, ele pode ser instalado sem interação do usuário. Para saber mais, veja [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Segurança de acesso do código  
 Segurança de acesso de código ajuda a limitar o acesso que o código tem a recursos protegidos. Na maioria dos casos, você pode escolher as zonas da Internet ou Intranet Local para limitar as permissões. Use o **segurança** página na **ProjectDesigner** para solicitar a zona apropriada para o aplicativo. Você também pode depurar aplicativos com permissões restritas para emular a experiência do usuário final. Para obter mais informações, consulte [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>Prompt confiável do ClickOnce  
 Se o aplicativo solicitar mais permissões do que permite que a zona, o usuário final pode ser solicitado a tomar uma decisão de confiança. O usuário final pode decidir se os aplicativos ClickOnce, como aplicativos do Windows Forms, aplicativos do Windows Presentation Foundation, aplicativos de console, aplicativos de navegador XAML e soluções do Office são confiáveis para executar. Para obter mais informações, confira [Como: Configurar o comportamento do Prompt confiável do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Como funciona a implantação do ClickOnce  
 O núcleo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] arquitetura de implantação se baseia em dois arquivos de manifesto XML: um manifesto de aplicativo e um manifesto de implantação. Os arquivos são usados para descrever onde os aplicativos ClickOnce são instalados a partir, como eles são atualizados e quando eles são atualizados.  
  
### <a name="publishing-clickonce-applications"></a>Publicando aplicativos ClickOnce  
 O manifesto do aplicativo descreve o próprio aplicativo. Isso inclui os assemblies, as dependências e os arquivos que compõem o aplicativo, as permissões necessárias e o local onde as atualizações estarão disponíveis. Os desenvolvedores de aplicativo criam o manifesto do aplicativo usando o Assistente de publicação no Visual Studio ou o Manifest Generation and Editing Tool (Mage.exe) na [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Para obter mais informações, confira [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 O manifesto de implantação descreve como o aplicativo é implantado. Isso inclui o local do manifesto do aplicativo e a versão do aplicativo que os clientes devem ser executados.  
  
### <a name="deploying-clickonce-applications"></a>Implantando aplicativos ClickOnce  
 Depois de criado, o manifesto de implantação é copiado para a localização de implantação. Pode ser um servidor Web, um compartilhamento de arquivo de rede ou uma mídia como um CD. O manifesto do aplicativo e todos os arquivos de aplicativo também são copiados para um local de implantação que é especificado no manifesto de implantação. Pode ser igual à localização de implantação ou não. Ao usar o **Assistente de publicação** no Visual Studio, as operações de cópia são executadas automaticamente.  
  
### <a name="installing-clickonce-applications"></a>Instalação de aplicativos ClickOnce  
 Depois de colocado na localização de implantação, os usuários finais podem baixar e instalar o aplicativo clicando em um ícone que representa o arquivo de manifesto de implantação em uma página da Web ou em uma pasta. Na maioria dos casos, o usuário final é apresentado com uma caixa de diálogo simples solicitando que o usuário confirme a instalação, depois que ela possa prosseguir e o aplicativo é iniciado sem intervenção adicional. Em casos em que o aplicativo requer permissões elevadas ou se o aplicativo não está assinado por um certificado confiável, a caixa de diálogo pede que o usuário para conceder permissão para que a instalação possa continuar. Embora instalações do ClickOnce são por usuário, elevação de permissões pode ser necessária se há pré-requisitos que requerem privilégios de administrador. Para obter mais informações sobre permissões elevadas, consulte [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 Certificados podem ser confiáveis no nível de máquina ou enterprise, para que os aplicativos ClickOnce assinados com um certificado confiável podem instalar silenciosamente. Para obter mais informações sobre certificados confiáveis, consulte [visão geral da implantação de aplicativo confiável](../deployment/trusted-application-deployment-overview.md).  
  
 O aplicativo pode ser adicionado para o usuário **inicie** menu e o **adicionar ou remover programas** grupo o **painel de controle**. Ao contrário de outras tecnologias de implantação, nada é adicionado a **arquivos de programas** pasta ou no registro e não há direitos administrativos são necessários para instalação  
  
> [!NOTE]
> Também é possível impedir que o aplicativo que está sendo adicionado para o **inicie** menu e **adicionar ou remover programas** grupo, em vigor tornando-se comportam como um aplicativo Web. Para obter mais informações, consulte [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="updating-clickonce-applications"></a>Atualizando aplicativos ClickOnce  
 Quando os desenvolvedores de aplicativos criam uma versão atualizada do aplicativo, eles geram um novo manifesto de aplicativo e copiar arquivos para um local de implantação — normalmente uma pasta irmã para a pasta de implantação do aplicativo original. O administrador atualiza o manifesto de implantação para que ele aponte para a localização da nova versão do aplicativo.  
  
> [!NOTE]
> O **Assistente de publicação** no Visual Studio pode ser usado para executar essas etapas.  
  
 Além da localização da implantação, o manifesto de implantação também contém uma localização de atualização (uma página da Web ou um compartilhamento de arquivo na rede), em que o aplicativo verifica a existência de versões atualizadas. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] **Publicar** propriedades são usadas para especificar quando e com que frequência o aplicativo deve verificar se há atualizações. Comportamento de atualização pode ser especificado no manifesto de implantação ou ele pode ser apresentado como opções ao usuário na interface do usuário do aplicativo por meio do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] APIs. Além disso, as propriedades **Publish** podem ser empregadas para tornar as atualizações obrigatórias ou para a reversão para uma versão anterior. Para obter mais informações, confira [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Instaladores de terceiros  
 Você pode personalizar o instalador do ClickOnce para instalar componentes de terceiros junto com seu aplicativo. Você deve ter o pacote redistribuível (arquivo. msi ou. .exe) e descrevem o pacote com um manifesto de produto com neutralidade de idioma e um manifesto de pacote de idioma específico. Para obter mais informações, consulte [criação de pacotes de Bootstrapper](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>Ferramentas de ClickOnce  
 A tabela a seguir mostra as ferramentas que você pode usar para gerar, editar, assinar e assinar novamente os manifestos de aplicativo e implantação.  
  
|Ferramenta|Descrição|  
|----------|-----------------|  
|[Página Segurança, Designer de Projeto](../ide/reference/security-page-project-designer.md)|Assina os manifestos de aplicativo e implantação.|  
|[Página de Publicação, Designer de Projeto](../ide/reference/publish-page-project-designer.md)|Gera e edita os manifestos do aplicativo e de implantação para aplicativos Visual Basic e Visual c#.|  
|[Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)|Gera os manifestos do aplicativo e de implantação para aplicativos Visual Basic, Visual c# e Visual C++.<br /><br /> Assina e assina novamente os manifestos de aplicativo e implantação.<br /><br /> Pode ser executado a partir do prompt de comando e scripts em lotes.|  
|[MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)|Gera e edita os manifestos de aplicativo e implantação.<br /><br /> Assina e assina novamente os manifestos de aplicativo e implantação.|  
|[Tarefa GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)|Gera o manifesto do aplicativo.<br /><br /> Podem ser executados do MSBuild. Para mais informações, confira [Referência do MSBuild](../msbuild/msbuild-reference.md).|  
|[Tarefa GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)|Gera o manifesto de implantação.<br /><br /> Podem ser executados do MSBuild. Para mais informações, confira [Referência do MSBuild](../msbuild/msbuild-reference.md).|  
|[Tarefa SignFile](../msbuild/signfile-task.md)|Assina os manifestos de aplicativo e implantação.<br /><br /> Podem ser executados do MSBuild. Para mais informações, confira [Referência do MSBuild](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Desenvolva seu próprio aplicativo para gerar os manifestos de aplicativo e implantação.|  
  
 A tabela a seguir mostra a versão do .NET Framework necessária para dar suporte a aplicativos ClickOnce nesses navegadores.  
  
|Navegador|Versão do .NET Framework|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## <a name="see-also"></a>Consulte também  
 [Implantação do ClickOnce no Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Implantando componentes do COM o ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Criação de aplicativos ClickOnce da linha de comando](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Depurando aplicativos ClickOnce que usam System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
