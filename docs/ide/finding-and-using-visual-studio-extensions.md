---
title: Encontre e instale extensões
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594403"
---
# <a name="manage-extensions-for-visual-studio"></a>Gerenciar extensões para visual studio

Extensões são pacotes de código que são executados dentro do Visual Studio e fornecem recursos novos ou aprimorados. As extensões podem ser controles, amostras, modelos, ferramentas ou outros componentes que adicionam funcionalidade ao Visual Studio, por exemplo, [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) ou Visual [Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode).

Para obter informações sobre a criação de extensões do Visual Studio, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Para obter informações sobre o uso de extensões, consulte a página de extensão individual no [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Caixa de diálogo Extensões e Atualizações

Use a caixa de diálogo **Extensões e Atualizações** para instalar e gerenciar extensões do Visual Studio. Para abrir a caixa de diálogo **Extensões e Atualizações**, escolha **Ferramentas** > **Extensões e Atualizações** ou digite **Extensões** na caixa de pesquisa **Início Rápido**.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Gerenciar caixa de diálogo Extensões

Use a caixa de diálogo **Gerenciar Extensões** para instalar e gerenciar extensões do Visual Studio. Para abrir a caixa de diálogo **Gerenciar Extensões**, escolha **Extensões** > **Gerenciar Extensões**. Ou digite **Extensões** na caixa de pesquisa e escolha **Gerenciar Extensões**.

::: moniker-end

![Janela Extensões no Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

O painel à esquerda categoriza as extensões entre aquelas que estão instaladas, as que estão disponíveis no Visual Studio Marketplace (**Online**) e aquelas que têm atualizações disponíveis. O **Gerenciador de Extensões de Roaming** mantém uma lista de todas as extensões do Visual Studio você instalou em qualquer computador ou instância do Visual Studio. Ele foi projetado para permitir que você encontre suas extensões favoritas com mais facilidade.

## <a name="find-and-install-extensions"></a>Encontre e instale extensões

::: moniker range="vs-2017"

Você pode instalar extensões do [Visual Studio Marketplace](https://marketplace.visualstudio.com) ou da caixa de diálogo Extensões e Atualizações no Visual Studio.

Para instalar extensões dentro do Visual Studio:

1. A partir**de Extensões e Atualizações de** **Ferramentas,** > encontre a extensão que deseja instalar. Se você sabe o nome ou parte do nome da extensão, você pode pesquisar na janela **pesquisar.**

2. Selecione **Baixar**.

   Esta extensão está agendada para instalação. Sua extensão será instalada depois que todas as instâncias do Visual Studio tiverem sido encerradas.

Se você tentar instalar uma extensão que tenha dependências, o instalador verificará se elas já foram instaladas. Se elas não tiverem sido instaladas, a caixa de diálogo **Extensões e Atualizações** listará as dependências que devem ser instaladas para que seja possível instalar a extensão.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Instalar sem usar a caixa de diálogo Extensões e Atualizações

As extensões que foram empacotadas em arquivos *.vsix* podem estar disponíveis em outros locais e não no Visual Studio Marketplace. A caixa de diálogo**Extensões e Atualizações de** **ferramentas** > não pode detectar esses arquivos, mas você pode instalar um arquivo *.vsix* clicando duas vezes no arquivo ou selecionando o arquivo e pressionando **Enter**. Depois disso, basta seguir as instruções. Depois que a extensão for instalada, será possível usar a caixa de diálogo **Extensões e Atualizações** para habilitá-la, desabilitá-la ou desinstalá-la.

> [!NOTE]
> - O Visual Studio Marketplace contém extensões VSIX e MSI. A caixa de diálogo Extensões e Atualizações não pode ativar ou desativar extensões baseadas em MSI.
> - Se uma extensão baseada em MSI incluir um arquivo *extension.vsixmanifest*, a extensão será exibida na caixa de diálogo **Extensões e Atualizações**.

::: moniker-end

::: moniker range=">=vs-2019"

Você pode instalar extensões do [Visual Studio Marketplace](https://marketplace.visualstudio.com) ou da caixa de diálogo Gerenciar extensões no Visual Studio.

Para instalar extensões dentro do Visual Studio:

1. A partir **de extensões** > **gerenciar extensões**, encontre a extensão que deseja instalar. Se você souber o nome ou parte do nome da extensão, será possível pesquisar na janela **Pesquisar**.

2. Selecione **Baixar**.

   Esta extensão está agendada para instalação. Sua extensão será instalada depois que todas as instâncias do Visual Studio tiverem sido encerradas.

Se você tentar instalar uma extensão que tenha dependências, o instalador verificará se elas já foram instaladas. Se elas não tiverem sido instaladas, a caixa de diálogo **Gerenciar Extensões** listará as dependências que devem ser instaladas para que seja possível instalar a extensão.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Instalar sem usar a caixa de diálogo Gerenciar Extensões

As extensões que foram empacotadas em arquivos *.vsix* podem estar disponíveis em outros locais e não no Visual Studio Marketplace. A caixa de diálogo **Extensões** > **Gerenciar extensões** não pode detectar esses arquivos, mas você pode instalar um arquivo *.vsix* clicando duas vezes no arquivo ou selecionando o arquivo e pressionando **Enter**. Depois disso, basta seguir as instruções. Depois que a extensão for instalada, será possível usar a caixa de diálogo **Gerenciar Extensões** para habilitá-la, desabilitá-la ou desinstalá-la.

> [!NOTE]
> - O Visual Studio Marketplace contém extensões VSIX e MSI. A caixa de diálogo Gerenciar extensões não pode ativar ou desativar extensões baseadas em MSI.
> - Se uma extensão baseada em MSI incluir um arquivo *extension.vsixmanifest*, a extensão será exibida na caixa de diálogo **Gerenciar Extensões**.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Desinstalar ou desativar uma extensão

Se desejar parar de usar uma extensão, você poderá desabilitá-la ou desinstalá-la. A desabilitação de uma extensão a mantém instalada, mas descarregada. Localize a extensão e clique em **Desinstalar** ou **Desabilitar**. Reinicie o Visual Studio para descarregar uma extensão desabilitada.

> [!NOTE]
> Você pode desativar extensões VSIX, mas não extensões que foram instaladas usando um MSI. As extensões instaladas em MSI só podem ser desinstaladas.

## <a name="per-user-and-administrative-extensions"></a>Extensões administrativas e por usuário

A maioria das extensões são por usuário e estão instaladas na pasta *%LocalAppData%\Microsoft\VisualStudio\\<versão do Visual Studio\>\Extensões.\\ * Algumas extensões são extensões administrativas e estão instaladas na * \<pasta de instalação\\ do Visual Studio>\Common7\IDE\Extensions.*

Para proteger seu sistema contra extensões que possam conter erros ou código mal-intencionado, é possível restringir que as extensões por usuário sejam carregadas somente quando o Visual Studio estiver em execução com permissões de usuário normal. Isso significa que as extensões por usuário são desativadas quando o Visual Studio é executado com permissões elevadas.

Para restringir a carga de extensões por usuário:

1. Abra a página de opções de extensões **(Tools** > **Options** > **Environment** > **Extensions).**

2. Limpe as **extensões Load por usuário ao ser executado como** caixa de seleção do administrador.

3. Reinicie o Visual Studio.

## <a name="automatic-extension-updates"></a>Atualizações automáticas de extensão

As extensões são atualizadas automaticamente quando uma nova versão está disponível no Visual Studio Marketplace. A nova versão da extensão é detectada e instalada em segundo plano. Na próxima vez que você abrir o Visual Studio, a nova versão da extensão será executada.

Se você deseja desativar atualizações automáticas, você pode desativar o recurso para todas as extensões ou apenas para extensões específicas.

::: moniker range="vs-2017"

- Para desabilitar as atualizações automáticas para todas as extensões, escolha o link **Alterar as configurações de Extensões e Atualizações** na caixa de diálogo **Ferramentas** > **Extensões e Atualizações**. Na caixa de diálogo **Opções**, desmarque a opção **Atualizar extensões automaticamente**.

- Para desabilitar as atualizações automáticas de uma extensão específica, desmarque a opção **Atualizar automaticamente essa extensão** no painel de detalhes da extensão do lado direito da caixa de diálogo **Extensões e Atualizações**.

::: moniker-end

::: moniker range=">=vs-2019"

- Para desabilitar as atualizações automáticas para todas as extensões, escolha o link **Alterar as configurações de Extensões** na caixa de diálogo **Ferramentas** > **Gerenciar Extensões**. Na caixa de diálogo **Opções**, desmarque a opção **Atualizar extensões automaticamente**.

- Para desabilitar as atualizações automáticas de uma extensão específica, desmarque a opção **Atualizar automaticamente essa extensão** no painel de detalhes da extensão do lado direito da caixa de diálogo **Gerenciar Extensões**.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Notificações de falha e não resposta

O Visual Studio notifica você se ele suspeita de que uma extensão estava envolvida em uma falha durante uma sessão anterior. Quando o Visual Studio falhar, ele armazenará a pilha de exceção. Na próxima vez em que o Visual Studio for iniciado, ele examinará a pilha, começando com a folha e funcionando em direção à base. Se o Visual Studio determinar que um quadro pertence a um módulo que faz parte de uma extensão instalada e habilitada, ele mostra uma notificação.

O Visual Studio também notifica você se ele suspeita de que uma extensão é responsável por uma interface do usuário sem resposta.

Quando essas notificações forem exibidas, você poderá ignorar a notificação ou executar uma das seguintes ações:

::: moniker range="vs-2017"

- Escolha **Desabilitar esta extensão**. O Visual Studio desabilita a extensão e permite que você saiba se precisa reiniciar o sistema para a desabilitação entrar em vigor. Você pode reativar a extensão na caixa de diálogo**Extensões e Atualizações** de **ferramentas,** > se quiser.

::: moniker-end

::: moniker range=">=vs-2019"

- Escolha **Desabilitar esta extensão**. O Visual Studio desabilita a extensão e permite que você saiba se precisa reiniciar o sistema para a desabilitação entrar em vigor. Você pode reativar a extensão na caixa de diálogo **Extensões** > **Gerenciar extensões,** se quiser.

::: moniker-end

- Escolha **Nunca mostrar essa mensagem novamente**.

  - Se a notificação for sobre uma falha em uma sessão anterior, o Visual Studio não mostrará mais uma notificação quando uma falha associada a essa extensão ocorrer. O Visual Studio ainda mostrará notificações quando a falta de resposta puder ser associada a essa extensão, ou para falhas ou falta de resposta que possam ser associadas a outras extensões.
  - Se a notificação diz respeito à falta de resposta, o ambiente de desenvolvimento integrado (IDE) não apresenta mais uma notificação quando essa extensão estiver associada à falta de resposta. O Visual Studio ainda mostrará notificações relacionadas a falhas para esta extensão e notificações relacionadas a falhas e não resposta para outras extensões.

- Escolha **Saiba mais** para navegar nesta página.

- Escolha o botão **X** no final da notificação para ignorar a notificação. Uma nova notificação será exibida para instâncias futuras da extensão que está sendo associada a uma falha ou falta de resposta da interface do usuário.

> [!NOTE]
> Uma notificação de falha ou de falta de resposta da interface do usuário significa apenas que um dos módulos de extensão estava na pilha quando a interface do usuário ficou sem resposta ou quando a falha ocorreu. Isso não significa necessariamente que a própria extensão foi a culpada. É possível que a extensão chamada código que faz parte do Visual Studio, que por sua vez resultou em ui não responsiva ou um acidente. No entanto, a notificação ainda pode ser útil se a extensão que levou à falha ou falta de resposta da interface do usuário não for importante para você. Nesse caso, desabilitar a extensão evita que a falta de resposta da IU ou a falha ocorra no futuro, sem afetar sua produtividade.

## <a name="samples"></a>Exemplos

Quando você instala um exemplo online, a solução é armazenada em dois locais:

- Uma cópia funcional é armazenada no local que você especificou quando criou o projeto.

- Uma cópia mestra separada é armazenada em seu computador.

::: moniker range="vs-2017"

É possível usar a caixa de diálogo **Ferramentas** > **Extensões e Atualizações** para executar estas tarefas relacionadas a amostras:

::: moniker-end

::: moniker range=">=vs-2019"

É possível usar a caixa de diálogo **Extensões** > **Gerenciar Extensões** para executar estas tarefas relacionadas a amostras:

::: moniker-end

- Listar as cópias mestras dos exemplos que você instalou.

- Desabilitar ou desinstalar a cópia mestra de um exemplo.

- Instale os Pacotes de Exemplos, que são coleções de exemplos que se relacionam a uma tecnologia ou um recurso.

- Instalar exemplos online individuais.

- Exibir notificações de atualização quando as alterações do código-fonte são publicadas para exemplos instalados.

- Atualize a cópia mestra de uma amostra instalada quando houver uma notificação de atualização.

## <a name="see-also"></a>Confira também

- [Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [SDK do Visual Studio](../extensibility/visual-studio-sdk.md)
