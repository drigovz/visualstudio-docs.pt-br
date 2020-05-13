---
title: Instalar o Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 04/15/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bfc573c30281e5bc976ee25ea3a80a2f874ab25
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445067"
---
# <a name="install-visual-studio-2015"></a>Instalar o Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta página inclui informações detalhadas para ajudá-lo com a instalação do **Visual Studio 2015**, nosso conjunto integrado de ferramentas de produtividade para desenvolvedores. Também incluímos links para levá-lo rapidamente a informações sobre [recursos,](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-version-history) [requisitos do sistema,](https://docs.microsoft.com/visualstudio/productinfo/vs2015-sysrequirements-vs) [downloads](https://visualstudio.microsoft.com/vs/older-downloads/)e muito mais.

## <a name="quick-links"></a>Links rápidos

Antes de nos aprofundarmos nos detalhes, aqui está uma lista dos nossos links mais solicitados.

|||
|------------------|----------------|
|![Baixar o Visual Studio](../install/media/downloads.png "Downloads") |**Downloads**: Para instalar o Visual Studio 2015, você pode baixar um arquivo executável do produto da página [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (assinatura necessária) ou usar a mídia de instalação do produto em caixa. [Saiba mais sobre como baixar versões atuais ou anteriores do Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Saiba mais sobre recursos](../install/media/features.png "Recursos") |**Características**: Para saber mais sobre os recursos no Visual Studio 2015, consulte as notas de lançamento para [RTM](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-rtm-vs), [Update 1](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update1-vs), [Update 2](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update2-vs)e Update [3](https://docs.microsoft.com/visualstudio/releasenotes/vs2015-update3-vs).|
|![Ver os requisitos do sistema](../install/media/system-requirements.png "Requisitos do Sistema") |**Requisitos do sistema**: Para visualizar os requisitos do sistema para cada edição do Visual Studio 2015, consulte a página [de Segmentação e Compatibilidade da Plataforma Visual Studio 2015.](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs)|
|![Localize sua chave de produto](../install/media/product-keys.png "Chaves do produto") |**Chaves do produto**: Para localizar a chave do produto, consulte o tópico [Como localizar o tópico Chave do Produto do Visual Studio.](../install/how-to-locate-the-visual-studio-product-key.md)|
|![Saiba mais sobre licenciamento](../install/media/licensing.png "Licenciamento") |**Licenciamento**: Para saber mais sobre as opções de licenciamento para pessoas físicas ou clientes corporativos, consulte o [Visual Studio 2015 Licensing White Paper](https://www.microsoft.com/download/details.aspx?id=13350).|

## <a name="default-vs-custom-setup"></a><a name="custom"></a>Configuração padrão vs. personalizada
 Quando você instala o Visual Studio 2015, você pode incluir ou excluir componentes que você usaria diariamente. Isso significa que uma instalação Padrão será muitas vezes menor e instalará mais rápido do que uma instalação Personalizada. Isso também significa que muitos componentes que foram instalados por padrão em versões anteriores agora são considerados componentes personalizados que você deve selecionar explicitamente nesta versão.

 ![Diálogo de configuração do Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Os componentes personalizados incluem Visual C++, Visual F#, SQL Server Data Tools, ferramentas móveis multiplataforma e SDKs, e SDKs e extensões de terceiros. Você pode instalar qualquer um dos componentes personalizados posteriormente se não os selecionar durante a configuração inicial.

> [!NOTE]
> Uma instalação Personalizada inclui automaticamente os componentes que estão em uma instalação Padrão.

 A lista completa de componentes personalizados é a seguinte:

|Conjuntos de recursos|Componentes|
|------------------|----------------|
|**Atualizações**|Visual Studio 2015 Atualização 3|
|**Linguagens de Programação**|Visual C++<br />Visual F#<br />Python Tools para Visual Studio|
|**Desenvolvimento Web e no Windows**|Cliqueememem nas ferramentas de publicação<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Ferramentas para Desenvolvedores Web da Microsoft<br />Ferramentas PowerShell para Visual Studio (3rd Party)<br />Kit de desenvolvimento do Silverlight<br />Ferramentas de desenvolvimento de aplicativos universais do Windows<br />Ferramentas e SDKs do Windows 10<br />Ferramentas para Windows 8.1 e Windows Phone 8.0/8.1<br />Ferramentas e SDKs do Windows 8.1|
|**Desenvolvimento móvel multiplataforma**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Desenvolvimento Móvel Visual C++ para iOS / Android<br />Clang com o Microsoft CodeGen|
|**Ferramentas Comuns e Kits de Desenvolvimento de Software**|Kit de desenvolvimento nativo do Android (3ª Parte)<br /> Android SDK [3rd Party]<br />APIs de configuração do Android SDK (3ª Parte)<br />Formiga Apache (3ª Parte)<br /> Kit de Desenvolvimento Java SE (3ª Parte)<br /> Joyent Node.js (3ª Parte)|
|**Ferramentas comuns**|Git para Windows (3rd Party)<br />Extensão GitHub para Visual Studio (3rd Party)<br /> Ferramentas de Extensibilidade do Visual Studio|

## <a name="install-visual-studio"></a><a name="installing"></a>Instale o Visual Studio
 Você pode instalar o Visual Studio usando a mídia de instalação (DVDs), usando seu serviço de assinatura Visual Studio a partir do site [My.VisualStudio.com,](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) baixando um instalador web do site [do Visual Studio Downloads](https://visualstudio.microsoft.com/vs/older-downloads/) ou criando um layout de instalação offline (consulte a [página Criar uma instalação offline do Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) para obter mais detalhes).

> [!IMPORTANT]
> Você deve ter credenciais de administrador para instalar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. No entanto, você não precisará delas para usar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] depois de instalá-lo.

 Sua conta de administrador local deve ter os seguintes privilégios habilitados para instalar tudo no Visual Studio.

|Nome de exibição do objeto de diretiva local|Direito do Usuário|
|--------------------------------------|----------------|
|Arquivos de backup e diretórios|SeBackupPrivilege|
|Depurar programas|SeDebugPrivilege|
|Gerenciar a auditoria e o log de segurança|SeSecurityPrivilege|

 Para obter mais informações sobre esse requisito de conta de administrador local, consulte o artigo Base de conhecimento, [a instalação do SQL Server falhará se a conta de configuração não tiver certos direitos de usuário](https://support.microsoft.com/kb/2000257).

### <a name="use-installation-media"></a><a name="BKMK_Media"></a>Use mídia de instalação
 Para instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no diretório raiz na mídia de instalação [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], execute o arquivo de instalação da edição que você deseja:

|Edition|Arquivo de instalação|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Comunidade Visual Studio|vs_community.exe|

### <a name="download-from-the-product-website"></a><a name="BKMK_Website"></a>Baixe no site do produto
 Visite a página [Do Visual Studio Downloads](https://visualstudio.microsoft.com/vs/older-downloads/) e selecione a edição do Visual Studio que você deseja.

### <a name="download-from-your-subscription-service"></a>Baixe do seu serviço de assinatura
 Visite a página [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) e selecione a edição do Visual Studio que você deseja.

### <a name="create-an-offline-installation-layout"></a><a name="BKMK_Offline"></a>Crie um layout de instalação offline
 Se você não [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tiver a mídia de instalação ou não tiver uma assinatura [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do Visual Studio ou não quiser instalar usando o instalador web, você pode executar uma instalação "desconectada" criando o que é conhecido como um layout de instalação offline. Para obter mais informações, consulte [a página Criar uma instalação offline do Visual Studio.](../install/create-an-offline-installation-of-visual-studio.md)

## <a name="deploy-visual-studio-in-an-enterprise"></a><a name="enterprise"></a>Implantar o Visual Studio em uma empresa
 Para obter informações [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sobre como implantar em uma rede, consulte o [Guia de Administrador do Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="install-visual-studio-in-a-virtualized-environment"></a><a name="BKMK_Virtualized"></a>Instale o Visual Studio em um ambiente virtualizado
 **Problemas de vídeo com hiper-v**

 Se você executar o Windows Server 2008 R2 com Hyper-V habilitado e um adaptador gráfico acelerado, é possível perceber lentidão no sistema.

 Para obter mais informações, consulte [O desempenho do vídeo pode diminuir quando um computador baseado no Windows Server 2008 ou no Windows Server 2008 R2 tiver a função Hyper-V ativada e um adaptador](https://support.microsoft.com/kb/961661)de exibição acelerado instalado .

 **Emulando dispositivos com hiper-v**

 Quando você instala o Visual Studio 2015 em hardware real sem virtualização, você pode escolher recursos que permitem a emulação de dispositivos Windows e Android usando Hyper-V. Quando você instalar no Hyper-V, você não será capaz de imitar os dispositivos Windows ou Android. Isso porque os emuladores são eles mesmos máquinas virtuais, e você não pode atualmente hospedar uma VM dentro de outra VM. A solução é ter dispositivos Windows ou Android reais aos quais você pode implantar e depurar diretamente seu aplicativo.

## <a name="install-optional-components"></a><a name="optionalComponents"></a>Instale componentes opcionais
 Se você quiser instalar componentes que talvez não tenha selecionado durante a instalação original, use o procedimento a seguir.

#### <a name="to-install-optional-components"></a>Para instalar componentes opcionais

1. No **Painel de Controle** na página **Programas e Recursos**, escolha a edição do produto à qual deseja adicionar um ou mais componentes e, em seguida, selecione **Alterar**.

2. No Assistente de instalação, escolha **Modificar** e, em seguida, escolha os componentes que deseja instalar.

3. Escolha **Avançar** e, em seguida, siga as instruções restantes.

## <a name="install-offline-help-content"></a><a name="helpContent"></a>Instale conteúdo de ajuda off-line
 Depois de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]instalar, você pode baixar conteúdo adicional de Ajuda para que ele esteja disponível offline.

#### <a name="to-install-or-uninstall-help-content"></a>Para instalar ou desinstalar conteúdo da Ajuda

1. Na barra de menus do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], escolha **Ajuda**, **adicionar e remover conteúdo da Ajuda**.

2. Na guia **Gerenciar Conteúdo** do **Visualizador da Ajuda da Microsoft**, selecione a fonte de instalação do conteúdo da Ajuda.

3. Se você estiver procurando uma coleção da Ajuda específica, digite o nome ou uma palavra-chave na caixa de texto **Pesquisar** e pressione **Enter**.

4. Ao lado do nome da coleção da Ajuda que você deseja, escolha o link **Adicionar** ou **Remover**.

5. Clique no botão **Atualizar.**

   Para obter mais informações sobre como instalar ou implantar ajuda offline, consulte o [Guia do Administrador do Visualizador de Ajuda](../ide/help-viewer-administrator-guide.md).

## <a name="check-for-service-releases-and-product-updates"></a><a name="serviceReleases"></a>Verifique se há lançamentos de serviços e atualizações de produtos
 Como nem todas as extensões são compatíveis, o Visual Studio não atualiza extensões automaticamente quando você atualiza de versões anteriores. Você deve reinstalar as extensões do [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou do editor de software.

#### <a name="to-automatically-check-for-service-releases"></a>Para verificar automaticamente as liberações de serviço

1. Na barra de menu, escolha **Ferramentas**, **Opções**.

2. Na caixa de diálogo **Opções**, expanda **Ambiente** e, em seguida, selecione **Extensões e Atualizações**. Confira se a caixa de seleção **Verificar atualizações automaticamente** está selecionada e, em seguida, escolha **OK**.

## <a name="register-visual-studio"></a>Registre-se Visual Studio

1. Na barra de menus, escolha **Ajuda**, **Sobre**.

     A caixa de diálogo **Sobre** mostra o PID (número de identificação do produto). Você precisará das credenciais pid e windows account (como um Hotmail ou Outlook.com endereço de e-mail e senha) para registrar o produto.

2. Na barra de menus, escolha **Ajuda**, **Registrar Produto**.

## <a name="repair-visual-studio"></a><a name="repair"></a>Estúdio visual de reparo

#### <a name="to-repair-visual-studio"></a>Para reparar o Visual Studio

1. No **Painel de Controle,** na página **Programas e Recursos,** escolha a edição do produto que deseja reparar e escolha **Alterar**.

2. No Assistente de instalação, escolha **Reparar**, escolha **Avançar** e, em seguida, siga as instruções restantes.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Para reparar o Visual Studio em modos silenciosos ou passivos (isto é, para reparar a partir da fonte)

1. No computador onde o Visual Studio está instalado, abra o prompt de comando do Windows.

2. Insira os parâmetros s seguir:

     *Arquivo de* \\ <\> `norestart`instalação DVDRoot> [/ ]/ *Installation File* \< `/quiet|/passive``Repair`

## <a name="troubleshoot-an-installation"></a><a name="troubleshooting"></a>Solucionar problemas de uma instalação
 Utilize os seguintes recursos para conseguir ajuda para problemas de configuração e instalação:

- Fórum de [Instalação e configuração do Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/vssetup/threads). Leia perguntas e respostas de outras pessoas na comunidade do Visual Studio. Se você não encontrar o que precisa, faça suas próprias perguntas.

- [Obtenha ajuda com o Visual Studio](https://visualstudio.microsoft.com/vs/support/vs2015/). Encontre artigos da Base de Conhecimento (KB) e aprenda a entrar em contato com o Microsoft Support para obter informações sobre problemas com a instalação do Visual Studio.

## <a name="related-topics"></a><a name="relatedTopics"></a>Tópicos Relacionados

|Title|Descrição|
|-----------|-----------------|
|[Crie uma instalação offline do Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Descreve como instalar o Visual Studio quando você não está conectado à Internet.
|[Instale versões do Visual Studio lado a lado](../install/install-visual-studio-versions-side-by-side.md)|Fornece informações sobre como instalar várias versões do Visual Studio no mesmo computador.|
|[Use parâmetros de linha de comando para instalar o Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Lista os parâmetros de linha de comando que você pode usar quando instala o Visual Studio a partir de um prompt de comando.|
|[Desinstalar o Visual Studio](../install/uninstall-visual-studio.md)|Descreve como desinstalar o Visual Studio.|
|[Guia de Administrador do Estúdio Visual](../install/visual-studio-administrator-guide.md)|Fornece informações sobre as opções de implantação do Visual Studio.|
|[A Biblioteca de Imagens do Estúdio Visual](../designers/the-visual-studio-image-library.md)|Fornece informações sobre como instalar os gráficos que podem ser usados em aplicativos do Visual Studio.|
|[Comece a se desenvolver com o Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Inclui informações e links que podem ajudá-lo a usar o Visual Studio de forma mais eficaz.|

## <a name="see-also"></a>Consulte Também

- [Entrando no Visual Studio](../ide/signing-in-to-visual-studio.md)
