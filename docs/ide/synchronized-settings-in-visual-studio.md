---
title: Sincronizar as configurações
ms.date: 12/10/2018
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b5f3eec072988c7ab093f305cf2903ae1079cc2
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57221873"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Sincronizar as configurações do Visual Studio em vários computadores

Quando você entra no Visual Studio em vários computadores usando a mesma conta de personalização, as configurações podem ser sincronizadas nos computadores.

## <a name="synchronized-settings"></a>Configurações sincronizadas

Por padrão, as seguintes configurações são sincronizadas:

- Configurações de desenvolvimento. Você seleciona uma coleção de configurações na primeira vez que abrir o Visual Studio, mas pode alterar a seleção a qualquer momento. Para obter mais informações, confira [Configurações do ambiente](../ide/environment-settings.md).

- Alias de comando definidos pelo usuário. Para saber mais sobre como definir aliases de comando, veja [Aliases de comando do Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Layouts de janela definidos pelo usuário na página **Janela** > **Gerenciar Layouts de Janela**.

- As seguintes opções nas páginas **Ferramentas** > **Opções**:

   - Configurações de tema e de uso de maiúsculas na barra de menus, na página de opções **Ambiente** > **Geral**.

   - Todas as configurações da página de opções **Ambiente** > **Fontes e Cores**.

   - Todos os atalhos de teclado da página de opções **Ambiente** > **Teclado**.

   - Todas as configurações da página de opções **Ambiente** > **Guias e Janelas**.

   - Todas as configurações da página de opções **Ambiente** > **Inicialização**.

   - Todas as configurações das páginas de opções **Editor de Texto**.

   - Todas as configurações das páginas de opções **Designer XAML**.

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Desligar configurações sincronizadas em um computador específico

As configurações sincronizadas para o Visual Studio são ativadas por padrão. Desligue as configurações sincronizadas em um computador acessando a página **Ferramentas** > **Opções** > **Ambiente** > **Contas** e desmarcando a opção **Sincronizar as configurações em dispositivos quando estiver conectado ao Visual Studio**.

Por exemplo, se você optar por não sincronizar as configurações do Visual Studio no computador "A", as alterações de configuração feitas no computador "A" não serão exibidas nos computadores "B" ou "C". Os computadores "B" e "C" continuarão sendo sincronizados um com o outro, mas não com o computador "A".

> [!NOTE]
> Caso você opte por não sincronizar as configurações desmarcando a opção na página **Ferramentas** > **Opções** > **Ambiente** > **Contas**, outras versões ou edições do Visual Studio existentes no mesmo computador não serão afetadas. Essas instalações lado a lado do Visual Studio continuarão sincronizando as configurações (a menos que você desmarque a opção nelas também).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Sincronizar configurações em edições e produtos da família Visual Studio

As configurações são sincronizadas em todas as versões e edições do Visual Studio instaladas *lado a lado*. As configurações também são sincronizadas em todos os produtos da família Visual Studio, incluindo o Blend para Visual Studio. No entanto, um produto individual da família pode ter suas próprias configurações que não são compartilhadas com o Visual Studio. Por exemplo, as configurações específicas do Blend para Visual Studio no computador "A" não são compartilhadas com o Visual Studio nos computadores "A" ou "B".

## <a name="side-by-side-synchronized-settings"></a>Configurações sincronizadas lado a lado

::: moniker range="vs-2017"

Algumas configurações, como o layout da janela de ferramentas, não são compartilhadas entre diferentes instalações lado a lado do Visual Studio. O arquivo *CurrentSettings.vssettings* em *%userprofile%\Documents\Visual Studio 2017\Settings* é uma pasta específica à instalação semelhante a *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Para usar as novas configurações específicas à instalação, faça uma nova instalação. Quando você atualiza uma instalação existente do Visual Studio, ela usa a localização compartilhada existente.

Se você tiver instalações lado a lado do Visual Studio e desejar usar a localização de arquivo das novas configurações específicas da instalação, siga estas etapas:

1. Atualizar para o Visual Studio 2017 versão 15.3 ou posterior.

2. Use o assistente de **configurações de Importação\Exportação** para exportar todas as configurações existentes para um local fora da pasta *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx*.

3. Abra o **Prompt de Comando do Desenvolvedor para VS 2017** e execute `devenv /resetuserdata`.

1. Inicie o Visual Studio e importe as configurações salvas do arquivo de configurações exportado.

::: moniker-end

::: moniker range=">=vs-2019"

Algumas configurações, como o layout da janela de ferramentas, não são compartilhadas entre diferentes instalações lado a lado do Visual Studio. O arquivo *CurrentSettings.vssettings* em *%userprofile%\Documents\Visual Studio 2019\Settings* é uma pasta específica da instalação semelhante a *%localappdata%\Microsoft\VisualStudio\16.0_xxxxxxxx\Settings*.

::: moniker-end

## <a name="see-also"></a>Consulte também

- [Personalizar o IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Configurações do ambiente](../ide/environment-settings.md)
- [Caixa de diálogo Ambiente > Opções de Contas](reference/accounts-environment-options-dialog-box.md)
