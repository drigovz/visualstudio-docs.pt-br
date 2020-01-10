---
title: Localizar e instalar extensões
ms.date: 09/18/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f016af58b5799ca37b1a8f0cc54366d639c57c03
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594403"
---
# <a name="manage-extensions-for-visual-studio"></a>Gerenciar extensões para o Visual Studio

Extensões são pacotes de código que são executados dentro do Visual Studio e fornecem recursos novos ou aprimorados. As extensões podem ser controles, amostras, modelos, ferramentas ou outros componentes que adicionam funcionalidade ao Visual Studio, por exemplo, [Live share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) ou [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode).

Para obter informações sobre como criar extensões do Visual Studio, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Para obter informações sobre como usar extensões, consulte a página de extensão individual em [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Caixa de diálogo extensões e atualizações

Use a caixa de diálogo **Extensões e Atualizações** para instalar e gerenciar extensões do Visual Studio. Para abrir a caixa de diálogo **Extensões e Atualizações**, escolha **Ferramentas** > **Extensões e Atualizações** ou digite **Extensões** na caixa de pesquisa **Início Rápido**.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Caixa de diálogo Gerenciar extensões

Use a caixa de diálogo **Gerenciar Extensões** para instalar e gerenciar extensões do Visual Studio. Para abrir a caixa de diálogo **Gerenciar Extensões**, escolha **Extensões** > **Gerenciar Extensões**. Ou digite **Extensões** na caixa de pesquisa e escolha **Gerenciar Extensões**.

::: moniker-end

![Janela Extensões no Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

O painel à esquerda categoriza as extensões entre aquelas que estão instaladas, as que estão disponíveis no Visual Studio Marketplace (**Online**) e aquelas que têm atualizações disponíveis. O **Gerenciador de Extensões de Roaming** mantém uma lista de todas as extensões do Visual Studio você instalou em qualquer computador ou instância do Visual Studio. Ele foi projetado para permitir que você encontre suas extensões favoritas com mais facilidade.

## <a name="find-and-install-extensions"></a>Localizar e instalar extensões

::: moniker range="vs-2017"

Você pode instalar extensões de [Visual Studio Marketplace](https://marketplace.visualstudio.com) ou a caixa de diálogo extensões e atualizações no Visual Studio.

Para instalar extensões de dentro do Visual Studio:

1. Em **Ferramentas** > **Extensões e Atualizações**, localize a extensão que você deseja instalar. Se você souber o nome ou parte do nome da extensão, poderá pesquisar na janela de **pesquisa** .

2. Selecione **Baixar**.

   Esta extensão está agendada para instalação. Sua extensão será instalada depois que todas as instâncias do Visual Studio tiverem sido fechadas.

Se você tentar instalar uma extensão que tenha dependências, o instalador verificará se elas já foram instaladas. Se elas não tiverem sido instaladas, a caixa de diálogo **Extensões e Atualizações** listará as dependências que devem ser instaladas para que seja possível instalar a extensão.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Instalar sem usar a caixa de diálogo Extensões e Atualizações

As extensões que foram empacotadas em arquivos *.vsix* podem estar disponíveis em outros locais e não no Visual Studio Marketplace. A caixa de diálogo **ferramentas** > **extensões e atualizações** não pode detectar esses arquivos, mas você pode instalar um arquivo *. vsix* clicando duas vezes no arquivo ou selecionando o arquivo e pressionando **Enter**. Depois disso, basta seguir as instruções. Depois que a extensão for instalada, será possível usar a caixa de diálogo **Extensões e Atualizações** para habilitá-la, desabilitá-la ou desinstalá-la.

> [!NOTE]
> - O Visual Studio Marketplace contém extensões VSIX e MSI. A caixa de diálogo extensões e atualizações não pode habilitar ou desabilitar extensões baseadas em MSI.
> - Se uma extensão baseada em MSI incluir um arquivo *extension.vsixmanifest*, a extensão será exibida na caixa de diálogo **Extensões e Atualizações**.

::: moniker-end

::: moniker range=">=vs-2019"

Você pode instalar extensões de [Visual Studio Marketplace](https://marketplace.visualstudio.com) ou a caixa de diálogo Gerenciar extensões no Visual Studio.

Para instalar extensões de dentro do Visual Studio:

1. Em **Extensões** > **Gerenciar Extensões**, localize a extensão que você deseja instalar. Se você souber o nome ou parte do nome da extensão, será possível pesquisar na janela **Pesquisar**.

2. Selecione **Baixar**.

   Esta extensão está agendada para instalação. Sua extensão será instalada depois que todas as instâncias do Visual Studio tiverem sido fechadas.

Se você tentar instalar uma extensão que tenha dependências, o instalador verificará se elas já foram instaladas. Se elas não tiverem sido instaladas, a caixa de diálogo **Gerenciar Extensões** listará as dependências que devem ser instaladas para que seja possível instalar a extensão.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Instalar sem usar a caixa de diálogo Gerenciar Extensões

As extensões que foram empacotadas em arquivos *.vsix* podem estar disponíveis em outros locais e não no Visual Studio Marketplace. A caixa de diálogo **extensões** > **gerenciar extensões** não pode detectar esses arquivos, mas você pode instalar um arquivo *. vsix* clicando duas vezes no arquivo ou selecionando o arquivo e pressionando **Enter**. Depois disso, basta seguir as instruções. Depois que a extensão for instalada, será possível usar a caixa de diálogo **Gerenciar Extensões** para habilitá-la, desabilitá-la ou desinstalá-la.

> [!NOTE]
> - O Visual Studio Marketplace contém extensões VSIX e MSI. A caixa de diálogo Gerenciar extensões não pode habilitar ou desabilitar extensões baseadas em MSI.
> - Se uma extensão baseada em MSI incluir um arquivo *extension.vsixmanifest*, a extensão será exibida na caixa de diálogo **Gerenciar Extensões**.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Desinstalar ou desabilitar uma extensão

Se desejar parar de usar uma extensão, você poderá desabilitá-la ou desinstalá-la. A desabilitação de uma extensão a mantém instalada, mas descarregada. Localize a extensão e clique em **Desinstalar** ou **Desabilitar**. Reinicie o Visual Studio para descarregar uma extensão desabilitada.

> [!NOTE]
> Você pode desabilitar as extensões VSIX, mas não as extensões que foram instaladas usando um MSI. As extensões instaladas por MSI só podem ser desinstaladas.

## <a name="per-user-and-administrative-extensions"></a>Extensões administrativas e por usuário

A maioria das extensões é por usuário e é instalada no *%LocalAppData%\Microsoft\VisualStudio\\< o Visual Studio versão\>pasta de\\\Extensions* . Algumas extensões são extensões administrativas e são instaladas na *\<pasta de instalação do Visual Studio>\Common7\IDE\Extensions\\* .

Para proteger seu sistema contra extensões que possam conter erros ou código mal-intencionado, é possível restringir que as extensões por usuário sejam carregadas somente quando o Visual Studio estiver em execução com permissões de usuário normal. Isso significa que as extensões por usuário são desabilitadas quando o Visual Studio é executado com permissões elevadas.

Para restringir quando as extensões por usuário são carregadas:

1. Abra a página opções de extensões (**ferramentas** > **opções** > **ambiente** > **extensões**).

2. Desmarque a caixa de seleção **carregar extensões por usuário ao executar como administrador** .

3. Reinicie o Visual Studio.

## <a name="automatic-extension-updates"></a>Atualizações automáticas de extensão

As extensões são atualizadas automaticamente quando uma nova versão está disponível no Visual Studio Marketplace. A nova versão da extensão é detectada e instalada em segundo plano. Na próxima vez que você abrir o Visual Studio, a nova versão da extensão será executada.

Se desejar desabilitar as atualizações automáticas, você poderá desabilitar o recurso para todas as extensões ou apenas para extensões específicas.

::: moniker range="vs-2017"

- Para desabilitar as atualizações automáticas para todas as extensões, escolha o link **Alterar as configurações de Extensões e Atualizações** na caixa de diálogo **Ferramentas** > **Extensões e Atualizações**. Na caixa de diálogo **Opções**, desmarque a opção **Atualizar extensões automaticamente**.

- Para desabilitar as atualizações automáticas de uma extensão específica, desmarque a opção **Atualizar automaticamente essa extensão** no painel de detalhes da extensão do lado direito da caixa de diálogo **Extensões e Atualizações**.

::: moniker-end

::: moniker range=">=vs-2019"

- Para desabilitar as atualizações automáticas para todas as extensões, escolha o link **Alterar as configurações de Extensões** na caixa de diálogo **Ferramentas** > **Gerenciar Extensões**. Na caixa de diálogo **Opções**, desmarque a opção **Atualizar extensões automaticamente**.

- Para desabilitar as atualizações automáticas de uma extensão específica, desmarque a opção **Atualizar automaticamente essa extensão** no painel de detalhes da extensão do lado direito da caixa de diálogo **Gerenciar Extensões**.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Notificações de falha e falta de resposta

O Visual Studio notifica você se ele suspeita de que uma extensão estava envolvida em uma falha durante uma sessão anterior. Quando o Visual Studio falhar, ele armazenará a pilha de exceção. Na próxima vez em que o Visual Studio for iniciado, ele examinará a pilha, começando com a folha e funcionando em direção à base. Se o Visual Studio determinar que um quadro pertence a um módulo que faz parte de uma extensão instalada e habilitada, ele mostra uma notificação.

O Visual Studio também notifica você se ele suspeita de que uma extensão é responsável por uma interface do usuário sem resposta.

Quando essas notificações forem exibidas, você poderá ignorar a notificação ou executar uma das seguintes ações:

::: moniker range="vs-2017"

- Escolha **Desabilitar esta extensão**. O Visual Studio desabilita a extensão e permite que você saiba se precisa reiniciar o sistema para a desabilitação entrar em vigor. Você poderá habilitar a extensão novamente na caixa de diálogo **Ferramentas** > **Extensões e Atualizações** se desejar.

::: moniker-end

::: moniker range=">=vs-2019"

- Escolha **Desabilitar esta extensão**. O Visual Studio desabilita a extensão e permite que você saiba se precisa reiniciar o sistema para a desabilitação entrar em vigor. Você poderá habilitar a extensão novamente na caixa de diálogo **Extensões** > **Gerenciar Extensões** se desejar.

::: moniker-end

- Escolha **Nunca mostrar essa mensagem novamente**.

  - Se a notificação for sobre uma falha em uma sessão anterior, o Visual Studio não mostrará mais uma notificação quando uma falha associada a essa extensão ocorrer. O Visual Studio ainda mostrará notificações quando a falta de resposta puder ser associada a essa extensão, ou para falhas ou falta de resposta que possam ser associadas a outras extensões.
  - Se a notificação estiver relacionada à falta de resposta, o ambiente de desenvolvimento integrado (IDE) não mostrará mais uma notificação quando essa extensão estiver associada à falta de resposta. O Visual Studio ainda mostrará notificações relacionadas a falhas para essa extensão e notificações relacionadas à falha e à falta de resposta para outras extensões.

- Escolha **saiba mais** para navegar até esta página.

- Escolha o botão **X** no final da notificação para ignorar a notificação. Uma nova notificação será exibida para instâncias futuras da extensão que está sendo associada a uma falha ou falta de resposta da interface do usuário.

> [!NOTE]
> Uma notificação de falha ou de falta de resposta da interface do usuário significa apenas que um dos módulos de extensão estava na pilha quando a interface do usuário ficou sem resposta ou quando a falha ocorreu. Isso não significa necessariamente que a própria extensão foi a culpada. É possível que a extensão chamada código que faz parte do Visual Studio, que, por sua vez, resultou em uma interface do usuário sem resposta ou uma falha. No entanto, a notificação ainda pode ser útil se a extensão que levou à falha ou falta de resposta da interface do usuário não for importante para você. Nesse caso, desabilitar a extensão evita que a falta de resposta da IU ou a falha ocorra no futuro, sem afetar sua produtividade.

## <a name="samples"></a>Exemplos do

Quando você instala um exemplo online, a solução é armazenada em dois locais:

- Uma cópia funcional é armazenada no local que você especificou quando criou o projeto.

- Uma cópia mestra separada é armazenada em seu computador.

::: moniker range="vs-2017"

Você pode usar a caixa de diálogo **ferramentas** > **extensões e atualizações** para executar estas tarefas relacionadas a exemplos:

::: moniker-end

::: moniker range=">=vs-2019"

Você pode usar a caixa de diálogo **extensões** > **gerenciar extensões** para executar estas tarefas relacionadas a exemplos:

::: moniker-end

- Listar as cópias mestras dos exemplos que você instalou.

- Desabilitar ou desinstalar a cópia mestra de um exemplo.

- Instale os Pacotes de Exemplos, que são coleções de exemplos que se relacionam a uma tecnologia ou um recurso.

- Instalar exemplos online individuais.

- Exibir notificações de atualização quando as alterações do código-fonte são publicadas para exemplos instalados.

- Atualize a cópia mestra de uma amostra instalada quando houver uma notificação de atualização.

## <a name="see-also"></a>Veja também

- [Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [SDK do Visual Studio](../extensibility/visual-studio-sdk.md)
