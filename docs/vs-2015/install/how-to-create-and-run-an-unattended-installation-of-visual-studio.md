---
title: Como criar e executar uma instalação autônoma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: deabd34896b327f7cbbb35c7af75f5810dcfbf17
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040540"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>Como criar e executar uma instalação autônoma do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode executar o aplicativo de instalação para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] como autônomo (ou seja, silencioso personalizado) em uma intranet em vez de a partir de mídia como DVDs. Este tópico descreve como preparar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para esse tipo de instalação em um compartilhamento de rede.

## <a name="creating-a-network-image"></a>Criando uma imagem de rede
 Primeiro, crie uma imagem de rede da mídia do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

#### <a name="to-create-a-network-image"></a>Para criar uma imagem de rede

1. Crie uma pasta no servidor (por exemplo, *Unidade*:\IDEinstall\\).

2. Baixe o instalador de [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) e execute *Product*.exe /Layout *Unidade*:\IDEinstall\

3. Compartilhe a pasta IDEinstall na rede e defina as configurações de segurança apropriadas.

     O caminho de rede do aplicativo de instalação para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se parece com \\\\*NomeDoservidor*\IDEinstall\\*Product*.exe.

    > [!NOTE]
    >  A instalação pode falhar se qualquer combinação de caminho e nome de arquivo exceder 260 caracteres. O comprimento máximo de um caminho no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] é de 221 caracteres.  O nome do caminho local deve ter no máximo 70 caracteres, e o nome do caminho de rede deve ter no máximo 39 caracteres.

     A instalação também pode falhar se os nomes de pastas no caminho incluírem espaços inseridos (por exemplo, "\\\\*NomeDoServidor*\IDE install" ou \\\\*NomeDoServidor*\Visual Studio\\).

## <a name="deploying-visual-studio-in-unattended-mode"></a>Implantando o Visual Studio no modo autônomo
 Para implantar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no modo autônomo, é necessário modificar o arquivo AdminDeployment.xml. Para fazer isso, primeiro crie o arquivo AdminDeployment.xml usando o parâmetro de linha de comando `/CreateAdminFile` *\<local do arquivo>*. Em seguida, você poderá usar esse arquivo a fim de enviar uma implantação do Visual Studio para sua rede ou receber em uma instalação, caso tenha colocado esse arquivo no diretório *Unidade*:\IDEinstall\packages. O arquivo AdminDeployment.xml não é exclusivo de um sistema operacional, uma arquitetura, uma edição Visual Studio ou de um idioma de sistema operacional.

> [!CAUTION]
>  Às vezes, os itens listados como selecionados no arquivo AdminDeployment.xml não são instalados. Para resolver esse problema, coloque os itens marcados como "Selected="yes"" no **final** do arquivo AdminDeployment.xml.
>
>  Se preferir não instalar as dependências opcionais de um item, primeiro selecione o pai e, em seguida, desmarque as dependências opcionais após o pai, conforme mostrado na captura de tela a seguir:
>
>  ![Itens de instalação no final do arquivo AdminDeployment.xml](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
>  Como alternativa, basta omitir os filhos opcionais de um pai, ou seja, não incluir itens marcados como "Selected="no"". No entanto, continua sendo necessário colocar todos os itens marcados como "Selected="yes"" no final do arquivo AdminDeployment.xml.

> [!IMPORTANT]
>  Durante a instalação, o computador pode reiniciar automaticamente uma ou mais vezes. Depois de reiniciado, entre novamente com a mesma conta de usuário com a qual você se conectou para executar a instalação, antes de reiniciar o computador. Você pode evitar reinicializações automáticos instalando os componentes de pré-requisitos, antes de executar uma instalação autônoma. Para saber mais, confira a seção chamada "Evite reiniciar durante a instalação", no [Guia do administrador do Visual Studio](../install/visual-studio-administrator-guide.md).

 O esquema do arquivo AdminDeployment contém os seguintes elementos:

|Elemento|Atributo|Valores|Descrição|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Path*|Comporta-se da mesma forma que a substituição do caminho na interface do usuário do aplicativo de instalação. Este elemento será ignorado se o Visual Studio já estiver instalado.|
|BundleCustomizations|NoWeb|sim&#124;padrão|Se o valor desse elemento for sim, o aplicativo de instalação nunca tentará ir para a Web durante a ação de instalação.|
|SelectableItemCustomization|Hidden|Sim&#124;Não|Se o valor desse elemento for Sim, oculta um item Selecionável na árvore de personalização.|
|SelectableItemCustomization|Selecionado|Sim&#124;Não|Marca ou desmarca um item selecionável na árvore de personalização.|
|BundleCustomizations|Feed|Caminho|Local do feed que o usuário pretende usar.  Este feed serve para operações de modificação subsequentes no computador ("Padrão" por padrão).|
|BundleCustomizations|SuppressRefreshPrompt|sim&#124;padrão|Impedirá que o usuário seja solicitado a atualizar a instalação, caso haja uma instalação nova disponível.|
|BundleCustomizations|NoRefresh|sim&#124;padrão|Não atualizará a instalação, caso haja uma instalação nova disponível.|
|BundleCustomizations|NoCacheOnlyMode|sim&#124;padrão|Impede pré-população do cache de pacote.|

> [!WARNING]
>  O aplicativo de instalação respeitará o estado Selecionado de um SelectableItem, mesmo se estiver oculto. Por exemplo, se você quiser instalar sempre um item selecionável, poderá marcá-lo como oculto e selecionado.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Para criar uma instalação autônoma do Visual Studio

1. No arquivo *Unidade*:\IDEinstall\AdminDeployment.xml, altere o valor do atributo NoWeb do elemento BundleCustomizations de "default" para "yes" como mostra o exemplo a seguir:

     Altere `<BundleCustomizations TargetDir="default" NoWeb="default"/>` para `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`

2. Altere o atributo SelectableItemCustomization conforme necessário para componentes opcionais e então salve o arquivo.

## <a name="running-unattended-setup"></a>Executando a instalação autônoma
 Você pode executar a instalação autônoma ao executar automaticamente o aplicativo de instalação do Visual Studio em computadores cliente ou ao permitir que os usuários executem o aplicativo por conta própria usando as configurações definidas por você.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>Para executar uma instalação autônoma em um computador cliente

- Abra o menu **Iniciar**, escolha **Executar** e insira \\\\*NomeDoServidor*\IDEinstall\vs_*Product*.exe /adminfile *CaminhoDoArquivoAdminDeployment.xml*<em>ParâmetrosAdicionaisNecessários</em>

   Você pode, por exemplo, especificar a seguinte linha de comando: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart`

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>Para permitir que clientes instalem manualmente o Visual Studio com configurações predefinidas

1. Copie o arquivo AdminDeployment.xml personalizado para um compartilhamento de rede somente leitura (por exemplo, \\\\*NomeDoServidor*\IDEinstall\packages\AdminDeployment.xml).

2. Permita que usuários instalem deste compartilhamento.

## <a name="maintaining-an-installation"></a>Mantendo uma instalação
 Ao abrir o **Painel de Controle** e executar novamente o aplicativo de instalação, você poderá modificar os recursos do Visual Studio, desinstalar linguagens de programação e reparar ou desinstalar o Visual Studio.

> [!NOTE]
>  Você deve ter credenciais administrativas no computador local para usar o modo de manutenção.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>Para manter uma instalação em um computador cliente

- Abra o **Painel de Controle** e, em seguida, escolha **Programas e Recursos**.

- Escolha [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e, em seguida, escolha **Alterar**.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Para alterar as configurações de AdminDeployment em um computador cliente após o Visual Studio ter sido instalado

1. Atualize AdminDeployment.xml, conforme o necessário.

2. Abra o menu **Iniciar** e, em seguida, escolha **Executar**.

3. Insira o seguinte texto: \\\\*NomeDoServidor*\IDEinstall\vs_*Product*.exe /AdminFile CaminhoParaArquivoAdmindeployment.xml

    AdditionalParametersAsNeeded

    Você pode, por exemplo, especificar a seguinte linha de comando: `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart`

   Reparar é o parâmetro padrão depois que o Visual Studio está instalado. Se reparar o Visual Studio com um /AdminFile atualizado, você substituirá as configurações de implantação do administrador pelas configurações atualizadas invocadas pelo arquivo AdminDeployment.xml.

## <a name="updating-an-installation"></a>Como atualizar uma instalação
 A Microsoft lançou várias atualizações para o Visual Studio 2015. Esta seção explica como atualizar a imagem de uma instalação autônoma do Visual Studio 2015, de modo que o programa inclua as atualizações.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Para atualizar uma instalação autônoma do Visual Studio

1. Localize o arquivo Product.exe na imagem da rede existente, clique nele com o botão direito do mouse e clique em **Propriedades**.

2. Clique na guia **Detalhes** e anote a propriedade da **versão do produto**.

    ![Exemplo da caixa de diálogo Propriedades em uma instalação autônoma do Visual Studio](../install/media/unattended-install-properties-dialog-box.PNG "Instalação autônoma – caixa de diálogo Propriedades")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>Se a versão do produto for 14.0.24720.0 ou 14.0.24720.1, faça o seguinte:
   1. Execute *Product.exe* /Layout *Unidade:* \IDEinstall em um computador com acesso à Internet. (Por exemplo, execute: `vs_enterprise.exe /Layout d:\IDEinstall`.)

   2. Quando concluir o /Layout, copie a nova imagem em um novo local.

   3. Crie e modifique o arquivo AdminDeployment.xml. Para fazer isso, use o parâmetro de linha de comando `/CreateAdminFile`*\<local do arquivo>*. Para saber mais, confira a seção "Como implantar o Visual Studio no modo autônomo" deste artigo.

   4. Execute o comando a seguir para atualizar a cópia do Visual Studio instalada no computador cliente: "\\\\*servidor1*\IDEinstall_Updated_1\\*Product.exe* /adminfile \\\servidor1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart".

        Por exemplo, execute: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>No caso de outros valores de versão do produto, faça o seguinte:
   1. Execute *Product.exe* /Layout *Unidade:* \IDEinstall em um computador com acesso à Internet. (Por exemplo, execute `vs-enterprise.exe /Layout d:\IDEinstall`.)

   2. Quando concluir o /Layout, copie a nova imagem em um novo local. Se preferir, você pode substituir a imagem da rede existente.

   3. Crie e, em seguida, modifique o arquivo AdminDeployment.xml. Para fazer isso, use o parâmetro de linha de comando `/CreateAdminFile`*\<local do arquivo>*. Para saber mais, confira a seção "Como implantar o Visual Studio no modo autônomo" deste artigo.

   4. Caso copie a imagem para um novo local, execute o comando a seguir para atualizar a cópia do Visual Studio instalada no computador cliente: "\\\\*servidor1*\IDEinstall_Updated_1\\*Product.exe* /adminfile \\\servidor1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart".

        Por exemplo, execute: `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5. Se substituir a imagem da rede existente, você poderá executar o comando, conforme descrito na etapa anterior, ou fazer o seguinte:
       1. Abra o **Painel de Controle** e, em seguida, escolha **Programas e Recursos**.

       2. Escolha o **Visual Studio** e escolha **Alterar**.

       3. Depois de iniciar o Visual Studio em modo de manutenção, clique em **Modificar**.

       4. A atualização mais recente será exibida na página Recursos. Selecione os outros recursos que você deseja instalar, clique em **Avançar** e, em seguida, clique em **Atualizar** para instalar a atualização e os novos recursos.

## <a name="registering-the-product"></a>Como registrar o produto
 Após a instalação ter sido concluída, será possível registrar sua cópia do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] de dentro do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

#### <a name="to-register"></a>Para registrar

1. Abra o menu **Ajuda** e, em seguida, escolha **Registrar Produto**.

2. Insira a chave do produto.

     Para saber mais, confira os tópicos [Como localizar a chave do produto (Product Key) do Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md) e [Aplicar chaves do produto (Product Keys) automaticamente durante a implantação do Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).

## <a name="see-also"></a>Consulte também
 [Instalar o Visual Studio](../install/install-visual-studio-2015.md)