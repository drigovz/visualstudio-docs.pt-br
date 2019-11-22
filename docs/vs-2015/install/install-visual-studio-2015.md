---
title: Instalar o Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: a31bc328c20aada21b05edeef61886d57e914165
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298045"
---
# <a name="install-visual-studio-2015"></a>Instalar o Visual Studio 2015

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta página inclui informações detalhadas para ajudá-lo a instalar o **Visual Studio 2015**, nosso pacote integrado de ferramentas de produtividade para desenvolvedores. Também incluímos links para obter informações rapidamente sobre [recursos](https://www.visualstudio.com/news/vs2015-vs.aspx), [edições](https://go.microsoft.com/fwlink/?LinkID=242142), [requisitos do sistema](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [downloads](https://go.microsoft.com/fwlink/?LinkId=517106)e muito mais.

## <a name="quick-links"></a>Links rápidos

Antes de nos aprofundarmos nos detalhes, aqui está uma lista de nossos links solicitados com mais frequência.

|||
|------------------|----------------|
|![Baixar o Visual Studio](../install/media/downloads.png "Downloads") |**Downloads**: para instalar o Visual Studio 2015, você pode baixar um arquivo executável do produto da página [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (assinatura necessária) ou usar a mídia de instalação do produto em caixa. [Saiba mais sobre como baixar versões atuais ou anteriores do Visual Studio](https://www.visualstudio.com/vs/older-downloads/).|
|![Saiba mais sobre os recursos](../install/media/features.png "Recursos") |**Recursos**: para saber mais sobre os recursos do Visual Studio 2015, consulte as notas de versão para [RTM](https://www.visualstudio.com/news/vs2015-vs), [atualização 1](https://www.visualstudio.com/news/vs2015-update1-vs), [atualização 2](https://www.visualstudio.com/news/vs2015-update2-vs)e [atualização 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs).|
|![Descubra o que há em cada SKU](../install/media/sku.png "SKUs") |**SKUs**: para descobrir o que está disponível em cada edição do Visual Studio 2015, consulte nossa página [comparar ofertas do Visual Studio](https://go.microsoft.com/fwlink/?LinkID=242142) .|
|![Exibir requisitos do sistema](../install/media/system-requirements.png "Requisitos de sistema") |**Requisitos do sistema**: para exibir os requisitos de sistema para cada edição do Visual Studio 2015, consulte a página de [compatibilidade do Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) .|
|![Localize a chave do produto](../install/media/product-keys.png "Chaves do produto") |**Chaves do produto**: para localizar a chave do produto, consulte o tópico [como localizar a chave do produto Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) .|
|![Saiba mais sobre licenciamento](../install/media/licensing.png "Licenciamento") |**Licenciamento**: para saber mais sobre as opções de licenciamento para indivíduos ou clientes corporativos, consulte o White Paper de [Licenciamento do Visual Studio e do MSDN](https://www.microsoft.com/download/details.aspx?id=13350) .|

## <a name="custom"></a>Configuração padrão vs. personalizada
 Ao instalar o Visual Studio 2015, você pode incluir ou excluir componentes que seriam usados diariamente. Isso significa que uma instalação padrão será geralmente menor e será instalada mais rapidamente do que uma instalação personalizada. Isso também significa que muitos componentes que foram instalados por padrão nas versões anteriores agora são considerados componentes personalizados que você deve selecionar explicitamente nesta versão.

 ![Caixa de diálogo de instalação do Visual Studio 2015](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 Os componentes personalizados incluem C++Visual, F#Visual, SQL Server Data Tools, ferramentas móveis de plataforma cruzada e SDKs, além de SDKs e extensões de terceiros. Você pode instalar qualquer um dos componentes personalizados posteriormente se não os selecionar durante a configuração inicial.

> [!NOTE]
> Uma instalação personalizada inclui automaticamente os componentes que estão em uma instalação padrão.

 A lista completa de componentes personalizados é a seguinte:

|Conjuntos de recursos|Componentes|
|------------------|----------------|
|**Atualizações**|Visual Studio 2015 Atualização 3|
|**Linguagens de programação**|Visual C++<br />Visual F#<br />Ferramentas Python para o Visual Studio|
|**Desenvolvimento Web e no Windows**|Ferramentas de publicação do ClickOnce<br />LightSwitch<br />Microsoft Office Developer Tools<br />Microsoft SQL Server Data Tools<br /> Ferramentas para Desenvolvedores Web da Microsoft<br />PowerShell Tools for Visual Studio (terceiros)<br />Kit de desenvolvimento do Silverlight<br />Ferramentas de desenvolvimento de aplicativos universais do Windows<br />Ferramentas e SDKs do Windows 10<br />Ferramentas Windows 8.1 e Windows Phone 8.0/8.1<br />Ferramentas e SDKs de Windows 8.1|
|**Desenvolvimento móvel multiplataforma**|C#/.NET (Xamarin)<br />HTML/JavaScript (Apache Cordova)<br />Desenvolvimento C++ móvel visual para IOS/Android<br />Clang com o Microsoft CodeGen|
|**Ferramentas comuns e kits de desenvolvimento de software**|Kit de desenvolvimento nativo do Android (terceiros)<br /> SDK do Android [terceiros]<br />APIs de instalação do SDK do Android (terceiros)<br />Apache Ant (terceiros)<br /> Java SE Development Kit (terceiros)<br /> Joyent node. js (terceiros)|
|**Ferramentas comuns**|Git para Windows (terceiros)<br />Extensão do GitHub para Visual Studio (terceiros)<br /> Ferramentas de Extensibilidade do Visual Studio|

## <a name="installing"></a> Instalando o Visual Studio
 Você pode instalar o Visual Studio usando a mídia de instalação (DVDs), usando o serviço de assinatura do Visual Studio no site do [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , baixando um instalador da Web no site de [downloads do Visual Studio](https://go.microsoft.com/fwlink/?LinkId=517106) ou criando um layout de instalação offline (consulte a página [criar uma instalação offline do Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) para obter mais detalhes).

> [!IMPORTANT]
> Você deve ter credenciais de administrador para instalar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. No entanto, você não precisará delas para usar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] depois de instalá-lo.

 Sua conta de administrador local deve ter os seguintes privilégios habilitados para instalar tudo no Visual Studio.

|Nome de exibição do objeto de política local|Direito do usuário|
|--------------------------------------|----------------|
|Arquivos e diretórios de backup|SeBackupPrivilege|
|Depurar programas|SeDebugPrivilege|
|Gerenciar auditoria e log de segurança|SeSecurityPrivilege|

 Para obter mais informações sobre esse requisito de conta de administrador local, consulte o artigo da base de dados de conhecimento, [SQL Server instalação falhará se a conta de instalação não tiver determinados direitos de usuário](https://support.microsoft.com/kb/2000257).

### <a name="BKMK_Media"></a>Usando a mídia de instalação
 Para instalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no diretório raiz na mídia de instalação [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], execute o arquivo de instalação da edição que você deseja:

|Edição|Arquivo de instalação|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Comunidade Visual Studio|vs_community.exe|

### <a name="BKMK_Website"></a>Baixando do site do produto
 Visite a página de [downloads do Visual Studio](https://go.microsoft.com/fwlink/?LinkId=517106) e selecione a edição do Visual Studio que você deseja.

### <a name="downloading-from-your-subscription-service"></a>Baixando de seu serviço de assinatura
 Visite a página [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) e selecione a edição do Visual Studio que você deseja.

### <a name="BKMK_Offline"></a>Criando um layout de instalação offline
 Se você não tiver a mídia de instalação do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou se não tiver uma assinatura do Visual Studio, ou se não quiser instalar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usando o instalador da Web, poderá executar uma instalação "desconectada" criando o que é conhecido como um layout de instalação offline. Para obter mais informações, consulte a página [criar uma instalação offline do Visual Studio](../install/create-an-offline-installation-of-visual-studio.md) .

## <a name="enterprise"></a>Implantando o Visual Studio em uma empresa
 Para obter informações sobre como implantar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] em uma rede, consulte o [Guia do administrador do Visual Studio](../install/visual-studio-administrator-guide.md).

### <a name="BKMK_Virtualized"></a>Instalando o Visual Studio em um ambiente virtualizado
 **Problemas de vídeo com o Hyper-V**

 Se você executar o Windows Server 2008 R2 com Hyper-V habilitado e um adaptador gráfico acelerado, é possível perceber lentidão no sistema.

 Para saber mais, confira a seguinte página no site da Microsoft: [O desempenho de vídeo pode diminuir quando um computador baseado em Windows Server 2008 ou Windows Server 2008 R2 tem a função Hyper-V habilitada e um adaptador de vídeo acelerado instalado](https://go.microsoft.com/fwlink/?LinkID=231084).

 **Emulando dispositivos com o Hyper-V**

 Ao instalar o Visual Studio 2015 em hardware real sem virtualização, você pode escolher recursos que habilitam a emulação de dispositivos Windows e Android usando o Hyper-V. Quando você instala o Hyper-V, não poderá emular os dispositivos Windows ou Android. Isso ocorre porque os emuladores são, em si, máquinas virtuais e não é possível hospedar atualmente uma VM dentro de outra VM. A solução alternativa é ter dispositivos Windows ou Android reais nos quais você pode implantar e depurar o aplicativo diretamente.

## <a name="optionalComponents"></a>Instalando componentes opcionais
 Se você quiser instalar os componentes que você pode não ter selecionado durante a instalação original, use o procedimento a seguir.

#### <a name="to-install-optional-components"></a>Para instalar componentes opcionais

1. No **Painel de Controle** na página **Programas e Recursos**, escolha a edição do produto à qual deseja adicionar um ou mais componentes e, em seguida, selecione **Alterar**.

2. No Assistente de instalação, escolha **Modificar** e, em seguida, escolha os componentes que deseja instalar.

3. Escolha **Avançar** e, em seguida, siga as instruções restantes.

## <a name="helpContent"></a>Instalando o conteúdo da ajuda offline
 Depois de instalar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], você pode baixar o conteúdo da ajuda adicional para que ele fique disponível offline.

#### <a name="to-install-or-uninstall-help-content"></a>Para instalar ou desinstalar conteúdo da Ajuda

1. Na barra de menus do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], escolha **Ajuda**, **adicionar e remover conteúdo da Ajuda**.

2. Na guia **Gerenciar Conteúdo** do **Visualizador da Ajuda da Microsoft**, selecione a fonte de instalação do conteúdo da Ajuda.

3. Se você estiver procurando uma coleção da Ajuda específica, digite o nome ou uma palavra-chave na caixa de texto **Pesquisar** e pressione **Enter**.

4. Ao lado do nome da coleção da Ajuda que você deseja, escolha o link **Adicionar** ou **Remover**.

5. Clique no botão **Atualizar** .

   Para obter mais informações sobre como instalar ou implantar a ajuda offline, consulte o [Guia do administrador do Help Viewer](../ide/help-viewer-administrator-guide.md).

## <a name="serviceReleases"></a> Verificando liberações de serviço e atualizações de produto
 Como nem todas as extensões são compatíveis, o Visual Studio não atualiza extensões automaticamente quando você atualiza de versões anteriores. Você deve reinstalar as extensões do [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou do fornecedor do software.

#### <a name="to-automatically-check-for-service-releases"></a>Para verificar automaticamente as liberações de serviço

1. Na barra de menus, escolha **Ferramentas**, **Opções**.

2. Na caixa de diálogo **Opções**, expanda **Ambiente** e, em seguida, selecione **Extensões e Atualizações**. Confira se a caixa de seleção **Verificar atualizações automaticamente** está selecionada e, em seguida, escolha **OK**.

## <a name="registering-visual-studio"></a>Registrando o Visual Studio

1. Na barra de menus, escolha **Ajuda**, **Sobre**.

     A caixa de diálogo **Sobre** mostra o PID (número de identificação do produto). Você precisará do PID e das credenciais da conta do Windows (como um endereço de email do hotmail ou Outlook.com e senha) para registrar o produto.

2. Na barra de menus, escolha **Ajuda**, **Registrar Produto**.

## <a name="repair"></a> Reparando o Visual Studio

#### <a name="to-repair-visual-studio"></a>Para reparar o Visual Studio

1. No **painel de controle**, na página **programas e recursos** , escolha a edição do produto que você deseja reparar e escolha **alterar**.

2. No Assistente de instalação, escolha **Reparar**, escolha **Avançar** e, em seguida, siga as instruções restantes.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>Para reparar o Visual Studio nos modos silencioso ou passivo (isto é, para reparar da origem)

1. No computador onde o Visual Studio está instalado, abra o prompt de comando do Windows.

2. Digite os seguintes parâmetros:

     *DVDRoot* \\< arquivo de instalação\> \<&#124;/Quiet/Passive > [/norestart]/Repair

## <a name="troubleshooting"></a>Solução de problemas de instalação
 Utilize os seguintes recursos para conseguir ajuda para problemas de configuração e instalação:

- Fórum de [Instalação e configuração do Visual Studio](https://go.microsoft.com/fwlink/?LinkID=151190). Leia perguntas e respostas de outras pessoas na comunidade do Visual Studio. Se você não encontrar o que precisa, faça suas próprias perguntas.

- Site do [Suporte da Microsoft para Visual Studio](https://go.microsoft.com/fwlink/?LinkID=251019). Leia artigos da base de dados de conhecimento e saiba como contatar o Suporte da Microsoft para obter informações sobre problemas com a instalação do Visual Studio.

## <a name="relatedTopics"></a> Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Criar uma instalação do Offline do Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)|Descreve como instalar o Visual Studio quando você não está conectado à Internet.
|[Instalar versões do Visual Studio lado a lado](../install/install-visual-studio-versions-side-by-side.md)|Fornece informações sobre como instalar várias versões do Visual Studio no mesmo computador.|
|[Usar parâmetros de linha de comando para instalar o Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|Lista os parâmetros de linha de comando que você pode usar ao instalar o Visual Studio a partir de um prompt de comando.|
|[Desinstalar o Visual Studio](../install/uninstall-visual-studio.md)|Descreve como desinstalar o Visual Studio.|
|[Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md) (Guia do administrador do Visual Studio)|Fornece informações sobre as opções de implantação do Visual Studio.|
|[A Biblioteca de Imagens do Visual Studio](../designers/the-visual-studio-image-library.md)|Fornece informações sobre como instalar os gráficos que podem ser usados em aplicativos do Visual Studio.|
|[Introdução ao desenvolvimento com o Visual Studio](../ide/get-started-developing-with-visual-studio.md)|Inclui informações e links que podem ajudá-lo a usar o Visual Studio com mais eficiência.|

## <a name="see-also"></a>Consulte também

- [Entrando no Visual Studio](../ide/signing-in-to-visual-studio.md)