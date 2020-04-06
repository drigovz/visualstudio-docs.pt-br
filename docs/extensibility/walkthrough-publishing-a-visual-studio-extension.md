---
title: 'Passo a passo: Publicando uma extensão visual studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34260124baedeba297dbd64e8a2c1856b55ec5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697134"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Passo a passo: Publique uma extensão do Visual Studio

Este passo a passo mostra como publicar uma extensão do Visual Studio no Visual Studio Marketplace. Quando você adiciona sua extensão ao Marketplace, os desenvolvedores podem usar **Extensões e Atualizações** para procurar extensões novas e atualizadas.

## <a name="prerequisites"></a>Pré-requisitos

 Para acompanhar este passo a passo, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Crie uma extensão do Visual Studio

Este artigo usa uma extensão VSPackage padrão, mas as etapas são válidas para todo tipo de extensão.

1. Crie um VSPackage em `TestPublish` C# nomeado que tenha um comando de menu. Para obter mais informações, consulte [Criar sua primeira extensão: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Empacotar sua extensão

1. Atualize a extensão *.vsixmanifest* com as informações corretas sobre nome do produto, autor e versão.

   ![atualizar extensão vsixmanifest](media/update-extension-vsixmanifest.png)

2. Construa sua extensão no modo **de liberação.** Agora sua extensão está embalada como um VSIX na pasta \bin\Release.

3. Você pode clicar duas vezes no VSIX para verificar a instalação.

## <a name="test-the-extension"></a>Teste a extensão

 Antes de distribuir a extensão, construa-a e teste-a para ter certeza de que ela está instalada corretamente na instância experimental do Visual Studio.

1. No Visual Studio, comece a depurar para abrir uma instância experimental do Visual Studio.

2. Na instância experimental, vá para o menu **Ferramentas** e clique **em Extensões e Atualizações**. A extensão TestPublish deve aparecer no painel central e ser ativada.

3. No menu **Ferramentas,** certifique-se de ver o comando de teste.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publique a extensão para o Visual Studio Marketplace

1. Certifique-se de que você construiu a versão de versão de sua extensão e que ela está atualizada.

2. Em um navegador web, abra o site [do Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

3. No canto superior direito, clique **em Entrar**.

4. Use sua conta microsoft para fazer login. Se você não tem uma conta microsoft, você pode criar uma neste momento.

5. Clique **em Publicar extensões**.  Esta opção navega até a página de gerenciamento de todas as suas extensões. Se você não tem uma conta de editor, você é solicitado a criar uma neste momento.

   ![Enviar para marketplace](media/upload-to-marketplace.png)

6. Escolha o editor que deseja usar para carregar sua extensão. Você pode alterar editores clicando nos nomes dos editores listados à esquerda. Clique em **Nova extensão** e selecione **Visual Studio**.

7. Em **1: Carregar extensão,** você pode optar por carregar um arquivo VSIX diretamente no Visual Studio Marketplace ou apenas adicionar um link ao seu próprio site. Neste exemplo, a extensão, *TestPublish.vsix* é carregada. Arraste e solte sua extensão ou use o link **clique** para navegar pelo arquivo. Encontre sua extensão na pasta \bin\Release do projeto.  Clique em **Continuar**.

8. Em **2: Forneça detalhes de extensão,** alguns campos são preenchidos automaticamente a partir do arquivo *source.extension.vsixmanifest* a partir de sua extensão. Veja mais detalhes sobre cada um abaixo:

    * **O nome interno** é usado na URL da página de detalhes da extensão. Por exemplo, publicar uma extensão sob o nome do editor "meu nome" e especificar o nome interno\.para ser "minha extensão" resulta em uma URL de "marketplace.visualstudio com/items?itemName=myname.myextension" para a página de detalhes da extensão.

    * **Exibir o nome** da sua extensão. Este nome é preenchido automaticamente a partir do arquivo *source.extension.vsixmanifest.*

    * **Número** da versão da extensão que você está carregando. Esta versão é preenchida automaticamente a partir do arquivo *source.extension.vsixmanifest.*

    * **VSIX ID** é o identificador exclusivo que o Visual Studio usa para sua extensão. Este identificador é necessário se você quiser ter sua extensão atualizada automaticamente. Este identificador é preenchido automaticamente a partir do arquivo *source.extension.vsixmanifest.*

    * **Logotipo** que é usado para sua extensão. Este logotipo é preenchido automaticamente a partir do arquivo *source.extension.vsixmanifest,* se fornecido.

    * **Breve descrição** do que sua extensão faz. Esta descrição é preenchida automaticamente a partir do arquivo *source.extension.vsixmanifest.*

    * **A visão geral** é um bom lugar para incluir capturas de tela e informações detalhadas sobre o que sua extensão faz.

    * **As versões suportadas do Visual Studio** permitem que você escolha em quais versões do Visual Studio sua extensão funcionará. Sua extensão só está instalada nessas versões.

    * **A edição do Visual Studio suportada permite que você escolha quais edições do Visual Studio sua extensão irá funcionar. Sua extensão só está instalada nessas edições.

    * **Tipo**. O tipo mais comum de extensões são **Ferramentas**.

    * **Categorias**. Pegue até três que são os mais adequados para a sua extensão.

    * **Tags** são palavras-chave que ajudam os usuários a encontrar sua extensão. As tags podem ajudar a aumentar a relevância da pesquisa de suas extensões no Marketplace.

    * **Categoria de Preços** é o custo da sua extensão.

    * **O repositório de código-fonte** permite que você compartilhe um link para o seu código fonte com a comunidade.

    * **Permitir q&A para sua extensão** permite que os usuários deixem perguntas em sua página de entrada de extensão.

9. Clique **em Salvar & carregar**. Essa opção o leva de volta à página de gerenciamento de seu editor. Sua extensão ainda não foi publicada. Para publicar sua extensão, clique com o botão direito do mouse na extensão e selecione **Fazer Público**. Você pode ver como sua extensão será no Marketplace selecionando **'Exibir extensão**' . Para obter números de aquisição, clique em **Relatórios**. Para fazer alterações na sua extensão, clique em **Editar**.

   ![Menu de entrada de extensão](media/extension-entry-menu.png)

10. Depois de clicar em **Fazer Público,** sua extensão agora é pública. Procure no Visual Studio Marketplace para obter sua extensão.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Adicione usuários adicionais para gerenciar sua conta de editor

O Marketplace suporta a concessão de permissões adicionais aos usuários para acessar e gerenciar uma conta de editor.

1. Navegue até a conta do editor a que deseja adicionar usuários adicionais.

2. Selecione **Membros** e clique em **Adicionar**.

   ![Adicionar usuário adicional](media/add-users.png)

3. Em seguida, você pode especificar o endereço de e-mail do usuário que deseja adicionar e conceder o nível certo de acesso em **Selecionar uma função**.  É possível escolher um das seguintes opções:

   * **Criador**: O usuário pode publicar extensões, mas não pode visualizar ou gerenciar extensões publicadas por outros usuários.

   * **Leitor**: O usuário pode visualizar extensões, mas não pode publicar ou gerenciar extensões.

   * **Contribuinte**: O usuário pode publicar e gerenciar extensões, mas não pode editar configurações do editor ou gerenciar o acesso.

   * **Proprietário**: O usuário pode publicar e gerenciar extensões, editar configurações do editor e gerenciar o acesso.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instale a extensão do Visual Studio Marketplace

Agora que a extensão foi publicada, instale-a no Visual Studio e teste-a lá.

1. No Visual Studio, no menu **Ferramentas,** clique em **Extensões e Atualizações**.

2. Clique **em Online** e, em seguida, procure por **TestPublish**.

3. Clique em **Download**. A extensão está então programada para ser instalada.

4. Para concluir a instalação, feche todas as instâncias do Visual Studio.

## <a name="remove-the-extension"></a>Remover a extensão

Você pode remover a extensão do Visual Studio Marketplace e do seu computador.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Para remover a extensão do Visual Studio Marketplace

1. Abra o site [do Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

2. No canto superior direito, clique em **Publicar** extensões. Escolha o editor que você usou para publicar **TestPublish**. A listagem para **TestPublish** é exibida.

3. Clique com o botão direito do mouse na entrada de extensão e clique **em Remover**. Você deve confirmar se deseja remover a extensão. Clique em **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Para remover a extensão do seu computador

1. No Visual Studio, no menu **Ferramentas,** clique em **Extensões e Atualizações**.

2. Selecione **TestePublicar** e clique **em Desinstalar**. A extensão está então programada para desinstalar.

3. Para concluir a desinstalação, feche todas as instâncias do Visual Studio.
