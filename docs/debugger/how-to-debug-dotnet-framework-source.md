---
title: Depurar origem de .NET Framework | Microsoft Docs
Description: Saiba como depurar .NET Framework origem. Você deve configurar para ele e baixar símbolos de depuração.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 890aeef41a9a0f4d893cfcf57d42b78ff32d88c4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846875"
---
# <a name="how-to-debug-net-framework-source"></a>Como depurar o código-fonte do .NET Framework

Para depurar .NET Framework origem, você deve:

- Habilite a depuração na fonte .NET Framework.

- Ter acesso a símbolos de depuração para o código.

  Você pode optar por baixar símbolos de depuração imediatamente ou definir opções para download posterior. Se você não baixar símbolos imediatamente, eles serão baixados na próxima vez que você iniciar a depuração do aplicativo. Durante a depuração, você também pode usar os **módulos** ou janelas de **pilha de chamadas** para baixar e carregar símbolos.

### <a name="to-enable-stepping-into-net-framework-source"></a>Para habilitar a depuração na fonte .NET Framework

1. Em **ferramentas** (ou **depurar**) > **Opções**  >  **depuração**  >  **geral**, selecione **Habilitar depuração de fonte de .NET Framework**.

   - Se Apenas Meu Código tiver sido habilitado, uma caixa de diálogo de aviso mostrará que Apenas Meu Código está desabilitado agora. Selecione **OK**.

   - Se você não tiver um conjunto de cache de símbolos local, uma caixa de diálogo de aviso indicará que um cache de símbolos padrão foi definido. Selecione **OK**.

1. Selecione **OK** para fechar a caixa de diálogo **Opções** .

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Para definir ou alterar os locais de origem do símbolo e o comportamento do carregamento

1. Selecione a categoria **símbolos** em **ferramentas** (ou **depurar**) >   >  **depuração** de opções.

1. Na página **símbolos** , em **locais de arquivo de símbolo (. pdb)**, selecione **servidores de símbolos da Microsoft** para acessar símbolos dos servidores de símbolos públicos da Microsoft. Selecione os botões da barra de ferramentas para adicionar outros locais de símbolo e alterar a ordem de carregamento.

1. Para alterar o cache de símbolos local, edite ou navegue para um local diferente em **símbolos de cache neste diretório**.

1. Para baixar símbolos imediatamente, selecione **carregar todos os símbolos**. Esse botão está disponível somente durante a depuração.

   Se você não baixar símbolos agora, eles serão baixados na próxima vez que você iniciar a depuração.

1. Selecione **OK** para fechar a caixa de diálogo **Opções** .

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Para carregar símbolos de módulos ou janelas de pilha de chamadas

1. Durante a depuração, abra a janela selecionando **depurar**  >    >  **módulos** do Windows (ou pressione **Ctrl + Alt + U**) ou **depurar**  >    >  **pilha de chamadas** do Windows (**Ctrl + Alt + C**).

1. Clique com o botão direito do mouse em um módulo para o qual os símbolos não foram carregados. Na janela **módulos** , o status de carregamento de símbolos está na coluna **status de símbolos** . Na janela **pilha de chamadas** , status está na coluna **status do quadro** e o quadro está esmaecido.

   - Selecione **carregar símbolos** no menu para localizar e carregar arquivos de símbolo de uma pasta em seu computador.

   - Selecione **informações de carregamento de símbolo** para mostrar os locais para os quais o depurador pesquisou os símbolos.

   - Selecione **configurações de símbolo** para abrir a página **símbolos** . Na página **símbolos** , em **locais de arquivo de símbolo (. pdb)**, selecione **servidores de símbolos da Microsoft** para acessar símbolos dos servidores de símbolos públicos da Microsoft. Selecione os botões da barra de ferramentas para adicionar outros locais de símbolo e alterar a ordem de carregamento. Selecione **OK** para fechar a caixa de diálogo.

### <a name="see-also"></a>Confira também
- [Depuração de código gerenciado](../debugger/debugging-managed-code.md)
- [Especificar o símbolo (. pdb) e os arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)