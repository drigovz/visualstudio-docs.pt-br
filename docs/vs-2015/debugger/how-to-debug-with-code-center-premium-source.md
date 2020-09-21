---
title: 'Como: Depurar com fonte do Code Center Premium | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db9a3e08e14e7fadca6df9e32361c0b042f565e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838304"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Como depurar com a origem do Code Center Premium
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Com o depurador do [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], você pode depurar a origem compartilhada segura do Microsoft MSDN Code Center Premium.  
  
 Este tópico explica como configurar e depurar o código-fonte superior do Code Center Premium no Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Para preparar para depurar com o Code Center Premium  
  
1. Conecte seu leitor de cartão inteligente e insira o cartão obtido da Shared Source Initiative.  
  
2. Inicie o Visual Studio.  
  
3. No menu **Ferramentas** , clique em **Opções**.  
  
4. Na caixa de diálogo **Opções** , abra o nó **depuração** e clique em **geral**.  
  
5. Desmarque a caixa de seleção **habilitar apenas meu código (somente gerenciado)** .  
  
6. Selecione **habilitar suporte ao servidor de origem**.  
  
7. Desmarque **exigir que os arquivos de origem correspondam exatamente à versão original**.  
  
8. No nó **depuração** , clique em **símbolos**.  
  
9. Na caixa de **localização do arquivo de símbolo (. pdb)** , desmarque a caixa de seleção **símbolos de servidor da Microsoft** e adicione os seguintes locais:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Certifique-se de incluir a barra à direita <strong>/</strong> no final do caminho.  
  
     Mova esses locais até a parte superior da lista para garantir que os símbolos sejam carregados primeiro.  
  
   > [!NOTE]
   > Esses locais do Code Center Premium devem ser listados primeiro para que sejam os primeiros locais a serem carregados. No Visual Studio 2010, você não pode mover nenhum servidor acima da entrada **servidores de símbolo da Microsoft** , motivo pelo qual você deve desmarcar a caixa de seleção.  
   > 
   >  Para carregar símbolos dos símbolos Microsoft durante uma sessão de depuração, faça isso:  
   > 
   > 1. No menu **depurar** , escolha **Windows** e, em seguida, escolha **módulos**.  
   >    2.  Selecione o módulo para o qual você deseja símbolos e abra o menu de atalho. Escolha **carregar símbolos de** e, em seguida, escolha **servidores de símbolos da Microsoft**.  
  
10. Na caixa **símbolos de cache dos servidores de símbolo neste diretório** , insira um local, como `C:\symbols` onde o Code Center Premium pode armazenar em cache os símbolos. O armazenamento em cache dos símbolos pode melhorar significativamente o desempenho durante a depuração.  
  
     Se você tiver dificuldade para depurar código-fonte com o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] depois de concluir este procedimento, verifique o local do cache para arquivos previamente armazenados em cache e arquivos de símbolo desatualizados. Remova os arquivos antigos desatualizados.  
  
11. Clique em **OK**.  
  
12. Reinicie o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para assegurar que as configurações persistiram.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Para depurar seu código-fonte usando Anexar ao Processo  
  
1. Conecte seu leitor de cartão inteligente e insira o cartão obtido da Shared Source Initiative.  
  
2. Inicie o Visual Studio.  
  
3. Abra seu projeto do Visual Studio.  
  
4. No menu **ferramentas** , clique em **anexar ao processo**.  
  
5. Na caixa de diálogo **anexar ao processo** , clique em **selecionar**.  
  
6. Na caixa de diálogo **Selecionar tipo de código** , **em detectar esses tipos de código**, selecione **nativo**, **gerenciado**e **gerenciado (v 4.0)**.  
  
7. Clique em **OK** para ignorar a caixa de diálogo **Selecionar tipo de código** .  
  
8. Na caixa **processos disponíveis** , selecione o processo que você deseja depurar.  
  
9. Clique em **Anexar**.  
  
10. Quando for solicitado a confirmar seu certificado, clique em **OK**. Em seguida, insira seu PIN. Aceite os termos de uso do Code Center Premium, se for solicitado.  
  
     O download de símbolos pode demorar muito tempo, dependendo da velocidade da rede. A barra de status indica quando todos os símbolos foram baixados com êxito.  
  
11. Repita as etapas de anexação para todos os projetos gerenciados em sua solução.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Para depurar o código-fonte de uma solução existente  
  
1. No **Gerenciador de soluções**, abra o menu de atalho da solução e escolha **Propriedades**.  
  
2. Na caixa de diálogo páginas de propriedades da solução, escolha **depurar arquivos de origem** no nó **Propriedades comuns** .  
  
3. Adicione o seguinte local aos **diretórios que contêm** a lista de arquivos de origem:  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Certifique-se de incluir a barra à direita <strong>/</strong> no final do caminho.  
  
4. Para cada projeto gerenciado na sua solução, faça o seguinte  
  
   1. No Gerenciador de Soluções, abra o menu de atalho do projeto e, em seguida, escolha **Propriedades**.  
  
   2. Selecione **depurar** e, em seguida, escolha **Habilitar depuração de código não-gerenciada**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Para depurar sua solução com código do Code Center Premium  
  
1. Na sua classe `Package`, defina um ponto de interrupção no construtor do pacote.  
  
2. No `Debug` menu, clique em **Iniciar Depuração**.  
  
3. Quando você atingir o ponto de interrupção no construtor do pacote, vá para a janela **pilha de chamadas** e clique com o botão direito do mouse no registro de ativação do assembly do qual você deseja carregar símbolos e clique em **carregar símbolos**.  
  
     Clique duas vezes no quadro de chamada para carregar a origem.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Para procurar o código-fonte no Code Center Premium  
  
1. Conecte seu leitor de cartão inteligente e insira o cartão obtido da Shared Source Initiative.  
  
2. Inicie o Internet Explorer e insira esta URL: `https://codepremium.msdn.microsoft.com`  
  
3. Navegue para encontrar a fonte que você deseja.  
  
## <a name="see-also"></a>Consulte Também  
 [Configurações e preparação do depurador](../debugger/debugger-settings-and-preparation.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Code Center Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
